You are operating in Senior Engineering Team Mode.

Complete the final production-readiness backend implementation for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must integrate all previously established domains without redesigning their approved architecture.

Do not generate frontend code.

Do not generate mobile code.

Do not generate Kubernetes manifests.

Do not generate Terraform files.

Do not generate infrastructure implementation code.

Do not generate CI/CD workflows.

────────────────────────────────────────

MISSION

Complete backend integration, hardening, reconciliation, performance optimization, security hardening, resilience, privacy validation, observability validation, and production-readiness work across the complete platform.

Validate and harden:

• Identity
• Accounts
• Profiles
• Authentication
• Authorization
• Sessions
• Devices
• Subscriptions
• Billing
• Payments
• Invoices
• Refunds
• Entitlements
• Artists
• Artist teams
• Labels
• Content partners
• Albums
• Releases
• Tracks
• Track versions
• Credits
• Metadata
• Audio assets
• Audio renditions
• Rights
• Availability
• Localization
• Audio processing
• Transcoding
• Packaging
• Playback authorization
• Playback sessions
• Playback progress
• Queue synchronization
• Multi-device synchronization
• Playlists
• Playlist collaboration
• User library
• Likes
• Saves
• Follows
• Listening history
• Search
• Discovery
• Recommendations
• Personalization
• Radio
• Charts
• Podcasts
• Notifications
• Advertising
• Analytics
• Reporting
• Moderation
• Administration
• Feature flags
• System configuration
• Audit
• Privacy

The final backend must be:

• Correct
• Secure
• Observable
• Idempotent
• Resilient
• Horizontally scalable
• Multi-region ready
• Testable
• Maintainable
• Production-ready

────────────────────────────────────────

TECHNOLOGY STACK

Use the established stack:

• Node.js
• NestJS
• TypeScript
• PostgreSQL
• Prisma ORM
• Redis
• Kafka or Redpanda
• BullMQ
• Elasticsearch/OpenSearch
• AWS S3
• CloudFront
• Stripe or approved payment provider
• FCM
• APNS
• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Do not replace approved technologies unless a genuine implementation blocker exists.

────────────────────────────────────────

IMPLEMENTATION RULES

Never generate pseudo-code.

Never generate placeholders.

Never generate TODO comments.

Never omit implementations.

Never say:

- "implement similarly"
- "left as an exercise"
- "for brevity"
- "remaining code omitted"

Every generated file must be complete.

Every generated file must compile.

Never regenerate unchanged files.

Only modify files when required.

When modifying an existing file:

1. Identify the exact path.
2. Explain why modification is required.
3. Provide the complete updated file.

Maintain backward compatibility whenever possible.

────────────────────────────────────────

CROSS-DOMAIN INTEGRATION AUDIT

Validate integrations between:

IDENTITY
→ SUBSCRIPTIONS
→ ENTITLEMENTS
→ PLAYBACK

CATALOG
→ RIGHTS
→ AVAILABILITY
→ SEARCH
→ RECOMMENDATIONS
→ PLAYBACK

MEDIA
→ PROCESSING
→ RENDITIONS
→ PACKAGING
→ CDN
→ PLAYBACK

PLAYBACK
→ HISTORY
→ RECOMMENDATIONS
→ ANALYTICS

PLAYLISTS
→ LIBRARY
→ SEARCH
→ DISCOVERY
→ PLAYBACK

PODCASTS
→ SEARCH
→ RECOMMENDATIONS
→ PLAYBACK
→ NOTIFICATIONS

SUBSCRIPTIONS
→ PAYMENTS
→ ENTITLEMENTS
→ NOTIFICATIONS

ADVERTISING
→ PLAYBACK
→ ANALYTICS
→ REPORTING

ADMINISTRATION
→ MODERATION
→ RIGHTS
→ SUBSCRIPTIONS
→ AUDIT

FEATURE FLAGS
→ APPLICATION SERVICES

SYSTEM CONFIGURATION
→ DYNAMIC PLATFORM BEHAVIOR

No domain may bypass another domain's authoritative state.

────────────────────────────────────────

CRITICAL BUSINESS INVARIANTS

Verify:

AUTHENTICATION

• Invalid credentials cannot authenticate
• Revoked sessions cannot continue privileged operations
• Passwords are never exposed
• Token replay is rejected according to security policy

AUTHORIZATION

• Users only access authorized profiles
• Artists only access their organizations
• Labels only access authorized catalogs
• Administrators require explicit permissions
• Private playlists remain private

SUBSCRIPTIONS

• Invalid subscription transitions are rejected
• Duplicate subscriptions cannot be created unintentionally
• Canceled subscriptions follow configured entitlement rules

PAYMENTS

• Duplicate payment effects cannot occur
• Webhooks are verified
• Webhooks are idempotent
• Refunds cannot exceed refundable amounts

ENTITLEMENTS

• Entitlements match subscription/provider state
• Expired entitlements are not treated as permanently active
• Regional restrictions are respected

CATALOG

• Unpublished tracks cannot become publicly playable
• Invalid content cannot become published
• Content ownership is enforced

RIGHTS

• Expired rights deny playback
• Regional rights are respected
• Platform restrictions are enforced

PLAYBACK

• Unauthorized users cannot obtain valid playback credentials
• Revoked devices cannot continue privileged playback
• Concurrent playback limits are enforced

OFFLINE

• Invalid/expired licenses cannot authorize playback
• Revoked devices cannot renew licenses

PLAYLISTS

• Private playlists remain private
• Collaborators cannot escalate permissions
• Stale mutations cannot silently overwrite newer state

LIBRARY

• Duplicate likes/saves/follows are prevented
• Profile scoping is enforced

SEARCH

• Private content is not indexed publicly
• Unavailable content is removed or filtered appropriately

RECOMMENDATIONS

• Unavailable content is filtered
• Restricted content is filtered
• Recommendation failure does not affect core playback

NOTIFICATIONS

• Duplicate delivery is minimized
• Security notifications follow mandatory rules

ADVERTISING

• Invalid campaigns cannot deliver
• Frequency caps are respected
• Ad events are idempotent

ADMINISTRATION

• Sensitive operations are permission-protected
• All high-risk actions are audited

────────────────────────────────────────

IDEMPOTENCY AUDIT

Perform a complete idempotency review.

Ensure idempotency for:

• Registration where required
• Session creation where required
• Subscription creation
• Subscription changes
• Payment creation
• Refund creation
• Webhook processing
• Entitlement updates
• Media processing
• Audio transcoding
• Publication
• Rights transitions
• Playlist mutations
• Offline mutations
• Playback-state mutations
• Search indexing
• Recommendation jobs
• Notifications
• Advertising events
• Report generation
• Privacy jobs
• Administrative workflows
• Background workers
• Event consumers

Define:

• Idempotency key
• Scope
• Storage
• TTL
• Replay behavior
• Conflict response

────────────────────────────────────────

EVENT CONSISTENCY AUDIT

Validate:

• Transactional outbox
• Event versioning
• Event schema compatibility
• Producer ownership
• Consumer ownership
• Consumer idempotency
• Retry
• Dead-letter handling
• Replay
• Partitioning
• Ordering assumptions

Verify that successful database transactions cannot silently lose required events.

────────────────────────────────────────

RECONCILIATION SYSTEMS

Implement or finalize reconciliation processes for:

SUBSCRIPTIONS

Compare:

• Internal subscription
• Payment-provider state
• Billing state
• Entitlement state

PAYMENTS

Compare:

• Internal payment
• Provider payment
• Subscription
• Refund

ENTITLEMENTS

Compare:

• Subscription
• Plan
• Entitlement
• Device/profile state

MEDIA

Compare:

• Catalog asset references
• S3 objects
• Processing state
• Renditions
• Published state

RIGHTS

Compare:

• Rights records
• Availability
• Publication state

SEARCH

Compare:

• Published catalog
• Search index

PLAYLISTS

Compare:

• Playlist metadata
• Playlist items
• Search representation where applicable

LIBRARY

Compare:

• Library membership
• Change cursors
• Derived caches

NOTIFICATIONS

Compare:

• Notification records
• Delivery state

ADVERTISING

Compare:

• Campaign state
• Delivery events
• Impression events

Each reconciliation process must:

• Detect mismatches
• Record mismatches
• Be idempotent
• Retry safely
• Expose metrics
• Avoid unsafe automatic destructive correction

────────────────────────────────────────

DATABASE INTEGRITY

Validate:

• Primary keys
• Foreign keys
• Unique constraints
• Check constraints
• Indexes
• Transaction boundaries
• Isolation levels
• Partitioning
• Connection pools
• Read replicas

Review for:

• N+1 queries
• Long transactions
• Lock contention
• Deadlocks
• Connection exhaustion
• Inefficient pagination
• Large sequential scans

────────────────────────────────────────

HIGH-GROWTH DATA REVIEW

Evaluate partitioning and retention for:

• Listening history
• Playback events
• Playback sessions
• Notification records
• Ad impressions
• Analytics references
• Audit logs
• Search analytics
• Financial records where appropriate

Separate:

• Hot operational data
• Warm data
• Archived data

Do not retain unlimited raw telemetry in transactional PostgreSQL.

────────────────────────────────────────

REDIS HARDENING

Review all Redis use.

Validate:

• Key naming
• TTL
• Memory limits
• Eviction
• Hot keys
• Cache stampede protection
• Distributed locks
• Failure behavior
• Namespaces

Verify Redis never becomes authoritative for:

• Accounts
• Subscriptions
• Payments
• Entitlements
• Catalog
• Playlists
• Library
• Financial data

────────────────────────────────────────

KAFKA HARDENING

Review:

• Topics
• Partition keys
• Partition count
• Consumer groups
• Consumer lag
• Retention
• Replay
• Dead-letter topics
• Schema evolution

Ensure high-volume events do not create hot partitions.

────────────────────────────────────────

BULLMQ HARDENING

Review:

• Queue concurrency
• Retry limits
• Backoff
• Timeouts
• Poison jobs
• Stuck jobs
• Dead-letter behavior
• Worker scaling

Prevent infinite retry loops.

────────────────────────────────────────

SEARCH HARDENING

Validate:

• Index mappings
• Aliases
• Reindexing
• Search freshness
• Failure handling
• Private-content filtering
• Rights filtering
• Explicit-content filtering
• Regional filtering

Provide operational mechanisms to detect:

• Missing documents
• Stale documents
• Duplicate documents
• Corrupt indexes

────────────────────────────────────────

MEDIA INTEGRITY

Verify:

• Upload ownership
• File validation
• Processing state
• Rendition availability
• Packaging
• CDN publication
• Object lifecycle
• Cleanup

Detect:

• Orphaned files
• Missing files
• Invalid renditions
• Stale manifests
• Unreferenced objects

────────────────────────────────────────

PLAYBACK HARDENING

Verify:

• Entitlement validation
• Rights validation
• Region validation
• Device validation
• Concurrent-stream limits
• Token expiration
• Session cleanup
• Playback progress throttling
• Queue synchronization

Measure:

• Playback authorization latency
• Playback authorization failures
• Session failures
• Token rejection
• Concurrent-stream conflicts

────────────────────────────────────────

OFFLINE HARDENING

Verify:

• Device authorization
• Entitlement validation
• License expiration
• License renewal
• Device revocation
• Content-right expiration
• Region changes

Offline features must fail securely.

Do not allow expired credentials/licenses to become permanently valid.

────────────────────────────────────────

PLAYLIST SYNCHRONIZATION HARDENING

Validate:

• Version numbers
• Mutation IDs
• Offline mutations
• Duplicate operations
• Conflicting edits
• Ownership changes
• Invitation races

The server must remain authoritative.

────────────────────────────────────────

SECURITY HARDENING

Perform a complete backend security review.

Validate:

AUTHENTICATION

• Password security
• Session management
• Token rotation
• MFA
• Passkeys where supported

AUTHORIZATION

• RBAC
• Resource ownership
• Profile scoping
• Organization scoping
• Administrative permissions

APPLICATION

• Input validation
• Output filtering
• Secure headers
• CORS
• CSRF where applicable
• XSS prevention
• SQL injection protection
• SSRF protections where applicable
• Rate limiting

MEDIA

• Malicious-upload handling
• Signed access
• Content validation
• Storage isolation

PAYMENTS

• Webhook verification
• Idempotency
• Provider secret handling

────────────────────────────────────────

THREAT MODEL VALIDATION

Validate protections against:

• Account takeover
• Credential stuffing
• Session theft
• Playback-token theft
• Unauthorized streaming
• Download abuse
• Subscription fraud
• Payment fraud
• Refund abuse
• Fake listening
• Playlist spam
• Search scraping
• Recommendation scraping
• Ad fraud
• API abuse
• Malicious uploads
• Privilege escalation
• Data leakage
• Insider threats

For each threat verify:

• Prevention
• Detection
• Response
• Recovery
• Audit

────────────────────────────────────────

PRIVACY HARDENING

Review:

• Profile data
• Listening history
• Recommendations
• Search behavior
• Device data
• Subscription data
• Payment references
• Analytics
• Messaging/communications
• Advertising signals
• Creator analytics

Minimize unnecessary collection and exposure.

Ensure APIs return only authorized fields.

────────────────────────────────────────

PERFORMANCE OPTIMIZATION

Optimize critical operations:

• Login
• Entitlement lookup
• Playback authorization
• Catalog reads
• Search
• Recommendation retrieval
• Playlist retrieval
• Library retrieval
• Queue synchronization
• Notification retrieval
• Subscription operations

Use:

• Efficient indexing
• Cursor pagination
• Caching
• Batching
• Asynchronous processing
• Connection pooling
• Read replicas where appropriate

Do not weaken correctness to improve latency.

────────────────────────────────────────

PLAYBACK PERFORMANCE

Optimize the critical path:

Client
→ Authentication
→ Entitlement
→ Rights
→ Device validation
→ Playback authorization
→ CDN

Identify bottlenecks.

Avoid unnecessary synchronous calls.

Use cached, bounded-lifetime data where safe.

────────────────────────────────────────

MEDIA-PROCESSING PERFORMANCE

Optimize:

• Queue throughput
• Worker concurrency
• CPU usage
• Temporary storage
• FFmpeg execution
• Rendition generation
• Cleanup

Define worker scaling based on:

• Queue depth
• Processing latency
• CPU
• Memory

────────────────────────────────────────

OBSERVABILITY VALIDATION

Ensure critical flows emit:

• Structured logs
• Metrics
• Distributed traces

Critical flows:

• Login
• Subscription
• Payment
• Entitlement
• Content publication
• Audio processing
• Playback authorization
• Playback session
• Playlist mutations
• Search
• Recommendations
• Notifications
• Advertising
• Analytics
• Administration

Use:

• Request IDs
• Correlation IDs
• Trace IDs

Never log:

• Passwords
• Tokens
• Secrets
• Payment credentials
• Playback credentials
• Private user behavioral data unnecessarily

────────────────────────────────────────

SLO / SLI VALIDATION

Define measurable SLOs for:

• Authentication
• Entitlement lookup
• Playback authorization
• Catalog retrieval
• Search
• Recommendations
• Playlist access
• Library access
• Notification delivery
• Subscription operations
• Payment processing

For each define:

• SLI
• Measurement source
• Target
• Alert threshold
• Error budget

────────────────────────────────────────

FAILURE SCENARIOS

Validate graceful behavior when:

• PostgreSQL fails
• Redis fails
• Kafka fails
• BullMQ workers fail
• Search fails
• S3 fails
• CDN degrades
• Payment provider fails
• Notification provider fails
• Recommendation service fails
• Ad decisioning fails
• Media-processing workers fail
• Region becomes unavailable

For each verify:

• Detection
• Timeout
• Retry
• Fallback
• Degraded functionality
• Recovery
• Reconciliation

Core playback and account functionality must degrade gracefully without unsafe authorization decisions.

────────────────────────────────────────

DISASTER-RECOVERY VALIDATION

Validate recovery for:

• PostgreSQL
• S3
• Kafka
• Redis
• Search
• Kubernetes
• Regional application failure

Measure:

• Actual RTO
• Actual RPO

Compare with architecture targets.

────────────────────────────────────────

TESTING

Implement comprehensive production-readiness testing.

UNIT TESTS

• Domain logic
• Authorization
• Entitlements
• Rights
• Playback authorization
• Playlist conflicts
• Subscription logic
• Recommendation rules
• Ad rules

INTEGRATION TESTS

• PostgreSQL
• Redis
• Kafka
• BullMQ
• Search
• S3
• Stripe
• FCM/APNS abstractions

CONTRACT TESTS

• REST APIs
• Events
• Webhooks
• Playback contracts

E2E TESTS

• Registration
• Subscription
• Search
• Playback
• Playlist
• Library
• Download
• Multi-device sync
• Podcast
• Notifications

────────────────────────────────────────

CONCURRENCY TESTING

Test:

• Concurrent subscription changes
• Duplicate payments
• Duplicate webhook events
• Concurrent playlist edits
• Inventory-like resource conflicts where applicable
• Multiple device playback
• Queue conflicts
• Duplicate offline mutations
• Concurrent administrative actions

────────────────────────────────────────

PERFORMANCE TESTING

Test:

• Authentication throughput
• Entitlement throughput
• Playback authorization throughput
• Search throughput
• Recommendation throughput
• Playlist reads
• Library reads
• Queue synchronization
• Notification throughput
• Event ingestion
• Media processing

Measure:

• p50
• p95
• p99
• Throughput
• Error rate
• Resource utilization

────────────────────────────────────────

LOAD / STRESS / SOAK TESTING

Simulate:

• Normal traffic
• Peak traffic
• Burst traffic
• Major release traffic
• High-concurrency playback
• Large search campaigns
• Large recommendation traffic

Run long-duration soak tests to identify:

• Memory leaks
• Connection leaks
• Queue growth
• Cache growth
• Worker instability
• Database degradation

────────────────────────────────────────

RESILIENCE TESTING

Inject controlled failures into:

• PostgreSQL
• Redis
• Kafka
• Search
• S3
• CDN
• Payment provider
• Notification providers
• Workers
• Kubernetes nodes
• Availability zones
• Region

Verify graceful recovery.

────────────────────────────────────────

DATABASE MIGRATION SAFETY

Review all database migrations.

Ensure support for:

• Expand-and-contract
• Backward-compatible schema changes
• Large-table migration safety
• Index creation strategy
• Production rollout sequencing
• Rollback/recovery procedures

Do not require unnecessary production downtime.

────────────────────────────────────────

FINAL API CONTRACT AUDIT

Verify:

• Versioning
• Authentication
• Authorization
• Request validation
• Response validation
• Error schema
• Pagination
• Cursor pagination
• Idempotency
• OpenAPI

Detect:

• Breaking changes
• Inconsistent naming
• Inconsistent error handling
• Inconsistent pagination

────────────────────────────────────────

FINAL EVENT CATALOG

Create the complete event dependency map.

For every event define:

• Event name
• Version
• Producer
• Consumers
• Topic
• Partition key
• Ordering expectations
• Retry
• Dead-letter
• Retention
• Consistency requirement

────────────────────────────────────────

FINAL QUEUE CATALOG

For every BullMQ queue define:

• Queue name
• Producer
• Worker
• Job schema
• Retry
• Backoff
• Timeout
• Concurrency
• Dead-letter handling
• Monitoring
• Scaling trigger

────────────────────────────────────────

FINAL SECURITY MATRIX

Create a complete permission matrix for:

• Listener
• Profile
• Family Manager
• Student
• Artist
• Artist Staff
• Label Staff
• Content Partner
• Moderator
• Support Agent
• Administrator
• Super Administrator
• System Services

Map permissions to:

• Accounts
• Profiles
• Subscriptions
• Catalog
• Media
• Rights
• Playback
• Playlists
• Library
• Search
• Recommendations
• Podcasts
• Advertising
• Analytics
• Moderation
• Administration
• Configuration
• Audit

────────────────────────────────────────

PRODUCTION READINESS REVIEW

Perform a complete review covering:

ARCHITECTURE

• Domain boundaries
• Service boundaries
• Dependencies
• Failure modes

CODE

• Type safety
• Validation
• Error handling
• Logging
• Maintainability

DATA

• Integrity
• Migrations
• Indexes
• Partitioning
• Backup
• Reconciliation

MEDIA

• Processing
• Storage
• Packaging
• CDN
• Cleanup

PLAYBACK

• Authorization
• Rights
• Entitlements
• Sessions
• Multi-device

SECURITY

• Authentication
• Authorization
• Secrets
• Rate limits
• Webhooks
• Abuse controls

PERFORMANCE

• Database
• Redis
• Search
• Kafka
• Workers
• Playback authorization

OPERATIONS

• Health
• Metrics
• Logs
• Traces
• Alerts
• Runbooks

────────────────────────────────────────

FINAL BACKEND PROJECT INDEX

Produce the complete final backend Project Index containing:

• All domains
• All services
• All modules
• All APIs
• All database objects
• All migrations
• All Redis keys
• All Kafka topics
• All events
• All BullMQ queues
• All workers
• All external providers
• All authentication mechanisms
• All authorization rules
• All rights controls
• All entitlement controls
• All media-processing workflows
• All playback workflows
• All search indexes
• All recommendation systems
• All notification systems
• All advertising systems
• All analytics systems
• All administration systems
• All security controls
• All reconciliation systems
• All tests
• All documentation
• Known risks
• Technical debt
• Remaining work
• Production-readiness status

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 71

Cross-domain integration review, dependency validation, and architecture conformance.

BACKEND MILESTONE 72

Idempotency audit, event consistency, transactional outbox validation, and reconciliation systems.

BACKEND MILESTONE 73

Authentication, authorization, profile isolation, organization isolation, privacy, and security hardening.

BACKEND MILESTONE 74

Database performance, indexes, partitioning, migrations, query optimization, and connection management.

BACKEND MILESTONE 75

Redis, Kafka, BullMQ, search, and media-processing optimization.

BACKEND MILESTONE 76

Playback-path optimization, entitlement caching, rights validation, CDN authorization, and multi-device resilience.

BACKEND MILESTONE 77

API contract validation, OpenAPI completion, event-catalog validation, queue-catalog validation, and observability validation.

BACKEND MILESTONE 78

Unit, integration, contract, E2E, concurrency, security, privacy, and abuse testing.

BACKEND MILESTONE 79

Load, stress, soak, resilience, failure-injection, and disaster-recovery testing.

BACKEND MILESTONE 80

Final production-readiness review, reconciliation verification, documentation, Project Index completion, and backend release certification.

Each milestone should contain approximately 20–40 files where practical.

Every milestone must compile and pass the applicable validation suite before proceeding.

────────────────────────────────────────

OUTPUT FORMAT

For every generated file provide:

1. Exact file path
2. Complete file contents

Never truncate code.

Never summarize source code instead of generating it.

Never generate pseudo-code.

Never generate placeholders.

Never generate TODO implementations.

When modifying an existing file:

1. Provide the exact file path.
2. State why it must change.
3. Provide the complete updated file.

Never regenerate unchanged files.

────────────────────────────────────────

SCOPE RESTRICTION

This is the final backend hardening and production-readiness volume.

Do not implement:

• New frontend functionality
• New mobile functionality
• Kubernetes infrastructure
• Terraform infrastructure
• CI/CD infrastructure

Do not redesign approved domains.

Do not replace approved technologies without concrete technical justification.

────────────────────────────────────────

QUALITY BAR

Treat the backend as mission-critical global infrastructure for a music streaming platform serving:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Massive CDN traffic
• High playback authorization traffic
• Large search traffic
• Large recommendation traffic
• Large analytics volumes
• Global content rights
• Multiple subscription plans
• Offline playback
• Multiple devices
• Advertising
• Podcasts
• Global operations

The final backend must demonstrate:

• Correct authorization
• Correct entitlements
• Correct rights enforcement
• Secure playback
• Reliable subscriptions
• Idempotent payments
• Reliable media processing
• Strong privacy
• High scalability
• Graceful failure
• Comprehensive observability
• Reconciliation
• Security
• Maintainability
• Production readiness
