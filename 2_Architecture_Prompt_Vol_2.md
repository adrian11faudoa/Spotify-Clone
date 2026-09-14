# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — ARCHITECTURE VOLUME 2

## ROLE

Act as the complete senior engineering organization responsible for defining the detailed technical architecture and cross-system contracts of a production-grade global music streaming platform comparable in capability and scale to major commercial music-streaming services.

Operate as:

* Principal Software Architect
* Staff Backend Engineer
* Staff Frontend Engineer
* Staff Mobile Engineer
* Database Architect
* Distributed Systems Engineer
* Security Engineer
* DevOps Engineer
* Cloud Architect
* QA Engineer
* UI/UX Engineer
* Performance Engineer
* Reliability Engineer
* Technical Writer

This prompt defines an independent architecture-design task.

Do not implement production source code.

Do not provide pseudo-code.

Do not create placeholder implementations.

Do not rely on another AI conversation being available.

Inspect the repository when this task is executed and reconcile the intended architecture below with the actual repository state.

The result must be a concrete technical blueprint covering detailed contracts, lifecycle behavior, state transitions, communication patterns, security controls, operational requirements, and client/server integration boundaries.

---

# PROJECT

Design the detailed technical architecture for an original global music streaming platform.

The platform must support:

* large-scale music catalog management
* artists and artist organizations
* albums and releases
* tracks and audio assets
* playlists
* user libraries
* likes and follows
* listening history
* personalized discovery
* search
* recommendations
* high-scale audio playback
* real-time playback state
* subscriptions
* payment workflows
* notifications
* analytics
* administration
* moderation
* responsive web clients
* iOS and Android applications
* asynchronous processing
* secure media delivery
* operational observability
* high availability
* disaster recovery

The architecture must support a large user population, high concurrent playback, high event volume, and large media storage requirements.

The implementation must remain original and must not reproduce proprietary implementation details of any existing commercial platform.

---

# TECHNOLOGY DIRECTION

Use this technology baseline:

## Web

* Next.js
* React
* TypeScript
* Tailwind CSS
* shadcn/ui
* TanStack Query
* Zustand where justified
* React Hook Form
* Zod

## Mobile

* React Native
* Expo
* TypeScript

## Backend

* NestJS
* TypeScript
* REST
* WebSockets where justified
* OpenAPI
* PostgreSQL
* Prisma
* Redis
* Kafka or Redpanda
* BullMQ
* Elasticsearch or OpenSearch
* S3-compatible object storage
* CDN
* FFmpeg

## Commercial Systems

* Stripe or another production payment provider through an internal abstraction
* email provider
* push notification provider
* optional external identity providers

## Infrastructure

* Docker
* Kubernetes
* Helm
* Terraform
* GitHub Actions

## Observability

* OpenTelemetry
* Prometheus
* Grafana
* centralized logs
* distributed tracing
* alerting

---

# SOURCE OF TRUTH

The repository is authoritative for currently implemented behavior.

The requirements in this prompt define the target architecture.

Inspect:

* repository structure
* package manifests
* source modules
* API definitions
* Prisma schema
* migrations
* tests
* environment configuration
* infrastructure definitions
* existing documentation

Reuse compatible decisions already present in the repository.

Do not perform destructive architectural rewrites merely because another implementation would be aesthetically preferable.

When the repository and this prompt differ, preserve working compatible behavior unless the required target architecture materially depends on changing it. When change is necessary, document the reason and migration implications.

Never assume that another AI-generated architecture document is available.

---

# ARCHITECTURAL OBJECTIVE

Translate the system-level architecture into concrete technical contracts that different implementation teams can independently implement without creating incompatible behavior.

Define:

* API boundaries
* request and response conventions
* domain commands
* domain events
* event envelopes
* queue contracts
* state machines
* database ownership
* cache behavior
* playback lifecycle
* media lifecycle
* recommendation interfaces
* search indexing contracts
* notification lifecycle
* subscription lifecycle
* authentication lifecycle
* authorization rules
* client/server boundaries
* error semantics
* idempotency behavior
* concurrency behavior
* observability context propagation

The architecture must support independent implementation of backend, web, mobile, infrastructure, and QA work while converging on one coherent system.

---

# DOMAIN CONTRACT MODEL

For every major bounded context, define:

* responsibilities
* authoritative entities
* commands
* queries
* state transitions
* emitted events
* consumed events
* synchronous dependencies
* asynchronous dependencies
* security boundary
* data exposure rules
* failure behavior

At minimum cover:

* Identity
* User Profile
* Music Catalog
* Media
* Playlists
* Listener Library
* Playback
* Search
* Recommendations
* Subscriptions
* Notifications
* Analytics
* Administration
* Moderation

Clearly distinguish commands from events and queries from state mutations.

---

# IDENTIFIER AND CORRELATION CONTRACTS

Define consistent identifiers for:

* users
* devices
* sessions
* artists
* albums
* tracks
* releases
* playlists
* playlist items
* media assets
* playback sessions
* subscriptions
* notifications
* events
* jobs
* audit records

Define:

* public identifier format
* internal identifier behavior
* correlation ID
* request ID
* trace ID
* causation ID
* idempotency key

The same identifier conventions must be respected by:

* REST APIs
* WebSocket messages
* events
* jobs
* logs
* traces
* analytics

---

# API CONTRACT ARCHITECTURE

Define a consistent REST architecture.

The API must support appropriate namespaces for:

* authentication
* users
* profiles
* artists
* albums
* tracks
* playlists
* libraries
* search
* recommendations
* playback
* subscriptions
* notifications
* administration
* moderation

Define conventions for:

* HTTP methods
* URL structure
* versioning
* pagination
* cursor strategy
* filtering
* sorting
* resource expansion
* conditional requests where useful
* idempotency
* error responses
* validation failures
* authentication failures
* authorization failures
* rate limiting
* correlation identifiers

Use cursor-based pagination for large, mutable collections where appropriate.

Avoid exposing database pagination implementation details directly.

---

# API ERROR CONTRACT

Define a stable structured error format.

Every error should expose enough information for clients and operators to understand the failure without leaking sensitive internals.

Define:

* stable error code
* human-readable message
* request/correlation identifier
* optional field-level validation details
* retryability indicator where appropriate
* relevant metadata where safe

Do not expose:

* stack traces
* database errors
* secrets
* provider credentials
* internal infrastructure details
* sensitive authorization information

Define consistent semantics for:

* validation error
* authentication error
* authorization error
* not found
* conflict
* rate limited
* dependency unavailable
* unsupported operation
* expired resource
* entitlement failure
* media unavailable

---

# PAGINATION CONTRACT

Define pagination separately for:

* tracks
* albums
* artists
* playlists
* playlist contents
* user libraries
* listening history
* notifications
* administrative lists
* search results
* recommendation feeds

Use cursor-based pagination where datasets are large or mutate frequently.

Define:

* cursor encoding
* cursor expiration where relevant
* stable ordering
* duplicate prevention
* page-size limits
* maximum limits
* behavior after underlying data changes

Never allow unbounded client-controlled page sizes.

---

# AUTHENTICATION STATE MACHINE

Define explicit authentication and session lifecycle states.

Cover:

* account creation
* email verification where applicable
* login
* token issuance
* token refresh
* refresh-token rotation
* logout
* session revocation
* password reset
* password change
* suspicious-session handling
* account disablement
* account deletion

Define:

* access-token TTL
* refresh-token TTL
* rotation behavior
* replay detection
* session/device linkage
* revocation strategy
* concurrent-session policy

Do not rely solely on client-side logout to invalidate privileged sessions.

---

# AUTHORIZATION MODEL

Define authorization at:

* endpoint level
* domain level
* resource level
* action level

Evaluate roles such as:

* listener
* premium listener
* artist
* artist representative
* moderator
* support operator
* administrator
* platform operator

Also define ownership-based access for:

* private playlists
* collaborative playlists
* artist resources
* account settings
* personal libraries
* personal history
* subscription details
* administrative resources

Authorization decisions must execute server-side.

---

# PLAYLIST STATE MODEL

Define the playlist lifecycle:

* draft where applicable
* active
* archived
* deleted

Define playlist item behavior for:

* addition
* deletion
* reordering
* deduplication policy
* duplicate track policy
* collaborative changes
* ownership changes
* privacy changes

Define concurrency controls.

Collaborative playlist updates must not silently overwrite unrelated changes.

Specify whether ordering uses:

* explicit integer positions
* fractional ranking
* linked ordering
* another stable strategy

Select an implementation appropriate for high-frequency reordering without forcing large table rewrites.

---

# LIBRARY STATE MODEL

Define authoritative state for:

* liked tracks
* saved albums
* followed artists
* followed playlists
* recently played
* listening history

Define:

* uniqueness
* deletion behavior
* idempotent writes
* ordering
* timestamps
* privacy
* retention

Repeated like/unlike requests must remain safe and idempotent where appropriate.

---

# CATALOG STATE MODEL

Define lifecycle states for:

## Artist

Examples:

* pending
* active
* suspended
* archived

## Album/Release

Examples:

* draft
* review
* scheduled
* published
* withdrawn
* archived

## Track

Examples:

* draft
* processing
* ready
* published
* restricted
* withdrawn
* archived

The exact state model may be refined, but every state transition must define:

* authorized actor
* validation rules
* persistence behavior
* events emitted
* downstream effects
* rollback/recovery expectations

---

# MEDIA STATE MACHINE

Define explicit media processing states such as:

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

For every transition define:

* allowed predecessor states
* actor/process responsible
* database mutation
* storage operation
* event
* retry behavior
* failure behavior

The state machine must prevent incomplete or failed media from becoming playable.

---

# MEDIA ACCESS ARCHITECTURE

Define authorization before media access.

For protected media, the flow should conceptually include:

1. client authenticates
2. client requests playback authorization
3. server validates user and entitlement
4. server validates content availability
5. server determines permitted media representation
6. server issues constrained access
7. client obtains media through CDN
8. CDN retrieves protected content from an origin
9. playback telemetry is generated independently

Do not embed unrestricted object-storage credentials in clients.

Define signed URL or equivalent mechanisms with:

* expiration
* scope
* resource binding
* optional session binding
* revocation considerations
* misuse monitoring

---

# PLAYBACK SESSION MODEL

Define the playback session entity and lifecycle.

A playback session should capture appropriate metadata such as:

* session ID
* user ID
* device ID
* track ID
* start time
* current position
* playback state
* client platform
* selected media variant
* authorization state
* expiration
* last heartbeat
* termination reason where needed

Define states such as:

* authorized
* active
* paused
* buffering
* interrupted
* completed
* expired
* revoked
* terminated

Do not persist every playback progress update synchronously to the primary database if this would create unnecessary write amplification.

Define a suitable strategy combining:

* ephemeral state
* periodic durable checkpoints
* event streams
* finalization events

---

# PLAYBACK PROGRESS

Define rules for:

* heartbeat frequency
* checkpoint frequency
* seek
* rewind
* skip
* completion
* resume position
* duplicate telemetry
* offline events where supported

Define how inconsistent client updates are handled.

Do not allow older delayed events to blindly overwrite newer state.

Use timestamps, sequence numbers, version numbers, or another explicit ordering mechanism.

---

# CONCURRENT DEVICES

Define behavior when one account is active on multiple devices.

Support configuration for:

* simultaneous playback
* device registration
* device naming
* device revocation
* device selection
* current device
* playback transfer

Where subscription rules impose limits, enforce those limits server-side.

Do not assume that all client updates arrive in order.

---

# WEBSOCKET CONTRACT

Define WebSocket channels/messages for features requiring real-time communication.

Each message must define:

* message ID
* message type
* version
* timestamp
* correlation data where useful
* payload
* authorization requirements

Define:

* authentication during connection
* subscription authorization
* heartbeat
* disconnect
* reconnect
* duplicate handling
* ordering
* backpressure
* fan-out
* connection limits
* abuse prevention

A reconnecting client must be able to reconstruct state without requiring every historical real-time message.

---

# EVENT CONTRACTS

Define representative events for:

## Identity

* UserCreated
* UserVerified
* SessionCreated
* SessionRevoked
* UserSuspended
* UserDeleted

## Catalog

* ArtistCreated
* ArtistUpdated
* AlbumPublished
* TrackCreated
* TrackPublished
* TrackRestricted
* TrackWithdrawn

## Media

* MediaUploadCompleted
* MediaProcessingStarted
* MediaProcessingCompleted
* MediaProcessingFailed
* MediaPublished
* MediaDeleted

## Library

* TrackLiked
* TrackUnliked
* AlbumSaved
* AlbumUnsaved
* ArtistFollowed
* ArtistUnfollowed

## Playlist

* PlaylistCreated
* PlaylistUpdated
* PlaylistItemAdded
* PlaylistItemRemoved
* PlaylistReordered
* PlaylistDeleted

## Playback

* PlaybackAuthorized
* PlaybackStarted
* PlaybackPaused
* PlaybackResumed
* PlaybackSeeked
* PlaybackSkipped
* PlaybackCompleted
* PlaybackSessionEnded

## Subscription

* SubscriptionCreated
* SubscriptionActivated
* SubscriptionRenewalSucceeded
* SubscriptionPaymentFailed
* SubscriptionCanceled
* SubscriptionExpired
* EntitlementChanged

## Notification

* NotificationCreated
* NotificationDelivered
* NotificationFailed
* NotificationRead

Every event contract must define:

* event name
* version
* aggregate
* producer
* payload
* ordering key
* delivery semantics
* consumer expectations
* idempotency strategy
* PII considerations

---

# EVENT VERSIONING

Define how event schemas evolve.

Require:

* version identifiers
* backward-compatible changes whenever possible
* explicit migration for breaking changes
* tolerant consumers where appropriate
* replay compatibility
* schema validation
* deprecation strategy

Do not silently reuse an old event name for a materially different payload.

---

# IDEMPOTENCY ARCHITECTURE

Define idempotency for:

* payment operations
* subscription transitions
* playlist mutations where retries may occur
* media processing
* event consumers
* notification delivery
* administrative destructive actions
* webhook processing

Specify:

* idempotency-key source
* key scope
* retention
* persistence
* duplicate response behavior
* concurrent duplicate behavior

Idempotency must protect against retries without masking legitimate distinct operations.

---

# WEBHOOK ARCHITECTURE

Define webhook ingestion for external providers.

Requirements:

* signature verification
* raw-body preservation where required
* timestamp/replay protection
* provider event ID
* deduplication
* durable persistence before processing
* asynchronous downstream handling
* retries
* auditability
* observability

Payment-provider events must not directly trust client-supplied billing state.

---

# SUBSCRIPTION STATE MACHINE

Define subscription states such as:

* incomplete
* active
* trialing where applicable
* past_due
* paused where applicable
* canceled
* expired

Define exact transitions for:

* initial signup
* successful payment
* failed payment
* retry
* cancellation
* renewal
* plan change
* provider webhook correction
* manual support adjustment

Separate:

* payment provider state
* local subscription state
* entitlement state

Entitlements must not become dependent on repeated live API calls to the payment provider.

---

# ENTITLEMENT ARCHITECTURE

Define a central entitlement decision model.

Entitlements may govern:

* premium playback
* audio-quality tiers
* ad-free behavior
* offline access
* device limits
* catalog availability
* premium features

Define:

* entitlement source
* cache
* TTL
* invalidation
* propagation latency
* fallback behavior

Security-sensitive entitlement decisions must be enforceable server-side.

---

# SEARCH INDEX CONTRACT

Define canonical index documents for:

* artist
* album
* track
* playlist

Each document should contain only search-relevant fields.

Define:

* document ID
* source entity ID
* searchable text
* normalized fields
* popularity signals
* ranking signals
* visibility state
* region availability
* explicit-content state
* updated timestamp
* document version

Define index lifecycle:

* create
* update
* hide
* delete
* reindex
* alias switch
* rollback

Search results must respect content authorization and visibility.

---

# RECOMMENDATION CONTRACT

Define the recommendation API contract independently of the ranking algorithm.

A recommendation request should support context such as:

* user
* device
* surface
* session
* locale
* region
* current track
* current artist
* playlist context
* time context

The response must contain enough metadata for clients to render:

* tracks
* albums
* artists
* playlists
* recommendation reasons where appropriate
* ranking metadata where safe

Never expose private model internals or sensitive user features to clients.

Define recommendation filtering for:

* unavailable content
* blocked content
* explicit-content preferences
* regional restrictions
* withdrawn tracks
* duplicate recommendations

---

# RECOMMENDATION EXPERIMENTATION

Define an experimentation model supporting:

* experiment ID
* variant
* assignment
* algorithm version
* ranking version
* exposure event
* outcome event

Experiment assignments must be:

* deterministic where appropriate
* observable
* privacy-aware
* independently disableable

Do not hardwire experiments into every client.

---

# ANALYTICS EVENT CONTRACT

Define a common analytics envelope.

It should support:

* event ID
* event type
* schema version
* occurred-at
* received-at where useful
* anonymous/session/user identifier strategy
* device/platform
* app version
* correlation ID
* context
* payload
* privacy classification

Explicitly distinguish:

* operational telemetry
* product analytics
* playback analytics
* security audit events

Do not mix sensitive audit records with unrestricted product analytics.

---

# DATA RETENTION

Define retention classes for:

* authentication logs
* audit logs
* playback telemetry
* raw analytics
* aggregated analytics
* notification records
* application logs
* metrics
* traces
* media processing artifacts
* deleted user data

Retention must consider:

* privacy requirements
* storage cost
* operational debugging
* security investigations
* legal/business requirements

Avoid indefinite storage by default.

---

# AUDIT ARCHITECTURE

Define immutable or append-oriented auditing for sensitive administrative and security operations.

Audit entries should capture:

* audit ID
* actor
* actor role
* action
* target
* target type
* timestamp
* outcome
* request/correlation ID
* relevant metadata
* source IP or network metadata where justified
* reason when required

Never include unnecessary secrets or private content.

---

# NOTIFICATION CONTRACT

Define:

* notification ID
* recipient
* type
* priority
* channel
* template
* payload
* scheduled time
* delivery state
* retry count
* provider reference
* created/read timestamps

Define states such as:

* pending
* queued
* sending
* delivered
* failed
* suppressed
* canceled

Notification creation must be independent from provider-specific delivery.

---

# FILE AND UPLOAD CONTRACT

Define secure upload operations.

An upload initiation contract should establish:

* upload ID
* intended asset type
* owner
* permitted content category
* maximum size
* allowed file classes
* expiration
* storage location
* processing status

Clients must not be trusted to declare that an uploaded file is valid.

Server-side processing must verify:

* file type
* file signature
* size
* structure
* duration where applicable
* codec
* metadata safety
* malware/security status where applicable

---

# OBSERVABILITY CONTRACT

Every cross-system request and event should carry enough context for tracing.

Define propagation of:

* request ID
* correlation ID
* trace ID
* span context
* user context where safe
* service identity

Define standard metric families for:

* API latency
* error rate
* database latency
* cache latency
* cache hit ratio
* queue depth
* queue failures
* event lag
* consumer failures
* search latency
* playback authorization latency
* media-processing duration
* CDN failures
* payment-provider failures
* notification delivery
* WebSocket connections

Avoid unbounded high-cardinality labels.

---

# SECURITY CONTRACTS

Define security requirements at contract boundaries.

For every externally reachable operation, define:

* authentication requirement
* authorization requirement
* input validation
* rate limit class
* abuse-control strategy
* audit requirement
* sensitive-data handling

For every protected media operation, define:

* entitlement check
* resource authorization
* signed-access requirements
* expiration
* replay/misuse considerations

For every administrative operation, define:

* privileged role
* resource scope
* audit requirement
* destructive-action safeguards

---

# RATE LIMITING

Define rate-limit classes for:

* authentication
* password reset
* public catalog APIs
* search
* playback authorization
* media access-token issuance
* playlist mutations
* comments/social actions where applicable
* notifications
* webhooks
* administrative APIs

Rate limits must account for:

* identity
* IP
* device
* API key/provider identity where relevant
* endpoint sensitivity

Avoid using a single global rate limit for all traffic.

Define behavior when Redis is unavailable.

---

# FAILURE AND DEGRADED-MODE CONTRACTS

For each major dependency, define the user-visible behavior during failure.

At minimum cover:

* PostgreSQL failure
* Redis failure
* Kafka/Redpanda failure
* BullMQ failure
* search failure
* object-storage failure
* CDN failure
* payment-provider failure
* email-provider failure
* push-provider failure
* recommendation failure
* analytics failure

Examples of expected design principles:

* search failure should not destroy catalog data
* recommendation failure should fall back to safe discovery/content
* analytics failure should not necessarily block playback
* email failure should not prevent account creation when email delivery is noncritical
* payment-provider failure must not produce false entitlement
* transient Redis failure must not corrupt authoritative state

Define fallback behavior explicitly rather than leaving it to individual implementers.

---

# CLIENT ARCHITECTURE CONTRACT

Define the server-facing contract required by web and mobile clients.

Clients must have predictable access to:

* authentication
* current user
* profile
* catalog
* search
* playlists
* library
* recommendations
* playback authorization
* playback state
* subscriptions
* notifications

Define server-authoritative versus client-local state.

Client-local state may include:

* UI state
* temporary playback controls
* local queue state
* transient navigation state

Server-authoritative state includes:

* account state
* authorization
* subscription entitlement
* private-resource access
* catalog availability
* billing state

---

# OFFLINE ARCHITECTURE

Where mobile offline playback is included, define a secure architecture for:

* offline entitlement
* encrypted local storage
* downloaded media manifests
* device binding
* expiration
* revocation
* download quotas
* license/authorization renewal
* local playback telemetry
* synchronization after reconnect

Downloaded media must never be treated as unrestricted files.

If the first production release does not include offline playback, document the boundary explicitly so later implementation can be introduced without corrupting the core playback model.

---

# MULTI-REGION ARCHITECTURE

Define the global architecture for:

* regional application deployments
* routing
* database topology
* media origins
* CDN
* search
* cache
* event replication where required

Differentiate:

* globally replicated data
* region-local data
* region-partitioned data
* eventually synchronized data

Avoid making every subsystem globally writable by default.

Define how the platform behaves during:

* regional network partition
* region failure
* database failover
* degraded cross-region connectivity

---

# DISASTER RECOVERY CONTRACT

Define recovery behavior for:

* PostgreSQL
* object storage
* Redis
* event broker
* search
* infrastructure
* secrets/configuration

Specify target concepts for:

* RPO
* RTO
* backup frequency
* backup retention
* restoration procedure
* integrity verification
* failover testing

Critical transactional data must receive stronger recovery guarantees than ephemeral state.

---

# ARCHITECTURE DECISION RECORDS

Create ADRs for decisions with long-term architectural impact.

At minimum address:

* modular monolith versus early service separation
* PostgreSQL ownership
* Redis responsibilities
* event broker selection
* search platform
* media storage and CDN
* playback authorization model
* event delivery semantics
* transactional outbox
* recommendation architecture
* subscription entitlement architecture
* multi-region strategy

Each ADR should contain:

* decision
* context
* alternatives considered
* rationale
* consequences
* operational implications

---

# IMPLEMENTATION BOUNDARIES

This prompt defines detailed technical architecture and contracts.

It must establish sufficient information for later implementation teams to independently implement:

* backend
* web
* mobile
* media processing
* search
* recommendations
* subscriptions
* infrastructure
* QA

Do not implement production source code inside this task.

Do not create actual migration files merely to illustrate the schema.

Do not generate frontend components.

Do not generate infrastructure manifests.

Those belong to implementation-specific work.

---

# ARCHITECTURAL VALIDATION

Before finalizing the architecture, verify:

* APIs have stable semantics
* state machines have legal transitions
* ownership is unambiguous
* events have explicit producers and consumers
* retries are idempotent
* queue jobs have failure handling
* search remains derived from authoritative data
* media access is protected
* playback does not depend unnecessarily on analytics
* subscription entitlement cannot be falsified by client state
* WebSocket state can recover after reconnect
* database transactions are bounded
* privacy boundaries are explicit
* audit boundaries are explicit
* observability context survives asynchronous boundaries
* region failures have defined behavior
* disaster recovery assumptions are realistic
* client contracts do not depend on implementation details
* infrastructure responsibilities are compatible with application contracts

Resolve contradictions before considering the architecture complete.

---

# REQUIRED ARCHITECTURE DELIVERABLES

Produce or update repository documentation covering:

* API contract conventions
* error contract
* pagination
* authentication lifecycle
* authorization model
* playlist state model
* catalog state model
* media state model
* playback state model
* subscription state model
* entitlement model
* event contracts
* event versioning
* queue contracts
* idempotency
* webhook architecture
* search documents
* recommendation contracts
* analytics envelopes
* audit model
* notification model
* upload model
* observability conventions
* rate limiting
* degraded-mode behavior
* client/server state ownership
* offline strategy
* multi-region behavior
* disaster recovery
* architecture decision records

Use Mermaid or another repository-friendly diagram format when diagrams materially improve understanding.

---

# COMPLETION CRITERIA

This architecture task is complete only when:

* API conventions are explicit
* error semantics are explicit
* pagination behavior is explicit
* authentication lifecycle is explicit
* authorization boundaries are explicit
* critical domain state machines are explicit
* playback lifecycle is explicit
* media lifecycle is explicit
* subscription lifecycle is explicit
* entitlement behavior is explicit
* event contracts are explicit
* event-versioning policy is explicit
* idempotency behavior is explicit
* webhook security is explicit
* search contracts are explicit
* recommendation contracts are explicit
* analytics contracts are explicit
* notification lifecycle is explicit
* observability propagation is explicit
* rate limits are explicit
* degraded behavior is explicit
* client/server state ownership is explicit
* multi-region behavior is explicit
* disaster recovery is explicit
* important architectural decisions are recorded

No important cross-system contract should remain dependent on interpretation by a future implementation agent.

---

# IMPLEMENTATION REPORT

At completion, report:

* architecture documents created
* architecture documents modified
* API contract decisions
* state machines defined
* event contracts defined
* queue contracts defined
* idempotency strategies defined
* media/playback decisions
* subscription/entitlement decisions
* search decisions
* recommendation decisions
* client/server contract decisions
* security decisions
* observability decisions
* resilience decisions
* multi-region decisions
* disaster-recovery decisions
* ADRs created
* validation performed
* unresolved issues, if any

Do not claim that a contract was validated unless it was actually reviewed.

---

# FINAL INSTRUCTION

Produce a detailed technical architecture that turns the global music-streaming platform into a system with explicit contracts rather than loosely defined components.

The architecture must allow separate implementation efforts to work independently without producing incompatible APIs, data ownership, event semantics, state transitions, or security behavior.

Favor stable contracts.

Favor explicit state machines.

Favor deterministic failure behavior.

Favor idempotent distributed workflows.

Favor secure media access.

Favor transactional authority.

Favor asynchronous processing where latency does not require synchronous execution.

Favor recoverable real-time state.

Favor observable cross-system behavior.

The final architecture must provide a sufficiently precise technical foundation for building the entire web, mobile, backend, media, search, recommendation, subscription, analytics, infrastructure, and QA layers as one coherent production-grade platform.
