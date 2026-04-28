# 1. Business volume assumptions

Start with the commercial baseline.

Estimate:

number of customer organizations onboarded
number of legal entities per organization
invoices per organization per day
peak invoices per hour
peak invoices per second
growth over 6–12 months

Example thought process:

100 organizations
each sends 5,000 invoices/day
total = 500,000 invoices/day
peak may be 5–10x average during month-end, quarter-end, VAT deadlines

This is the first and most important input.

# 2. Ingestion patterns

Not all traffic arrives the same way.

Consider:

API real-time submissions
bulk file uploads
scheduled batch loads
portal/manual entry
managed-service uploads from enterprise clients

Why it matters:
API traffic needs low latency.
Batch traffic needs high throughput.
Both drive different sizing decisions.

# 3. Peak-load behavior

Average volume is useless without peak estimation.

You should estimate:

normal day volume
month-end spike
tax filing deadline spike
retry/replay spike after outage
onboarding spike when large client goes live

This is where many systems fail.

Use:
Peak factor = 3x to 10x average, depending on business pattern.

# 4. Payload size

You need average and max invoice payload size.

Estimate:

invoice JSON/XML size
attachments, if any
metadata
signed documents, if any

This affects:

network throughput
API gateway sizing
message broker storage
object storage growth
processing latency

# 5. Processing stages

Capacity is not only about ingestion. It is about every stage.

Estimate per stage:

ingestion
validation
transformation
enrichment
routing
transmission to Peppol / authority
notification / webhook
audit logging
reporting

Each stage has different CPU, memory, and I/O needs.

# 6. Latency and SLA requirements

Define what the business expects.

Examples:

API response under 2 seconds for submission acknowledgment
validation completed within 10 seconds
transmission within 1 minute
portal availability 99.9% or higher

This determines whether you can process synchronously or asynchronously.

# 7. Synchronous vs asynchronous flow

This is a major capacity decision.

Use synchronous for:

quick submission acknowledgment
status query

Use asynchronous for:

heavy validation
transformation
transmission
retries
notifications

This reduces peak pressure on the API layer.

# 8. Storage estimation

You need to estimate multiple storage types.

Consider:

invoice payload storage
audit logs
transaction status data
error records
retry queues
archival retention
analytics/reporting data

Ask:

how many invoices retained?
for how many years?
hot vs warm vs archive storage?

Very often, audit and retention become much bigger than transaction tables.

# 9. Compute estimation

Estimate compute separately for:

API layer
validation services
transformation services
workflow/orchestration
notification/webhook service
reporting jobs
background retry workers

Look at:

CPU-heavy tasks
memory-heavy tasks
burstable workloads
horizontal scaling needs

# 110. Messaging / queue sizing

If using event-driven architecture, size the message layer carefully.

Estimate:

events per invoice
queue depth during peak
retry backlog
dead-letter queue volume
retention duration for messages

Example:
1 invoice may generate:

invoice_received
validated
transformed
transmitted
delivered
customer_notified

So 500,000 invoices/day may create several million events/day.

# 11. External dependency limits

This is critical.

Your capacity is also constrained by:

Peppol gateway throughput
tax authority API limits
client ERP rate limits
email/SMS notification provider limits
webhook consumer responsiveness

Your platform must absorb and buffer around slower downstream systems.

# 12. Multi-tenancy model

Capacity depends on tenant isolation.

Consider:

shared platform vs dedicated tenant resources
noisy neighbor protection
per-tenant throttling
premium client SLAs
tenant-specific storage/reporting needs

This matters a lot in SaaS design.

# 13. Availability and resilience

Capacity planning must include failure scenarios.

Estimate for:

node failure
AZ failure
queue backlog recovery
replay processing
retry storm after outage

You must answer:
Can the system recover quickly after downtime without collapsing under backlog?

# 14. Observability load

Logging and monitoring also consume capacity.

Estimate:

logs per invoice
audit events
metrics volume
tracing volume
alerting thresholds

In regulated systems, logging can become surprisingly expensive.

# 15. Growth and headroom

Never size only for today.

Plan for:

2x or 3x customer growth
regulatory expansion
new countries
more invoice types
added analytics / dashboards / AI features

Good rule:
keep 30–50% headroom in critical components.

A practical checklist for your architecture

For each component, estimate these 6 things:

requests/events per second
average and peak payload size
processing time per request
storage growth per day/month
SLA / latency target
failover / retry load
The key areas to mention in your design discussion

If they ask what you considered for capacity estimation, say:

“Capacity planning should cover tenant volume, invoice throughput, peak-period spikes, payload size, synchronous versus asynchronous processing, compute and queue sizing, storage retention, external dependency limits, and resilience under retry or recovery scenarios.”

That sounds architect-level.

-----------------------------------


## API architecture components you should draw ## 

When you create the architecture, include these blocks:

Client ERP / External System
→ API Gateway
→ Authentication / Authorization
→ Invoice Ingestion Service
→ Validation Service
→ Transformation Service
→ Workflow / Orchestration Layer
→ Transmission Service
→ Audit & Tracking Database
→ Notification / Webhook Service

That is the clean enterprise view.

What API Gateway should handle

Your API Gateway should manage:

authentication
authorization
throttling
rate limiting
request validation
routing
logging

This is important because many organizations may connect to the platform.

Security requirements for API

For interview or architecture discussion, mention:

OAuth 2.0 or token-based authentication
TLS encryption in transit
payload validation
RBAC for tenant access
audit logging
idempotency for duplicate invoice submission

That last point is very important.

Why idempotency matters

Sometimes client systems retry the same request.

You must prevent duplicate invoices from being processed twice.

So your API should support:

unique invoice ID
idempotency key
duplicate detection logic
Non-functional API requirements

Your API layer should also support:

high availability
low latency
retry handling
observability
versioning
scalability for high invoice volumes