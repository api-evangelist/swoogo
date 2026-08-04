# Swoogo (swoogo)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Swoogo is an event management and event registration platform for building event websites, registration forms, agendas, session catalogs, speaker rosters, and badges across in-person, virtual, and hybrid events. Swoogo exposes a documented public REST API at `https://api.swoogo.com/api/v1` covering events, registrants, sessions, speakers, sponsors, tracks, packages, discount codes, transactions, organization-level contacts (CRM), call-for-speakers submissions, invitation lists, and webhooks - roughly 140 endpoints in all.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/swoogo/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/swoogo/refs/heads/main/apis.yml)

## Access Model

The Swoogo API documentation is public and readable without an account (developer portal at [developer.swoogo.com](https://developer.swoogo.com), full reference at [swoogo.readme.io](https://swoogo.readme.io/docs)), but **making live API calls requires a paid Swoogo subscription**. Swoogo has no free tier or free trial; it sells annual, team-based (per-user) subscriptions that include unlimited events and unlimited registrations. API credentials (a key and secret) are self-issued from inside the Swoogo app under **My Profile > API Credentials**.

Authentication uses the **OAuth2 client-credentials** grant:

1. URL-encode your API key and secret, join them with a colon (`key:secret`), and Base64-encode the result.
2. `POST https://api.swoogo.com/api/v1/oauth2/token` with an `Authorization: Basic <base64>` header, `Content-Type: application/x-www-form-urlencoded;charset=UTF-8`, and body `grant_type=client_credentials`.
3. Send the returned bearer token as `Authorization: Bearer <token>` on subsequent requests.

**Bearer tokens expire every 30 minutes** and must be re-requested.

The endpoint paths in this repository are grounded in Swoogo's published reference. Because live calls require paid credentials, the request/response schemas in the OpenAPI are **modeled** (illustrative) rather than exhaustively confirmed against live responses.

## Tags

- Event Management
- Event Registration
- Events
- Sessions
- Speakers
- Attendees
- SaaS

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Swoogo Events API

Create, list, retrieve, update, and clone events, and manage their custom fields, questions, folders, websites, and badges. The event is the top-level container under which registrants, sessions, speakers, and pages are organized.

- **Human URL:** [https://swoogo.readme.io/reference/get_events](https://swoogo.readme.io/reference/get_events)
- **Base URL:** `https://api.swoogo.com/api/v1`

#### Tags

- Events
- Event Management
- Fields

#### Properties

- [Documentation](https://swoogo.readme.io/docs)
- [API Reference](https://swoogo.readme.io/reference/get_events)
- [OpenAPI](openapi/swoogo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/swoogo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/swoogo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Swoogo Registrants API

Create, list, retrieve, and update registrants (attendees), check them in, email them, mint registrant tokens, add or remove them from groups, and register them for or waitlist them on sessions. Registrant types define the ticket/category structure.

- **Human URL:** [https://swoogo.readme.io/reference/get_registrants](https://swoogo.readme.io/reference/get_registrants)
- **Base URL:** `https://api.swoogo.com/api/v1`

#### Tags

- Registrants
- Registration
- Attendees
- Check-In

#### Properties

- [Documentation](https://swoogo.readme.io/docs)
- [API Reference](https://swoogo.readme.io/reference/get_registrants)
- [OpenAPI](openapi/swoogo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/swoogo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/swoogo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Swoogo Sessions API

Create, list, retrieve, update, and delete agenda sessions, plus manage session custom fields, locations, fees, attendance records, and QR/badge scans. Sessions can be grouped into tracks and priced individually.

- **Human URL:** [https://swoogo.readme.io/reference/get_sessions](https://swoogo.readme.io/reference/get_sessions)
- **Base URL:** `https://api.swoogo.com/api/v1`

#### Tags

- Sessions
- Agenda
- Tracks
- Attendance

#### Properties

- [Documentation](https://swoogo.readme.io/docs)
- [API Reference](https://swoogo.readme.io/reference/get_sessions)
- [OpenAPI](openapi/swoogo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/swoogo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/swoogo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Swoogo Speakers API

Create, list, retrieve, and delete speakers and assign them to sessions. Complements the Call for Speakers (CFS) surface, where submissions and reviews feed the speaker roster for an event.

- **Human URL:** [https://swoogo.readme.io/reference/get_speakers](https://swoogo.readme.io/reference/get_speakers)
- **Base URL:** `https://api.swoogo.com/api/v1`

#### Tags

- Speakers
- Sessions
- Call For Speakers

#### Properties

- [Documentation](https://swoogo.readme.io/docs)
- [API Reference](https://swoogo.readme.io/reference/get_speakers)
- [OpenAPI](openapi/swoogo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/swoogo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/swoogo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Swoogo Contacts API

Manage the organization-level contacts (CRM) that persist across events - create, list, retrieve, and update contacts, read contact fields, forget a contact for GDPR, and build invitation lists that target contacts for specific events.

- **Human URL:** [https://swoogo.readme.io/reference/get_contacts](https://swoogo.readme.io/reference/get_contacts)
- **Base URL:** `https://api.swoogo.com/api/v1`

#### Tags

- Contacts
- CRM
- Invitation Lists
- GDPR

#### Properties

- [Documentation](https://swoogo.readme.io/docs)
- [API Reference](https://swoogo.readme.io/reference/get_contacts)
- [OpenAPI](openapi/swoogo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/swoogo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/swoogo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Rate Limits

Swoogo uses a **credit-based** rate limit: 2000 credits per rolling 10-minute window. A "get all" list request costs 10 credits; retrieving a single record costs 1 credit. See [rate-limits/swoogo-rate-limits.yml](rate-limits/swoogo-rate-limits.yml).

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/swoogo)
- [Website](https://swoogo.events)
- [Developer Portal](https://developer.swoogo.com)
- [Documentation](https://swoogo.readme.io/docs)
- [Authentication](https://swoogo.readme.io/docs/authentication)
- [Sign Up / Pricing](https://swoogo.events/pricing)
- [Plans](plans/swoogo-plans-pricing.yml)
- [Rate Limits](rate-limits/swoogo-rate-limits.yml)
- [Fin Ops](finops/swoogo-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
