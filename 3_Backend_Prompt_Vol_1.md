# Spotify-Style Music Streaming Platform — Backend Prompt — Volume 1

## ROLE

Act as the senior backend engineering team responsible for implementing the foundational backend of an original, production-grade music streaming platform.

Act as:

* Principal Software Architect
* Staff Backend Engineer
* Database Architect
* Distributed Systems Engineer
* Security Engineer
* QA Engineer
* DevOps Engineer

You are not acting as a programming tutor.

Implement real production-quality backend functionality in the existing repository.

Do not provide pseudo-code, placeholders, TODOs, incomplete implementations, fake integrations, or explanations instead of implementation.

The repository is the source of truth for existing implementation state.

---

# 1. PROJECT

Build the backend foundation for an original Spotify-style music streaming platform.

The backend must eventually support:

* users
* authentication
* profiles
* artists
* albums
* tracks
* genres
* playlists
* libraries
* likes
* follows
* search
* playback
* queues
* playback history
* media processing
* audio streaming
* recommendations
* subscriptions
* notifications
* analytics
* administration

This volume implements the **foundational backend/platform layer**.

Do not attempt to fully implement every music-domain feature in this volume.

Future backend work will build the catalog, playlists, playback, media, search, subscriptions, analytics, and other domains on top of this foundation.

---

# 2. REQUIRED TECHNOLOGY

Use:

* Node.js
* NestJS
* TypeScript
* PostgreSQL
* Prisma
* Redis
* REST
* OpenAPI/Swagger
* BullMQ where appropriate
* Docker-compatible development
* OpenTelemetry-compatible observability

Use Kafka/Redpanda only if the repository already contains it or the implementation of this foundational layer genuinely requires it.

Do not introduce unnecessary infrastructure.

---

# 3. REPOSITORY-FIRST RULE

Before writing code:

1. Inspect the entire repository structure.
2. Identify the backend application.
3. Identify existing NestJS modules.
4. Inspect package manifests.
5. Inspect TypeScript configuration.
6. Inspect NestJS bootstrap configuration.
7. Inspect Prisma schema and migrations.
8. Inspect existing authentication.
9. Inspect Redis integration.
10. Inspect configuration management.
11. Inspect logging.
12. Inspect error handling.
13. Inspect testing.
14. Inspect Docker configuration.
15. Inspect CI/CD.
16. Inspect existing API conventions.
17. Inspect existing documentation.

The actual repository implementation takes precedence over assumptions.

If compatible functionality already exists:

* reuse it
* improve it only when required
* do not duplicate it
* do not rewrite it unnecessarily

If the repository is partially implemented, complete or safely adapt the existing implementation.

---

# 4. ARCHITECTURAL BOUNDARIES

The backend must establish clear boundaries for future domains.

The architecture should be capable of supporting:

* Identity
* User/Profile
* Catalog
* Artist
* Album/Track
* Library
* Playlist
* Playback
* Media
* Search
* Recommendation
* Subscription
* Notification
* Analytics
* Administration

This volume should establish the infrastructure and foundational domain contracts without prematurely implementing all later domains.

Do not create fake modules merely to satisfy a list.

---

# 5. APPLICATION STRUCTURE

Use a maintainable NestJS architecture.

Prefer clear separation between:

* presentation/API
* application services
* domain logic
* persistence
* infrastructure

Apply:

* SOLID
* dependency inversion
* explicit interfaces
* repository abstractions where useful
* DTO validation
* strong typing

Avoid putting business logic directly into controllers.

Controllers should remain thin.

---

# 6. CONFIGURATION

Implement centralized configuration.

Support environment-specific configuration.

Validate required configuration at startup.

Configuration should cover, as applicable:

* application environment
* port
* PostgreSQL
* Redis
* JWT/session configuration
* authentication settings
* CORS
* rate limiting
* logging
* OpenTelemetry
* API configuration
* external provider configuration boundaries

Never hardcode:

* passwords
* API keys
* JWT secrets
* private keys
* database credentials
* provider credentials

Fail safely when required configuration is missing or invalid.

---

# 7. DATABASE

Implement the PostgreSQL/Prisma foundation.

Ensure:

* Prisma client lifecycle is correct
* connection handling is reliable
* graceful shutdown is supported
* migrations are reproducible
* database errors are handled consistently

The database must be authoritative for durable transactional state.

Use:

* foreign keys
* unique constraints
* appropriate indexes
* timestamps
* explicit relationships
* transactions

Avoid unnecessary database coupling to framework-specific code.

---

# 8. INITIAL IDENTITY MODEL

Implement the foundational identity model required for authentication.

At minimum evaluate entities such as:

### User

Possible fields:

* id
* email
* normalized email
* display name
* status
* createdAt
* updatedAt
* deletedAt where appropriate

### Credential

Support secure password authentication if password-based authentication is selected.

Store only secure password hashes.

Never store plaintext passwords.

### Session

Represent authenticated sessions where the selected authentication architecture requires durable session records.

Support:

* session identity
* user ownership
* expiration
* revocation
* timestamps
* device association where appropriate

### Device

Represent authenticated devices where required.

Support:

* user association
* device identifier
* platform
* name/metadata where appropriate
* last seen
* revocation state

Do not collect unnecessary device information.

---

# 9. USER STATUS

Define explicit account lifecycle states.

Examples may include:

* ACTIVE
* SUSPENDED
* DISABLED
* PENDING_VERIFICATION
* DELETED

Use the actual state model appropriate to the repository.

Server-side authorization must account for account status.

A suspended or disabled account must not continue to receive privileged access merely because an existing token remains valid.

---

# 10. USER PROFILE

Implement foundational profile functionality.

Support appropriate fields such as:

* display name
* username where used
* profile image reference
* locale
* timezone
* preferences

Do not expose private account fields unnecessarily.

Separate authentication credentials from profile data.

---

# 11. AUTHENTICATION

Implement secure authentication.

Support, as appropriate:

* registration
* login
* logout
* session renewal
* password hashing
* password verification
* session revocation
* account status checks

Use a modern password hashing algorithm such as Argon2 or another secure repository-compatible choice.

Never implement custom cryptography.

Never return password hashes.

Never expose authentication secrets.

---

# 12. TOKEN/SESSION ARCHITECTURE

Choose a secure session/token architecture compatible with the repository.

If JWTs are used:

* keep signing secrets server-side
* validate issuer/audience where appropriate
* validate expiration
* use appropriate token lifetimes
* support secure refresh/session renewal
* support revocation strategy
* avoid putting unnecessary private data into tokens

If refresh tokens are used:

* rotate them where appropriate
* detect replay where appropriate
* store only secure representations where appropriate
* revoke compromised sessions

Do not store long-lived sensitive tokens insecurely on the client.

---

# 13. DEVICE AND SESSION MANAGEMENT

Provide server-side mechanisms for:

* listing sessions/devices
* revoking a session
* revoking other sessions
* logout
* invalidating compromised sessions

Ensure one user cannot access another user's sessions.

Prevent session enumeration.

Do not expose internal security metadata unnecessarily.

---

# 14. AUTHORIZATION

Implement server-side authorization foundations.

Support:

* authenticated user
* administrator
* future artist/content-management roles

Do not rely on client-side authorization.

Define reusable guards/decorators/policies as appropriate.

Every protected resource must verify:

* authentication
* account status
* ownership
* role
* permission

where relevant.

---

# 15. ADMIN FOUNDATION

Create the authorization boundary required for future administration.

Administrative permissions must be explicit.

Do not create an unrestricted "admin" backdoor.

Administrative operations should be auditable.

Do not expose administrative APIs to ordinary users.

---

# 16. CUSTOMER/USER APIs

Implement appropriate versioned REST endpoints for foundational account operations.

Potential endpoints include:

* registration
* login
* logout
* session refresh
* current user
* profile
* sessions/devices
* session revocation

Use the repository's established route conventions where they already exist.

Do not blindly create duplicate routes.

---

# 17. DTOs

Use explicit DTOs for API input and output.

Validate:

* email
* password requirements
* display names
* usernames
* IDs
* pagination parameters
* request payload sizes

Reject malformed input.

Do not expose Prisma/database entities directly from controllers.

---

# 18. ERROR HANDLING

Implement a consistent API error model.

Errors should provide:

* stable error code
* safe human-readable message
* HTTP status
* request/correlation ID where appropriate

Do not expose:

* stack traces
* SQL queries
* database credentials
* internal filesystem paths
* provider secrets
* sensitive authentication information

Differentiate:

* validation errors
* authentication failures
* authorization failures
* not found
* conflict
* rate limiting
* dependency failures
* unexpected internal failures

---

# 19. REQUEST CONTEXT

Implement appropriate request context.

Support:

* request ID
* correlation ID
* authenticated user identity
* device/session identity where appropriate
* trace context

Make this information available to:

* logging
* auditing
* observability
* downstream operations

Do not trust arbitrary client-provided security identities.

---

# 20. LOGGING

Implement structured server-side logging.

Logs should include useful operational metadata such as:

* timestamp
* level
* service
* environment
* request ID
* correlation ID
* route
* status
* latency
* error code

Never log:

* passwords
* access tokens
* refresh tokens
* private signing keys
* API secrets
* database credentials
* raw authorization headers
* unnecessary private listening data

---

# 21. HEALTH CHECKS

Implement health endpoints appropriate for the backend.

Distinguish between:

### Liveness

Whether the process is alive.

### Readiness

Whether required dependencies are available enough to accept traffic.

Evaluate:

* PostgreSQL
* Redis
* other actually required dependencies

Do not make noncritical dependencies unnecessarily block readiness.

Health endpoints must not leak secrets or internal credentials.

---

# 22. REDIS FOUNDATION

Implement the Redis integration.

Provide safe:

* connection handling
* configuration
* lifecycle management
* error handling
* graceful shutdown

Establish conventions for:

* key naming
* TTL
* serialization
* invalidation

Redis may later support:

* caching
* rate limiting
* playback state
* queues
* distributed coordination
* temporary state

Do not make Redis the authoritative store for critical user data.

---

# 23. RATE LIMITING

Implement foundational rate limiting for security-sensitive endpoints.

Prioritize:

* registration
* login
* password recovery
* token/session operations
* sensitive account operations

Rate limits should account for abuse patterns where appropriate.

Avoid a rate-limit implementation that can be trivially bypassed by manipulating arbitrary request headers.

Use Redis when distributed rate limiting is required.

Return appropriate rate-limit responses.

---

# 24. SECURITY HEADERS AND HTTP SECURITY

Implement appropriate HTTP security controls.

Evaluate:

* security headers
* CORS
* request size limits
* content-type validation
* trusted proxy behavior
* secure cookies where used
* CSRF protections where cookie authentication requires them

CORS must not become an unrestricted production configuration.

Do not disable security controls simply to make local development convenient.

---

# 25. INPUT VALIDATION

Validate every externally controlled input.

Protect against:

* SQL injection
* command injection
* path traversal
* XSS
* malicious payloads
* oversized requests
* invalid IDs
* malformed pagination
* unexpected enum values

Prisma parameterization must not be treated as a reason to skip application validation.

---

# 26. API VERSIONING

Establish a stable API versioning strategy.

Use a version such as:

`/api/v1/...`

unless the repository already uses a different compatible convention.

Document the versioning behavior.

Avoid breaking changes to existing APIs without a deliberate migration strategy.

---

# 27. OPENAPI

Configure Swagger/OpenAPI documentation.

Document:

* authentication
* endpoints
* request DTOs
* response DTOs
* error responses
* pagination
* authorization requirements

Keep API documentation synchronized with implementation.

Do not document endpoints that do not actually exist.

---

# 28. PAGINATION FOUNDATION

Establish a consistent pagination model.

Support cursor pagination where appropriate for large datasets.

Avoid unrestricted result sets.

Define:

* page/cursor input
* maximum page size
* stable ordering
* next cursor
* invalid cursor behavior

The design must support future:

* playlists
* tracks
* library items
* playback history
* notifications
* search results

---

# 29. IDEMPOTENCY FOUNDATION

Establish infrastructure for idempotent mutation requests where appropriate.

Evaluate idempotency for:

* account mutations
* playlist mutations later
* likes later
* playback events
* subscription webhooks
* media-processing jobs

Do not force idempotency onto read operations unnecessarily.

If implementing an idempotency record system, define:

* key
* user/session ownership
* request fingerprint where appropriate
* status
* response
* expiration
* conflict behavior

Prevent one user from replaying another user's idempotency key.

---

# 30. AUDIT EVENTS

Implement an audit foundation.

Audit security-sensitive actions such as:

* login
* logout
* failed authentication where useful
* password changes
* session revocation
* account status changes
* administrative actions

An audit record should contain appropriate:

* event ID
* actor
* action
* target
* timestamp
* request/correlation ID
* metadata

Do not store unnecessary secrets or sensitive payloads.

Audit records should not be casually mutable.

---

# 31. BACKGROUND JOB FOUNDATION

Establish BullMQ infrastructure if it is not already implemented.

Provide safe support for future jobs such as:

* media processing
* search indexing
* analytics
* notifications
* cleanup
* recommendation processing

Define configuration for:

* Redis connection
* queues
* worker concurrency
* retries
* backoff
* timeouts
* graceful shutdown

Do not create meaningless queues with no actual purpose.

---

# 32. JOB SAFETY

All background-job implementations must account for:

* duplicate delivery
* worker crashes
* retries
* timeouts
* partial failure
* idempotency
* graceful shutdown

Do not assume a job executes exactly once.

Do not acknowledge successful completion before durable work is actually complete.

---

# 33. OUTBOX FOUNDATION

If the repository architecture requires domain events, implement a durable transactional outbox foundation.

The outbox must allow future domain operations to:

1. update PostgreSQL state
2. create an outbox event
3. commit both atomically
4. publish asynchronously
5. mark the event appropriately

The architecture must tolerate:

* retries
* duplicate publication
* worker crashes
* delayed delivery

Do not publish critical events only after a transaction without a durable recovery mechanism.

---

# 34. EVENT CONTRACT FOUNDATION

If event infrastructure is present, establish a common event envelope containing appropriate:

* event ID
* event type
* version
* aggregate/entity ID
* producer
* timestamp
* correlation ID
* trace context
* payload

Do not expose secrets or unnecessary private user data in events.

Do not create Kafka/Redpanda infrastructure merely for an empty event system.

---

# 35. DATABASE TRANSACTIONS

Use explicit transactions for operations requiring atomicity.

Examples include:

* account creation with related records
* session rotation
* session revocation
* security-sensitive state changes
* idempotency state transitions
* audit operations where required

Avoid long-running external network calls inside database transactions.

---

# 36. CONCURRENCY

Account for concurrency in:

* login/session rotation
* session revocation
* account updates
* idempotency
* rate limiting
* audit creation

Avoid lost updates.

Use database constraints and transactional logic where appropriate.

---

# 37. PRIVACY

Protect:

* email addresses
* profile data
* sessions
* device information
* account security information

Do not expose another user's information through:

* IDs
* search parameters
* pagination
* predictable routes
* error messages

Design future privacy boundaries for:

* playlists
* listening history
* likes
* recommendations
* analytics

---

# 38. SECURITY TESTING

Add tests covering at minimum:

### Authentication

* valid registration
* invalid registration
* duplicate account
* valid login
* invalid password
* disabled account
* suspended account
* expired session
* revoked session

### Authorization

* unauthenticated access
* authenticated access
* user isolation
* administrative access
* non-admin administrative denial

### Session Security

* session creation
* session renewal
* session revocation
* revocation of another session
* unauthorized session access

### Validation

* malformed email
* weak/invalid password
* oversized payload
* invalid IDs
* invalid pagination

### Rate Limiting

* repeated login attempts
* repeated sensitive operations
* distributed rate limiting if implemented

### Security Regression

* IDOR
* privilege escalation
* token leakage
* secret leakage
* unsafe error responses

---

# 39. TEST INFRASTRUCTURE

Create deterministic tests.

Use:

* isolated test database
* controlled fixtures/factories
* predictable configuration
* cleanup between tests
* test-specific secrets

Do not use production data.

Do not depend on a developer's local environment.

Do not write tests that pass only because security controls are disabled.

---

# 40. DATABASE MIGRATIONS

Create or update Prisma migrations safely.

Validate:

* clean database migration
* migration from existing repository state
* schema consistency
* indexes
* constraints
* rollback/recovery strategy where supported

Never silently delete production data.

Do not reset databases as part of normal application startup.

---

# 41. DOCKER COMPATIBILITY

Ensure the backend can run in a reproducible development/container environment.

If Docker configuration exists:

* inspect it
* reuse it
* update only where necessary

If required, provide appropriate backend container configuration.

Do not embed secrets in Dockerfiles or compose files.

---

# 42. GRACEFUL SHUTDOWN

Implement graceful shutdown for:

* HTTP server
* PostgreSQL/Prisma
* Redis
* BullMQ workers
* other active resources

Workers should stop accepting new work and allow active safe work to finish or terminate according to the job contract.

Avoid corrupting state during shutdown.

---

# 43. OBSERVABILITY

Prepare the backend for distributed observability.

Implement or establish compatibility with:

* OpenTelemetry
* structured logging
* metrics
* tracing

Instrument important foundational operations:

* HTTP
* PostgreSQL
* Redis
* authentication
* background jobs

Do not collect unnecessary sensitive information.

---

# 44. PERFORMANCE

Avoid:

* N+1 queries
* unrestricted database queries
* unrestricted pagination
* unnecessary Redis calls
* expensive synchronous work inside HTTP requests

Database indexes must support actual access patterns.

Authentication and session operations should remain efficient under high concurrency.

Do not prematurely optimize without evidence.

---

# 45. DOCUMENTATION

Update documentation for the actual implementation.

Include:

* backend setup
* required environment variables
* database setup
* migrations
* Redis
* test commands
* API documentation
* authentication behavior
* development workflow

Do not document features that were not implemented.

---

# 46. PROHIBITED IMPLEMENTATION

Do not:

* implement fake authentication
* store plaintext passwords
* hardcode secrets
* expose JWT secrets
* expose password hashes
* trust client authorization
* use Redis as the only durable account store
* create fake payment behavior
* create fake media streaming
* create fake catalog data as production functionality
* invent provider capabilities
* create TODO placeholders
* create pseudo-code
* weaken security to make tests pass
* bypass repository conventions without justification

---

# 47. VALIDATION

Before declaring the work complete:

Run the repository's actual applicable:

* formatting
* linting
* TypeScript checks
* unit tests
* integration tests
* API tests
* Prisma validation
* migration validation
* build
* Docker validation where applicable

Inspect changed files.

Confirm:

* no secrets were added
* no unrelated files were modified unnecessarily
* no duplicate implementation was introduced
* APIs match their DTOs
* migrations match the schema
* tests actually execute
* authentication works through the real implementation
* authorization is enforced server-side

---

# 48. SCOPE LIMIT

This volume establishes the backend foundation.

Do not prematurely implement the full:

* music catalog
* artist management
* album/track management
* playlists
* playback engine
* audio transcoding
* HLS streaming
* search
* recommendation engine
* subscriptions
* notifications
* analytics platform

Those areas require their own implementation work.

However, the foundation must be designed so those domains can integrate cleanly without redesigning the authentication, configuration, database, API, security, observability, and job infrastructure.

---

# 49. BACKWARD COMPATIBILITY

If the repository already contains APIs or functionality:

* preserve compatible contracts
* avoid unnecessary breaking changes
* migrate deliberately
* update consumers when a breaking change is genuinely necessary
* document meaningful changes

Never silently remove existing functionality.

---

# 50. COMPLETION REPORT

At the end, provide a factual report containing:

### Repository inspected

List the important existing backend components discovered.

### Implemented

List actual modules, files, database changes, APIs, infrastructure, and tests implemented.

### Validation

List the actual commands executed and their results.

### Remaining work

List functionality intentionally deferred to later backend volumes.

### External configuration

Identify external services or environment variables required.

### Issues

Report real failures, limitations, or unresolved issues.

Do not claim production readiness unless the repository evidence supports it.

Do not claim a test passed unless it actually passed.

Do not claim an external provider integration works unless it was actually configured and validated.

---

# 51. STANDALONE REQUIREMENT

This prompt is fully standalone.

It must not depend on:

* a previous prompt
* a previous architecture response
* an assumed approved architecture document
* hidden conversation context
* undocumented decisions

The repository is the implementation source of truth.

Inspect the repository and adapt the implementation accordingly.

---

# FINAL OBJECTIVE

Leave the repository with a secure, maintainable, production-quality backend foundation capable of supporting the complete music-streaming platform.

The foundation must provide reliable:

* application configuration
* PostgreSQL/Prisma
* Redis
* identity
* authentication
* sessions
* devices
* authorization
* user profiles
* API infrastructure
* validation
* error handling
* rate limiting
* audit logging
* health checks
* background jobs
* event/outbox foundations where justified
* observability
* testing
* migrations
* graceful shutdown

Implement real functionality.

Do not leave placeholders.

Do not invent completed functionality.

Do not claim anything that the repository and validation do not support.
