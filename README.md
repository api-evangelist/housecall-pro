# Housecall Pro

API Evangelist profile of [Housecall Pro](https://www.housecallpro.com) — an all-in-one home services
business management platform headquartered in Denver, Colorado (with offices in San Diego),
founded in 2013 by Ian Heidt, Roland Ligtenberg, Reza Olfat, Adam Perry-Pelletier, and Chris Zwickilton
under the parent entity Codefied Inc. The platform serves 200K+ residential and commercial service pros
across 50+ trades — HVAC, plumbing, electrical, cleaning, landscaping, pest control, garage doors,
locksmiths, appliance repair, and more.

## At a Glance

- **Provider:** Housecall Pro (Codefied Inc.)
- **Headquarters:** Denver, CO (with San Diego, CA office)
- **Founded:** 2013
- **Category:** Home Services / Field Service Management
- **API base URL:** `https://api.housecallpro.com`
- **Docs:** [docs.housecallpro.com](https://docs.housecallpro.com/) (Stoplight-hosted)
- **Authentication:** Bearer / `Authorization: Token {API_KEY}`; OAuth 2.0 available for partner apps
- **Plan required for API:** MAX
- **Webhooks:** Yes — customer, estimate, invoice, job, lead, and payment events with a signing secret
- **Tier:** **Tier 1** (real, documented, public REST API with OpenAPI on Stoplight)

## APIs

### Housecall Pro Public API

REST + JSON API covering the core platform resources:

| Resource | Endpoint root | Notes |
|---|---|---|
| Customers | `/customers` | CRUD; multi-location enabled |
| Leads | `/leads` | Create and read job-inbox leads |
| Jobs | `/jobs` | CRUD; nested appointments and line items |
| Estimates | `/estimates` | CRUD; multi-option approval flow |
| Invoices | `/invoices` | CRUD; nested payments |
| Payments | `/invoices/{id}/payments` | Read processed payments |
| Employees | `/employees` | Read field techs, office staff, admins |
| Companies | `/companies` | Vendor / company records |
| Schedule items | `/jobs/{id}/appointments` | Job appointments and arrival windows |
| Line items | `/jobs/{id}/line_items` | Job line items with pricing |
| Webhooks | `/webhooks` | Subscription management |

Spec: [`openapi/housecall-pro-public-api-openapi.yml`](openapi/housecall-pro-public-api-openapi.yml)

## Artifacts in this Repository

| Path | Description |
|---|---|
| [`apis.yml`](apis.yml) | APIs.json profile of Housecall Pro. |
| [`openapi/`](openapi/) | OpenAPI 3.1 description of the Public API. |
| [`json-schema/`](json-schema/) | JSON Schemas for Customer, Job, and Invoice. |
| [`json-ld/`](json-ld/) | JSON-LD context mapping Housecall Pro terms to schema.org. |
| [`capabilities/`](capabilities/) | Naftiko capability definitions for each resource group. |
| [`plans/`](plans/) | API Commons Plans 0.1 description of Housecall Pro pricing tiers. |
| [`rate-limits/`](rate-limits/) | API Commons Rate Limits 0.1 (Housecall Pro does not publish numeric limits). |
| [`finops/`](finops/) | FinOps Framework / FOCUS-aligned cost surface. |

## Plans (Summary)

| Plan | Annual / mo | Monthly | Users | API |
|---|---|---|---|---|
| Basic | $59 | $79 | 1 | No |
| Essentials | $149 | $189 | up to 5 | No |
| **MAX** | **$299** | **$329** | up to 8 (+$35/user) | **Yes** |

Add-ons: Sales Proposals ($40/mo), Vehicle GPS ($20/vehicle/mo), Premium Price Book ($149/mo).
See [`plans/housecall-pro-plans-pricing.yml`](plans/housecall-pro-plans-pricing.yml).

## Webhook Events

- **Customer:** `customer.created`, `customer.updated`, `customer.deleted`
- **Estimate:** `estimate.created`, `estimate.updated`, `estimate.sent`, `estimate.scheduled`,
  `estimate.on_my_way`, `estimate.completed`, `estimate.copy_to_job`, `estimate.option.created`,
  `estimate.option.approval_status_changed`
- **Invoice:** `invoice.created`, `invoice.amount_updated`, `invoice.sent`, `invoice.paid`,
  `invoice.payment.succeeded`, `invoice.payment.failed`, `invoice.refund.succeeded`,
  `invoice.canceled`, `invoice.voided`
- **Job:** `job.appointment.appointment_discarded` (plus the broader job lifecycle events on the
  partner-jobs surface)

## Notes for Integrators

- Housecall Pro does not offer dedicated developer support; partner-built integrations are the norm.
- A single MAX-admin API key can pull across all locations for multi-location accounts.
- Deleting an API key immediately breaks any active integration using it.
- The GitHub organization [github.com/housecallpro](https://github.com/housecallpro) exists but has
  no public repositories — no official SDKs are published. Community SDKs and integration platforms
  (Zapier, Make, Pipedream, Rollout, n8n) cover most use cases.

## Sources

- [Housecall Pro](https://www.housecallpro.com)
- [Pricing](https://www.housecallpro.com/pricing/)
- [Public API docs (Stoplight)](https://docs.housecallpro.com/)
- [API Overview help article](https://help.housecallpro.com/en/articles/8505035-api-overview)
- [Webhooks documentation](https://docs.housecallpro.com/docs/housecall-public-api/46e9e1be07621-webhooks)

---

Profiled by [API Evangelist](https://apievangelist.com).
