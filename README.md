# MISO (miso)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MISO — the Midcontinent Independent System Operator — is the not-for-profit Regional Transmission Organization that operates the electric grid and the wholesale electricity markets across fifteen US states and the Canadian province of Manitoba, serving a footprint of roughly forty-five million people from headquarters in Carmel, Indiana. Formed in 1998 and operating the region since December 2001, it is regulated by the Federal Energy Regulatory Commission, dispatches generation in real time, clears day-ahead and real-time energy and ancillary services markets, runs the ARR/FTR market and the generator interconnection queue, and plans the transmission system. It sits squarely in the middle of the value chain: it owns no generation, no wires and no retail customers, but it holds the market-wide operational data that every generator, transmission owner, load-serving entity and trader in the Midwest and the South depends on. Its API posture is the classic system operator split, and it is an unusually clean example of it. On the market side MISO is genuinely open — thirty-seven JSON endpoints at public-api.misoenergy.org return real-time fuel mix, load, prices, binding constraints and interchange to an anonymous GET with no key, no account and no click-through, and the full market report archive at docs.misoenergy.org downloads anonymously as CSV and XLSX. On the consumer side there is nothing to open: MISO is not a retail utility, holds no customer usage or billing data, and no energy-data mandate of any kind applies to it. Green Button is voluntary in the United States and is a distribution-utility standard; MISO publishes no Green Button, ESPI, or consumer data-sharing surface, and makes no claim to. Its newer MISO Data Exchange developer portal adds a keyed but self-serve tier over historical market report data, and its MUI 2.0 market interface is a genuinely closed, client-certificate-gated API for registered market participants only.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/miso/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/miso/refs/heads/main/apis.yml)

## Tags

- Energy
- United States
- Electricity
- Energy Markets
- Grid
- System Operator
- Market Operator
- Wholesale Power
- Open Energy Data
- Renewables
- Solar
- Demand Response
- Utilities

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### MISO Public API - Operations Displays

The anonymous half of MISO's data posture and the reason market_data_open is true. Twenty-six JSON endpoints publishing the source data behind MISO's public Operations Displays: area control error at thirty-second resolution, CSAT supply and demand, CSAT next-day short-term reserve requirement, the real-time fuel mix (current interval plus full today and yesterday series), real-time total load, the system snapshot, wind and solar actuals and forecasts, net actual and net scheduled interchange at one-minute and five-minute resolution both system-wide and per neighbouring balancing authority, regional directional transfer, and generation outages plus or minus five days. Verified anonymous on 2026-07-27 — every one of the twenty-six paths returned HTTP 200 with content-type application/json to a plain GET carrying no key, no cookie and no account. The current-interval fuel mix returned a real 96,122 MW total broken out by coal, natural gas, nuclear, wind, solar, battery storage and other. MISO restructured this surface on 2025-12-12, moving it to public-api.misoenergy.org and dropping CSV and XML in favour of JSON only; the older MISORTWDDataBroker endpoints on api.misoenergy.org are marked deprecated or retired and now return {"error": "no data"}. MISO publishes no OpenAPI here, so the specification in openapi/ was assembled from MISO's own published endpoint table plus the live payloads it served — see its x-provenance block.

- **Human URL:** [https://www.misoenergy.org/markets-and-operations/RTDataAPIs/](https://www.misoenergy.org/markets-and-operations/RTDataAPIs/)
- **Base URL:** `https://public-api.misoenergy.org`

#### Tags

- Open Data
- Grid
- Fuel Mix
- Load
- Interchange
- Wind
- Solar
- Outages
- Anonymous Access

#### Properties

- [OpenAPI](openapi/miso-public-api-operations-displays-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.misoenergy.org/markets-and-operations/RTDataAPIs/)
- [API Reference](https://public-api.misoenergy.org/)
- [Website](https://www.misoenergy.org/markets-and-operations/real-time--market-data/operations-displays/)

### MISO Public API - Markets Displays

Eleven JSON endpoints publishing the source data behind MISO's public Markets Displays: ancillary services market clearing prices for all eight reserve zones across regulation, spin, supplemental, short-term reserve and ramp; ex-ante locational marginal prices for the nine MISO hubs with loss and congestion components; the LMP consolidated table; real-time five-minute ex-post intervals for the current interval, the rolling current day and the previous day; real-time transmission, sub-regional power balance and reserve product binding constraints; coordinated transaction scheduling; and real-time RSG commitments. Verified anonymous on 2026-07-27 — all eleven paths returned HTTP 200 application/json with no key and no account, and the ex-ante LMP endpoint returned live prices for ARKANSAS.HUB, ILLINOIS.HUB, INDIANA.HUB, LOUISIANA.HUB, MICHIGAN.HUB, MINN.HUB, MS.HUB, SWPP and TEXAS.HUB. The previous-day and rolling ex-post interval feeds are large — 47 MB and 16 MB respectively — and are served without any pagination or authentication. MISO publishes no OpenAPI here; the specification in openapi/ was assembled from MISO's own published endpoint table plus the live payloads it served, with provenance recorded in the document.

- **Human URL:** [https://www.misoenergy.org/markets-and-operations/RTDataAPIs/](https://www.misoenergy.org/markets-and-operations/RTDataAPIs/)
- **Base URL:** `https://public-api.misoenergy.org`

#### Tags

- Open Data
- Energy Markets
- LMP
- Prices
- Ancillary Services
- Binding Constraints
- Anonymous Access

#### Properties

- [OpenAPI](openapi/miso-public-api-markets-displays-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://www.misoenergy.org/markets-and-operations/RTDataAPIs/)
- [API Reference](https://public-api.misoenergy.org/)
- [Website](https://www.misoenergy.org/markets-and-operations/real-time--market-data/markets-displays/)

### MISO Data Exchange Pricing API

The pricing half of MISO Data Exchange, MISO's Azure API Management developer programme over Market Report data. Ten documented GET operations covering day-ahead and real-time ex-ante and ex-post locational marginal prices by commercial pricing node, day-ahead and real-time ex-ante and ex-post ancillary services market clearing prices by reserve zone, a real-time MCP summary, and an aggregated pricing node reference list. Responses are paged and carry the four LMP components — lmp, mcc (marginal congestion), mec (marginal energy) and mlc (marginal losses). A subscription key is required: an anonymous GET to https://apim.misoenergy.org/pricing/v1/day-ahead/2026-07-26/lmp-expost returned HTTP 401 "Access denied due to missing subscription key" on 2026-07-27, while a fabricated path on the same gateway returned HTTP 404 "Resource not found" — which is what makes the 401 meaningful. The key is self-serve: MISO's own portal product metadata returns approvalRequired false. The full API reference, every operation definition and the component schemas were all readable anonymously from the portal's data API, and the OpenAPI in openapi/ was assembled verbatim from them.

- **Human URL:** [https://data-exchange.misoenergy.org/api-details#api=pricing-api](https://data-exchange.misoenergy.org/api-details#api=pricing-api)
- **Base URL:** `https://apim.misoenergy.org/pricing`

#### Tags

- Energy Markets
- LMP
- Prices
- Ancillary Services
- Day-Ahead
- Real-Time

#### Properties

- [OpenAPI](openapi/miso-data-exchange-pricing-api-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Developer Portal](https://data-exchange.misoenergy.org/)
- [API Reference](https://data-exchange.misoenergy.org/apis)
- [Documentation](https://help.misoenergy.org/knowledgebase/article/KA-01489/en-us)
- [Plans](https://data-exchange.misoenergy.org/products)

### MISO Data Exchange Load, Generation, and Interchange API

The system-data half of MISO Data Exchange. Twenty-two documented GET operations spanning actual load, day-ahead and real-time cleared demand, day-ahead cleared generation both physical and virtual, day-ahead and real-time generation by fuel type, offered and committed generation at ECOMAX and ECOMIN, fuel-on-the-margin, day-ahead, real-time and historical net scheduled interchange, real-time net actual interchange, real-time binding constraints, real-time and forecast outages, the medium-term load forecast, and state estimator load. MISO's own operation metadata carries the warning that interchange data is subject to change up to one hundred and five days after the market day due to reconciliation. Every operation is date-pathed (/v1/{market}/{yyyy-mm-dd}/...) with optional interval, region and paging filters. A subscription key is required — an anonymous GET to https://apim.misoenergy.org/lgi/v1/real-time/2026-07-26/demand/actual returned HTTP 401 "Access denied due to missing subscription key" on 2026-07-27 — and that key is self-serve with no approval step. The OpenAPI in openapi/ was assembled verbatim from MISO's anonymously served portal metadata.

- **Human URL:** [https://data-exchange.misoenergy.org/api-details#api=load-generation-and-interchange-api](https://data-exchange.misoenergy.org/api-details#api=load-generation-and-interchange-api)
- **Base URL:** `https://apim.misoenergy.org/lgi`

#### Tags

- Load
- Generation
- Interchange
- Demand Forecast
- Outages
- Fuel Mix
- Energy Markets

#### Properties

- [OpenAPI](openapi/miso-data-exchange-load-generation-interchange-api-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Developer Portal](https://data-exchange.misoenergy.org/)
- [API Reference](https://data-exchange.misoenergy.org/apis)
- [Documentation](https://help.misoenergy.org/knowledgebase/article/KA-01489/en-us)
- [Plans](https://data-exchange.misoenergy.org/products)

### MISO Market Reports

MISO's long-running bulk market report surface — the second fully anonymous layer of its open market data, and the archive the Data Exchange APIs sit on top of. Every published report is a plain HTTP GET against docs.misoenergy.org/marketreports/ with no key, no account, no login and no licence click-through, returning real CSV, XLSX, XML, ZIP and PDF files named by market date. Confirmed anonymous on 2026-07-27: 20260726_da_expost_lmp.csv returned HTTP 200 with 1,165,710 bytes of day-ahead ex-post LMP, 20260726_sr_gfm.xlsx returned HTTP 200 with 21,922 bytes, and Dead_Node_Reports_Readers_Guide.pdf returned HTTP 200. The report catalogue is browsed from the Market Reports page, which drives an internal Episerver Find search service — there is no documented query API, no directory listing (docs.misoenergy.org/marketreports/ itself returns HTTP 404) and no specification, so this is recorded as a verified public data surface rather than a specified API.

- **Human URL:** [https://www.misoenergy.org/markets-and-operations/real-time--market-data/market-reports/](https://www.misoenergy.org/markets-and-operations/real-time--market-data/market-reports/)
- **Base URL:** `https://docs.misoenergy.org/marketreports`

#### Tags

- Open Data
- CSV
- Market Reports
- Settlements
- Energy Markets
- Anonymous Access

#### Properties

- [Documentation](https://www.misoenergy.org/markets-and-operations/real-time--market-data/market-reports/)
- [Website](https://www.misoenergy.org/markets-and-operations/real-time--market-data/market-report-archives/)

### MISO Market User Interface (MUI) 2.0 API

The closed counterpart to everything else in this profile — MISO's programmatic JSON web API for registered market participants to submit energy supply offers and demand bids, query submissions, and query day-ahead and real-time market results as they clear. MISO documents it publicly in the MUI 2.0 API User Guide, which states verbatim that "All market participants using the JSON programmatic interface must be registered with MISO" and gives the base URL as https://markets.midwestiso.org/dart2 for production and https://cce.midwestiso.org/dart2 for the customer-facing test environment. Access is gated by a client digital certificate issued through the MISO Market Portal: an anonymous TLS connection to markets.midwestiso.org on 2026-07-27 failed at the handshake with an SSL alert rather than returning any HTTP status, which is direct evidence of mutual-TLS client-certificate enforcement. No OpenAPI is published and none could be harvested; the guide PDF is the only contract.

- **Human URL:** [https://cdn.misoenergy.org/MUI%202.0%20API%20User%20Guide629008.pdf](https://cdn.misoenergy.org/MUI%202.0%20API%20User%20Guide629008.pdf)
- **Base URL:** `https://markets.midwestiso.org/dart2`

#### Tags

- Energy Markets
- Market Participants
- Bids and Offers
- Day-Ahead
- Real-Time
- Client Certificate

#### Properties

- [Documentation](https://cdn.misoenergy.org/MUI%202.0%20API%20User%20Guide629008.pdf)
- [Onboarding](https://www.misoenergy.org/markets-and-operations/mp-registration/market-participation/)

## Common Properties

- [Website](https://www.misoenergy.org/)
- [Developer Portal](https://data-exchange.misoenergy.org/)
- [Documentation](https://www.misoenergy.org/markets-and-operations/RTDataAPIs/)
- [API Reference](https://public-api.misoenergy.org/)
- [Onboarding](https://help.misoenergy.org/knowledgebase/article/KA-01489/en-us)
- [Sign Up](https://www.misoenergy.org/account/create-profile/)
- [Sign In](https://data-exchange.misoenergy.org/signin)
- [Plans](https://data-exchange.misoenergy.org/products)
- [Terms of Service](https://www.misoenergy.org/meet-miso/legal-and-privacy/)
- [Support](https://help.misoenergy.org/)
- [Blog](https://www.misoenergy.org/meet-miso/media-center/miso-matters/)
- [LinkedIn](https://www.linkedin.com/company/midcontinent-iso/)
- [YouTube](https://www.youtube.com/user/MISOenergy)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
