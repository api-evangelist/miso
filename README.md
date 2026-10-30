# MISO

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

**Areas:** Energy · United States · Electricity · Energy Markets · Grid · System Operator · Market Operator · Wholesale Power · Open Energy Data · Renewables · Solar · Demand Response

## MISO on APIs.io

Everything profiled for MISO is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/miso/](https://apis.io/providers/miso/)** — or go straight to one of the APIs or properties below.

### APIs (38)

- [MISO Market Reports](https://apis.io/apis/miso/miso-market-reports/) — MISO's long-running bulk market report surface — the second fully anonymous layer of its open market data, and the archive the Data Exchange APIs sit on top…
- [MISO File Download API](https://apis.io/apis/miso/miso-file-download-api/) — The bulk file-retrieval counterpart to MUI 2.0, on the same two client-certificate-gated hosts and documented only in a PDF. MISO's File Download…
- [MISO FTR MPMA Market User API](https://apis.io/apis/miso/miso-ftr-mpma-market-user-api/) — The Financial Transmission Rights / Multi-Period Multi-Auction market user API — four SOAP services covering the FTR market itself, auctions, bulk download…
- [MISO EDR Service (Electronic Data Reporting)](https://apis.io/apis/miso/miso-edr-service/) — A SOAP service for uploading meter data and offer data to MISO, with a published WSDL and six XSD schemas (MdUploadPayload, MdUploadResponse, MeterData,…
- [MISO CROW API (Outage Scheduling)](https://apis.io/apis/miso/miso-crow-api/) — The outage-scheduling interface, built on the CROW product, documented in a PDF reference plus a MISO-specific addendum and shipped with worked XML request…
- [MISO Fuel and Consumables Data Request API](https://apis.io/apis/miso/miso-fuel-and-consumables-api/) — Data request API for fuel and consumables information, documented in a 171KB PDF API guide on MISO's CDN and nowhere else.
- [MISO Market Portal Meter Data and Settlement Statements API](https://apis.io/apis/miso/miso-meter-data-and-settlement-statements-api/) — Market Portal API for retrieving meter data and settlement statements, documented in a 1MB PDF on MISO's CDN. Sits alongside the File Download API in the…
- [MISO Ace API](https://apis.io/apis/miso/miso-ace-api/) — The Ace API from MISO — 1 operation(s) for ace.
- [MISO Admin API](https://apis.io/apis/miso/miso-admin-api/) — The Admin API from MISO — 6 operation(s) for admin.
- [MISO Aggregated Pnode API](https://apis.io/apis/miso/miso-aggregated-pnode-api/) — The Aggregated Pnode API from MISO — 1 operation(s) for aggregated pnode.
- [MISO Bidding API](https://apis.io/apis/miso/miso-bidding-api/) — The Bidding API from MISO — 2 operation(s) for bidding.
- [MISO Binding Constraints API](https://apis.io/apis/miso/miso-bindingconstraints-api/) — The BindingConstraints API from MISO — 3 operation(s) for bindingconstraints.
- [MISO Contracts API](https://apis.io/apis/miso/miso-contracts-api/) — The Contracts API from MISO — 4 operation(s) for contracts.
- [MISO Coordinated Transaction Scheduling API](https://apis.io/apis/miso/miso-coordinatedtransactionscheduling-api/) — The CoordinatedTransactionScheduling API from MISO — 1 operation(s) for coordinatedtransactionscheduling.
- [MISO Csat Next Day Short Term Reserve Requirement API](https://apis.io/apis/miso/miso-csatnextdayshorttermreserverequirement-api/) — The CsatNextDayShortTermReserveRequirement API from MISO — 1 operation(s) for csatnextdayshorttermreserverequirement.
- [MISO Csat Supply Demand API](https://apis.io/apis/miso/miso-csatsupplydemand-api/) — The CsatSupplyDemand API from MISO — 1 operation(s) for csatsupplydemand.
- [MISO Day Ahead API](https://apis.io/apis/miso/miso-day-ahead-api/) — The Day Ahead API from MISO — 11 operation(s) for day ahead.
- [MISO Forecast API](https://apis.io/apis/miso/miso-forecast-api/) — The Forecast API from MISO — 6 operation(s) for forecast.
- [MISO Fuel Mix API](https://apis.io/apis/miso/miso-fuelmix-api/) — The FuelMix API from MISO — 3 operation(s) for fuelmix.
- [MISO Generation Outages API](https://apis.io/apis/miso/miso-generationoutages-api/) — The GenerationOutages API from MISO — 1 operation(s) for generationoutages.
- [MISO Historical API](https://apis.io/apis/miso/miso-historical-api/) — The Historical API from MISO — 1 operation(s) for historical.
- [MISO IMM API](https://apis.io/apis/miso/miso-imm-api/) — The IMM API from MISO — 1 operation(s) for imm.
- [MISO Interchange API](https://apis.io/apis/miso/miso-interchange-api/) — The Interchange API from MISO — 9 operation(s) for interchange.
- [MISO Market Pricing API](https://apis.io/apis/miso/miso-marketpricing-api/) — The MarketPricing API from MISO — 6 operation(s) for marketpricing.
- [MISO Model API](https://apis.io/apis/miso/miso-model-api/) — The Model API from MISO — 1 operation(s) for model.
- [MISO Notifications API](https://apis.io/apis/miso/miso-notifications-api/) — The Notifications API from MISO — 6 operation(s) for notifications.
- [MISO Notifications Format API](https://apis.io/apis/miso/miso-notifications-format-api/) — The Notifications Format API from MISO — 7 operation(s) for notifications format.
- [MISO Offer API](https://apis.io/apis/miso/miso-offer-api/) — The Offer API from MISO — 7 operation(s) for offer.
- [MISO Real Time RSG Commitments API](https://apis.io/apis/miso/miso-realtimersgcommitments-api/) — The RealTimeRSGCommitments API from MISO — 1 operation(s) for realtimersgcommitments.
- [MISO Real Time Total Load API](https://apis.io/apis/miso/miso-realtimetotalload-api/) — The RealTimeTotalLoad API from MISO — 1 operation(s) for realtimetotalload.
- [MISO Regional Directional Transfer API](https://apis.io/apis/miso/miso-regionaldirectionaltransfer-api/) — The RegionalDirectionalTransfer API from MISO — 1 operation(s) for regionaldirectionaltransfer.
- [MISO Reports API](https://apis.io/apis/miso/miso-reports-api/) — The Reports API from MISO — 14 operation(s) for reports.
- [MISO Reserves API](https://apis.io/apis/miso/miso-reserves-api/) — The Reserves API from MISO — 6 operation(s) for reserves.
- [MISO Snapshot API](https://apis.io/apis/miso/miso-snapshot-api/) — The Snapshot API from MISO — 1 operation(s) for snapshot.
- [MISO Transactions API](https://apis.io/apis/miso/miso-transactions-api/) — The Transactions API from MISO — 5 operation(s) for transactions.
- [MISO Weather API](https://apis.io/apis/miso/miso-weather-api/) — The Weather API from MISO — 1 operation(s) for weather.
- [MISO Wind Solar API](https://apis.io/apis/miso/miso-windsolar-api/) — The WindSolar API from MISO — 7 operation(s) for windsolar.
- [MISO Realtime API](https://apis.io/apis/miso/miso-realtime-api/) — The Realtime API from MISO — 17 operation(s) for realtime.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [miso](https://apis.io/servers/miso/miso/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Miso Agentic Access](https://apis.io/agentic-access/miso/miso-agentic-access/)

#### Examples (63)

Example requests and responses.

- [Miso Data Exchange Lgi Get_V1_Day_Ahead_Date_Demand](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_day_ahead_date_demand/)
- [Miso Data Exchange Lgi Get_V1_Day_Ahead_Date_Generation_Cleared_Physical](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_day_ahead_date_generation_cleared_physical/)
- [Miso Data Exchange Lgi Get_V1_Day_Ahead_Date_Generation_Cleared_Virtual](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_day_ahead_date_generation_cleared_virtual/)
- [Miso Data Exchange Lgi Get_V1_Day_Ahead_Date_Generation_Fuel_Type](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_day_ahead_date_generation_fuel_type/)
- [Miso Data Exchange Lgi Get_V1_Day_Ahead_Date_Generation_Offered_Ecomax](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_day_ahead_date_generation_offered_ecomax/)
- [Miso Data Exchange Lgi Get_V1_Day_Ahead_Date_Generation_Offered_Ecomin](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_day_ahead_date_generation_offered_ecomin/)
- [Miso Data Exchange Lgi Get_V1_Day_Ahead_Date_Interchange_Net_Scheduled](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_day_ahead_date_interchange_net_scheduled/)
- [Miso Data Exchange Lgi Get_V1_Forecast_Date_Load](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_forecast_date_load/)
- [Miso Data Exchange Lgi Get_V1_Forecast_Date_Outage](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_forecast_date_outage/)
- [Miso Data Exchange Lgi Get_V1_Historical_Date_Interchange_Net_Scheduled](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_historical_date_interchange_net_scheduled/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Binding_Constraint](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_binding_constraint/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Demand_Forecast](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_demand_forecast/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Demand_Load_State_Estimator](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_demand_load_state_estimator/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Generation_Cleared_Supply](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_generation_cleared_supply/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Generation_Committed_Ecomax](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_generation_committed_ecomax/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Generation_Fuel_On_The_Margin](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_generation_fuel_on_the_margin/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Generation_Fuel_Type](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_generation_fuel_type/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Generation_Offered_Ecomax](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_generation_offered_ecomax/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Interchange_Net_Actual](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_interchange_net_actual/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Interchange_Net_Scheduled](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_interchange_net_scheduled/)
- [Miso Data Exchange Lgi Get_V1_Real_Time_Date_Outage](https://apis.io/examples/miso/miso-data-exchange-lgi-get_v1_real_time_date_outage/)
- [Miso Data Exchange Pricing Get_V1_Aggregated_Pnode](https://apis.io/examples/miso/miso-data-exchange-pricing-get_v1_aggregated_pnode/)
- [Miso Data Exchange Pricing Get_V1_Day_Ahead_Date_Asm_Exante](https://apis.io/examples/miso/miso-data-exchange-pricing-get_v1_day_ahead_date_asm_exante/)
- [Miso Data Exchange Pricing Get_V1_Day_Ahead_Date_Asm_Expost](https://apis.io/examples/miso/miso-data-exchange-pricing-get_v1_day_ahead_date_asm_expost/)
- [Miso Data Exchange Pricing Get_V1_Day_Ahead_Date_Lmp_Exante](https://apis.io/examples/miso/miso-data-exchange-pricing-get_v1_day_ahead_date_lmp_exante/)
- …and 38 more published on APIs.io

#### Collections (32)

Postman and Open Collection request collections.

- [MISO Public Ace API](https://apis.io/collections/miso/open-miso-ace-api/)
- [MUI - Public Specification Admin API](https://apis.io/collections/miso/open-miso-admin-api/)
- [Pricing Aggregated Pnode API](https://apis.io/collections/miso/open-miso-aggregated-pnode-api/)
- [MUI - Public Specification Bidding API](https://apis.io/collections/miso/open-miso-bidding-api/)
- [MISO Public Binding Constraints API](https://apis.io/collections/miso/open-miso-bindingconstraints-api/)
- [MUI - Public Specification Contracts API](https://apis.io/collections/miso/open-miso-contracts-api/)
- [MISO Public Coordinated Transaction Scheduling API](https://apis.io/collections/miso/open-miso-coordinatedtransactionscheduling-api/)
- [MISO Public Csat Next Day Short Term Reserve Requirement API](https://apis.io/collections/miso/open-miso-csatnextdayshorttermreserverequirement-api/)
- [MISO Public Csat Supply Demand API](https://apis.io/collections/miso/open-miso-csatsupplydemand-api/)
- [Miso Day Ahead API](https://apis.io/collections/miso/open-miso-day-ahead-api/)
- [Miso Forecast API](https://apis.io/collections/miso/open-miso-forecast-api/)
- [MISO Public Fuel Mix API](https://apis.io/collections/miso/open-miso-fuelmix-api/)
- [MISO Public Generation Outages API](https://apis.io/collections/miso/open-miso-generationoutages-api/)
- [Load, Generation, and Interchange Historical API](https://apis.io/collections/miso/open-miso-historical-api/)
- [MUI - Public Specification IMM API](https://apis.io/collections/miso/open-miso-imm-api/)
- [MISO Public Interchange API](https://apis.io/collections/miso/open-miso-interchange-api/)
- [MISO Public Market Pricing API](https://apis.io/collections/miso/open-miso-marketpricing-api/)
- [MUI - Public Specification Model API](https://apis.io/collections/miso/open-miso-model-api/)
- [API Collection](https://apis.io/collections/miso/open-miso-mui-provenance/)
- [MUI - Public Specification Notifications API](https://apis.io/collections/miso/open-miso-notifications-api/)
- [MUI - Public Specification Notifications Format API](https://apis.io/collections/miso/open-miso-notifications-format-api/)
- [MUI - Public Specification Offer API](https://apis.io/collections/miso/open-miso-offer-api/)
- [Miso Real Time API](https://apis.io/collections/miso/open-miso-real-time-api/)
- [MISO Public Real Time RSG Commitments API](https://apis.io/collections/miso/open-miso-realtimersgcommitments-api/)
- [MISO Public Real Time Total Load API](https://apis.io/collections/miso/open-miso-realtimetotalload-api/)
- …and 7 more published on APIs.io

#### Overlays (4)

OpenAPI overlays, including conversational phrasing for each operation.

- [Miso Data Exchange Lgi Overlay](https://apis.io/overlays/miso/miso-data-exchange-lgi-overlay/)
- [Miso Data Exchange Pricing Overlay](https://apis.io/overlays/miso/miso-data-exchange-pricing-overlay/)
- [Miso Public Api Markets Displays Overlay](https://apis.io/overlays/miso/miso-public-api-markets-displays-overlay/)
- [Miso Public Api Operations Displays Overlay](https://apis.io/overlays/miso/miso-public-api-operations-displays-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Miso Authentication](https://apis.io/security/miso/miso-authentication/)
- [Miso Domain Security](https://apis.io/security/miso/miso-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Miso Plans](https://apis.io/plans/miso/miso-plans/)

#### Rate limits (1)

Published request limits.

- [Miso Rate Limits](https://apis.io/rate-limits/miso/miso-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.misoenergy.org/)
- [Documentation](https://www.misoenergy.org/markets-and-operations/RTDataAPIs/)
- [Getting started](https://cdn.misoenergy.org/MISO%20Data%20Exchange%20User%20Guide674561.pdf)
- [API reference](https://public-api.misoenergy.org/)
- [Sign up](https://www.misoenergy.org/account/create-profile/)
- [Support](https://help.misoenergy.org/)
- [Blog](https://www.misoenergy.org/meet-miso/media-center/miso-matters/)
- [Terms of service](https://www.misoenergy.org/meet-miso/legal-and-privacy/)
- [Privacy policy](https://www.misoenergy.org/meet-miso/legal-and-privacy/)
- [Status](https://www.misoenergy.org/markets-and-operations/notifications/it-and-system-notifications/)

## API Evangelist rating

**Kin Score 49.3** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 69.6 |
| Contract quality | 28.8 |
| Contract governance | 4.5 |
| Operational transparency | 52.6 |
| Developer ergonomics | 66.1 |
| Access clarity | 65.8 |

**Agent readiness 33.5** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 27.0** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/miso/](https://apis.io/providers/miso/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for MISO: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/miso/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
