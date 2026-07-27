---
name: Pull historical MISO market prices
description: Retrieve settled day-ahead and real-time locational marginal prices by Commercial Pricing Node, and ancillary services clearing prices by reserve zone, from the keyed MISO Data Exchange Pricing API — including how to get a key, page a full market day, and stay inside the quota.
api: openapi/miso-data-exchange-pricing-api-openapi.json
base_url: https://apim.misoenergy.org/pricing
auth: apiKey (Ocp-Apim-Subscription-Key)
operations:
  - get-v1-aggregated-pnode
  - get-v1-day-ahead-date-lmp-expost
  - get-v1-day-ahead-date-lmp-exante
  - get-v1-real-time-date-lmp-expost
  - get-v1-day-ahead-date-asm-expost
  - get-v1-real-time-date-asm-summary
generated: '2026-07-27'
method: generated
source: openapi/miso-data-exchange-pricing-api-openapi.json
---

# Pull historical MISO market prices

This is the keyed half of MISO's data programme. Unlike the Public API it needs a credential —
but the credential is free, self-serve and issued without an approval step, so treat getting
one as a setup task, not a business-development negotiation.

## Before you start

1. Create a profile on the MISO public website, then create a MISO Data Exchange account at
   `https://data-exchange.misoenergy.org/`.
2. Subscribe to the **Pricing API** product. MISO's own product metadata returns
   `approvalRequired: false` — the key is issued immediately.
3. Send the key on every request:
   - Header (preferred): `Ocp-Apim-Subscription-Key: <key>`
   - Or query parameter: `?subscription-key=<key>`
4. Keys do not expire. The MISO account behind them requires a password reset every 12 months.

**Watch this trap:** every operation declares its 401 as *"Invalid or missing Bearer Token in
the Authorization header"*. That description is wrong — it is leftover template text. There is
no bearer token and no OAuth anywhere in this API. The live gateway message is
`{"statusCode": 401, "message": "Access denied due to missing subscription key"}`. Send the
subscription key, not an `Authorization` header.

## Steps

1. **Resolve the nodes you care about.** `get-v1-aggregated-pnode` —
   `GET /v1/aggregated-pnode`. The only operation in this API that is not date-pathed. Cache
   the result; it is reference data that changes rarely, and re-fetching it burns quota.

2. **Pull settled day-ahead prices.** `get-v1-day-ahead-date-lmp-expost` —
   `GET /v1/day-ahead/{date}/lmp-expost` where `{date}` is `yyyy-mm-dd`. Optional query filters:
   `node` (a single Commercial Pricing Node such as `ALTW.WELLS1`), `interval` (for example
   `"13"` or `"13:05"`, Eastern Standard Time), and `pageNumber`.
   - Each record carries `lmp` plus its three components: `mec` (marginal energy), `mcc`
     (marginal congestion) and `mlc` (marginal losses). They sum back to `lmp` — use that as a
     validation check on any transformation you apply.
   - `timeInterval` carries `resolution`, `start`, `end` and `value`.

3. **Page the whole market day.** Responses are `{data: [...], page: {...}}`. Start at
   `pageNumber=1` and increment until `page.lastPage` is `true`.
   - **Page size is fixed.** MISO states plainly: *"The page size cannot be changed at this
     time."* There is no `pageSize` parameter to raise.
   - **Date ranges are not supported.** *"this feature is not available at this time."* One
     market date per call; loop dates yourself.

4. **Budget the calls before you start looping.** Limits are per subscription:
   - 100 calls/minute → exceeding returns **HTTP 429**.
   - 24,000 calls/day → exceeding returns **HTTP 403**.
   - Neither code is declared in the OpenAPI, so a generated client will not handle them. Add
     the handling yourself: on 429 back off at least 60 seconds (there is no `Retry-After`
     header), on 403 stop until the next day.
   - Filter with `node` wherever you can. Pulling one node instead of the full node set is the
     single biggest quota saving available.

5. **Add the other price series as needed.**
   - `get-v1-day-ahead-date-lmp-exante` — `GET /v1/day-ahead/{date}/lmp-exante`, available at
     2pm EST the day before.
   - `get-v1-real-time-date-lmp-expost` — `GET /v1/real-time/{date}/lmp-expost`.
   - `get-v1-day-ahead-date-asm-expost` — `GET /v1/day-ahead/{date}/asm-expost` for ancillary
     services clearing prices by reserve zone.
   - `get-v1-real-time-date-asm-summary` — `GET /v1/real-time/{date}/asm-summary`.

## Timing and correctness

- Day-ahead data refreshes at approximately **6:45 PM GMT**; real-time at approximately
  **8:45 AM GMT**. Requesting a date before its refresh returns **404 "Date not found"** — that
  is a timing answer, not an error to retry aggressively.
- A malformed `{date}` returns **400 "Invalid date format"**. Format as `yyyy-mm-dd`.
- Distinguish the two 404s: `{"statusCode": 404, "message": "Resource not found"}` is the
  gateway saying your *path* is wrong; a bare 404 on a valid operation is MISO saying that
  *date* has no data.
- Every interval is Eastern Standard Time (UTC−05:00) year-round.

## Cross-references

`authentication/miso-authentication.yml` · `conventions/miso-conventions.yml` ·
`errors/miso-problem-types.yml` · `rate-limits/miso-rate-limits.yml` ·
`data-model/miso-data-model.yml`
