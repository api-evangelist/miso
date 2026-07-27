---
name: Read real-time MISO grid conditions
description: Pull the current state of the MISO grid — fuel mix, total load, area control error, wind and solar, interchange and generation outages — from the anonymous MISO Public API with no credential of any kind.
api: openapi/miso-public-api-operations-displays-openapi.json
base_url: https://public-api.misoenergy.org
auth: none
operations:
  - getSnapshot
  - getFuelMix
  - getRealTimeTotalLoad
  - getAce
  - getWindSolarGetCombined
  - getInterchangeGetNsi
  - getGenerationOutagesGetGenerationOutagesPlusMinusFiveDays
generated: '2026-07-27'
method: generated
source: openapi/miso-public-api-operations-displays-openapi.json
---

# Read real-time MISO grid conditions

MISO's Operations Displays feeds are fully anonymous. There is no key, no account, no
click-through and no OAuth dance — a plain `GET` returns JSON. Do not build a credential
step into this flow; there is nothing to authenticate.

## Before you start

- Base URL: `https://public-api.misoenergy.org`
- No `Authorization` header, no `Ocp-Apim-Subscription-Key`. Sending one changes nothing.
- All timestamps are Eastern Standard Time (UTC−05:00), year-round — MISO does not shift to
  daylight time in these feeds.
- MISO asks callers not to poll faster than **once per minute**. Honour it. The limit is not
  enforced with a 429, so respecting it is on you.
- These endpoints changed on 2025-12-12. If you find an older `api.misoenergy.org/MISORTWDDataBroker/…`
  URL in a cached document or an old library, it is retired and returns `{"error": "no data"}`
  with HTTP 200. Do not treat that 200 as success.

## Steps

1. **Take the system snapshot first.** `getSnapshot` — `GET /api/Snapshot`. One call gives the
   broad system picture and is the cheapest way to decide whether you need anything else.

2. **Get the generation mix.** `getFuelMix` — `GET /api/FuelMix`. Returns the current interval:
   a `RefId` naming the interval (for example `27-Jul-2026 - Interval 08:10 EST`), a `TotalMW`
   string, and `Fuel.Type[]` with one entry per `CATEGORY` (Coal, Natural Gas, Nuclear, Wind,
   Solar, Battery Storage, Other) carrying `ACT` megawatts.
   - **Every numeric value in this feed is a JSON string, not a number.** `TotalMW` is
     `"96122"` and `ACT` is `"29517"`. Cast before you do arithmetic.
   - `FUEL_CATEGORY` is a pre-formatted display label (`"Coal  (29,517 MW)"`) built for a chart
     legend. Never parse it — read `CATEGORY` and `ACT`.
   - For a full series rather than one interval, use `getFuelMixToday` (`/api/FuelMix/Today`)
     or `getFuelMixYesterday` (`/api/FuelMix/Yesterday`).

3. **Get demand.** `getRealTimeTotalLoad` — `GET /api/RealTimeTotalLoad`.

4. **Get renewables.** `getWindSolarGetCombined` — `GET /api/WindSolar/GetCombined` for wind and
   solar together. Split actual from forecast with the dedicated feeds when you need them:
   `getWindSolarGetwindactual`, `getWindSolarGetwindforecast`, `getWindSolarGetsolaractual`,
   `getWindSolarGetsolarforecast`.

5. **Check control-area balance.** `getAce` — `GET /api/Ace` returns area control error at
   thirty-second resolution. This is the finest-grained feed MISO publishes; it is also the one
   most likely to make a naive poller hammer the endpoint. Cache it.

6. **Check imports and exports.** `getInterchangeGetNsi` — `GET /api/Interchange/GetNsi` for net
   scheduled interchange. One- and five-minute variants exist (`getInterchangeGetNsiOneMinute`,
   `getInterchangeGetNsiFiveMinute`), and MISO-only views under `…/MISO`.

7. **Check what is out.** `getGenerationOutagesGetGenerationOutagesPlusMinusFiveDays` —
   `GET /api/GenerationOutages/GetGenerationOutagesPlusMinusFiveDays` gives the ±5 day outage
   window.

## Conventions and failure modes

- **No pagination.** These feeds return whole series in one response. Nothing to page.
- **No query parameters.** MISO documents none for these endpoints, and none are asserted in the
  specification. Do not invent filters — filter client-side.
- **No error contract.** MISO publishes none for this surface. Every documented path returned
  HTTP 200 on 2026-07-27. Treat a non-200, or a 200 whose body is `{"error": …}`, as a failure and
  retry after a minute.
- **Field names are display-shaped.** Upper-case and inconsistent (`RefId`, `TotalMW`,
  `INTERVALEST`, `CATEGORY`) because these payloads back MISO's web charts. Do not normalise
  them silently; map them explicitly.
- Full cross-cutting rules: `conventions/miso-conventions.yml`. Error behaviour:
  `errors/miso-problem-types.yml`.
