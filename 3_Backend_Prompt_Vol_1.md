# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — BACKEND VOLUME 1

## ROLE

Act as the complete senior backend engineering organization responsible for implementing the production backend foundation and core transactional domains of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

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

Do not rely on another AI conversation being available.

Inspect the repository before making changes and integrate the implementation with the actual repository state.

Implement the requested backend functionality completely, with production-grade validation, testing, security, observability, reliability, and documentation.

---

# PROJECT

Build the production backend foundation and core transactional domains for an original global music streaming platform.

The backend must support:

* anonymous and authenticated users
* listener accounts
* artist accounts
* role-based and resource-based authorization
* music catalog management
* artists
* albums
* releases
* tracks
* genres
* user profiles
* playlists
* playlist items
* listener libraries
* likes
* follows
* listening history foundations
* playback authorization foundations
* subscription-aware authorization
* administrative capabilities
* moderation foundations
* notifications foundations
* event publishing
* background jobs
* Redis-backed infrastructure
* PostgreSQL persistence
* API documentation
* structured error handling
* observability
* automated testing

This volume is responsible for the application foundation and the core transactional backend required by later backend functionality.

Do not implement unrelated frontend or mobile functionality.

Do not create production Kubernetes or Terraform infrastructure in this task unless an existing repository integration requires a narrowly scoped configuration change.

---

# TECHNOLOGY DIRECTION

Use:

## Backend

* NestJS
* TypeScript
* REST
* WebSockets only where required by the current scope
* OpenAPI/Swagger
* PostgreSQL
* Prisma
* Redis
* Kafka or Redpanda integration boundaries
* BullMQ where background jobs are required by the current scope

Use the repository's existing package versions when compatible.

Do not upgrade unrelated dependencies merely for preference.

## Security

Use production-grade authentication and authorization mechanisms appropriate to the selected backend architecture.

Secrets must come from environment/configuration management.

## Validation

Use strong runtime validation at external boundaries.

Where the repository uses class-validator, DTO validation, Zod, or another established convention, preserve the repository's compatible convention rather than introducing unnecessary parallel validation systems.

---

# SOURCE OF TRUTH

Before implementing anything:

1. Inspect the repository structure.
2. Inspect the backend package configuration.
3. Inspect existing NestJS modules.
4. Inspect Prisma schema and migrations.
5. Inspect existing authentication code.
6. Inspect configuration handling.
7. Inspect existing API conventions.
8. Inspect tests.
9. Inspect Redis integration.
10. Inspect event and queue infrastructure already present.
11. Inspect documentation.
12. Identify existing compatible implementations.

The repository defines what currently exists.

This prompt defines what this backend volume must achieve.

Do not assume that an earlier architecture prompt is available to the implementation agent.

Do not recreate working infrastructure merely because it is described again here.

Preserve compatible existing behavior unless a required implementation change makes modification necessary.

---

# BACKEND RESPONSIBILITY

This backend volume is responsible for establishing:

* NestJS application structure
* configuration
* database integration
* migration discipline
* shared API infrastructure
* security foundations
* authentication
* authorization
* user/profile management
* artist management foundations
* catalog management foundations
* album/release management
* track management
* playlist management
* listener library management
* core transactional events
* Redis foundations
* background job foundations where required
* audit foundations
* operational error handling
* observability foundations
* automated testing

The implementation must establish stable contracts for later backend domains.

---

# BACKEND APPLICATION ARCHITECTURE

Implement a modular backend architecture with clear boundaries.

Use cohesive NestJS modules.

At minimum evaluate modules for:

* Config
* Database
* Health
* Identity
* Users
* Artists
* Catalog
* Albums/Releases
* Tracks
* Playlists
* Library
* Playback foundation
* Subscriptions foundation
* Notifications foundation
* Administration
* Audit
* Events
* Jobs
* Redis
* Search integration boundary
* Observability

Do not create empty modules merely because they appear on a list.

Every module included in this implementation must contain meaningful functionality or a concrete infrastructure integration.

Keep:

* transport/controller logic
* application orchestration
* domain rules
* persistence
* infrastructure integrations

appropriately separated.

Avoid placing domain logic directly into controllers.

---

# CONFIGURATION SYSTEM

Implement centralized configuration.

Configuration must support values such as:

* environment
* application name
* API version
* server port
* database URL
* Redis URL
* event-broker configuration
* queue configuration
* JWT/authentication configuration
* CORS configuration
* rate-limit configuration
* logging configuration
* OpenTelemetry configuration
* object-storage configuration where required by current scope
* payment-provider configuration where required by current scope

Validate required configuration during application startup.

Do not silently boot with missing security-critical configuration.

Do not hardcode secrets.

Use typed configuration access.

Separate:

* local development
* test
* staging
* production

where the existing repository configuration supports those environments.

---

# DATABASE INTEGRATION

Implement PostgreSQL access through Prisma.

Configure:

* database client lifecycle
* connection handling
* graceful shutdown
* transaction support
* health checks
* error translation
* migration integration

Do not instantiate uncontrolled Prisma clients throughout the application.

Use a managed database service/provider abstraction consistent with NestJS lifecycle management.

Ensure graceful shutdown closes database resources correctly.

---

# DATABASE MODEL FOUNDATION

Implement the transactional data model required by this backend volume.

At minimum cover the authoritative representations for:

* User
* UserCredential where applicable
* UserSession
* Device
* Role
* Permission
* Artist
* ArtistMember/Representative where applicable
* Album
* Release
* Track
* Genre
* Playlist
* PlaylistItem
* PlaylistCollaborator where applicable
* UserLibrary or equivalent library representations
* TrackLike
* ArtistFollow
* AlbumSave
* AuditEvent

Refine entity structure where necessary to produce a sound relational design.

Use:

* primary keys
* foreign keys
* uniqueness
* indexes
* check constraints where appropriate
* timestamps
* soft deletion only where justified
* explicit lifecycle fields

Do not create redundant ownership of the same business entity.

---

# IDENTIFIER STRATEGY

Implement a consistent identifier strategy.

Identifiers must:

* remain globally unique within their domain
* be safe to expose through APIs
* work efficiently with PostgreSQL indexes
* work in event payloads
* avoid accidental reliance on sequential public identifiers

Use the repository's established identifier convention when compatible.

Do not introduce different ID strategies for different domains without a technical reason.

---

# USER DOMAIN

Implement account and profile functionality required by the current scope.

Support:

* account creation
* user retrieval
* profile update
* locale/preferences foundations
* account status
* account deletion workflow foundation
* account suspension support
* privacy-related profile controls where applicable

Separate authentication credentials from public profile data.

Do not expose sensitive account fields through ordinary user endpoints.

Protect private information at query and serialization boundaries.

---

# AUTHENTICATION

Implement production-grade authentication.

Support, as applicable:

* registration
* login
* logout
* access-token issuance
* refresh-token rotation
* session creation
* session listing/revocation
* device association
* password change
* password reset foundation
* account verification foundation
* account disablement

Use secure password hashing.

Never store plaintext passwords.

Never return password hashes to clients.

Never log credentials.

Protect authentication endpoints with suitable rate limits and abuse controls.

---

# TOKEN AND SESSION SECURITY

Define and implement:

* access-token lifetime
* refresh-token lifetime
* refresh rotation
* revocation
* replay detection where appropriate
* device/session linkage
* session expiration
* logout behavior

Do not rely solely on deleting client-side tokens.

The server must be capable of invalidating sessions.

Sensitive token material must not appear in application logs.

Use secure secret configuration.

---

# AUTHORIZATION

Implement server-side authorization.

Support:

* role-based permissions
* resource ownership
* resource-level access
* action-level access

At minimum evaluate:

* listener
* premium listener
* artist
* artist representative
* moderator
* support operator
* administrator
* platform operator

Implement authorization guards/policies/interceptors using the repository's architecture.

Authorization must occur before sensitive resource access.

Prevent:

* IDOR
* privilege escalation
* cross-user data access
* unauthorized artist administration
* unauthorized playlist modification
* unauthorized catalog mutation
* unauthorized administrative operations

Do not trust role information supplied by clients.

---

# API FOUNDATION

Establish consistent REST API behavior.

Implement:

* API prefix/versioning
* global validation
* standardized serialization
* structured errors
* request IDs
* correlation IDs
* consistent HTTP status semantics
* OpenAPI documentation
* authentication middleware/guards
* authorization guards
* rate limiting foundations
* health endpoints

Controllers must remain thin.

Use DTOs/request models at external boundaries.

Do not expose Prisma models directly as API contracts.

---

# API ERROR CONTRACT

Implement a stable error response shape containing appropriate fields such as:

* stable error code
* message
* request ID
* validation details where applicable
* retryability metadata where useful

Do not expose:

* database stack traces
* SQL statements
* internal provider credentials
* stack traces in production
* secret configuration
* sensitive authorization internals

Translate expected domain errors into stable HTTP responses.

Unexpected errors must be captured by centralized exception handling and observability.

---

# REQUEST CONTEXT

Implement request context handling for:

* request ID
* correlation ID
* authenticated user identity
* device/session context where applicable
* trace context

Ensure context can be included in:

* structured logs
* metrics
* traces
* domain operations
* events
* jobs

Do not place secrets or unnecessary personal information into request context.

---

# VALIDATION

Validate all externally supplied input.

Validate:

* authentication input
* identifiers
* pagination
* sorting
* filters
* playlist fields
* artist fields
* album fields
* track fields
* library operations
* administrative input

Reject malformed input before business logic execution.

Do not rely solely on TypeScript static typing for external input.

---

# PAGINATION

Implement a reusable pagination strategy appropriate for large datasets.

Support cursor-based pagination where required for:

* playlists
* playlist items
* artist catalogs
* albums
* tracks
* user library
* follows
* administrative collections
* audit collections

Define:

* page-size limits
* default page size
* stable ordering
* cursor encoding
* invalid cursor handling

Never permit unbounded collection retrieval.

---

# USER LIBRARY

Implement transactional library operations for:

* liking/unliking tracks
* saving/unsaving albums
* following/unfollowing artists

Operations must be idempotent where appropriate.

Use database constraints to protect uniqueness.

Avoid race conditions during concurrent like/follow requests.

Return stable API semantics for already-existing or already-removed relationships.

Emit appropriate domain events after successful authoritative mutations.

Do not emit duplicate business events for transactions that did not produce a state change unless the event semantics explicitly require it.

---

# PLAYLIST DOMAIN

Implement production playlist functionality.

Support:

* playlist creation
* retrieval
* update
* deletion
* visibility
* ownership
* playlist items
* adding tracks
* removing tracks
* reordering
* playlist metadata
* collaboration foundations where included by the repository architecture

Protect private playlists.

Only authorized users may mutate collaborative playlists.

Define ownership rules explicitly.

---

# PLAYLIST CONCURRENCY

Protect playlist mutations from conflicting concurrent updates.

Use appropriate mechanisms such as:

* transaction boundaries
* optimistic version checks
* unique constraints
* deterministic ordering
* atomic update operations

Do not allow stale clients to silently overwrite unrelated playlist changes.

For collaborative playlists, preserve the integrity of item ordering and membership under concurrent modifications.

Do not rewrite an entire playlist unnecessarily when a targeted mutation is sufficient.

---

# PLAYLIST ITEM ORDERING

Implement a scalable ordering representation.

The strategy must support frequent:

* insertion
* deletion
* reordering

without requiring expensive full-list rewrites on every request.

Use the selected repository-compatible ordering model.

Define behavior for:

* first insertion
* insertion between items
* moving items
* duplicate ordering values
* rebalancing when required

Rebalancing must be safe under concurrent access.

---

# MUSIC CATALOG

Implement transactional catalog foundations for:

* artists
* albums
* releases
* tracks
* genres

Support appropriate lifecycle fields.

Catalog resources must have explicit visibility/publication states.

Do not expose unpublished or restricted content to ordinary listeners.

---

# ARTISTS

Implement artist functionality such as:

* artist creation
* artist retrieval
* artist profile update
* artist representative membership
* artist status
* artist verification foundation
* artist catalog relationships

Artist-management APIs must require appropriate authorization.

Do not allow arbitrary users to modify verified artist data.

---

# ALBUMS AND RELEASES

Implement album/release operations supporting:

* creation
* metadata
* artwork references
* release date
* status
* track association
* publication state
* visibility

Distinguish a logical album from individual release variants when the data model requires it.

Do not expose drafts as published catalog content.

---

# TRACKS

Implement track functionality supporting:

* metadata
* artist association
* album/release association
* duration
* explicit-content classification
* genre/category relationships
* availability state
* publication state
* media-asset references where applicable

Do not mark a track playable until the corresponding media pipeline state allows it.

The backend must treat media availability as a controlled state, not an arbitrary client-provided boolean.

---

# CATALOG AUTHORIZATION

Define server-side access rules for:

* creating catalog content
* editing catalog content
* publishing
* withdrawing
* restricting
* archiving

Separate:

* ordinary listener access
* artist management
* moderator actions
* administrator actions

Every privileged catalog mutation must be auditable.

---

# CATALOG EVENTS

Publish appropriate domain events after successful transactional changes.

Events should include sufficient metadata for downstream systems such as:

* search indexing
* analytics
* recommendation pipelines
* notifications
* moderation
* media-processing workflows

Do not publish events before the authoritative transaction has successfully committed.

Where consistency between database transaction and event publication is required, implement a transactional outbox.

---

# TRANSACTIONAL OUTBOX

Implement an outbox mechanism where appropriate for this backend volume.

The outbox must support:

* event ID
* aggregate ID
* event type
* event version
* payload
* created timestamp
* processing state
* attempt count
* next-attempt timestamp
* error metadata where appropriate

Publishing must be retryable.

Duplicate publication must be safely handled by consumers.

Do not delete outbox records before the configured retention/reconciliation policy allows it.

Do not silently discard failed events.

---

# EVENT PUBLISHING

Integrate with Kafka or Redpanda through a controlled infrastructure abstraction.

The event publishing layer must define:

* topic
* event type
* version
* key
* envelope
* correlation context
* trace context
* serialization
* error handling

The backend must not scatter broker-specific implementation details throughout domain services.

Use application-level event contracts.

Do not publish arbitrary database objects as event payloads.

Publish only the information consumers legitimately require.

---

# REDIS FOUNDATION

Implement the Redis infrastructure layer where not already present.

Provide controlled access for:

* caching
* rate limiting
* ephemeral state
* session support where applicable
* distributed coordination where justified

Define namespaced keys.

Use explicit TTLs.

Handle Redis failure appropriately.

Do not make Redis the only source of truth for user accounts, playlists, catalog, subscriptions, or financial records.

---

# CACHING

Implement caching only for data where it materially improves performance.

For every implemented cache define:

* key
* TTL
* invalidation trigger
* stale behavior
* failure fallback

Do not cache authorization decisions indefinitely.

Do not cache mutable private information without considering invalidation and privacy.

Do not introduce cache complexity without a measurable access pattern.

---

# RATE LIMITING

Implement rate limiting for security-sensitive endpoints.

At minimum protect:

* login
* registration
* password reset
* token refresh
* public search
* playlist mutation endpoints
* high-frequency library actions
* sensitive administrative operations

Use Redis-backed coordination where appropriate.

Define behavior if Redis is unavailable.

Rate limits must not be trivially bypassed through a different equivalent endpoint.

---

# AUDIT LOGGING

Implement an audit subsystem for sensitive operations.

Audit at minimum:

* authentication security events
* session revocation
* account suspension
* privileged catalog changes
* publishing/withdrawal
* administrative operations
* moderation actions
* subscription-support actions where applicable

Audit records should include:

* actor
* action
* target
* timestamp
* outcome
* correlation/request ID
* relevant metadata

Never record:

* passwords
* access tokens
* refresh tokens
* secret keys
* payment credentials

---

# SUBSCRIPTION FOUNDATION

Establish backend foundations for subscription-aware authorization without implementing the complete payment lifecycle in this volume.

The backend should support a durable representation of:

* subscription
* plan
* status
* provider reference where applicable
* entitlement state

The representation must allow later payment-provider integration without redesigning the user/account model.

Do not trust client-submitted premium flags.

Premium access must be determined from server-authoritative state.

---

# PLAYBACK FOUNDATION

Establish transactional foundations required by later playback implementation.

Support durable representations for:

* playback session
* device
* playback entitlement checks
* durable playback checkpoints where appropriate

Do not implement bulk media streaming through REST.

Do not expose storage credentials.

The playback subsystem must remain compatible with a future CDN/signed-access architecture.

---

# NOTIFICATION FOUNDATION

Create the backend boundary required for asynchronous notifications without implementing every delivery provider in this volume.

The architecture must permit:

* notification creation
* recipient targeting
* notification type
* priority
* delivery state
* read state
* provider-independent payload
* asynchronous processing

Keep provider-specific delivery out of core business logic.

---

# BACKGROUND JOB FOUNDATION

Where the repository already contains BullMQ infrastructure or where current backend functionality requires background processing, establish typed queue abstractions.

Potential current jobs include:

* outbox publishing
* catalog indexing triggers
* audit maintenance
* cleanup
* notification preparation

Every job must define:

* payload
* timeout
* retry policy
* backoff
* idempotency
* concurrency
* failure handling
* observability

Do not create speculative workers that have no current responsibility.

---

# SEARCH INTEGRATION BOUNDARY

Establish the application-level interface required for future search indexing.

The transactional catalog module must be able to emit change events without depending synchronously on the search cluster.

Do not make Elasticsearch/OpenSearch a required dependency for basic transactional catalog mutations.

Search failures must not roll back valid catalog transactions.

---

# SECURITY

Apply security controls across every implemented endpoint and domain.

Protect against:

* authentication bypass
* IDOR
* privilege escalation
* SQL/ORM injection
* malicious input
* brute force
* credential stuffing
* token replay
* session theft
* rate-limit bypass
* secret exposure

Use:

* secure password hashing
* validated JWT/token handling
* authorization guards
* resource ownership checks
* rate limiting
* secure headers
* safe serialization
* configuration validation
* secure logging
* dependency hygiene

Never bypass authorization merely to make tests or development easier.

---

# DATABASE SECURITY

Protect the data layer through:

* parameterized Prisma operations
* least-privilege database credentials
* migration control
* proper constraints
* sensitive-column handling
* access boundaries

Avoid exposing internal database exception messages in public APIs.

Use transaction boundaries deliberately.

---

# PRIVACY

Protect:

* credentials
* sessions
* personal profile data
* listening relationships
* private playlists
* private library information
* subscription data
* administrative data

Personal resources must be scoped to the authenticated user.

Do not return private data through public catalog endpoints.

Account deletion must have a defined path for dependent data and downstream asynchronous cleanup.

---

# ERROR AND FAILURE HANDLING

Implement predictable failure behavior for:

* invalid input
* database constraint errors
* missing resources
* unauthorized requests
* forbidden requests
* duplicate mutations
* Redis unavailable
* event-broker unavailable
* queue unavailable
* external provider failure

Critical transactional operations must fail safely.

Do not swallow exceptions.

Do not return success after an authoritative database mutation failed.

Use retries only where retrying is safe.

---

# OBSERVABILITY

Instrument the backend with:

* structured logs
* metrics
* traces
* request IDs
* correlation IDs

Trace:

* HTTP requests
* database operations where appropriate
* Redis operations
* event publication
* queue execution
* authentication flows
* privileged operations
* major catalog mutations

Capture useful metrics for:

* request rate
* latency
* errors
* authentication failures
* authorization failures
* database latency
* Redis latency
* queue depth
* event-publishing failures
* cache hit/miss
* rate-limit events

Do not log sensitive credentials or private user content unnecessarily.

---

# HEALTH AND READINESS

Implement production health endpoints.

Separate:

* liveness
* readiness
* dependency health

Readiness must verify only dependencies that are required for the instance to serve correctly.

Do not make optional systems such as analytics unnecessarily determine application readiness.

Health responses must not reveal sensitive infrastructure information to unauthenticated public callers.

---

# TESTING

Implement comprehensive automated backend tests.

At minimum, cover:

* user registration
* authentication
* token refresh
* logout/revocation
* authorization
* resource ownership
* user profile access
* artist management
* catalog creation/update
* publication rules
* playlist creation
* playlist mutation
* playlist concurrency
* library operations
* duplicate requests
* validation failures
* forbidden operations
* not-found behavior
* audit logging
* transactional behavior
* outbox creation
* event publishing behavior
* Redis failure behavior where practical
* rate limiting
* subscription entitlement checks

Use:

* unit tests for domain/application logic
* integration tests for database behavior
* API tests for HTTP contracts

Do not replace meaningful integration tests with excessive mocks.

---

# DATABASE MIGRATIONS

Create complete Prisma migrations for schema changes.

Validate:

* migration ordering
* foreign-key integrity
* index creation
* uniqueness
* rollback considerations
* development bootstrap

Do not manually alter production database state outside migration workflows.

Avoid destructive migrations without a safe migration strategy.

---

# API DOCUMENTATION

Maintain OpenAPI/Swagger documentation for implemented APIs.

Document:

* request schemas
* response schemas
* authentication requirements
* authorization expectations where useful
* pagination
* errors
* examples where they materially improve integration

The API documentation must reflect actual behavior.

Do not document endpoints that do not exist.

---

# PERFORMANCE

Optimize core transactional operations appropriately.

Pay particular attention to:

* authentication
* user retrieval
* playlist retrieval
* playlist mutation
* library operations
* catalog queries

Avoid:

* N+1 queries
* unbounded joins
* unnecessary full-table scans
* returning large payloads by default
* loading entire playlists into memory
* duplicate database calls

Use indexes based on real query paths.

Measure before introducing complicated caching.

---

# RELIABILITY

Implement:

* graceful shutdown
* database connection lifecycle
* timeout handling
* safe retries
* idempotent mutations
* event publishing recovery
* job retry handling
* dependency failure handling

Ensure an application restart does not lose durable business state.

Ensure background jobs can resume after worker termination where the queue system supports it.

---

# IMPLEMENTATION BOUNDARIES

This backend volume owns the backend foundation and core transactional domains.

Implement only the backend scope described here.

Do not build:

* complete web UI
* complete mobile UI
* complete media transcoding pipeline
* complete CDN infrastructure
* complete recommendation engine
* complete analytics warehouse
* complete production Kubernetes infrastructure

Create only the interfaces and foundations needed for those systems to integrate cleanly later.

Do not redesign the entire repository unnecessarily.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before modifying files:

1. Inspect the repository.
2. Identify current backend architecture.
3. Identify existing compatible modules.
4. Identify existing database models.
5. Identify existing migrations.
6. Identify existing APIs and conventions.
7. Identify existing tests.
8. Identify integration constraints.

Then:

1. implement the required scope
2. integrate it with existing modules
3. preserve compatible behavior
4. add migrations
5. add automated tests
6. update API documentation
7. update operational documentation
8. run validation
9. inspect changed files for security and contract consistency

Do not regenerate unrelated code.

Do not replace working implementations merely because a different design is preferred.

---

# COMPLETION CRITERIA

This backend task is complete only when:

* the backend starts correctly
* configuration is validated
* database integration is production-oriented
* migrations are valid
* authentication works securely
* authorization is enforced server-side
* user/profile operations work
* artist/catalog operations work
* album/release operations work
* track operations work
* playlist operations work
* library operations work
* privileged operations are audited
* stable API errors are implemented
* pagination is bounded
* transactional events are safely published
* Redis integration is controlled
* sensitive endpoints are rate limited
* observability is implemented
* health/readiness behavior is implemented
* automated tests cover critical behavior
* OpenAPI documentation reflects actual APIs
* no known required functionality is intentionally left incomplete

Do not declare completion if compilation, tests, migrations, or required validation fail.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* major backend functionality implemented
* database schema changes
* migrations created
* API endpoints added or modified
* authentication changes
* authorization changes
* event changes
* outbox changes
* queue/job changes
* Redis changes
* audit changes
* observability changes
* tests added or updated
* validation performed
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified results from assumptions.

Do not claim that a test, migration, build, or runtime validation succeeded unless it was actually executed and succeeded.

---

# FINAL INSTRUCTION

Implement the production backend foundation and core transactional capabilities of the music streaming platform.

Build real functionality.

Use the repository as the implementation source of truth.

Maintain secure server-side authorization.

Maintain authoritative transactional ownership.

Use idempotent operations.

Use strong database constraints.

Use asynchronous event publication where required.

Keep search, analytics, recommendation, payment-provider, and media-delivery concerns appropriately decoupled from core transactions.

Do not create superficial scaffolding and call it complete.

The resulting backend must provide a stable, secure, observable foundation upon which the remaining music-streaming backend capabilities can be implemented without requiring destructive architectural rewrites.
