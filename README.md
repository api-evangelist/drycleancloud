# CleanCloud (drycleancloud)

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

CleanCloud is cloud-based point-of-sale (POS) and business management software for dry cleaners, laundromats, laundry services, and shoe repair businesses. It handles orders, garment tracking, customers, pickup and delivery routing, payments, inventory, marketing, and reporting. CleanCloud exposes a documented public REST API (base `https://cleancloudapp.com/api`) for programmatic access to customers, orders, garments, products, price lists, inventory, pickup and delivery scheduling, payments, subscriptions, invoices, promotions, and reporting, plus outbound Webhooks for order and customer events. API access is available on the Grow and Grow+ subscription tiers, authenticated with a per-account API token (the `api_token` field in the JSON request body) and metered at 50,000 requests per month (max 3 requests per second).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/drycleancloud/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/drycleancloud/refs/heads/main/apis.yml)

## Tags

- Dry Cleaning
- Laundry
- Point of Sale
- POS
- Field Service
- Pickup and Delivery
- SMB Software

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## API Overview

- **Base URL:** `https://cleancloudapp.com/api`
- **Protocol:** HTTPS REST; every endpoint is a `POST` with a JSON body and returns JSON.
- **Authentication:** Per-account API token passed as the `api_token` field in the request body (Settings > Admin > Pickup and Delivery > API).
- **Rate limits:** 50,000 requests/month, max 3 requests/second; additional 25,000-request bundles (~$15) available.
- **Access:** Grow and Grow+ subscription tiers (Pro in Mexico).

## APIs

### CleanCloud Customers API

Create, update, delete, retrieve, and authenticate customer accounts, trigger password-reset emails, and query customers by ID or a created/updated date range.

- **Human URL:** [https://cleancloudapp.com/api](https://cleancloudapp.com/api)
- **Base URL:** `https://cleancloudapp.com/api`
- Endpoints: `/addCustomer`, `/updateCustomer`, `/deleteCustomer`, `/getCustomer`, `/loginCustomer`, `/passwordCustomer`

### CleanCloud Orders API

Create, update, delete, and list orders, and manage the individual garments within an order (lookup by barcode, list per order, and update color, notes, location, or status).

- **Human URL:** [https://cleancloudapp.com/api](https://cleancloudapp.com/api)
- **Base URL:** `https://cleancloudapp.com/api`
- Endpoints: `/addOrder`, `/updateOrder`, `/deleteOrder`, `/getOrders`, `/getGarment`, `/getGarments`, `/updateGarment`

### CleanCloud Products & Inventory API

Retrieve the active product catalog (optionally including parent products and upcharges), all active price lists, and current inventory stock levels.

- **Human URL:** [https://cleancloudapp.com/api](https://cleancloudapp.com/api)
- **Base URL:** `https://cleancloudapp.com/api`
- Endpoints: `/getProducts`, `/getPriceLists`, `/getInventory`

### CleanCloud Pickup & Delivery API

Schedule and manage recurring pickups, resolve delivery routes from an address or coordinates, list available pickup/delivery dates and time slots, and fetch a driver's current location for an order.

- **Human URL:** [https://cleancloudapp.com/api](https://cleancloudapp.com/api)
- **Base URL:** `https://cleancloudapp.com/api`
- Endpoints: `/repeatPickup`, `/updateRepeatPickup`, `/deletePickup`, `/getPickups`, `/getDates`, `/getSlots`, `/getRoute`, `/driverLocation`

### CleanCloud Payments & Promotions API

List payments and invoices, save and charge payment cards (Stripe, Clearent, Amazon) and set a default card, manage recurring customer subscriptions, apply or validate promo/coupon codes, and convert loyalty points to account credit.

- **Human URL:** [https://cleancloudapp.com/api](https://cleancloudapp.com/api)
- **Base URL:** `https://cleancloudapp.com/api`
- Endpoints: `/getPayments`, `/getInvoices`, `/addCard`, `/chargeCard`, `/getCards`, `/setDefaultCard`, `/addSubscription`, `/deleteSubscription`, `/getSubscription`, `/usePromo`, `/convertLoyaltyPoints`

### CleanCloud Business & Reporting API

Retrieve business (commercial) account configurations, pull daily summary report metrics for a date range, fetch photos attached to an order, add a customer to a customer group, and get a customer's referral code and gift details. CleanCloud does not document a dedicated multi-store listing endpoint; business/location context is exposed through `/getBusinessAccounts`.

- **Human URL:** [https://cleancloudapp.com/api](https://cleancloudapp.com/api)
- **Base URL:** `https://cleancloudapp.com/api`
- Endpoints: `/getBusinessAccounts`, `/summaryReport`, `/getPhotos`, `/addToCustomerGroup`, `/getReferral`

### CleanCloud Messaging API

Send messages between a customer and a store and retrieve message history (with an optional result limit), plus register and remove Firebase push notification tokens for iOS and Android apps.

- **Human URL:** [https://cleancloudapp.com/api](https://cleancloudapp.com/api)
- **Base URL:** `https://cleancloudapp.com/api`
- Endpoints: `/addMessage`, `/getMessages`, `/addPushToken`, `/deletePushToken`

### CleanCloud Webhooks

Outbound webhooks that POST to a configured external URL when an event occurs. Configured under Settings > Admin > Pickup and Delivery > API > Webhooks. 10 events:

- `order.created` (In Store Orders)
- `order.created` (Pickup and Delivery Orders)
- `order.status_changed`
- `order.pickup_rescheduled`
- `order.delivery_rescheduled`
- `order.nothing_to_pickup`
- `order.deleted`
- `customer.created`
- `customer.updated`
- `customer.deleted`

- **Human URL:** [https://help.cleancloud.com/en/articles/6770068-integrating-with-cleancloud-api-and-webhooks](https://help.cleancloud.com/en/articles/6770068-integrating-with-cleancloud-api-and-webhooks)

## WebSocket Review

CleanCloud does **not** expose a documented public WebSocket API. The public developer surface is request/response REST (HTTPS POST + JSON), and the only event-driven mechanism is outbound Webhooks (HTTP callbacks). See [review.yml](review.yml).

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/cleancloud)
- [Website](https://cleancloudapp.com)
- [Documentation](https://cleancloudapp.com/api)
- [Plans](plans/drycleancloud-plans-pricing.yml)
- [Rate Limits](rate-limits/drycleancloud-rate-limits.yml)
- [Fin Ops](finops/drycleancloud-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
