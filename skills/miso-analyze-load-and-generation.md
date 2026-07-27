---
name: Analyze MISO load, generation and interchange
description: Build a demand-and-supply picture for any MISO market day — actual load, generation by fuel type, fuel-on-the-margin, the medium-term load forecast and net interchange — from the keyed MISO Data Exchange Load, Generation and Interchange API.
api: openapi/miso-data-exchange-load-generation-interchange-api-openapi.json
base_url: https://apim.misoenergy.org/lgi
auth: apiKey (Ocp-Apim-Subscription-Key)
operations:
  - get-v1-real-time-date-demand-actual
  - get-v1-real-time-date-generation-fuel-type
  - get-v1-real-time-date-generation-fuel-on-the-margin
  - get-v1-forecast-date-load
  - get-v1-real-time-date-interchange-net-actual
  - get-v1-day-ahead-date-demand
  - get-v1-real-time-date-outage
generated: '2026-07-27'
method: generated
source: openapi/miso-data-exchange-load-generation-interchange-api-openapi.json
---

# Analyze MISO load, generation and interchange

The system-data half of MISO Data Exchange: 22 date-pathed operations covering what was
demanded, what was generated, what was on the margin, what was forecast and what crossed the
Balancing Authority boundaries.

## Before you start

- Subscribe to the **Load, Generation, and Interchange API** product at
  `https://data-exchange.misoenergy.org/`. Free, self-serve, `approvalRequired: false`.
- Send `Ocp-Apim-Subscription-Key: <key>` on every request (or `?subscription-key=<key>`).
- The Pricing API and this API are **separate subscriptions with separate keys and separate
  quotas**. Do not assume one key works on both paths.
- Every operation is `GET /v1/{market}/{yyyy-mm-dd}/...` where `{market}` is `real-time`,
  `day-ahead`, `forecast` or `historical`.

## Steps

1. **Get actual demand.** `get-v1-real-time-date-demand-actual` —
   `GET /v1/real-time/{date}/demand/actual`. Richest filter set in the API:
   `geoResolution`, `localResourceZone`, `region`, `interval`, `timeResolution`, `pageNumber`.
   Set `timeResolution` deliberately — hourly versus five-minute changes the row count by more
   than an order of magnitude, and therefore changes how much of your quota the pull costs.

2. **Get generation by fuel.** `get-v1-real-time-date-generation-fuel-type` —
   `GET /v1/real-time/{date}/generation/fuel-type`. Filters: `interval`, `region`, `pageNumber`.
   Pair with `get-v1-day-ahead-date-generation-fuel-type` when you want cleared versus actual.

3. **Get what set the price.** `get-v1-real-time-date-generation-fuel-on-the-margin` —
   `GET /v1/real-time/{date}/generation/fuel-on-the-margin`, filterable by `fuelType`, `region`
   and `interval`. This is the operation that turns a price series into an explanation: the
   marginal fuel is why the LMP is where it is. Join it to the Pricing API's ex-post LMP on
   (date, interval, region).

4. **Get the forecast.** `get-v1-forecast-date-load` — `GET /v1/forecast/{date}/load` is the
   medium-term load forecast, filterable by `init`, `localResourceZone`, `region`, `interval`
   and `timeResolution`. The `init` parameter selects which forecast vintage you want — a
   forecast is only meaningful alongside the moment it was issued, so record `init` with every
   value you store.

5. **Get interchange — and handle the revision window.**
   `get-v1-real-time-date-interchange-net-actual` —
   `GET /v1/real-time/{date}/interchange/net-actual`, filterable by `adjacentBa` and `interval`.
   - **MISO's own warning, verbatim:** *"Data available within the interchange endpoints are
     subject to change up to 105 days after the market day due to reconciliation."*
   - Treat any interchange value less than 105 days old as provisional. If you cache it, stamp
     it provisional and re-pull after the window closes. Do not publish it as final.
   - For settled history use `get-v1-historical-date-interchange-net-scheduled` —
     `GET /v1/historical/{date}/interchange/net-scheduled`.

6. **Add supply-side context as needed.**
   - `get-v1-day-ahead-date-demand` — `GET /v1/day-ahead/{date}/demand` (cleared demand).
   - `get-v1-real-time-date-outage` — `GET /v1/real-time/{date}/outage`, and
     `get-v1-forecast-date-outage` for the forward view.
   - `get-v1-real-time-date-binding-constraint` — `GET /v1/real-time/{date}/binding-constraint`.
   - Offered generation at ECOMAX/ECOMIN via `get-v1-day-ahead-date-generation-offered-ecomax`,
     `…-ecomin`, and `get-v1-real-time-date-generation-committed-ecomax`.

## Paging, quota and failure modes

- Page with `pageNumber` until `page.lastPage` is `true`. Page size is fixed and cannot be
  changed; date ranges are not supported, so loop one market date at a time.
- 100 calls/minute → **429**. 24,000 calls/day → **403**. Neither is declared in the spec;
  handle both yourself. Back off at least 60 seconds on 429 — no `Retry-After` is published.
- **400** = malformed `{date}` (use `yyyy-mm-dd`). **404** = no data for that date, usually
  because the refresh has not run yet (day-ahead ~6:45 PM GMT, real-time ~8:45 AM GMT).
- **401** claims a missing bearer token; it means a missing subscription key.
- All intervals are Eastern Standard Time (UTC−05:00) year-round.

## Cross-references

`authentication/miso-authentication.yml` · `conventions/miso-conventions.yml` ·
`errors/miso-problem-types.yml` · `rate-limits/miso-rate-limits.yml` ·
`data-model/miso-data-model.yml`
