# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — BACKEND VOLUME 3

## ROLE

Act as the complete senior backend engineering organization responsible for implementing the production-grade commercial, notification, analytics, administration, moderation, and platform-operations capabilities of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

Operate as:

* Principal Software Architect
* Staff Backend Engineer
* Database Architect
* Distributed Systems Engineer
* Security Engineer
* Performance Engineer
* Reliability Engineer
* QA Engineer
* DevOps Engineer
* Technical Writer

This prompt defines an independent backend implementation task.

Do not provide a tutorial.

Do not provide pseudo-code.

Do not create fake implementations.

Do not create placeholder services.

Do not leave TODO/FIXME implementation gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and integrate the implementation with the actual repository state.

Implement the requested backend functionality completely, with production-grade security, validation, testing, observability, reliability, performance, and documentation.

---

# PROJECT

Build the production backend capabilities required for the commercial and operational ecosystem surrounding the music-streaming platform.

This backend volume is responsible for:

* subscription plans
* subscription lifecycle
* payment-provider integration
* billing webhooks
* entitlement management
* subscription history
* notification orchestration
* notification preferences
* in-app notifications
* email notification integration
* push-notification integration
* product analytics processing foundations
* administrative operations
* moderation workflows
* reporting
* support workflows
* audit capabilities
* platform configuration foundations
* feature-flag foundations where appropriate
* data-retention enforcement
* account deletion orchestration
* privacy-related data workflows
* operational backend APIs

The implementation must integrate with the existing backend without assuming that any earlier AI-generated prompt is available.

Do not implement frontend or mobile interfaces in this task.

Do not allow clients to determine payment status, premium entitlement, moderation decisions, or administrative privileges.

---

# TECHNOLOGY DIRECTION

Use:

## Backend

* NestJS
* TypeScript
* REST
* WebSockets only where required
* OpenAPI/Swagger
* PostgreSQL
* Prisma
* Redis
* Kafka or Redpanda
* BullMQ

## External Providers

* Stripe or another production payment provider through an internal abstraction
* email provider
* push-notification provider

Provider-specific dependencies must remain behind application-level interfaces.

## Observability

* OpenTelemetry
* Prometheus
* Grafana
* structured logging
* distributed tracing

Use the repository's existing versions and abstractions whenever compatible.

Do not perform unrelated dependency upgrades.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect existing subscription and plan models.
3. Inspect authentication and user models.
4. Inspect existing payment abstractions.
5. Inspect existing event/outbox infrastructure.
6. Inspect Redis and BullMQ infrastructure.
7. Inspect notification models and providers.
8. Inspect analytics/event models.
9. Inspect administration and moderation functionality.
10. Inspect audit logging.
11. Inspect tests.
12. Inspect configuration and secret management.

The repository defines what currently exists.

This prompt defines the functionality that must be achieved.

Preserve compatible implementations.

Do not recreate existing infrastructure unnecessarily.

Do not assume that an earlier prompt or architecture document is available to the implementation agent.

---

# BACKEND RESPONSIBILITY

This volume owns:

* commercial subscription state
* payment-provider integration
* payment webhooks
* entitlement propagation
* billing records
* notification orchestration
* notification preferences
* delivery workers
* analytics processing foundations
* moderation
* administration
* support operations
* reporting
* audit expansion
* privacy workflows
* account-deletion orchestration
* operational configuration APIs where appropriate

---

# SUBSCRIPTION DOMAIN

Implement a production-grade subscription subsystem.

Support:

* plans
* plan features
* subscription
* subscription items where required
* billing cycle
* provider customer reference
* provider subscription reference
* provider payment references where required
* local subscription status
* entitlement state
* cancellation state
* billing timestamps
* renewal timestamps
* trial state where applicable

Keep provider identifiers separate from internal identifiers.

Do not expose provider secrets to clients.

---

# PLAN MODEL

Implement plans with explicit business meaning.

A plan must support appropriate fields such as:

* stable ID
* internal name
* display name
* description
* billing interval
* price representation
* currency
* active state
* provider price reference
* feature configuration
* creation/update timestamps

Money must use exact database representations.

Never use floating-point numbers for monetary values.

Do not trust client-submitted pricing.

---

# SUBSCRIPTION STATE MACHINE

Implement explicit subscription states.

Support an appropriate lifecycle including:

* incomplete
* trialing
* active
* past_due
* paused where applicable
* canceling
* canceled
* expired

The exact state model may follow provider capabilities and repository conventions.

Every transition must define:

* source state
* destination state
* triggering event
* authorization
* database mutation
* entitlement effect
* emitted event
* audit behavior

Invalid transitions must be rejected.

---

# PAYMENT PROVIDER ABSTRACTION

Implement an internal payment-provider interface.

Application business logic must interact with provider-independent concepts such as:

* customer
* product/plan
* price
* checkout
* subscription
* invoice
* payment
* cancellation

Do not scatter Stripe SDK calls throughout domain services.

The provider adapter owns:

* API requests
* response mapping
* provider errors
* provider identifiers
* webhook verification

The domain layer owns:

* business rules
* local state
* entitlement decisions
* audit behavior

---

# CUSTOMER CREATION

Implement provider-customer lifecycle.

Ensure that:

* one application account maps deterministically to the correct provider customer
* duplicate customer creation is prevented
* provider references are stored securely
* reconciliation can recover from partially completed operations

Use idempotency where provider APIs support it.

Never treat a client-supplied provider customer ID as authoritative.

---

# CHECKOUT

Implement secure subscription checkout orchestration.

The server must:

1. authenticate the user
2. validate selected plan
3. verify plan availability
4. resolve the provider price from authoritative configuration
5. create or reuse provider customer
6. create the provider checkout/session
7. persist sufficient local correlation state
8. return only the provider-facing information the client requires

Never accept arbitrary amounts or provider price IDs from untrusted clients without server-side validation.

---

# SUBSCRIPTION CREATION

A local subscription must only become active after authoritative provider confirmation.

Support:

* checkout completion
* asynchronous webhook confirmation
* provider reconciliation
* idempotent state transition
* entitlement propagation

Do not grant premium access merely because a checkout session was opened.

---

# PAYMENT WEBHOOK INGESTION

Implement secure webhook processing.

Requirements:

* preserve raw request body where signature verification requires it
* verify provider signature
* validate timestamp/replay protections where supported
* persist provider event ID
* deduplicate events
* acknowledge safely
* process business changes asynchronously where appropriate
* preserve event ordering assumptions
* maintain auditability
* emit internal events only after authoritative local state is updated

Do not trust webhook payloads without cryptographic verification.

---

# WEBHOOK IDEMPOTENCY

Provider events may be delivered multiple times.

Implement idempotent handling using:

* provider event identifiers
* unique database constraints
* persisted processing state

Repeated delivery must not:

* duplicate subscriptions
* double-grant entitlements
* duplicate invoices
* duplicate notifications
* duplicate analytics events

---

# WEBHOOK ORDERING

Do not assume webhook arrival order unless the provider guarantees it.

Where a later-state event arrives before an earlier event:

* validate the provider's authoritative state where appropriate
* avoid regressing local state
* reconcile if required

Do not let stale provider events blindly overwrite newer local state.

---

# ENTITLEMENT SERVICE

Implement a server-authoritative entitlement layer.

Entitlements may include:

* premium access
* higher audio quality
* ad-free access
* offline capability where supported
* increased device limits
* premium product features

Separate entitlement state from raw payment-provider objects.

The entitlement layer must support:

* activation
* change
* suspension
* expiration
* revocation
* reconciliation

---

# ENTITLEMENT PROPAGATION

When subscription state changes:

1. persist authoritative local state
2. calculate resulting entitlement state
3. persist entitlement transition
4. publish internal domain event
5. update appropriate caches
6. notify downstream systems asynchronously

Playback authorization must consume server-authoritative entitlement state.

Client-local subscription state must never override backend entitlement state.

---

# ENTITLEMENT CACHING

Where Redis caching is used:

* use explicit TTL
* use scoped keys
* invalidate on entitlement changes
* fail safely
* prevent cross-user leakage

Do not cache entitlements indefinitely.

During cache failure, fall back to an authoritative data path where practical.

Do not fail open for high-risk authorization decisions.

---

# BILLING HISTORY

Implement durable billing history appropriate to the product.

Track:

* invoices
* payment attempts
* successful payments
* failed payments
* refunds where applicable
* provider references
* timestamps
* amounts
* currencies
* subscription relationships

Do not store prohibited raw payment credentials.

Billing records must be protected by strict user authorization.

---

# CANCELLATION

Implement subscription cancellation behavior.

Support:

* immediate cancellation where the plan permits it
* end-of-period cancellation
* cancellation reversal where appropriate
* provider synchronization
* entitlement preservation until the actual expiration point where applicable

Do not revoke entitlements simply because a user scheduled an end-of-period cancellation.

---

# FAILED PAYMENT HANDLING

Support:

* failed payment event
* retry state
* past-due state
* grace period where applicable
* entitlement consequences
* notification
* recovery
* expiration

Do not immediately destroy user data merely because payment failed.

Keep business state transitions explicit.

---

# PLAN CHANGES

Support plan upgrades/downgrades where applicable.

Validate:

* current plan
* target plan
* availability
* billing rules
* provider capability
* proration behavior where applicable
* effective date

Do not let clients select arbitrary prices.

Record the change for auditability.

---

# PAYMENT RECONCILIATION

Implement a reconciliation capability for provider/local differences.

It must detect situations such as:

* local active subscription with provider canceled
* provider active subscription missing locally
* entitlement inconsistent with subscription
* missing payment records
* webhook processing gaps

Reconciliation should be safe, observable, and auditable.

Do not automatically mutate high-impact financial state without appropriate validation.

---

# NOTIFICATION DOMAIN

Implement a provider-independent notification subsystem.

Support:

* notification
* notification preference
* notification template
* delivery attempt
* channel
* priority
* schedule
* read state
* suppression state

Channels may include:

* in-app
* email
* push

---

# NOTIFICATION PREFERENCES

Implement user-configurable notification preferences.

Preferences must support appropriate dimensions such as:

* notification type
* channel
* enabled/disabled
* quiet-period configuration where appropriate

Server-side preference enforcement is mandatory.

Do not allow a downstream provider to decide whether a user opted out.

Security-critical notifications may require special handling and may not always be suppressible.

---

# NOTIFICATION LIFECYCLE

Implement notification states such as:

* pending
* queued
* sending
* delivered
* failed
* suppressed
* canceled
* read

Use explicit transitions.

A failed email does not mean the underlying product notification never existed.

---

# NOTIFICATION ORCHESTRATION

Implement notification creation independently from provider delivery.

The orchestration path must:

1. receive a domain/business event
2. determine whether a notification applies
3. retrieve preferences
4. select channels
5. render or construct provider-independent notification content
6. persist notification
7. enqueue delivery
8. track attempts
9. update delivery state

Do not call external email/push providers directly from critical transactional requests.

---

# NOTIFICATION IDEMPOTENCY

Prevent duplicate notifications from:

* repeated domain events
* webhook retries
* job retries
* worker restarts

Use deterministic notification keys or source-event identifiers where appropriate.

Do not suppress legitimate repeated notifications solely because their type is identical.

---

# EMAIL DELIVERY

Implement provider abstraction for email.

Support:

* template identifier
* rendered payload
* recipient
* locale
* provider message reference
* retry
* failure state

Do not embed provider-specific templates throughout business logic.

Protect against:

* header injection
* untrusted template content
* accidental secret inclusion

---

# PUSH DELIVERY

Implement provider abstraction for mobile push notifications.

Support:

* device token
* platform
* notification payload
* provider reference
* delivery response
* token invalidation

Do not send sensitive personal information unnecessarily in push payloads.

Invalid device tokens must be retired safely.

---

# IN-APP NOTIFICATIONS

Implement durable in-app notification records.

Support:

* unread count
* list
* read
* mark-all-read where appropriate
* expiration where applicable

Use efficient indexes for unread queries.

Do not calculate unread counts using unbounded table scans.

---

# ANALYTICS PROCESSING

Implement backend foundations for product analytics.

Support validated event ingestion for:

* playback
* search
* discovery
* playlist operations
* likes
* follows
* recommendations
* subscriptions
* notifications

The analytics subsystem must be decoupled from critical user-facing transactions.

---

# ANALYTICS EVENT PROCESSING

Process analytics events asynchronously.

Support:

* event validation
* schema versioning
* deduplication
* enrichment where appropriate
* privacy classification
* partitioning
* aggregation foundations
* failed-event handling

Do not block playback or account operations while waiting for analytical processing.

---

# ANALYTICS PRIVACY

Analytics must minimize personal data.

Do not include:

* passwords
* tokens
* secret keys
* unnecessary precise location
* raw payment credentials
* private content

Implement deletion/retention behavior consistent with account lifecycle.

---

# ANALYTICS RETENTION

Define different retention periods for:

* raw events
* aggregated data
* operational metrics
* audit records

Do not retain analytics data forever by default.

Use cleanup jobs for expired records where the selected storage layer requires it.

---

# MODERATION

Implement moderation foundations for:

* catalog content
* artists
* playlists where applicable
* uploaded media
* reported content
* abusive behavior

Support:

* report creation
* report state
* review assignment
* moderator decision
* resolution
* escalation
* appeal foundation where appropriate

Moderation operations must be auditable.

---

# REPORTING

Implement report creation for users and internal systems.

A report should capture:

* reporter
* target type
* target ID
* reason
* description where applicable
* evidence references where appropriate
* status
* assigned moderator
* timestamps

Do not store arbitrary unvalidated payloads or sensitive content unnecessarily.

---

# MODERATION STATE MACHINE

Support explicit states such as:

* submitted
* queued
* under_review
* action_required
* resolved
* dismissed
* escalated
* appealed where applicable

Transitions must require the appropriate roles.

Administrative and moderation decisions must be auditable.

---

# CONTENT ENFORCEMENT

Support server-side moderation actions such as:

* hide
* restrict
* suspend
* withdraw
* restore where authorized

The action must propagate to:

* catalog visibility
* search indexing
* playback authorization
* recommendations
* cached responses
* notifications where relevant

Do not rely solely on a search-index deletion to enforce access restrictions.

---

# ADMINISTRATION

Implement secure administrative APIs.

Support appropriate capabilities for:

* user inspection
* account suspension
* account restoration
* artist inspection
* catalog management
* moderation
* subscription support
* notification inspection
* audit inspection
* operational diagnostics

Administration must use dedicated authorization policies.

Do not expose broad unrestricted database access through generic admin endpoints.

---

# SUPPORT OPERATIONS

Support controlled customer-support workflows such as:

* account lookup
* subscription status inspection
* entitlement inspection
* session/device inspection
* cancellation assistance
* account-security investigation

Support operators must not automatically receive unrestricted access to private user data.

Sensitive support actions should require explicit authorization and audit records.

---

# ADMINISTRATIVE SEARCH

Provide appropriately scoped administrative search.

Support filtering by:

* stable user ID
* email where authorized
* subscription ID
* artist ID
* track/album ID
* report ID

Protect sensitive search fields.

Avoid wildcard database scans over massive tables.

---

# ADMINISTRATIVE AUDIT

Expand audit coverage for:

* administrative login
* user suspension
* user restoration
* catalog changes
* moderation decisions
* entitlement adjustments
* support actions
* configuration changes
* destructive operations

Every privileged mutation must be attributable to a human/service actor.

---

# PRIVILEGED ENTITLEMENT ADJUSTMENT

Where support operations require manual entitlement changes, implement a controlled workflow.

Require:

* authorized actor
* target user
* reason
* requested change
* expiration where applicable
* audit record

Manual changes must be distinguishable from provider-derived entitlement state.

Do not permanently override provider state without an explicit business rule.

---

# FEATURE FLAGS

Implement a controlled feature-flag abstraction where it materially benefits platform operations.

Support appropriate targeting by:

* environment
* user
* role
* percentage
* application version
* platform

Feature flags must have:

* owner
* purpose
* default value
* evaluation behavior
* auditability

Do not make feature flags an excuse to leave incomplete implementations hidden behind permanent disabled states.

---

# CONFIGURATION MANAGEMENT

Where backend runtime configuration is mutable, distinguish:

* deployment configuration
* business configuration
* feature flags
* secrets

Never store secrets as ordinary business configuration.

Sensitive configuration changes must be audited.

---

# DATA RETENTION

Implement retention policies for appropriate records:

* old notifications
* expired sessions
* obsolete playback checkpoints
* raw analytics
* failed jobs
* processed webhook records
* temporary media state
* stale administrative data

Retention jobs must be:

* idempotent
* batch-oriented
* observable
* safe under concurrent execution

Never delete authoritative financial or audit records merely because they are old unless the defined retention policy explicitly allows it.

---

# ACCOUNT DELETION

Implement a secure account-deletion workflow.

It must support:

* authenticated deletion request
* authorization/confirmation
* account state transition
* session revocation
* future-login prevention
* privacy cleanup
* asynchronous dependent-data deletion
* notification
* audit trail

Do not perform an unbounded synchronous deletion transaction across every subsystem.

Use durable jobs/events for downstream cleanup.

---

# DATA DELETION ORCHESTRATION

Downstream systems must react to an account-deletion event.

Consider:

* playlists
* library
* playback history
* notification data
* recommendation profiles
* analytics identifiers
* search representations
* cached state
* device state

Do not allow deleted users to continue influencing personalized serving indefinitely.

Where legal/operational retention prevents immediate physical deletion, implement appropriate data minimization or anonymization.

---

# SECURITY

Secure all implemented administrative and commercial capabilities.

Protect against:

* privilege escalation
* IDOR
* forged entitlement
* payment webhook forgery
* replay
* duplicate billing actions
* notification abuse
* admin abuse
* support-data overexposure
* moderation privilege abuse
* secret leakage

Require:

* strong authentication
* server-side authorization
* provider signature validation
* idempotency
* rate limiting
* audit logging
* least privilege
* secure secret management

Never trust:

* client subscription state
* provider IDs supplied by clients
* user roles from request bodies
* moderation status from clients
* notification opt-in state asserted by clients

---

# FINANCIAL SECURITY

Protect billing data.

Do not store raw:

* credit-card numbers
* CVVs
* payment secrets

Use provider-hosted/tokenized mechanisms where possible.

Validate:

* amounts
* currency
* plan
* customer
* provider event signatures

Every financial mutation must be auditable.

---

# NOTIFICATION SECURITY

Prevent:

* notification spoofing
* recipient substitution
* template injection
* provider credential exposure
* sensitive-data leakage

Notification recipient must be resolved from authoritative server state.

Do not let clients send arbitrary email addresses through internal notification APIs without explicit authorization and business justification.

---

# OBSERVABILITY

Instrument:

## Billing

* checkout creation
* webhook latency
* webhook failures
* subscription transitions
* entitlement changes
* provider latency
* reconciliation mismatches

## Notifications

* notification creation
* queue latency
* delivery latency
* provider failures
* retry counts
* suppression rates
* invalid push tokens

## Analytics

* ingestion volume
* validation failures
* consumer lag
* processing latency
* duplicate rate
* dead-letter volume

## Moderation

* reports created
* review latency
* action counts
* escalation counts

## Administration

* privileged requests
* authorization failures
* destructive operations

Never log:

* payment credentials
* webhook signing secrets
* access tokens
* refresh tokens
* full private user records

---

# RELIABILITY

Implement:

* webhook retries
* job retries
* provider timeouts
* provider backoff
* reconciliation
* idempotency
* graceful shutdown
* failure recovery
* durable state transitions

External-provider outages must not corrupt local state.

Notification outages must not block critical account operations.

Analytics outages must not block playback.

Billing-provider outages must not automatically revoke valid entitlements without authoritative evidence.

---

# PERFORMANCE

Optimize:

* entitlement checks
* subscription status queries
* notification unread queries
* admin search
* webhook ingestion
* notification creation
* analytics ingestion

Use:

* indexed queries
* batching
* asynchronous processing
* bounded page sizes
* Redis caching where justified

Avoid synchronous provider calls inside high-volume user-facing requests unless unavoidable.

---

# TESTING

Implement automated tests covering:

## Subscriptions

* plan retrieval
* checkout
* subscription activation
* renewal
* cancellation
* failed payment
* plan changes
* webhook verification
* duplicate webhooks
* out-of-order events
* entitlement transitions
* reconciliation

## Notifications

* preference enforcement
* notification creation
* deduplication
* email delivery
* push delivery
* invalid token handling
* retry behavior
* in-app read state

## Analytics

* event validation
* deduplication
* privacy filtering
* processing
* failure recovery

## Moderation

* report creation
* authorization
* state transitions
* content enforcement
* audit records

## Administration

* role enforcement
* resource scoping
* support workflows
* entitlement adjustments
* audit logging

## Privacy

* account deletion
* session revocation
* downstream deletion events
* restricted access after deletion

Use integration tests for persistence and webhook processing.

Test provider adapters independently from domain logic.

Do not depend exclusively on mocks.

---

# MIGRATIONS

Create complete Prisma migrations for all new transactional models.

Ensure:

* foreign keys
* unique provider-event IDs
* subscription state constraints
* notification indexes
* report indexes
* audit indexes
* retention-related indexes
* deletion-state indexes

Consider large-table migration behavior.

Do not perform destructive schema modifications without a safe migration strategy.

---

# API DOCUMENTATION

Document implemented APIs for:

* plans
* subscriptions
* checkout
* billing history
* notifications
* notification preferences
* reports
* administration
* support
* moderation
* account deletion
* operational configuration where exposed

Document:

* authentication
* authorization
* request/response schemas
* errors
* idempotency requirements
* pagination
* rate limits where appropriate

The documentation must match actual behavior.

---

# IMPLEMENTATION BOUNDARIES

This backend volume owns the commercial, notification, analytics, moderation, administration, support, and privacy-related backend capabilities described here.

Do not implement:

* complete web application
* complete mobile application
* production Kubernetes platform
* full analytics warehouse
* data-science training infrastructure
* infrastructure-as-code for the entire platform

Implement only the application/backend integrations required for these capabilities.

Do not duplicate existing functionality already implemented correctly.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before making changes:

1. inspect the current repository
2. inspect subscription/payment models
3. inspect event/outbox infrastructure
4. inspect queues
5. inspect authentication/authorization
6. inspect notifications
7. inspect audit functionality
8. inspect existing tests
9. identify contracts that must remain compatible
10. implement only the required scope

Then:

1. implement commercial state
2. implement provider adapters
3. implement webhook processing
4. implement entitlements
5. implement notifications
6. implement analytics processing
7. implement moderation
8. implement administration
9. implement privacy/deletion workflows
10. add migrations
11. add tests
12. add observability
13. update documentation
14. perform validation

Do not rewrite unrelated modules.

---

# COMPLETION CRITERIA

This backend task is complete only when:

* subscription state is durable and authoritative
* payment-provider integration is abstracted
* webhooks are cryptographically verified
* webhook processing is idempotent
* entitlement state is server-authoritative
* billing history is protected
* cancellation works correctly
* failed-payment state is handled
* plan changes are validated
* reconciliation is available
* notification preferences are enforced
* notification creation is asynchronous where appropriate
* email and push integrations are provider-independent
* in-app notifications work
* analytics processing is decoupled from critical requests
* moderation workflows are implemented
* administrative access is strongly authorized
* privileged actions are audited
* account deletion is durable and recoverable
* retention workflows are implemented where required
* feature/configuration foundations are safe
* observability covers commercial and operational behavior
* automated tests cover critical success and failure paths
* migrations are valid
* APIs are documented
* no required functionality is intentionally incomplete

Do not claim completion if required validation fails.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* subscription functionality implemented
* payment-provider changes
* webhook changes
* entitlement changes
* billing/database changes
* notification functionality
* notification-provider integrations
* analytics changes
* moderation changes
* administration changes
* support workflows
* privacy/deletion changes
* migrations created
* API endpoints added or modified
* event changes
* queue/job changes
* Redis changes
* security changes
* observability changes
* tests added or updated
* validation performed
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified results from assumptions.

Do not claim that a payment webhook, provider integration, job, migration, test, or deletion workflow was successfully validated unless it was actually tested.

---

# FINAL INSTRUCTION

Implement the commercial and operational backend layer required to turn the music-streaming platform into a real service.

Make subscription and entitlement state authoritative.

Make payment-provider integrations verifiable and idempotent.

Make notifications asynchronous, reliable, and privacy-aware.

Make analytics scalable without blocking critical workloads.

Make moderation and administration explicitly authorized and auditable.

Make account deletion and retention behavior durable and recoverable.

Build real provider integrations, real state transitions, real security controls, real background processing, real tests, and real observability.

Do not create superficial scaffolding and call it complete.

The resulting backend must support the commercial, operational, administrative, moderation, notification, analytics, and privacy requirements of a production-scale music streaming platform without requiring incompatible architectural changes later.
