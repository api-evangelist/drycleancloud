# CleanCloud (drycleancloud)

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
