# Spotify-Style Music Streaming Platform — Architecture Prompt

## ROLE

Act as a Principal Software Architect and senior distributed-systems architecture team designing an original, production-grade global music streaming platform.

Produce the detailed technical architecture for the system described below.

This is an **architecture-only task**.

Do not implement application source code.

Do not generate production implementation files.

Do not write pseudo-code as a substitute for architecture.

The architecture must be sufficiently detailed that backend, mobile, infrastructure, media-processing, search, analytics, and QA engineers can implement the system consistently from the repository and this architectural specification.

The actual repository is the source of truth for any existing implementation.

---

# 1. PROJECT

Design an original music streaming platform comparable in capability and scale to a modern Spotify-style service.

The system must support, as appropriate:

* user accounts
* authentication
* profiles
* devices and sessions
* artists
* albums
* tracks
* genres
* music catalog
* playlists
* playlist collaboration
* playlist visibility
* liked/saved music
* follows
* music library
* search
* discovery
* recommendations
* playback
* queues
* playback sessions
* playback history
* recently played music
* audio streaming
* adaptive audio quality
* media processing
* artwork
* subscriptions
* entitlements
* analytics
* notifications
* administration
* content management
* moderation
* operational tooling

The product must be original.

Do not reproduce Spotify's proprietary implementation, internal APIs, private architecture, source code, or copyrighted assets.

---

# 2. REQUIRED TECHNOLOGY DIRECTION

Design around this technology stack unless repository inspection demonstrates an existing compatible implementation that should be preserved.

## Mobile

* React Native
* Expo
* TypeScript
* React Navigation
* Zustand
* TanStack Query

## Backend

* Node.js
* NestJS
* TypeScript

## Database

* PostgreSQL
* Prisma

## Cache / Ephemeral State

* Redis / compatible Redis implementation

## Search

* Elasticsearch or OpenSearch

## Object Storage / CDN

* AWS S3
* AWS CloudFront

## Audio Processing

* FFmpeg
* background processing
* adaptive streaming
* HLS where appropriate

## Background Jobs

* BullMQ
* Redis

## Event Streaming

* Kafka or Redpanda where justified

## API

* REST
* OpenAPI / Swagger

## Infrastructure

* AWS
* Docker
* Terraform or OpenTofu
* Kubernetes/EKS where justified

## Observability

Where appropriate:

* OpenTelemetry
* Prometheus
* Grafana
* Loki
* Tempo

The architecture must justify significant infrastructure choices instead of adding technologies merely because they are listed.

---

# 3. REPOSITORY-FIRST ARCHITECTURE AUDIT

Before defining architecture, inspect the repository.

Determine:

* repository structure
* applications
* packages
* services
* modules
* existing database schema
* existing migrations
* API structure
* authentication
* media handling
* storage
* queues
* event infrastructure
* search
* mobile architecture
* tests
* CI/CD
* Docker configuration
* infrastructure
* environment configuration
* observability
* documentation

Identify:

* implemented architecture
* partially implemented architecture
* conflicting architecture
* reusable components
* technical debt
* architectural risks

Do not assume an empty repository.

Do not discard compatible existing architecture.

When the repository already contains implementation decisions, explicitly distinguish:

1. Existing authoritative implementation
2. Architecture that should be preserved
3. Architecture that should be migrated
4. Architecture that should not be duplicated

---

# 4. ARCHITECTURAL PRINCIPLES

Establish these principles:

* PostgreSQL is authoritative for durable transactional business state.
* Search is a derived projection.
* Redis is not the authoritative store for critical durable data.
* Object storage is authoritative for media objects.
* CDN delivery is separate from media ownership.
* Background processing must be asynchronous where appropriate.
* External providers must be isolated behind explicit boundaries.
* API authorization is server-side.
* Sensitive operations are auditable.
* Distributed operations are idempotent where necessary.
* Event consumers tolerate duplicate delivery.
* Critical operations are transactionally safe.
* Noncritical dependencies must not unnecessarily block critical workflows.
* Privacy is enforced across every storage and processing layer.
* Media uploaded by users or content operators is untrusted.
* Client applications are never authoritative for security-sensitive business rules.

---

# 5. SYSTEM CONTEXT

Define the complete system context.

Identify:

* mobile application
* optional web/public surface
* API
* authentication
* PostgreSQL
* Redis
* search
* object storage
* CDN
* media-processing workers
* BullMQ
* Kafka/Redpanda if justified
* analytics pipeline
* recommendation systems
* notification providers
* payment provider
* monitoring infrastructure
* administration tools
* content-management workflows
* external identity/provider boundaries where appropriate

For every external dependency define:

* purpose
* trust boundary
* authentication
* failure behavior
* timeout strategy
* retry strategy
* data exchanged
* privacy implications
* observability

---

# 6. BOUNDED CONTEXTS

Define explicit domain boundaries.

At minimum evaluate:

## Identity

Responsibilities:

* users
* credentials
* sessions
* devices
* authentication
* account security

## User / Profile

Responsibilities:

* profile
* preferences
* account settings
* user state

## Catalog

Responsibilities:

* artists
* albums
* tracks
* genres
* releases
* metadata
* availability
* content status

## Library

Responsibilities:

* liked tracks
* saved albums
* saved playlists
* follows
* user collections

## Playlist

Responsibilities:

* playlist ownership
* playlist items
* ordering
* visibility
* collaboration
* playlist followers

## Playback

Responsibilities:

* playback sessions
* playback state
* queue
* current track
* device coordination
* playback history

## Media

Responsibilities:

* source audio
* audio validation
* transcoding
* HLS generation
* artwork
* manifests
* media lifecycle

## Search

Responsibilities:

* indexing
* querying
* suggestions
* ranking
* filtering

## Recommendation

Responsibilities:

* discovery
* personalized recommendations
* related music
* recommendation candidates
* ranking

## Subscription

Responsibilities:

* plans
* subscriptions
* entitlements
* billing state

## Analytics

Responsibilities:

* playback events
* engagement events
* aggregation
* analytical projections

## Notification

Responsibilities:

* in-app notifications
* push delivery
* notification preferences
* delivery attempts

## Administration

Responsibilities:

* user administration
* content management
* moderation
* media operations
* operational controls
* auditing

Define ownership and communication rules between these contexts.

---

# 7. SOURCE-OF-TRUTH MATRIX

Create an explicit source-of-truth matrix.

At minimum cover:

| Data             | Authoritative Source                                   | Derived Consumers               |
| ---------------- | ------------------------------------------------------ | ------------------------------- |
| User             | PostgreSQL                                             | cache/search/analytics          |
| Credentials      | PostgreSQL + secure secret handling                    | authentication                  |
| Sessions         | PostgreSQL and/or controlled session infrastructure    | Redis                           |
| Artist           | PostgreSQL                                             | search/cache/analytics          |
| Album            | PostgreSQL                                             | search/cache/analytics          |
| Track metadata   | PostgreSQL                                             | search/cache/analytics          |
| Audio source     | S3                                                     | processing/CDN                  |
| Transcoded audio | S3                                                     | CloudFront                      |
| Playlist         | PostgreSQL                                             | cache/search/analytics          |
| Playlist items   | PostgreSQL                                             | cache/search                    |
| Likes            | PostgreSQL                                             | cache/recommendations/analytics |
| Playback history | PostgreSQL and/or dedicated durable event architecture | recommendations/analytics       |
| Search documents | Search engine                                          | none                            |
| Recommendations  | Recommendation pipeline                                | client cache                    |
| Subscription     | PostgreSQL + payment provider boundary                 | entitlement cache               |
| Notifications    | PostgreSQL                                             | push provider                   |
| Analytics events | event/analytics pipeline                               | dashboards/recommendations      |

Adjust this according to actual architecture.

Do not create conflicting authorities.

---

# 8. DOMAIN MODEL

Define conceptual entities and their responsibilities.

At minimum evaluate:

### Identity

* User
* Credential
* Session
* Device
* UserRole
* Permission

### User

* UserProfile
* UserPreference
* UserPrivacySetting

### Catalog

* Artist
* ArtistMember where appropriate
* Album
* Track
* TrackArtist
* AlbumArtist
* Genre
* TrackGenre
* Release
* ContentAvailability

### Media

* MediaAsset
* AudioSource
* AudioVariant
* MediaProcessingJob
* StreamingManifest
* ArtworkAsset

### Playlist

* Playlist
* PlaylistItem
* PlaylistCollaborator
* PlaylistFollower

### Library

* SavedTrack
* SavedAlbum
* SavedPlaylist
* Follow

### Playback

* PlaybackSession
* PlaybackState
* QueueItem
* PlaybackEvent
* PlaybackHistory

### Subscription

* SubscriptionPlan
* Subscription
* Entitlement
* PaymentCustomer
* BillingEvent

### Recommendation

* RecommendationCandidate
* RecommendationFeed
* RecommendationSignal

### Notification

* Notification
* NotificationPreference
* DevicePushToken
* NotificationDeliveryAttempt

### Administration

* AuditEvent
* ModerationCase
* ContentReport

Define:

* ownership
* lifecycle
* relationships
* aggregate boundaries
* invariants
* mutability
* deletion behavior

Do not over-normalize or create entities without a clear responsibility.

---

# 9. CATALOG ARCHITECTURE

Define the catalog hierarchy.

Clearly distinguish:

* artist
* album
* track
* release
* recording where useful
* genre
* artwork
* audio asset

Define how tracks relate to:

* artists
* featured artists
* albums
* releases
* genres

Support appropriate music structures such as:

* albums
* singles
* EPs
* compilations
* multiple artists
* featured artists
* explicit-content flags
* release dates
* track numbers
* disc numbers
* duration
* ISRC or equivalent identifiers where legitimately available

Define catalog lifecycle:

* draft
* processing
* pending review
* published
* hidden
* archived
* removed

Use states appropriate to the actual product.

---

# 10. ARTIST ARCHITECTURE

Define:

* artist profiles
* display names
* biographies
* artwork
* genres
* releases
* relationships
* followers
* verification/status
* content-management permissions

Define how artist accounts differ from ordinary users.

Prevent unauthorized users from modifying artist content.

---

# 11. ALBUM AND TRACK ARCHITECTURE

Define:

* album metadata
* track metadata
* ordering
* multiple discs
* explicit flags
* duration
* availability
* artwork
* artists
* featured artists
* release information

Determine how track availability interacts with:

* subscription
* geographic restrictions if implemented
* content status
* media processing
* takedowns
* catalog lifecycle

---

# 12. PLAYLIST ARCHITECTURE

Define:

* playlist ownership
* public/private/unlisted visibility
* playlist metadata
* playlist ordering
* playlist item identity
* collaborative editing
* collaborators
* follower relationships

Playlist operations must handle concurrency.

Consider:

* concurrent inserts
* deletes
* reordering
* duplicate tracks
* stale clients
* optimistic updates
* race conditions

Define an ordering strategy that scales.

Prevent unauthorized modification.

---

# 13. LIBRARY ARCHITECTURE

Define:

* liked tracks
* saved albums
* saved playlists
* followed artists
* followed playlists

Define:

* uniqueness
* idempotent mutation
* pagination
* synchronization
* cache invalidation
* privacy

A repeated like/unlike request must not corrupt state.

---

# 14. PLAYBACK ARCHITECTURE

Define the complete playback model.

Distinguish:

* playback intent
* playback authorization
* playback session
* playback state
* media authorization
* playback progress
* playback completion
* playback history
* analytics event

Define:

* player session
* device
* current track
* queue
* position
* duration
* playback state
* playback start time
* last heartbeat/progress
* quality/variant where appropriate

Support multiple devices while preventing unintended state corruption.

Define whether and how users can control playback across devices.

---

# 15. QUEUE ARCHITECTURE

Define:

* queue ownership
* queue ordering
* queue items
* insertion
* deletion
* reordering
* persistence
* synchronization across devices

Handle concurrent modifications safely.

Define whether the queue is:

* durable
* session-scoped
* device-scoped
* user-scoped

Do not store more data durably than necessary.

---

# 16. AUDIO MEDIA ARCHITECTURE

Design the complete audio lifecycle:

1. Source upload
2. Validation
3. Metadata extraction
4. Security inspection
5. Processing
6. Normalization where appropriate
7. Transcoding
8. Quality variants
9. Segmentation
10. Manifest generation
11. Storage
12. CDN publication
13. Playback authorization
14. Lifecycle management

Define:

* source object keys
* derived object keys
* processing states
* retries
* idempotency
* cleanup
* versioning
* deletion

Treat uploaded media as untrusted.

Do not permit unsafe shell command construction.

---

# 17. ADAPTIVE STREAMING

Define how HLS or another justified streaming protocol is used.

Specify:

* master manifest
* media playlists
* segments
* audio variants
* bitrate strategy
* sample rate/channel considerations
* codec strategy
* segment duration
* CDN caching
* access control
* expiration
* playback authorization

Explain how clients obtain authorized streaming access.

Do not expose private S3 credentials.

Determine whether manifests and segments are:

* public
* signed
* token-authorized
* session-authorized

Choose an approach appropriate to the threat model.

---

# 18. ARTWORK AND IMAGE MEDIA

Define:

* upload
* validation
* resizing
* thumbnails
* format variants
* storage
* CDN
* cache strategy
* ownership
* deletion
* moderation

Support appropriate artwork sizes for:

* mobile
* high-density displays
* playlists
* albums
* artists
* search
* recommendations

---

# 19. MEDIA PROCESSING JOB ARCHITECTURE

Define BullMQ jobs for operations such as:

* audio processing
* transcoding
* waveform generation
* artwork processing
* metadata extraction
* media cleanup
* search indexing

For each job specify:

* job name
* input
* output
* idempotency key
* retries
* timeout
* backoff
* concurrency
* failure behavior
* DLQ behavior
* observability
* cancellation/recovery

Avoid duplicate processing after worker crashes.

---

# 20. SEARCH ARCHITECTURE

Define the search projection.

Search should support:

* tracks
* artists
* albums
* playlists
* genres
* other legitimately searchable public entities

Define:

* document structures
* mappings
* analyzers
* aliases
* index versions
* reindexing
* incremental updates
* event-driven synchronization
* reconciliation

Search must not become authoritative for transactional catalog state.

Define:

* prefix search
* typo tolerance
* relevance
* exact identifiers
* filtering
* pagination
* suggestions
* ranking

Prevent:

* unrestricted DSL
* query abuse
* excessive resource consumption
* private-data leakage

---

# 21. RECOMMENDATION ARCHITECTURE

Design a practical recommendation architecture.

Potential signals:

* likes
* follows
* listening history
* completion rate
* skips
* repeats
* search activity
* playlist additions
* artist affinity
* genre affinity

Define:

* event collection
* candidate generation
* feature generation
* ranking
* personalization
* freshness
* fallback recommendations

Provide deterministic fallback behavior when personalization is unavailable.

Recommendations must not block core playback.

Do not claim machine-learning functionality unless an actual implementable pipeline is defined.

---

# 22. ANALYTICS ARCHITECTURE

Define event categories including:

* playback started
* playback progress
* playback completed
* playback skipped
* track liked
* track unliked
* playlist created
* playlist edited
* playlist followed
* artist followed
* search performed
* recommendation selected

Define an event envelope containing appropriate:

* event ID
* event type
* version
* timestamp
* user ID where permitted
* session ID
* device ID where appropriate
* entity ID
* correlation ID
* trace context
* safe metadata

Define:

* ingestion
* validation
* deduplication
* retention
* aggregation
* privacy
* downstream consumers

Avoid logging unnecessary private information.

---

# 23. EVENT-DRIVEN ARCHITECTURE

Where Kafka/Redpanda is justified, define:

* topics
* partitions
* keys
* ordering guarantees
* event schemas
* versions
* retention
* replay
* consumer groups
* retries
* dead-letter handling

Use transactional outbox where database state and events must remain consistent.

Consumers must be idempotent.

Design for:

* duplicate events
* delayed events
* out-of-order events
* consumer restarts
* replay
* schema evolution

---

# 24. REDIS ARCHITECTURE

Create a Redis responsibility matrix.

Potential uses:

* API cache
* playback ephemeral state
* rate limits
* session coordination
* recommendation cache
* search suggestion cache
* queue support
* BullMQ
* distributed locks only where genuinely necessary

For each important keyspace define:

* key format
* value
* TTL
* owner
* invalidation
* stale behavior
* failure behavior

Do not use Redis as the sole authoritative store for:

* users
* subscriptions
* playlists
* likes
* catalog
* orders/billing state
* other critical durable state

---

# 25. SUBSCRIPTION ARCHITECTURE

If premium subscriptions are included, define:

* plans
* pricing
* currencies
* subscription lifecycle
* entitlement calculation
* billing state
* provider boundary
* webhook processing
* reconciliation
* cancellation
* expiration
* grace periods where appropriate

Define states such as:

* ACTIVE
* TRIALING
* PAST_DUE
* CANCELLED
* EXPIRED
* PAUSED

Use states appropriate to the selected billing model.

The client must never be authoritative for entitlement.

---

# 26. PAYMENT ARCHITECTURE

If Stripe or another provider is used:

Define:

* customer mapping
* subscription mapping
* payment boundary
* webhook endpoint
* signature validation
* durable webhook event storage
* provider event deduplication
* idempotency
* reconciliation
* failure recovery

Never store card numbers or CVV.

Never trust client payment status.

Never invent provider behavior.

---

# 27. NOTIFICATION ARCHITECTURE

Define:

* notification record
* notification types
* preferences
* recipient resolution
* device push tokens
* delivery attempts
* provider state
* retries
* deduplication

Separate:

* transactional notifications
* security notifications
* product notifications
* optional marketing notifications

Never expose push credentials or device tokens unnecessarily.

---

# 28. AUTHENTICATION AND AUTHORIZATION

Define:

* registration
* login
* logout
* session management
* token/session renewal
* password recovery
* email verification
* device management
* account security

Define authorization for:

* ordinary users
* artists
* artist managers
* playlist owners
* playlist collaborators
* moderators
* administrators
* media operators

Create a permission matrix.

Prevent:

* IDOR
* privilege escalation
* ownership bypass
* role manipulation
* unauthorized artist-content modification

---

# 29. API ARCHITECTURE

Define versioned REST APIs.

At minimum evaluate API groups for:

* authentication
* users
* profiles
* artists
* albums
* tracks
* genres
* playlists
* library
* playback
* queue
* history
* search
* recommendations
* subscriptions
* notifications
* administration

For each API family define:

* ownership
* authentication
* authorization
* request DTO
* response DTO
* validation
* pagination
* filtering
* sorting
* error model
* idempotency
* rate limiting
* caching
* observability

Do not expose internal database models directly.

---

# 30. PLAYBACK API CONTRACT

Define secure playback APIs.

Potential flow:

1. Client requests playback authorization.
2. Backend validates:

   * authentication
   * entitlement
   * track availability
   * catalog status
   * device/session state
3. Backend returns an appropriate short-lived media authorization mechanism.
4. Client obtains streaming media through the CDN.
5. Client reports playback telemetry through controlled APIs.
6. Backend records authoritative playback history/events.

Do not return permanent unrestricted media URLs for protected content.

---

# 31. DATABASE ARCHITECTURE

Define the conceptual PostgreSQL schema.

For every major entity specify:

* primary key
* important fields
* foreign keys
* unique constraints
* indexes
* lifecycle state
* ownership
* timestamps
* soft deletion where justified
* retention behavior

Define:

* transaction boundaries
* isolation considerations
* concurrency controls
* migration strategy

Important constraints should be enforced by the database whenever practical.

---

# 32. CONCURRENCY AND IDEMPOTENCY

Explicitly design concurrency for:

* playlist edits
* likes
* follows
* queue operations
* playback history
* subscription webhooks
* media-processing jobs
* search indexing
* notification delivery
* recommendation events

For every mutation determine:

* idempotency requirement
* unique constraint
* transaction
* locking strategy
* retry behavior
* duplicate handling

---

# 33. PRIVACY ARCHITECTURE

Define privacy controls across:

* PostgreSQL
* Redis
* search
* events
* analytics
* recommendations
* notifications
* logs
* media
* backups

Separate:

* public catalog information
* private user information
* private playlists
* listening history
* personalization signals
* operational information

Do not allow private data to enter public search indexes.

---

# 34. SECURITY THREAT MODEL

Create a threat model covering:

* authentication
* authorization
* account takeover
* token theft
* IDOR
* API abuse
* media access
* malicious uploads
* FFmpeg execution
* CDN access
* search abuse
* playlist collaboration abuse
* WebSocket abuse if used
* push notification abuse
* provider webhook spoofing
* subscription manipulation
* event injection
* analytics poisoning
* secret leakage
* SSRF
* injection
* rate-limit bypass

For each threat define:

* attack surface
* mitigation
* detection
* recovery

---

# 35. OBSERVABILITY ARCHITECTURE

Define:

## Logs

* structured
* correlation-aware
* privacy-safe

## Metrics

Include:

* API latency
* API errors
* authentication failures
* playback authorization failures
* playback starts
* playback failures
* streaming authorization latency
* queue latency
* media-processing duration
* transcoding failures
* queue depth
* event lag
* search latency
* search errors
* database performance
* Redis performance
* recommendation latency
* notification delivery
* subscription webhook failures

## Tracing

Trace:

* HTTP
* database
* Redis
* queues
* events
* search
* media-processing workflows
* external providers

Define important SLO candidates.

---

# 36. RELIABILITY ARCHITECTURE

Define behavior during:

* PostgreSQL outage
* Redis outage
* search outage
* CDN failure
* S3 failure
* media-worker failure
* queue failure
* Kafka/Redpanda failure
* payment-provider outage
* notification-provider outage
* recommendation outage

For each:

* user-visible behavior
* retry behavior
* timeout
* fallback
* recovery
* data-consistency strategy

Core playback and core account operations should degrade gracefully when noncritical systems fail.

---

# 37. DATA RETENTION AND LIFECYCLE

Define retention for:

* sessions
* playback history
* analytics events
* notifications
* audit events
* media-processing records
* source media
* derived media
* search documents
* deleted accounts
* deleted playlists
* recommendation signals

Define:

* deletion
* archival
* anonymization
* expiration
* legal/operational retention boundaries where applicable

Do not claim regulatory compliance without validating actual requirements and implementation.

---

# 38. MOBILE ARCHITECTURE

Define the mobile application architecture.

Use:

* React Native
* Expo
* TypeScript
* React Navigation
* TanStack Query
* Zustand

Define:

* navigation
* authentication state
* server-state management
* player state
* queue state
* local persistence
* secure storage
* deep linking
* offline behavior
* network recovery
* background playback
* audio interruptions
* device media controls
* push notifications
* accessibility

Clearly separate:

* server state
* local UI state
* playback engine state
* durable local preferences

---

# 39. MOBILE PLAYBACK ARCHITECTURE

Define:

* audio player abstraction
* playback service
* queue
* background playback
* lock-screen controls where supported
* headset/Bluetooth interactions where supported
* interruptions
* network transitions
* buffering
* quality changes
* playback errors
* telemetry

Avoid tying business logic directly to a specific platform implementation.

---

# 40. CACHE AND SYNCHRONIZATION STRATEGY

Define:

* server cache
* client cache
* Redis cache
* CDN cache
* TanStack Query cache
* local mobile persistence

For every cache define:

* authority
* TTL
* invalidation
* stale behavior
* refresh behavior

Ensure mutations invalidate affected cached data.

---

# 41. API SECURITY

Define:

* rate limits
* request validation
* payload limits
* authentication throttling
* pagination limits
* query complexity limits
* search limits
* upload limits
* playback authorization limits
* abuse prevention

Prevent users from bypassing limits by:

* rotating IDs
* using multiple sessions
* manipulating pagination
* replaying requests
* exploiting unauthenticated endpoints

---

# 42. MEDIA ACCESS SECURITY

Define the authorization flow for:

* source audio
* processed audio
* HLS manifests
* HLS segments
* artwork
* private media

Consider:

* short-lived authorization
* signed URLs
* signed cookies
* CDN controls
* entitlement validation
* expiration
* revocation limitations

The architecture must acknowledge that CDN-delivered media cannot be made absolutely impossible to capture once legitimately delivered to a client.

Design for reasonable access control rather than impossible guarantees.

---

# 43. ADMINISTRATION AND MODERATION

Define administrative boundaries for:

* users
* artists
* albums
* tracks
* playlists where appropriate
* media
* reports
* moderation
* catalog publication
* takedowns
* account restrictions
* operational jobs

Every privileged operation must be:

* authenticated
* authorized
* auditable

---

# 44. INFRASTRUCTURE ARCHITECTURE

Define the production topology.

Evaluate:

* AWS regions
* availability zones
* VPC
* public/private subnets
* load balancing
* application compute
* worker compute
* PostgreSQL
* Redis
* OpenSearch
* S3
* CloudFront
* DNS
* TLS
* WAF
* secrets
* IAM
* monitoring

Explain why each component exists.

---

# 45. SCALABILITY

Design for substantial scale.

The architecture should be capable of supporting growth toward:

* millions of users
* high concurrent playback
* large music catalogs
* large playlist counts
* high search traffic
* large playback-event volume
* large media-processing workloads

Do not invent exact capacity guarantees without load testing.

Identify likely bottlenecks:

* playback authorization
* CDN traffic
* PostgreSQL
* Redis
* search
* media processing
* analytics ingestion
* event streams
* recommendation computation

Define scaling strategies for each.

---

# 46. FAILURE MATRICES

Create explicit failure matrices for critical workflows.

At minimum:

### Authentication

* database unavailable
* Redis unavailable
* invalid credentials
* expired session
* replayed token

### Playback

* authorization failure
* entitlement unavailable
* CDN failure
* manifest failure
* segment failure
* network loss
* player interruption

### Playlist

* concurrent update
* stale client
* unauthorized collaborator
* duplicate request

### Media Processing

* worker crash
* FFmpeg failure
* corrupted input
* duplicate job
* storage failure

### Search

* stale index
* indexing failure
* search outage
* malformed query

### Subscription

* provider outage
* duplicate webhook
* out-of-order webhook
* reconciliation mismatch

### Notifications

* provider outage
* duplicate event
* invalid token
* worker failure

---

# 47. SECURITY AND PRIVACY INVARIANTS

Define explicit invariants such as:

* users cannot access another user's private data
* users cannot modify playlists without permission
* only authorized users can manage artist content
* clients cannot grant themselves premium entitlements
* private playlists never enter public search
* raw provider secrets never reach clients
* private media cannot be accessed without authorization
* duplicate likes do not create duplicate records
* duplicate webhook events do not create duplicate subscription state transitions
* duplicate jobs do not corrupt media state
* search cannot expose unpublished content
* analytics cannot modify authoritative business state

---

# 48. ARCHITECTURAL DECISION RECORDS

Define ADRs for major decisions.

At minimum evaluate ADRs for:

* PostgreSQL as transactional authority
* Redis usage
* search architecture
* HLS/adaptive streaming
* S3/CloudFront media architecture
* BullMQ
* Kafka/Redpanda
* mobile architecture
* playback synchronization
* recommendation architecture
* subscription/payment architecture
* authentication/session strategy
* multi-region strategy
* Kubernetes/EKS decision

Each ADR should contain:

* decision
* alternatives
* rationale
* consequences
* operational implications

---

# 49. TEST ARCHITECTURE

Define the architecture-level testing strategy.

Include:

* unit testing
* integration testing
* database testing
* API testing
* contract testing
* authorization testing
* concurrency testing
* event testing
* queue testing
* media-processing testing
* playback authorization testing
* search testing
* subscription webhook testing
* mobile testing
* E2E
* accessibility
* performance
* resilience
* security regression

Define test boundaries and environments.

---

# 50. DEPLOYMENT ARCHITECTURE

Define:

* local development
* development environment
* staging
* production
* CI/CD
* database migrations
* application deployment
* worker deployment
* media-processing deployment
* search index migration
* rollback strategy
* configuration
* secrets
* health checks
* graceful shutdown

Deployment must support safe incremental releases.

---

# 51. VERSIONING AND EVOLUTION

Define versioning for:

* REST APIs
* database migrations
* events
* search indexes
* media-processing contracts
* job payloads
* recommendation data
* mobile/backend compatibility

Design for rolling deployments where old and new application versions may coexist temporarily.

Avoid breaking event consumers during schema evolution.

---

# 52. ARCHITECTURE DELIVERABLE

Produce a comprehensive architecture specification containing:

1. Repository architecture audit
2. System context
3. Architecture principles
4. Bounded contexts
5. Dependency rules
6. Source-of-truth matrix
7. Domain model
8. Catalog architecture
9. Playlist architecture
10. Library architecture
11. Playback architecture
12. Queue architecture
13. Media architecture
14. Adaptive streaming architecture
15. Media-processing architecture
16. Search architecture
17. Recommendation architecture
18. Analytics architecture
19. Event architecture
20. Redis architecture
21. Subscription/payment architecture
22. Notification architecture
23. Authentication architecture
24. Authorization model
25. API architecture
26. Database architecture
27. Concurrency model
28. Idempotency model
29. Privacy architecture
30. Security threat model
31. Observability architecture
32. Reliability architecture
33. Data lifecycle
34. Mobile architecture
35. Cache/synchronization strategy
36. Media access security
37. Administration/moderation
38. Infrastructure topology
39. Scalability model
40. Failure matrices
41. Security/privacy invariants
42. ADRs
43. Testing architecture
44. Deployment architecture
45. Versioning strategy
46. Architectural risks
47. Migration strategy for existing repository code

---

# 53. IMPLEMENTATION BOUNDARY

This prompt defines architecture only.

Do NOT:

* implement backend modules
* implement mobile screens
* implement database migrations
* implement API controllers
* implement media workers
* implement infrastructure
* write production source code
* create fake implementation files
* create placeholder files
* claim implementation is complete

The output must describe the architecture precisely enough for later engineering implementation.

---

# 54. REPOSITORY COMPATIBILITY

If existing repository implementation conflicts with the desired architecture:

* identify the conflict
* determine whether the existing implementation is reusable
* define the migration required
* preserve compatible behavior
* avoid unnecessary rewrites
* avoid duplicate systems

Never assume a clean-slate project when the repository contains implementation.

---

# 55. FINAL ARCHITECTURAL VALIDATION

Before completing the architecture, verify:

* every major domain has a clear owner
* dependencies do not form uncontrolled cycles
* PostgreSQL authority is clear
* Redis authority is limited
* search is a projection
* media lifecycle is defined
* playback authorization is secure
* CDN access is controlled
* subscription entitlement is server-authoritative
* webhook processing is idempotent
* events have schemas and versions
* background jobs are idempotent
* private data boundaries are explicit
* administrative permissions are explicit
* concurrency behavior is defined
* failure behavior is defined
* observability is defined
* scalability bottlenecks are identified
* mobile/server responsibilities are clear
* deployment strategy is defined
* migration/versioning strategy is defined
* testing boundaries are defined

Do not leave critical architectural decisions implicit.

---

# 56. FACTUAL REPORTING

At the end, clearly distinguish:

* architecture discovered in the repository
* architecture proposed for the platform
* existing implementation gaps
* architectural conflicts
* migration requirements
* unresolved decisions
* assumptions
* risks

Do not claim that code was implemented.

Do not claim that tests passed unless tests were actually executed.

Do not claim that infrastructure exists unless it actually exists in the repository.

Do not claim production readiness based solely on architectural design.

---

# 57. STANDALONE REQUIREMENT

This architecture prompt is fully standalone.

It must be executable without requiring:

* a previous prompt
* a previous architecture document
* a previous AI response
* hidden conversation context
* an assumed approved design

The repository remains the implementation source of truth.

Any later implementation prompt must independently contain enough project context and technical constraints to perform its assigned work safel

You are operating in Senior Engineering Team Mode.

Design the complete foundational architecture for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

Do not implement backend code.

Do not implement frontend code.

Do not implement mobile code.

Do not generate infrastructure implementation files.

Do not generate Dockerfiles.

Do not generate Kubernetes manifests.

Do not generate Terraform files.

Do not generate application source code.

Produce architecture, specifications, contracts, diagrams, schemas, ownership rules, engineering decisions, and implementation guidance only.

────────────────────────────────────────

PROJECT

Build a production-ready global music streaming and audio entertainment platform supporting:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Millions of albums and releases
• Large artist and creator ecosystem
• Podcasts
• Episodes
• Audiobooks where supported
• Personalized recommendations
• Search
• Discovery
• Playlists
• Libraries
• Liked songs
• Artist following
• Listening history
• Radio and stations
• Charts
• New releases
• Multiple subscription plans
• Free/ad-supported plans
• Premium plans
• Family plans
• Student plans
• Regional pricing
• Payments
• Billing
• Entitlements
• Offline downloads
• Multi-device synchronization
• Background playback
• Global CDN delivery
• Content rights management
• Artist/content-partner workflows
• Analytics
• Advertising
• Moderation
• Administration
• Multi-region deployment
• High availability
• Disaster recovery

The platform must be:

• Cloud-native
• Horizontally scalable
• Fault tolerant
• Secure
• Observable
• Cost-conscious
• Extensible
• Production-ready

────────────────────────────────────────

PRIMARY TECHNOLOGY STACK

WEB

• Next.js
• React
• TypeScript
• Tailwind CSS
• shadcn/ui
• TanStack Query
• Zustand

MOBILE

• React Native
• Expo
• TypeScript

BACKEND

• Node.js
• NestJS
• TypeScript

DATABASE

• PostgreSQL
• Prisma ORM

CACHE

• Redis

EVENT STREAMING

• Kafka or Redpanda

BACKGROUND PROCESSING

• BullMQ

SEARCH

• Elasticsearch or OpenSearch

OBJECT STORAGE

• AWS S3-compatible object storage

CDN

• CloudFront or equivalent CDN

MEDIA PROCESSING

• FFmpeg
• Approved audio-processing infrastructure

PAYMENTS

• Stripe or approved payment abstraction

NOTIFICATIONS

• Firebase Cloud Messaging
• Apple Push Notification Service
• Email provider abstraction

AUDIO DELIVERY

• HLS or equivalent adaptive audio streaming
• CDN-based delivery
• Signed playback authorization where appropriate

INFRASTRUCTURE

• Docker
• Kubernetes
• Helm
• Terraform
• GitHub Actions

OBSERVABILITY

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

SECRETS

• AWS Secrets Manager
• HashiCorp Vault or approved cloud-native secret management

────────────────────────────────────────

ARCHITECTURAL APPROACH

Determine whether the platform should initially use:

• Modular Monolith
• Service-Oriented Architecture
• Microservices

Do not blindly create a microservice for every domain.

Evaluate:

• Playback scale
• Media delivery
• Catalog size
• Search scale
• Recommendation scale
• Transactional consistency
• Latency
• Operational complexity
• Team ownership
• Deployment independence
• Failure isolation
• Cost
• Developer productivity
• Future extensibility

Clearly identify:

• Independently deployable services
• Shared transactional boundaries
• Authoritative data ownership
• Synchronous communication
• Asynchronous communication
• Event-driven communication
• Read models
• CQRS requirements
• Strong consistency requirements
• Eventual consistency boundaries

Provide a future extraction strategy where appropriate.

────────────────────────────────────────

APPLICATION ARCHITECTURE

Design:

CUSTOMER WEB

• Home
• Search
• Discovery
• Artist
• Album
• Track
• Playlist
• Library
• Podcasts
• Player
• Queue
• Subscription
• Account

CUSTOMER MOBILE

• iOS
• Android
• Background playback
• Offline downloads
• Push notifications
• Deep links
• Device synchronization

ARTIST / CREATOR PLATFORM

• Artist profiles
• Content submission
• Release management
• Metadata
• Media uploads
• Rights
• Analytics
• Audience insights

ADMINISTRATION

• Users
• Content
• Rights
• Moderation
• Subscriptions
• Payments
• Advertising
• Analytics
• Feature flags
• Audit

PUBLIC API

• Catalog
• Search
• Playback
• Playlists
• Library
• Recommendations

INTERNAL SERVICES

• Service-to-service APIs
• Event processing
• Background workers
• Schedulers

────────────────────────────────────────

DOMAIN DECOMPOSITION

Define bounded contexts for:

Identity

Accounts

Profiles

Authentication

Authorization

Sessions

Devices

Subscriptions

Billing

Payments

Entitlements

Catalog

Artists

Artist Teams

Labels

Albums

Releases

Tracks

Audio Assets

Audio Renditions

Artwork

Genres

Tags

Lyrics

Explicit Content

Rights

Availability

Localization

Search

Discovery

Recommendations

Personalization

Playlists

Playlist Items

Library

Liked Songs

Saved Albums

Followed Artists

Listening History

Playback

Playback Sessions

Playback Progress

Queue

Radio

Stations

Charts

Podcasts

Shows

Episodes

Audiobooks

Downloads

Offline Licenses

Notifications

Advertising

Analytics

Moderation

Administration

Audit

Feature Flags

System Configuration

For each bounded context define:

• Responsibility
• Aggregate roots
• Entities
• Value objects
• Repository boundaries
• Domain services
• Events
• Data ownership
• Consistency model
• Scaling characteristics

────────────────────────────────────────

SERVICE DECOMPOSITION

Evaluate appropriate service boundaries for:

API Gateway

Authentication Service

Identity Service

Account Service

Profile Service

Session Service

Device Service

Subscription Service

Billing Service

Payment Service

Entitlement Service

Catalog Service

Artist Service

Release Service

Track Service

Metadata Service

Media Service

Audio Processing Service

Artwork Service

Rights Service

Availability Service

Localization Service

Playback Authorization Service

Playback Session Service

Playback Progress Service

Download Service

Offline License Service

Playlist Service

Library Service

Search Service

Discovery Service

Recommendation Service

Personalization Service

Radio Service

Chart Service

Podcast Service

Podcast Episode Service

Notification Service

Advertising Service

Ad Decision Service

Analytics Service

Moderation Service

Administration Service

Audit Service

Feature Flag Service

Configuration Service

Do not create unnecessary services.

Combine cohesive responsibilities where strong transactional consistency and operational simplicity justify it.

For every final service define:

• Responsibility
• Owned data
• APIs
• Events produced
• Events consumed
• Synchronous dependencies
• Asynchronous dependencies
• Scaling requirements
• Availability requirements
• Security boundaries

────────────────────────────────────────

SERVICE OWNERSHIP MATRIX

Create a complete ownership matrix.

For each domain identify:

• Authoritative service
• Database ownership
• Read-model ownership
• Event ownership
• Cache ownership
• Search ownership
• Administrative ownership

Explicitly define which services must never directly modify another service's authoritative data.

────────────────────────────────────────

COMMUNICATION MATRIX

For major service interactions define:

• Producer
• Consumer
• Protocol
• Direction
• Synchronous/asynchronous
• Purpose
• Timeout
• Retry
• Idempotency
• Consistency expectation
• Failure behavior

Evaluate:

• REST
• Kafka/Redpanda
• BullMQ
• Redis
• WebSockets
• Server-Sent Events where appropriate

Avoid unnecessary synchronous chains.

────────────────────────────────────────

SYSTEM ARCHITECTURE

Generate text-based architecture diagrams covering:

CLIENT LAYER

• Web
• iOS
• Android
• Future TV/device integrations

EDGE LAYER

• DNS
• CDN
• WAF
• Load balancing
• API Gateway
• Playback authorization boundary

APPLICATION LAYER

• Domain services
• Playback services
• Search
• Recommendation services
• Background workers
• Event consumers
• Schedulers

DATA LAYER

• PostgreSQL
• Read replicas
• Redis
• Kafka/Redpanda
• Elasticsearch/OpenSearch
• Object storage

MEDIA LAYER

• Source upload
• Validation
• Audio processing
• Rendition generation
• Packaging
• Content protection
• CDN delivery

OBSERVABILITY LAYER

• Logs
• Metrics
• Traces
• Alerts

SECURITY LAYER

• IAM
• Authentication
• Authorization
• Secrets
• Encryption
• Audit

Do not use images.

────────────────────────────────────────

MONOREPO ARCHITECTURE

Design a production-ready monorepo containing:

APPLICATIONS

• Customer Web
• Customer Mobile
• Artist/Creator Platform
• Administration

BACKEND

• API Gateway
• Domain services
• Playback services
• Workers
• Event consumers

SHARED PACKAGES

• API contracts
• Event contracts
• Shared types
• Validation
• Configuration
• Authentication interfaces
• Authorization utilities
• Observability
• Media interfaces
• Testing utilities
• Design tokens where appropriate

INFRASTRUCTURE

• Docker
• Kubernetes
• Helm
• Terraform
• CI/CD

DOCUMENTATION

• Architecture
• API
• Events
• Database
• Media
• Security
• Operations
• ADRs
• Runbooks

Do not create uncontrolled shared packages.

Shared packages must have clear ownership.

────────────────────────────────────────

FOLDER HIERARCHY

Generate a detailed hierarchy for:

• Monorepo root
• Web
• Mobile
• Artist platform
• Admin
• API Gateway
• Backend services
• Workers
• Shared packages
• Database
• Infrastructure
• Tests
• Documentation
• Configuration
• Migrations

Include major directories and files.

Do not generate implementation code.

────────────────────────────────────────

CORE DOMAIN MODEL

Evaluate and define:

Account

User

Profile

Session

Device

Subscription

SubscriptionPlan

BillingAccount

Payment

PaymentMethod

Invoice

Refund

Entitlement

Artist

ArtistMember

Label

Album

Release

Track

TrackCredit

AudioAsset

AudioRendition

Artwork

Genre

Tag

Lyrics

ContentAvailability

ContentRight

Region

Language

Playlist

PlaylistItem

PlaylistCollaborator

LibraryItem

LikedTrack

SavedAlbum

FollowedArtist

ListeningHistory

PlaybackSession

PlaybackProgress

Queue

Recommendation

RecommendationFeed

PersonalizationProfile

Download

OfflineLicense

Podcast

PodcastShow

PodcastEpisode

Audiobook

Notification

NotificationPreference

AdvertisingCampaign

AdCreative

AdImpression

ModerationCase

AuditLog

FeatureFlag

SystemConfiguration

Do not force every conceptual entity into a separate table.

Use aggregates and normalized relational structures appropriately.

────────────────────────────────────────

ERD

Generate a complete text-based ERD.

Include:

• Primary keys
• Foreign keys
• Cardinality
• Ownership
• Important indexes
• High-growth tables
• Partitioning candidates

Clearly show relationships between:

• Accounts
• Profiles
• Devices
• Subscriptions
• Entitlements
• Artists
• Albums
• Releases
• Tracks
• Audio assets
• Playlists
• Library
• Listening history
• Playback
• Downloads
• Offline licenses
• Podcasts
• Recommendations
• Notifications

────────────────────────────────────────

POSTGRESQL ARCHITECTURE

Design PostgreSQL for:

• Hundreds of millions of accounts
• Millions of tracks
• Large playlist volume
• Billions of playback/listening events
• Large subscription volume
• Large device/session volume

Define:

• Database ownership
• Schema boundaries
• Primary/replica architecture
• Connection pooling
• Indexing
• Partitioning
• Archival
• Retention
• Backup
• Read/write separation

Identify partitioning candidates for:

• Listening history
• Playback events
• Playback sessions
• Notifications
• Audit logs
• Analytics references

Do not place raw high-volume playback telemetry directly into ordinary transactional tables unless specifically justified.

────────────────────────────────────────

PRISMA STRATEGY

Define:

• Schema ownership
• Service-specific Prisma clients where appropriate
• Migration ownership
• Transaction boundaries
• Read replica strategy
• Connection pooling
• Query performance rules

Avoid uncontrolled cross-service database access.

────────────────────────────────────────

REDIS ARCHITECTURE

Design Redis usage for:

• Session caching
• Rate limiting
• Recommendation caching
• Home-feed caching
• Search caching
• Playback coordination
• Device synchronization
• Queue infrastructure
• Distributed locks
• Temporary download state

For every major use case define:

• Key pattern
• TTL
• Invalidation
• Consistency
• Failure behavior

Redis must never become the system of record for:

• Payments
• Subscriptions
• Entitlements
• Playlists
• Libraries
• Historical listening records

────────────────────────────────────────

MEDIA AND AUDIO ARCHITECTURE

Design the audio ingestion and delivery pipeline.

Support:

• Source upload
• File validation
• Malware-scanning boundary
• Metadata extraction
• Loudness analysis
• Audio validation
• FFmpeg processing
• Multiple codecs
• Multiple bitrate renditions
• Artwork processing
• Lyrics metadata
• Packaging
• Content protection
• CDN delivery

Define:

• Original storage
• Processing storage
• Final storage
• Temporary storage
• Cleanup
• Signed uploads
• CDN integration

Application servers must not proxy high-bandwidth audio delivery.

────────────────────────────────────────

AUDIO RENDITION ARCHITECTURE

Define a flexible audio capability abstraction.

Support conceptual quality tiers such as:

• Low
• Standard
• High
• Lossless where supported

Support future codecs and formats.

Do not hard-code architecture to a single codec.

Define:

• Codec
• Container
• Bitrate
• Sample rate
• Channels
• Quality profile
• Device compatibility

────────────────────────────────────────

ADAPTIVE AUDIO STREAMING

Design:

• Master manifests
• Variant playlists
• Audio segments
• Segment storage
• CDN caching
• Playback authorization
• Signed access
• Token expiration
• Quality selection

Support HLS or equivalent adaptive audio streaming.

Future formats must be possible without redesigning playback APIs.

────────────────────────────────────────

PLAYBACK ARCHITECTURE

Define:

• Playback authorization
• Entitlement validation
• Rights validation
• Regional availability validation
• Device validation
• Concurrent stream limits
• Playback session creation
• Secure playback token generation
• Playback progress
• Resume
• Queue synchronization
• Session expiration
• Playback termination

Define how the platform mitigates:

• Unauthorized playback
• Expired credential reuse
• Basic credential sharing abuse
• Excessive simultaneous streams

Do not claim perfect account-sharing prevention.

────────────────────────────────────────

PLAYBACK CONSISTENCY

Define consistency requirements for:

• Playback session
• Current track
• Queue
• Playback progress
• Device state
• Recently played
• Listening history

Separate:

• Real-time player state
• Persisted playback progress
• Historical analytics

Do not write every player event synchronously to PostgreSQL.

────────────────────────────────────────

OFFLINE DOWNLOAD ARCHITECTURE

Design offline listening.

Support:

• Download authorization
• Device registration
• Entitlement validation
• Download manifest
• Encrypted local storage
• Offline license
• License expiration
• License renewal
• Device limits
• Download limits
• Device revocation
• Cleanup

Do not store downloadable audio as unprotected files.

Do not implement custom cryptographic DRM in the architecture.

────────────────────────────────────────

SUBSCRIPTION ARCHITECTURE

Support:

• Free plan
• Premium
• Family
• Student
• Regional plans
• Trial
• Upgrade
• Downgrade
• Cancellation
• Grace period
• Payment failure
• Renewal

Separate:

• Billing state
• Payment state
• Subscription state
• Entitlement state

────────────────────────────────────────

ENTITLEMENT ARCHITECTURE

Define entitlement decisions for:

• Streaming
• Downloads
• Premium features
• Family access
• Student access
• Regional content
• Device capabilities

Entitlement validation must be available with low latency.

Define caching and failure behavior.

────────────────────────────────────────

PAYMENT ARCHITECTURE

Use a payment abstraction.

Support:

• Checkout
• Payment methods
• Payment intents
• Webhooks
• Verification
• Idempotency
• Refunds
• Reconciliation
• Failed-payment recovery

Do not store unnecessary raw payment information.

────────────────────────────────────────

RIGHTS AND AVAILABILITY

Design:

• Content rights
• Region
• Start date
• End date
• Subscription restriction
• Platform restriction
• Device restriction
• Content removal
• Rights expiration

Playback authorization must validate rights before issuing access.

────────────────────────────────────────

CONTENT CATALOG

Support:

• Artists
• Albums
• Releases
• Tracks
• Credits
• Genres
• Tags
• Lyrics
• Artwork
• Explicit content
• Localized metadata

Support future media types without redesigning the catalog.

Define content lifecycle:

Draft
→ Submitted
→ Validating
→ Processing
→ Review
→ Approved
→ Scheduled
→ Published
→ Unpublished
→ Archived
→ Removed

────────────────────────────────────────

ARTIST / LABEL / PARTNER ARCHITECTURE

Support:

• Artist accounts
• Artist staff
• Labels
• Content partners
• Releases
• Metadata
• Asset upload
• Rights declarations
• Publishing workflow
• Analytics

Define strict partner isolation.

Artist users must only manage authorized content.

────────────────────────────────────────

PLAYLIST ARCHITECTURE

Support:

• Private playlists
• Public playlists
• Shared playlists
• Collaborative playlists
• Playlist ownership
• Collaborators
• Ordering
• Reordering
• Versioning
• Permissions

Define concurrency handling for collaborative updates.

Do not expose private playlists through public search.

────────────────────────────────────────

USER LIBRARY

Support:

• Liked tracks
• Saved albums
• Followed artists
• Saved playlists
• Recently played
• Library organization

Define:

• Device synchronization
• Offline cache
• Consistency

────────────────────────────────────────

PODCAST ARCHITECTURE

Support:

• Shows
• Episodes
• Episode metadata
• Artwork
• Playback progress
• Downloads
• Subscriptions/follows

Design podcast playback separately enough to accommodate different metadata and monetization requirements.

────────────────────────────────────────

AUDIOBOOK ARCHITECTURE

Create extensibility for future audiobooks.

Support conceptual boundaries for:

• Books
• Chapters
• Narrators
• Playback progress
• Entitlements
• Offline access

Do not require audiobook-specific complexity in the initial implementation if not needed.

────────────────────────────────────────

SEARCH ARCHITECTURE

Design indexes for:

• Artists
• Albums
• Tracks
• Playlists
• Podcasts
• Episodes
• Genres
• Audiobooks
• Users where permitted

Support:

• Full-text
• Autocomplete
• Typo tolerance
• Language-aware search
• Filters
• Ranking
• Popularity
• Recency

Define:

• Index ownership
• Mapping
• Indexing pipeline
• Event-driven updates
• Reindexing
• Aliases
• Versioning

Private user data must not become publicly searchable.

────────────────────────────────────────

RECOMMENDATION ARCHITECTURE

Design for:

• Personalized home
• Daily mixes
• Similar tracks
• Similar artists
• Trending
• New releases
• Genre discovery
• Radio
• Personalized playlists
• Recently played recommendations

Define:

• Candidate generation
• Ranking
• User signals
• Context signals
• Content metadata
• Batch processing
• Real-time signals
• Recommendation cache
• Experimentation
• Fallback strategy

Architecture must support future ML systems.

────────────────────────────────────────

RADIO AND STATIONS

Design:

• Artist radio
• Track radio
• Genre stations
• Personalized stations
• Trending stations

Define:

• Candidate generation
• Ranking
• Session continuity
• Deduplication
• Personalization

Radio failure must degrade gracefully.

────────────────────────────────────────

CHARTS

Support:

• Global charts
• Regional charts
• Genre charts
• Trending charts
• Time-windowed rankings

Define:

• Aggregation windows
• Ranking methodology
• Update frequency
• Anti-fraud signals
• Historical snapshots

────────────────────────────────────────

ANALYTICS ARCHITECTURE

Define event ingestion for:

• Playback
• Search
• Playlist behavior
• Likes
• Saves
• Follows
• Downloads
• Subscription
• Advertisement
• Recommendation interaction

Separate:

• Transactional data
• Operational data
• Analytical events

Define long-term analytics storage boundaries.

────────────────────────────────────────

ADVERTISING ARCHITECTURE

Design support for:

• Free/ad-supported plans
• Audio ads
• Campaigns
• Creatives
• Targeting
• Ad breaks
• Ad decisions
• Impressions
• Completions
• Frequency capping
• Reporting
• Consent

Advertising failure must not break basic playback.

────────────────────────────────────────

NOTIFICATION ARCHITECTURE

Support:

• Push
• Email
• In-app

Events:

• New releases
• Followed artist releases
• Playlist updates
• Subscription events
• Payment failures
• Security events
• Recommendations
• Download completion

Define:

• Preferences
• Deduplication
• Scheduling
• Retry
• Provider failures
• Rate limits

────────────────────────────────────────

SECURITY ARCHITECTURE

Define complete security architecture covering:

IDENTITY

• Password security
• MFA
• Passkeys
• Sessions
• Token rotation
• Device management

AUTHORIZATION

• RBAC
• Resource ownership
• Playlist permissions
• Artist permissions
• Administrative permissions

CONTENT

• Playback authorization
• Rights enforcement
• Secure playback credentials
• Download protection

APPLICATION

• Input validation
• Rate limiting
• Secure headers
• CORS
• CSRF where applicable
• XSS protection
• SQL injection protection

INFRASTRUCTURE

• IAM
• Least privilege
• Network segmentation
• Secrets
• Encryption
• Audit

────────────────────────────────────────

ABUSE PREVENTION

Design defenses against:

• Stream manipulation
• Fake listening
• Bot accounts
• Playlist spam
• Follow abuse
• Automated scraping
• Credential stuffing
• Malicious media uploads
• API abuse
• Account takeover

Define:

• Detection
• Risk scoring
• Rate limiting
• Reputation
• Automated enforcement
• Manual review

────────────────────────────────────────

MODERATION

Design moderation for:

• Artist profiles
• Album metadata
• Playlist content
• Podcast content
• User content
• Reviews/comments where applicable
• Malicious uploads

Support:

• Reports
• Automated checks
• Manual review
• Appeals
• Policy versioning
• Audit

────────────────────────────────────────

DATA CONSISTENCY

Explicitly define consistency for:

• Accounts
• Subscriptions
• Payments
• Entitlements
• Catalog
• Rights
• Playlists
• Library
• Playback progress
• Downloads
• Search
• Recommendations
• Notifications
• Analytics

Define where to use:

• Strong consistency
• Eventual consistency
• Idempotency
• Optimistic concurrency
• Distributed locks
• Transactional outbox
• Saga patterns where justified

────────────────────────────────────────

SCALABILITY

Design for:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Large playlist volume
• High playback authorization traffic
• High playback telemetry volume
• Large search traffic
• Large recommendation traffic
• Large CDN traffic

Analyze scaling for:

• API gateway
• Authentication
• Catalog
• Playback authorization
• Redis
• Kafka
• Search
• Recommendation
• Audio processing
• S3
• CDN
• Analytics

Identify bottlenecks and mitigations.

────────────────────────────────────────

MULTI-REGION ARCHITECTURE

Design:

• Regional application clusters
• Global routing
• Regional data ownership
• Content replication
• CDN delivery
• Search recovery
• Event replication where required
• Failover

Classify data as:

• Region-local
• Globally replicated
• Eventually consistent
• Strongly consistent

Avoid unnecessary cross-region synchronous calls.

────────────────────────────────────────

FAILURE SCENARIOS

Define graceful behavior for:

• PostgreSQL failure
• Redis failure
• Kafka failure
• Search failure
• Recommendation failure
• Payment-provider failure
• S3 failure
• CDN degradation
• Audio-processing backlog
• Notification-provider failure
• Region failure

For every failure define:

• Detection
• Retry
• Fallback
• Degraded mode
• Recovery
• Reconciliation

────────────────────────────────────────

OBSERVABILITY ARCHITECTURE

Define:

• Metrics
• Structured logs
• Distributed traces
• Correlation IDs
• Trace propagation
• Dashboards
• Alerts

Required metrics include:

Playback:

• Startup latency
• Playback success
• Playback failure
• Buffering
• Quality changes

Search:

• Latency
• Zero-result rate
• Index freshness

Recommendations:

• Generation latency
• Cache hit rate
• Interaction rate

Subscriptions:

• Conversion
• Renewal
• Churn
• Payment failures

Media:

• Processing latency
• Queue depth
• Failure rate

Infrastructure:

• CPU
• Memory
• Database
• Redis
• Kafka
• Search

────────────────────────────────────────

DISASTER RECOVERY

Define:

• RTO
• RPO
• PostgreSQL backup
• PITR
• S3 replication
• Kafka recovery
• Redis recovery
• Search recovery
• Kubernetes recovery
• Regional failover

Include recovery procedures for:

• Database failure
• Region failure
• CDN failure
• Search failure
• Event-stream failure
• Media-processing failure

────────────────────────────────────────

TESTING ARCHITECTURE

Define:

UNIT TESTING

• Domain logic
• Authorization
• Entitlements
• Playback policy
• Subscription logic
• Playlist logic
• Recommendation rules

INTEGRATION TESTING

• PostgreSQL
• Redis
• Kafka
• BullMQ
• Search
• S3
• Payment provider
• Notification providers

CONTRACT TESTING

• REST
• Playback APIs
• Webhooks
• Event schemas

END-TO-END TESTING

• Registration
• Search
• Subscription
• Playback
• Playlist
• Library
• Download
• Multi-device synchronization
• Notifications

PERFORMANCE TESTING

• Playback authorization
• Search
• Recommendations
• API throughput
• Event throughput
• Media processing

RESILIENCE TESTING

• Dependency failures
• Database failover
• Kafka failure
• Search failure
• Regional failure

SECURITY TESTING

• Authentication
• Authorization
• Playback authorization
• Download security
• Abuse prevention
• Secret handling

────────────────────────────────────────

ARCHITECTURAL DECISION RECORDS

Create ADRs for:

• Architecture style
• Service decomposition
• PostgreSQL ownership
• Prisma
• Redis
• Kafka/Redpanda
• BullMQ
• Search
• Audio processing
• Adaptive audio streaming
• CDN architecture
• Playback authorization
• Offline architecture
• Rights architecture
• Subscription/entitlement model
• Payment abstraction
• Playlist architecture
• Recommendation architecture
• Advertising architecture
• Multi-region
• Kubernetes
• Terraform
• Observability
• Secrets management

Each ADR must contain:

• Context
• Decision
• Alternatives considered
• Consequences

────────────────────────────────────────

ARCHITECTURE VOLUME 1 OUTPUT

Produce:

1. Executive Architecture Overview
2. System Context
3. System Architecture
4. Architectural Approach
5. Application Architecture
6. Domain Decomposition
7. Service Decomposition
8. Service Ownership Matrix
9. Communication Matrix
10. Monorepo Architecture
11. Detailed Folder Hierarchy
12. Core Domain Model
13. Aggregate Boundaries
14. Complete Text-Based ERD
15. PostgreSQL Architecture
16. Prisma Strategy
17. Redis Architecture
18. Media and Audio Architecture
19. Audio Rendition Architecture
20. Adaptive Audio Streaming Architecture
21. Playback Architecture
22. Playback Consistency Strategy
23. Offline Download Architecture
24. Subscription Architecture
25. Entitlement Architecture
26. Payment Architecture
27. Rights and Availability Architecture
28. Content Catalog Architecture
29. Artist/Label/Partner Architecture
30. Playlist Architecture
31. User Library Architecture
32. Podcast Architecture
33. Audiobook Extensibility Architecture
34. Search Architecture
35. Recommendation Architecture
36. Radio and Stations Architecture
37. Charts Architecture
38. Analytics Architecture
39. Advertising Architecture
40. Notification Architecture
41. Security Architecture
42. Abuse Prevention
43. Moderation Architecture
44. Data Consistency Strategy
45. Scalability Strategy
46. Multi-Region Architecture
47. Failure Scenario Analysis
48. Observability Architecture
49. Disaster Recovery
50. Testing Architecture
51. Architectural Decision Records
52. Complete Project Index

────────────────────────────────────────

QUALITY REQUIREMENTS

Every architectural decision must evaluate:

• Scalability
• Availability
• Security
• Privacy
• Latency
• Data consistency
• Operational complexity
• Cost
• Developer productivity
• Maintainability
• Future extensibility

Prefer:

• Explicit ownership
• Clear bounded contexts
• CDN-based media delivery
• Stateless application services
• Event-driven communication where appropriate
• Idempotent consumers
• Transactional outbox
• Horizontal scaling
• Strong entitlement correctness
• Reliable playback authorization
• Graceful degradation
• Observable systems

Avoid:

• Unnecessary microservices
• Shared database ownership
• Distributed transactions where avoidable
• Tight coupling
• Single points of failure
• Redis as a system of record
• PostgreSQL as a raw analytics event store
• Application servers proxying high-bandwidth audio
• Proprietary cryptography
• Frontend-only authorization
• Unnecessary cross-region synchronous operations
• Premature ML infrastructure complexity
• Premature complexity

────────────────────────────────────────

OUTPUT RULES

This is an architecture document only.

Do not generate source code.

Do not generate placeholder implementations.

Do not generate Dockerfiles.

Do not generate Kubernetes manifests.

Do not generate Terraform files.

Do not generate frontend components.

Do not generate mobile components.

Do not implement backend services.

Provide detailed:

• Architecture specifications
• Domain boundaries
• Service responsibilities
• Ownership rules
• State machines
• Database architecture
• ERD
• API contracts
• Event contracts
• Queue definitions
• Playback architecture
• Media architecture
• Rights architecture
• Subscription architecture
• Security architecture
• Scalability strategies
• Multi-region architecture
• Disaster recovery
• Testing architecture
• ADRs
• Project Index

The resulting architecture must be sufficiently detailed that separate backend, frontend, mobile, infrastructure, DevOps, and QA teams can implement the complete music streaming platform without making major architectural decisions themselves.
