You are operating in Senior Engineering Team Mode.

Build the production-ready backend foundation for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must follow the approved Spotify-like architecture, domain boundaries, service ownership, database architecture, media architecture, playback architecture, subscription architecture, rights architecture, API conventions, event architecture, security architecture, and Project Index.

Do not redesign the architecture.

Do not generate frontend code.

Do not generate mobile code.

Do not generate infrastructure implementation code.

Do not generate Terraform.

Do not generate Kubernetes manifests.

Do not generate CI/CD workflows.

────────────────────────────────────────

MISSION

Build the production-ready backend foundation required for:

• API Gateway
• Backend service structure
• Configuration
• Authentication foundations
• Authorization foundations
• PostgreSQL
• Prisma
• Redis
• Kafka/Redpanda
• BullMQ
• OpenTelemetry
• Structured logging
• Metrics
• Health checks
• Graceful shutdown
• Error handling
• Request context
• Validation
• OpenAPI
• Testing foundation
• Local development

This volume establishes the shared backend platform that all later music-streaming domains will use.

The backend must eventually support:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Large playlist volumes
• Large listening-history volumes
• Global CDN audio delivery
• Search
• Recommendations
• Subscriptions
• Payments
• Entitlements
• Offline downloads
• Artist workflows
• Podcasts
• Advertising
• Analytics

────────────────────────────────────────

PRIMARY TECHNOLOGY STACK

Backend:

• Node.js
• NestJS
• TypeScript

Database:

• PostgreSQL
• Prisma ORM

Cache:

• Redis

Event Streaming:

• Kafka or Redpanda

Background Processing:

• BullMQ

Search:

• Elasticsearch or OpenSearch

Object Storage:

• AWS S3-compatible object storage

Payments:

• Stripe or approved payment abstraction

Notifications:

• Firebase Cloud Messaging
• Apple Push Notification Service
• Email provider abstraction

Observability:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Testing:

• Jest
• Supertest
• Integration testing tools

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

Only modify existing files when required.

Use strict TypeScript.

Use dependency injection.

Keep controllers thin.

Keep business logic outside controllers.

Use repositories for persistence.

Use DTOs for external contracts.

Use centralized validation.

Use centralized error handling.

Use structured logging.

Use graceful shutdown.

Use production-safe configuration.

────────────────────────────────────────

BACKEND ARCHITECTURE

Use:

• Clean Architecture
• Domain-Driven Design
• SOLID
• Repository Pattern
• Service Layer
• Dependency Injection
• Feature-first organization
• Explicit domain boundaries
• CQRS where justified
• Event-driven architecture where appropriate
• Transactional Outbox where appropriate
• Idempotent consumers
• Stateless application services where possible

Do not create unnecessary microservices.

The implementation must permit future service extraction without forcing a full rewrite.

────────────────────────────────────────

MONOREPO FOUNDATION

Create the backend structure required by the approved architecture.

Support:

apps/

• API Gateway

workers/

• Background workers
• Scheduled workers
• Event consumers

services/

Prepare service boundaries for:

• Identity
• Accounts
• Profiles
• Sessions
• Devices
• Subscriptions
• Billing
• Payments
• Entitlements
• Catalog
• Artists
• Releases
• Tracks
• Media
• Audio Processing
• Rights
• Availability
• Playback
• Downloads
• Playlists
• Library
• Search
• Discovery
• Recommendations
• Radio
• Charts
• Podcasts
• Notifications
• Advertising
• Analytics
• Moderation
• Administration

Do not implement all domain services in this volume.

packages/

• Configuration
• Logging
• Errors
• Validation
• Database
• Redis
• Events
• Queues
• Observability
• API contracts
• Shared types
• Testing utilities

────────────────────────────────────────

APPLICATION BOOTSTRAP

Implement the NestJS application foundation.

Support:

• Application initialization
• Environment loading
• Configuration initialization
• Global validation
• Global exception handling
• Structured logging
• Request IDs
• Correlation IDs
• Trace IDs
• Secure headers
• CORS
• Request size limits
• API versioning
• Graceful shutdown
• Health endpoints
• OpenAPI

Use production-safe defaults.

────────────────────────────────────────

CONFIGURATION

Implement centralized strongly typed configuration.

Support:

APPLICATION

• Environment
• Service name
• Version
• Host
• Port

POSTGRESQL

• Host
• Port
• Database
• Username
• Password
• SSL/TLS
• Connection pool

REDIS

• Host
• Port
• Username
• Password
• TLS

KAFKA / REDPANDA

• Brokers
• Client ID
• Authentication
• TLS
• Consumer groups

BULLMQ

• Redis connection
• Queue defaults
• Retry defaults

S3

• Region
• Bucket
• Endpoint where applicable

SEARCH

• Endpoint
• Authentication
• TLS

PAYMENTS

• Provider configuration
• Webhook configuration

OBSERVABILITY

• Log level
• OpenTelemetry endpoint
• Metrics configuration

NOTIFICATIONS

• FCM configuration
• APNS configuration
• Email-provider configuration

Never hard-code secrets.

Never access environment variables directly throughout business modules.

Validate configuration during startup.

Fail fast when required configuration is invalid.

────────────────────────────────────────

REQUEST CONTEXT

Implement reusable request context containing:

• Request ID
• Correlation ID
• Trace ID
• Service
• Environment
• User ID when authenticated
• Profile ID when authenticated
• Device ID when available

Propagate context into:

• Logs
• Metrics
• Traces
• Kafka events
• Background jobs
• External requests

────────────────────────────────────────

LOGGING

Implement structured JSON logging.

Support:

• Timestamp
• Service
• Environment
• Log level
• Request ID
• Correlation ID
• Trace ID
• Operation
• Duration
• Result
• Safe error details

Never log:

• Passwords
• Access tokens
• Refresh tokens
• Payment secrets
• Private keys
• Encryption keys
• Database credentials
• Sensitive user data unnecessarily

────────────────────────────────────────

ERROR HANDLING

Implement centralized error handling.

Define errors for:

• Validation
• Authentication
• Authorization
• Not found
• Conflict
• Rate limit
• Dependency failure
• Payment-provider failure
• Entitlement failure
• Content-rights failure
• Playback authorization failure
• Internal failure

Use a consistent API error format containing:

• Error code
• Public-safe message
• Request ID
• Correlation ID where appropriate
• Validation details where appropriate

Never expose internal stack traces in production.

────────────────────────────────────────

VALIDATION

Implement centralized validation for:

• Request bodies
• Query parameters
• Path parameters
• Headers
• Configuration
• Event payloads
• Queue payloads
• Webhook payloads

Use strict schemas.

Reject invalid input before business logic executes.

────────────────────────────────────────

SECURITY FOUNDATION

Implement:

• Secure headers
• CORS
• Rate-limiting foundation
• Authentication guards
• Authorization guards
• RBAC foundation
• Permission foundation
• Secret handling
• Audit hooks

Prepare for:

• JWT or secure session architecture
• Refresh tokens
• MFA
• Passkeys
• Device authentication

Never store plaintext passwords.

────────────────────────────────────────

API FOUNDATION

Implement reusable REST API infrastructure.

Support:

• API versioning
• Request validation
• Response conventions
• Error conventions
• Cursor pagination
• Pagination utilities
• Filtering conventions
• Sorting conventions
• Request IDs
• Correlation IDs
• Authentication guards
• Authorization guards
• Rate limiting
• OpenAPI / Swagger

Implement reusable abstractions for:

• Idempotency
• Request timeouts
• Request cancellation
• Safe retries

Do not implement the complete domain API catalog yet.

────────────────────────────────────────

DATABASE FOUNDATION

Implement PostgreSQL integration using Prisma.

Create:

• Prisma configuration
• Database module
• Prisma service
• Connection lifecycle
• Graceful shutdown
• Health checks
• Transaction helper
• Query logging controls
• Migration structure

Define conventions for:

• IDs
• Timestamps
• Soft deletion where justified
• Optimistic concurrency
• Foreign keys
• Constraints
• Indexes
• Decimal values
• Monetary values

Do not create the entire music-domain schema in this volume.

Only create foundation structures required now.

────────────────────────────────────────

PRISMA FOUNDATION

Implement:

• Prisma client lifecycle
• Migration workflow
• Transaction helpers
• Database error translation
• Query logging
• Connection pooling
• Repository boundaries

Prepare for service-specific Prisma clients or domain-specific schemas where appropriate.

Do not allow uncontrolled cross-domain database access.

────────────────────────────────────────

REDIS FOUNDATION

Implement reusable Redis infrastructure.

Support:

• Connection management
• TLS
• Authentication
• Health checks
• Graceful shutdown
• Namespaced keys
• Serialization
• TTL
• Cache abstraction
• Distributed lock abstraction
• Idempotency support

Define conventions for:

• Key naming
• TTL
• Invalidations
• Failure behavior

Redis must never be authoritative for:

• Payments
• Subscriptions
• Entitlements
• Playlists
• Library
• Listening history

────────────────────────────────────────

KAFKA / REDPANDA FOUNDATION

Implement reusable event-streaming infrastructure.

Support:

• Producer lifecycle
• Consumer lifecycle
• Topic configuration
• Consumer groups
• Serialization
• Event metadata
• Event IDs
• Event versions
• Correlation IDs
• Causation IDs where appropriate
• Retry
• Dead-letter handling
• Graceful shutdown

Create an event envelope containing:

• Event ID
• Event type
• Event version
• Aggregate type
• Aggregate ID
• Timestamp
• Correlation ID
• Causation ID where appropriate
• Producer
• Payload

Do not implement the complete domain event catalog yet.

────────────────────────────────────────

TRANSACTIONAL OUTBOX

Implement reusable transactional-outbox infrastructure.

Support:

• Outbox ID
• Event type
• Event version
• Aggregate type
• Aggregate ID
• Payload
• Status
• Retry count
• Next retry timestamp
• Published timestamp
• Error information
• Created timestamp

Define how domain transactions and event publication remain consistent.

Support recovery when:

• Database transaction succeeds
• Event publication fails

Event publishing must be retryable and idempotent.

────────────────────────────────────────

BULLMQ FOUNDATION

Implement background-job infrastructure.

Support:

• Queue registration
• Queue configuration
• Producers
• Workers
• Job IDs
• Retry
• Exponential backoff
• Timeouts
• Concurrency
• Failure handling
• Dead-letter behavior
• Graceful shutdown
• Queue metrics

Prepare reusable infrastructure for future:

• Audio processing
• Search indexing
• Recommendation refresh
• Notification delivery
• Download cleanup
• Rights expiration
• Analytics aggregation
• Report generation

Do not implement full domain jobs in this volume.

────────────────────────────────────────

HEALTH CHECKS

Implement:

• Liveness
• Readiness
• Startup health where appropriate

Support dependency checks for:

• PostgreSQL
• Redis
• Kafka/Redpanda
• BullMQ infrastructure
• Elasticsearch/OpenSearch where applicable
• S3 connectivity where appropriate

Differentiate:

• Process alive
• Service ready
• Dependency degraded

Do not make liveness depend on every external dependency.

────────────────────────────────────────

GRACEFUL SHUTDOWN

Implement safe shutdown for:

• HTTP server
• NestJS modules
• PostgreSQL
• Redis
• Kafka producers
• Kafka consumers
• BullMQ workers

Define shutdown ordering.

Stop accepting new work before closing dependencies.

Allow safe completion or failure of in-flight work.

────────────────────────────────────────

OBSERVABILITY FOUNDATION

Implement:

• Structured logging
• Metrics
• OpenTelemetry tracing
• Correlation IDs
• Request duration metrics
• Error metrics
• Database metrics
• Redis metrics
• Kafka metrics
• Queue metrics
• Health metrics

Use:

• OpenTelemetry
• Prometheus-compatible metrics
• Grafana-compatible dashboards

Create reusable observability utilities.

────────────────────────────────────────

TESTING FOUNDATION

Implement:

• Unit-testing configuration
• Integration-testing configuration
• API testing
• Database testing
• Redis testing
• Kafka testing
• BullMQ testing
• Configuration testing
• Health-check testing

Configure:

• Jest
• Test environments
• Test database strategy
• Fixtures
• Factories
• Test helpers
• Coverage reporting

Tests must be deterministic.

────────────────────────────────────────

LOCAL DEVELOPMENT

Provide local development infrastructure for:

• PostgreSQL
• Redis
• Kafka/Redpanda
• Elasticsearch/OpenSearch where appropriate

Use Docker Compose where appropriate.

The local environment must support backend development and integration tests without requiring AWS.

Do not create production Kubernetes infrastructure here.

Do not create Terraform infrastructure here.

────────────────────────────────────────

API CONTRACT FOUNDATION

Create shared conventions for:

• Request schemas
• Response schemas
• Pagination
• Errors
• Authentication
• Authorization
• Idempotency
• Versioning

Prepare contract packages for future domains:

• Catalog
• Playback
• Playlists
• Library
• Subscriptions
• Search
• Recommendations
• Downloads
• Notifications

Do not implement domain business logic in the contract package.

────────────────────────────────────────

EVENT CONTRACT FOUNDATION

Create reusable conventions for:

• Event naming
• Versioning
• Metadata
• Payload ownership
• Schema validation
• Compatibility

Prepare event-contract packages without implementing the complete domain catalog.

────────────────────────────────────────

DOCUMENTATION

Generate backend foundation documentation for:

• Backend structure
• Local development
• Configuration
• Database workflow
• Prisma workflow
• Redis conventions
• Kafka conventions
• BullMQ conventions
• Logging
• Error handling
• API conventions
• Event conventions
• Observability
• Testing workflow

Documentation must reflect actual generated files.

────────────────────────────────────────

PROJECT INDEX

Maintain the backend Project Index.

Track:

• Current milestone
• Generated files
• Modified files
• Backend modules
• Database objects
• Shared packages
• API infrastructure
• Redis infrastructure
• Kafka infrastructure
• BullMQ infrastructure
• Observability
• Testing
• Local development
• Remaining work
• Dependencies
• Next milestone

Do not claim functionality that has not been implemented.

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 1

Monorepo backend structure and application bootstrap.

BACKEND MILESTONE 2

Configuration, request context, logging, errors, validation, security foundation, and API foundation.

BACKEND MILESTONE 3

PostgreSQL and Prisma foundation.

BACKEND MILESTONE 4

Redis infrastructure.

BACKEND MILESTONE 5

Kafka/Redpanda and event infrastructure.

BACKEND MILESTONE 6

Transactional outbox infrastructure.

BACKEND MILESTONE 7

BullMQ and background-job infrastructure.

BACKEND MILESTONE 8

OpenTelemetry, metrics, health checks, and graceful shutdown.

BACKEND MILESTONE 9

Testing infrastructure and local integration environment.

BACKEND MILESTONE 10

Shared API/event contracts, documentation, hardening, and Project Index.

Each milestone should contain approximately 20–40 files where practical.

Every milestone must compile before proceeding.

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

This volume covers only:

• Backend foundation
• Configuration
• Request context
• Logging
• Errors
• Validation
• Security foundation
• API foundation
• PostgreSQL
• Prisma
• Redis
• Kafka/Redpanda
• Transactional outbox
• BullMQ
• Observability
• Health checks
• Graceful shutdown
• Testing foundation
• Local development
• Shared API/event contracts
• Backend documentation

Do not implement complete:

• Identity
• Accounts
• Profiles
• Subscriptions
• Payments
• Entitlements
• Catalog
• Artists
• Albums
• Tracks
• Rights
• Availability
• Media processing
• Playback
• Downloads
• Playlists
• Library
• Search
• Recommendations
• Radio
• Charts
• Podcasts
• Notifications
• Advertising
• Analytics
• Moderation
• Administration

Those belong to later backend implementation volumes.

────────────────────────────────────────

QUALITY BAR

Treat this backend foundation as critical infrastructure for a globally distributed music streaming platform.

Assume:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Large playback traffic
• Large search traffic
• Large recommendation traffic
• Large analytics traffic
• Global deployment
• High availability
• Zero-downtime operation
• Strict security requirements

Prioritize:

• Correctness
• Reliability
• Security
• Observability
• Scalability
• Testability
• Maintainability
• Clear ownership
• Future service extraction
• Production readiness
