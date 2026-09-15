# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — BACKEND VOLUME 2

## ROLE

Act as the complete senior backend engineering organization responsible for implementing the production-grade media, playback, search, recommendation, event-processing, and asynchronous-processing capabilities of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

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

Build the production backend capabilities required for large-scale music discovery and audio playback.

This backend volume is responsible for the implementation of:

* media asset management
* secure media ingestion
* asynchronous media processing orchestration
* audio metadata extraction
* audio processing state management
* artwork processing foundations
* playback authorization
* playback sessions
* playback progress
* playback history
* device management
* secure media-access issuance
* search indexing
* search APIs
* autocomplete
* recommendation APIs and serving foundations
* playback telemetry ingestion foundations
* event consumers
* background workers
* analytics event publishing foundations
* cache-backed playback state
* media and playback observability

The implementation must integrate with the transactional foundation already present in the repository without assuming that any earlier AI-generated prompt is available.

Do not implement frontend or mobile user interfaces in this task.

Do not expose raw media through ordinary application API endpoints.

Do not make search, recommendation, analytics, or Redis the authoritative source of transactional truth.

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
* Kafka or Redpanda
* BullMQ
* Elasticsearch or OpenSearch
* S3-compatible object storage
* CDN integration
* FFmpeg

## Media

Use object storage for durable media assets.

Use asynchronous workers for media processing.

Use a CDN or equivalent edge-delivery mechanism for playback delivery.

## Search

Use Elasticsearch or OpenSearch as a derived search system.

## Events

Use Kafka or Redpanda for durable event transport where the repository provides it.

## Jobs

Use BullMQ for asynchronous jobs where appropriate.

Use the repository's existing dependency versions and abstractions whenever compatible.

Do not perform unrelated dependency upgrades.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect existing backend modules.
3. Inspect the Prisma schema and migrations.
4. Inspect the existing user, catalog, playlist, library, and authentication models.
5. Inspect existing event/outbox infrastructure.
6. Inspect Redis infrastructure.
7. Inspect BullMQ infrastructure.
8. Inspect object-storage integrations.
9. Inspect search integrations.
10. Inspect tests.
11. Inspect environment configuration.
12. Identify reusable interfaces and contracts.

The repository defines what currently exists.

This prompt defines the functionality and behavior that must be implemented.

Do not assume previous architecture conversations are available to the implementation agent.

Preserve compatible existing behavior.

Do not rewrite unrelated functionality.

---

# BACKEND RESPONSIBILITY

This volume owns:

* media asset lifecycle
* media ingestion
* media processing
* secure media access
* playback authorization
* playback sessions
* playback state
* playback progress
* playback history
* devices
* search indexing
* search API
* autocomplete
* recommendation serving
* recommendation filtering
* event consumers
* background workers
* analytics event ingestion foundations

The implementation must integrate these capabilities with the existing transactional backend.

---

# MEDIA ASSET DOMAIN

Implement durable media asset management.

Support appropriate representations for:

* source audio asset
* processed audio asset
* delivery variant
* artwork asset
* thumbnail/derivative asset
* waveform or metadata derivative where applicable

Each asset must have:

* stable ID
* owning content entity
* asset type
* storage reference
* processing state
* metadata
* creation timestamp
* updated timestamp
* deletion state where appropriate

Do not store binary media inside PostgreSQL.

Store durable object references and authoritative metadata in PostgreSQL.

---

# MEDIA PROCESSING STATE

Implement explicit media-processing states.

At minimum support an appropriate lifecycle equivalent to:

* upload_pending
* uploaded
* validating
* rejected
* queued
* processing
* processed
* quality_check
* approved
* available
* failed
* deleting
* deleted

The exact enum names may follow repository conventions.

Prevent invalid transitions.

Use transactional updates when state transitions affect business visibility.

A media asset must not become playable while required validation or processing remains incomplete.

---

# SECURE MEDIA INGESTION

Implement a secure upload-initiation and finalization workflow.

The upload flow must:

1. authenticate the requesting principal
2. authorize the requested content operation
3. validate intended asset type
4. establish upload constraints
5. create an upload/media record
6. issue constrained storage-upload authorization
7. allow direct client-to-object-storage upload where appropriate
8. finalize the upload
9. validate the object
10. enqueue processing
11. expose processing state

Do not trust client-provided:

* MIME type
* file size
* codec
* duration
* extension
* metadata
* object completion state

Validate the stored object server-side.

---

# UPLOAD SECURITY

Treat all uploaded media as untrusted.

Enforce:

* maximum object size
* allowed file classes
* file signature verification
* MIME validation
* media-structure validation
* codec validation
* metadata validation
* malicious-content protections where appropriate
* ownership verification
* authorization
* upload expiration
* orphan cleanup

Never expose storage credentials to clients.

Never allow clients to choose arbitrary object-storage paths.

Object keys must be generated server-side.

---

# STORAGE ARCHITECTURE

Implement integration with S3-compatible object storage.

Define controlled storage boundaries for:

* source audio
* processed audio
* artwork
* derivatives
* temporary processing artifacts

Storage operations must support:

* secure upload
* server-side metadata
* controlled retrieval
* deletion
* lifecycle compatibility
* cleanup
* error handling

Do not make protected media publicly readable by default.

---

# MEDIA PROCESSING WORKERS

Implement BullMQ workers for media processing.

Workers must perform real processing rather than merely changing status fields.

Where applicable, process:

* audio validation
* metadata extraction
* audio normalization
* transcoding
* multiple delivery variants
* artwork normalization
* image derivative generation
* duration extraction
* codec information
* bitrate information
* sample-rate information

Use FFmpeg or an appropriate media-processing implementation.

Workers must:

* validate inputs
* update processing state
* produce durable outputs
* record failures
* retry safe failures
* avoid duplicate processing
* clean up temporary artifacts
* emit lifecycle events
* expose useful metrics

Do not silently mark processing complete when an output asset is missing or invalid.

---

# MEDIA JOB IDEMPOTENCY

Media processing jobs must be idempotent.

A retry must not:

* corrupt a valid output
* create uncontrolled duplicate assets
* publish invalid media
* leave inconsistent state

Use stable job identifiers or media-processing version keys where appropriate.

Define behavior for:

* worker crashes
* duplicate jobs
* partially generated outputs
* expired uploads
* invalid input
* storage failure
* FFmpeg failure

Failed jobs must remain observable and recoverable.

---

# MEDIA QUALITY VALIDATION

After processing, validate generated output.

Validate appropriate:

* existence
* readable container
* codec
* duration
* bitrate
* sample rate
* channel configuration
* expected format
* file integrity

Reject or quarantine invalid output.

Only publish assets that satisfy the platform's media requirements.

---

# MEDIA PUBLICATION

Integrate media readiness with catalog availability.

A track must not become playable because metadata is published while the required media asset remains unavailable.

Support publication transitions that account for:

* catalog state
* media state
* moderation/review state where applicable

Avoid race conditions between catalog publication and media-processing completion.

---

# ARTWORK PROCESSING

Implement secure artwork processing for supported catalog assets.

Where required, generate:

* normalized image
* thumbnails
* delivery variants

Validate:

* image type
* dimensions
* file size
* integrity

Strip or normalize unsafe metadata where appropriate.

Do not allow malformed image files to bypass validation because their extension appears valid.

---

# MEDIA CLEANUP

Implement cleanup workflows for:

* abandoned uploads
* failed processing artifacts
* replaced media variants
* deleted content
* orphaned objects
* expired temporary files

Cleanup must not delete objects still referenced by authoritative application data.

Use conservative reconciliation where object-storage state and database state differ.

---

# PLAYBACK AUTHORIZATION

Implement a dedicated playback-authorization flow.

A playback authorization request must validate:

* authenticated user
* account state
* subscription entitlement where applicable
* track state
* media availability
* content restrictions
* regional availability
* device/session rules where applicable

Never authorize playback based solely on:

* client-provided premium flags
* client-provided track status
* client-provided region
* stale local UI state

Return a controlled playback authorization response containing only the information the client requires.

---

# PLAYBACK ACCESS TOKENS

Implement secure media-access issuance.

Where signed URLs, signed cookies, or equivalent mechanisms are used, ensure that access is:

* time-limited
* resource-scoped
* tied to the authorized media representation
* generated only after authorization
* resistant to uncontrolled reuse

Do not expose object-storage credentials.

Do not return unrestricted permanent URLs.

Do not make bucket policies public merely to simplify development.

---

# PLAYBACK SESSION

Implement durable playback-session behavior.

Support:

* session creation
* session retrieval
* state updates
* termination
* expiration
* revocation
* device association

A session should track appropriate information such as:

* session ID
* user ID
* device ID
* track ID
* playback state
* current position
* last activity
* selected quality/variant
* authorization state
* client platform
* timestamps

Keep high-frequency ephemeral updates out of PostgreSQL when unnecessary.

---

# REDIS PLAYBACK STATE

Use Redis for appropriate high-frequency ephemeral playback state.

Possible state includes:

* current position
* current track
* playback state
* device presence
* playback heartbeat
* active session markers

Every Redis value must have:

* explicit key namespace
* TTL
* serialization format
* maximum size
* fallback behavior

Redis playback state is not the sole durable source of truth.

Durable playback state must be recoverable through the authoritative database or event/analytics pipeline where applicable.

---

# PLAYBACK STATE TRANSITIONS

Support:

* authorized
* active
* playing
* paused
* buffering
* interrupted
* completed
* skipped
* expired
* revoked
* terminated

Reject invalid state transitions.

Use timestamps or sequence/version metadata to prevent delayed client updates from overwriting newer server state.

---

# PLAYBACK PROGRESS

Implement progress handling appropriate for high-frequency clients.

Support:

* periodic heartbeat
* durable checkpoint
* seek
* pause
* resume
* completion
* skip
* replay/resume

Do not synchronously persist every progress event into PostgreSQL if doing so would create excessive write amplification.

Use controlled buffering or event processing where appropriate.

Define how:

* duplicate events
* out-of-order events
* delayed events
* client retries
* reconnection

are handled.

---

# PLAYBACK HISTORY

Implement durable listening-history functionality.

History must support:

* user association
* track association
* start time
* progress/completion information where useful
* playback session
* source/context where appropriate

Define:

* retention
* privacy
* pagination
* ordering
* deletion behavior

Do not expose one user's history to another user.

---

# PLAYBACK TELEMETRY

Create an asynchronous telemetry ingestion path for:

* playback started
* playback paused
* playback resumed
* seek
* skip
* completion
* buffering
* playback error
* quality change

Telemetry must not unnecessarily block playback.

Validate telemetry payloads.

Protect the ingestion path against:

* oversized payloads
* event floods
* malformed data
* unauthorized submission
* replayed events

---

# PLAYBACK COMPLETION SEMANTICS

Define how the system determines whether a track was meaningfully listened to.

The implementation must distinguish:

* start
* partial listen
* seek
* skip
* meaningful completion
* repeated playback

Use a consistent completion rule for analytics and history.

Do not let malicious clients arbitrarily inflate completion counts through uncontrolled repeated requests.

---

# DEVICE MANAGEMENT

Implement device registration and management.

Support:

* device ID
* user association
* platform
* application version
* display name where applicable
* last activity
* active/revoked state

Protect device-management APIs.

Support server-side device revocation.

Avoid storing unnecessary hardware-identifying data.

---

# CONCURRENT PLAYBACK

Enforce configurable concurrent-playback rules.

Where subscription rules limit active devices, implement server-side enforcement.

Concurrent playback detection may use:

* Redis presence
* playback sessions
* heartbeat timestamps

Define a safe expiration strategy so abandoned sessions do not permanently consume capacity.

Avoid aggressive session eviction caused solely by transient network loss.

---

# SEARCH INDEXING

Implement asynchronous search indexing for catalog entities.

Support indexing of:

* artists
* albums
* tracks
* playlists
* genres or categories where applicable

Index updates must be triggered from authoritative domain changes.

Do not write to Elasticsearch/OpenSearch as part of the same synchronous PostgreSQL transaction.

Use events/outbox processing.

---

# SEARCH DOCUMENTS

Implement typed search documents.

Documents must contain only the data needed for search and ranking.

Support fields such as:

* entity ID
* entity type
* searchable title/name
* normalized text
* artist/album context
* genre/category
* popularity signals
* visibility
* explicit-content state
* region availability
* update timestamp
* document version

Do not index:

* passwords
* private user data
* private playlists
* secrets
* unnecessary personal information

---

# SEARCH INDEXING WORKER

Implement an asynchronous indexing worker.

It must support:

* create
* update
* visibility changes
* deletion
* retry
* failure handling
* idempotency
* reindexing

A duplicate indexing event must converge to the correct document state.

The worker must not cause transactional catalog operations to fail because the search cluster is unavailable.

---

# SEARCH API

Implement search endpoints supporting appropriate:

* query normalization
* result-type filtering
* pagination
* ranking
* explicit-content filtering
* visibility filtering
* region filtering
* authentication-aware access

Return typed API results.

Do not expose raw Elasticsearch/OpenSearch response structures to clients.

---

# AUTOCOMPLETE

Implement a production autocomplete path where justified.

Support:

* prefix matching
* normalized matching
* result limiting
* low latency
* appropriate caching

Autocomplete must be rate limited.

Do not issue unrestricted wildcard searches against the search cluster.

---

# SEARCH FAILURE BEHAVIOR

Define safe degraded behavior when the search cluster is:

* unavailable
* overloaded
* returning errors
* stale
* partially indexed

Do not fabricate results.

Return an explicit service-degraded response where appropriate.

Catalog transactions must continue independently.

---

# SEARCH CONSISTENCY

Search is eventually consistent.

Ensure that:

* newly published content may take time to appear
* withdrawn content is removed or hidden promptly where required
* stale documents cannot bypass authorization
* indexing retries converge toward the latest authoritative state

Do not treat search results as sufficient authorization for accessing protected content.

---

# RECOMMENDATION SERVING

Implement the backend serving layer for personalized recommendations.

Support recommendation surfaces such as:

* home
* discover
* related tracks
* related artists
* personalized playlists
* contextual recommendations

The recommendation API must be independent of any one ranking algorithm.

---

# RECOMMENDATION REQUEST

Support contextual inputs such as:

* authenticated user
* surface
* locale
* region
* current track
* current artist
* session
* device
* content context

Validate all client-provided context.

Do not allow clients to impersonate another user.

---

# RECOMMENDATION PIPELINE BOUNDARY

Separate:

* candidate generation
* filtering
* ranking
* personalization
* response formatting

The serving layer should be able to call or consume candidate/ranking systems without rewriting the public API.

Do not place computationally expensive model training inside synchronous API requests.

---

# RECOMMENDATION FALLBACK

Implement safe fallbacks for cases where personalized recommendations are unavailable.

Fallbacks may use:

* popular content
* editorial content
* recently played context
* related catalog content

The fallback must obey:

* visibility
* content restrictions
* region availability
* explicit-content settings
* publication state

Do not return unavailable tracks simply because they were previously recommended.

---

# RECOMMENDATION FILTERING

Before returning recommendations, filter out:

* withdrawn tracks
* unavailable tracks
* content outside allowed region
* blocked content
* content incompatible with user preferences
* duplicates when inappropriate
* unpublished content

The final eligibility check must not depend solely on stale recommendation data.

---

# RECOMMENDATION EXPERIMENTS

Support backend-level metadata for:

* experiment
* variant
* algorithm version
* ranking version

Record exposure events asynchronously.

Do not expose sensitive recommendation features to clients.

Experiment failures must have safe defaults.

---

# RECOMMENDATION CACHING

Cache recommendation results only where appropriate.

Define:

* cache key
* user/context dimensions
* TTL
* invalidation
* stale behavior

Avoid caching personalized data under keys that could collide between users.

Prevent cross-user cache leakage.

---

# EVENT CONSUMERS

Implement event consumers required for:

* search indexing
* analytics propagation
* recommendation signals
* media workflows
* notification triggers where applicable

Every consumer must:

* validate event schema
* support event version
* be idempotent
* handle duplicates
* handle retries
* expose failures
* preserve trace/correlation context

Do not trust event payloads merely because they came from the internal broker.

---

# EVENT CONSUMER IDEMPOTENCY

Implement a strategy for preventing duplicate processing.

Appropriate approaches may include:

* processed-event records
* idempotency keys
* unique database constraints
* deterministic state transitions

Select a method appropriate to each consumer rather than applying one mechanism blindly.

---

# DEAD-LETTER HANDLING

Provide a recoverable path for events/jobs that repeatedly fail.

Failed items must expose:

* event/job ID
* type
* failure reason
* attempts
* timestamps
* correlation information

Do not silently discard failed events.

Dead-letter behavior must be observable.

---

# ANALYTICS EVENT INGESTION

Implement backend foundations for receiving and publishing product analytics events.

Support validated events for:

* search
* playback
* playlist actions
* likes
* follows
* recommendations
* subscription interactions

Analytics ingestion must be asynchronous where appropriate.

Do not allow analytics overload to block critical transactional APIs.

---

# ANALYTICS PRIVACY

Strip unnecessary personal information.

Do not send:

* passwords
* access tokens
* refresh tokens
* private message content
* private secrets

Apply privacy classification to sensitive event fields.

Respect account deletion and retention policies.

---

# NOTIFICATION TRIGGERS

Implement event-driven notification triggers where appropriate.

Potential triggers include:

* account security events
* subscription changes
* relevant artist/content updates
* playlist collaboration events
* administrative notices

Notification generation must be separated from provider delivery.

A provider outage must not invalidate the underlying business event.

---

# QUEUE MANAGEMENT

Implement production BullMQ configuration for current workers.

Each queue must define:

* queue name
* payload schema
* concurrency
* retries
* backoff
* timeout
* deduplication
* observability
* graceful shutdown

Avoid one enormous generic queue for unrelated workloads when isolation is important.

Use separate queues for workloads with materially different:

* throughput
* latency
* retry behavior
* resource requirements

---

# WORKER RESOURCE CONTROL

Media-processing workers may be CPU- and memory-intensive.

Do not configure them like lightweight notification workers.

Define appropriate concurrency and resource expectations.

Prevent one media-processing workload from starving:

* event consumers
* notification jobs
* indexing workers
* critical maintenance tasks

Use worker isolation where appropriate.

---

# OBSERVABILITY

Instrument all implemented processing paths.

Capture metrics for:

## Media

* upload count
* validation failures
* processing duration
* processing failures
* queue latency
* output generation
* storage failures

## Playback

* authorization latency
* authorization failures
* session count
* active sessions
* progress ingestion
* playback errors
* concurrent-device violations

## Search

* request latency
* error rate
* zero-result rate
* indexing latency
* indexing failures
* stale-document indicators

## Recommendations

* request latency
* fallback rate
* result count
* filtering rate
* provider/model failures
* cache hit rate

## Workers

* queue depth
* job latency
* retry count
* failed jobs
* concurrency utilization

Never log sensitive media URLs containing long-lived credentials or signatures.

---

# SECURITY

Secure every implemented flow.

Protect against:

* unauthorized media access
* IDOR
* malicious uploads
* path manipulation
* storage-bucket exposure
* signed-URL misuse
* playback-session spoofing
* telemetry flooding
* search abuse
* recommendation abuse
* queue/job manipulation
* event injection
* privilege escalation
* unauthorized artist asset access

Validate ownership and authorization server-side.

Do not trust:

* upload paths
* content metadata
* playback state
* client device identity
* premium status
* subscription status
* analytics identity assertions

---

# RATE LIMITING

Implement or extend rate limits for:

* upload initiation
* upload finalization
* playback authorization
* playback telemetry
* search
* autocomplete
* recommendation requests
* device registration
* playback-session mutation

Use different limits for:

* authentication users
* authenticated users
* administrative users
* internal workers

Prevent trivial bypass through request-shape variation.

---

# PRIVACY

Protect sensitive listening behavior.

Ensure that:

* playback history is user-scoped
* recommendation context cannot expose private listening data
* analytics identifiers are handled consistently
* deleted users are excluded from future personalized serving
* private playlists are excluded from public search
* administrative access is audited

Do not expose internal user-feature vectors or recommendation signals.

---

# RELIABILITY

Implement resilient behavior for:

* object-storage failures
* FFmpeg failures
* Redis failures
* search failures
* Kafka/Redpanda failures
* BullMQ failures
* CDN failures
* recommendation-service failures

Use:

* bounded retries
* exponential backoff
* idempotency
* timeouts
* graceful degradation
* durable state transitions

Do not retry indefinitely.

Do not retry unsafe operations without idempotency.

---

# PERFORMANCE

Optimize for high concurrency.

Pay particular attention to:

* playback authorization latency
* media-access-token generation
* playback state updates
* search latency
* autocomplete
* recommendation latency
* queue throughput
* media-processing throughput
* Redis read/write pressure
* database write amplification from playback telemetry

Avoid synchronous dependencies on:

* analytics
* search
* recommendation generation
* notification delivery

when playback can safely proceed without them.

---

# TESTING

Implement automated tests for:

## Media

* upload authorization
* invalid files
* valid files
* processing success
* processing failure
* duplicate processing
* cleanup behavior
* unauthorized media access

## Playback

* authorization
* entitlement validation
* unavailable content
* expired session
* revoked session
* concurrent-device behavior
* progress updates
* out-of-order events
* duplicate telemetry
* playback completion

## Search

* indexing
* updates
* deletion
* reindexing
* search
* autocomplete
* visibility filtering
* unavailable content
* indexing failure

## Recommendations

* request validation
* personalization boundaries
* content filtering
* fallback behavior
* caching
* experiment metadata

## Workers and events

* event consumption
* duplicate handling
* retries
* dead-letter handling
* queue failure
* idempotency

Use meaningful integration tests against real or appropriately isolated infrastructure where practical.

Do not test only mocked happy paths.

---

# MIGRATIONS

Create Prisma migrations for all required schema changes.

Verify:

* foreign keys
* indexes
* unique constraints
* state fields
* data retention implications
* migration ordering

Do not use ad hoc database modifications as a substitute for migration files.

For large tables, consider operational implications of index creation and migration strategy.

---

# API DOCUMENTATION

Document implemented endpoints for:

* media
* playback
* devices
* playback history
* search
* autocomplete
* recommendations
* relevant telemetry

Document:

* request schemas
* response schemas
* errors
* authentication
* authorization
* pagination
* rate-limit behavior where useful

The documentation must reflect actual implementation.

---

# IMPLEMENTATION BOUNDARIES

This backend volume owns the server-side capabilities for media, playback, search, recommendations, and asynchronous processing.

Do not implement:

* complete web application
* complete mobile application
* full payment-provider lifecycle
* full production Kubernetes infrastructure
* full analytics warehouse
* full data-science/model-training platform

Implement interfaces and durable backend contracts required for those systems to integrate later.

Do not duplicate functionality already correctly implemented in the repository.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before making changes:

1. inspect the current repository
2. map existing domain modules
3. inspect database state
4. inspect existing event infrastructure
5. inspect queues
6. inspect Redis abstractions
7. inspect storage integrations
8. inspect tests
9. identify conflicts
10. implement only the required changes

Then:

1. integrate media lifecycle
2. integrate playback lifecycle
3. integrate search
4. integrate recommendations
5. integrate event consumers
6. integrate workers
7. add migrations
8. add tests
9. add observability
10. update documentation
11. validate the complete affected backend surface

Do not regenerate unrelated modules.

Do not remove working behavior without a concrete compatibility reason.

---

# COMPLETION CRITERIA

This backend task is complete only when:

* media upload is securely authorized
* uploaded objects are validated server-side
* media-processing jobs execute real processing
* processing failures are recoverable
* processed assets are stored securely
* media publication respects processing state
* playback authorization is server-side
* protected media access is constrained
* playback sessions are implemented
* playback state is resilient to retries and stale updates
* playback history is persisted appropriately
* device management is implemented
* search indexing is asynchronous and idempotent
* search APIs are implemented
* autocomplete is safely implemented where applicable
* recommendation serving is implemented
* recommendation fallbacks are implemented
* recommendations respect content eligibility
* event consumers are idempotent
* failed events/jobs remain recoverable
* analytics ingestion does not block critical playback
* observability covers the implemented systems
* security boundaries are enforced
* automated tests cover critical success and failure paths
* migrations are valid
* APIs are documented
* no required implementation is intentionally omitted

Do not declare completion if a required test, build, migration, or validation step fails.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* media functionality implemented
* storage changes
* media-processing jobs
* playback functionality
* device functionality
* playback-history changes
* search functionality
* indexing workers
* recommendation functionality
* event consumers
* queue changes
* Redis changes
* database schema changes
* migrations created
* API endpoints added or modified
* security changes
* observability changes
* tests added or updated
* validation performed
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified results from assumptions.

Do not claim successful processing, indexing, playback, tests, or migrations unless those behaviors were actually validated.

---

# FINAL INSTRUCTION

Implement the production backend capabilities that make large-scale music delivery and discovery possible.

Treat media as untrusted input.

Treat playback as a high-concurrency distributed workload.

Treat search as an eventually consistent derived system.

Treat recommendations as an independent serving capability.

Treat analytics as noncritical to playback availability.

Treat events and jobs as at-least-once by default.

Make all distributed processing idempotent.

Keep protected media inaccessible without server-authorized access.

Keep authoritative transactional state in PostgreSQL.

Use Redis for appropriate ephemeral high-frequency state rather than replacing durable persistence.

Build real workers, real processing, real validation, real failure handling, and real tests.

The resulting backend must provide a reliable production foundation for secure music ingestion, media processing, discovery, personalized recommendations, and high-scale playback without requiring incompatible architectural rewrites later.
