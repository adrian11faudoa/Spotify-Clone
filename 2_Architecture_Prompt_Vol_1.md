# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — ARCHITECTURE VOLUME 1

## ROLE

Act as the complete senior engineering organization responsible for defining the production architecture of a global music streaming platform comparable in product capability and scale to major commercial music-streaming services.

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

Do not implement the application.

Do not produce a tutorial.

Do not provide pseudo-code.

Do not create placeholder architecture.

Produce a concrete engineering blueprint that can be used by implementation agents to build the system against an existing repository.

The architecture must be internally consistent, production-oriented, scalable, secure, observable, testable, and commercially realistic.

---

# PROJECT

Design the architecture for an original global music streaming platform inspired by the product capabilities of large commercial music-streaming services.

The platform must support:

* anonymous visitors
* registered listeners
* free listeners
* premium/subscribed listeners
* artists
* artist representatives
* content managers
* moderators
* support operators
* administrators
* platform operators
* system/service identities

The system must ultimately support:

* music discovery
* audio playback
* albums
* tracks
* artists
* playlists
* user libraries
* listening history
* follows
* likes
* search
* recommendations
* social interactions
* subscriptions
* payment workflows
* notifications
* artist workflows
* catalog administration
* moderation
* analytics
* media processing
* scalable content delivery
* web applications
* mobile applications
* real-time playback state
* asynchronous processing
* operational monitoring

The architecture must be capable of scaling to:

* millions of catalog entities
* large registered-user populations
* millions of daily active listeners
* very high concurrent playback
* high-volume API traffic
* high-volume telemetry
* large object-storage datasets
* large search indexes
* high event throughput
* large background-processing workloads

Do not design around a single-server deployment.

Do not make the application server the primary media-delivery layer.

Do not make Redis, the search engine, or the event broker the transactional source of truth.

---

# TECHNOLOGY DIRECTION

Use the following technology direction as the architectural baseline.

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
* REST APIs
* WebSockets where justified
* OpenAPI/Swagger
* PostgreSQL
* Prisma
* Redis
* Kafka or Redpanda
* BullMQ
* Elasticsearch or OpenSearch
* S3-compatible object storage
* CDN
* FFmpeg

## Payments

* Stripe or another production-grade provider behind an application-level payment abstraction

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
* centralized structured logging
* distributed tracing
* alerting

Technology substitutions are permitted only when they preserve the architectural intent and have a concrete engineering justification.

---

# SOURCE OF TRUTH

The repository is the implementation source of truth during actual implementation.

For architecture design, this document must define the intended system behavior independently of any earlier AI conversation.

When implementation agents later inspect the repository, they must reconcile the architecture with the actual repository state rather than assuming that an earlier AI response is available.

The architecture must therefore explicitly document:

* intended module boundaries
* intended service boundaries
* authoritative data ownership
* contracts
* communication patterns
* lifecycle behavior
* infrastructure responsibilities
* failure behavior

Do not write "as previously defined" or depend on another AI-generated document being present.

---

# ARCHITECTURAL OBJECTIVE

Design one coherent platform rather than a collection of unrelated applications.

The system must separate workloads that have materially different scaling or reliability characteristics.

At minimum, distinguish:

* transactional application workloads
* authentication and identity
* catalog management
* listener library operations
* playlist operations
* playback authorization
* real-time playback state
* search
* media ingestion
* media processing
* media delivery
* recommendations
* analytics
* notifications
* subscriptions and billing
* administration
* moderation
* asynchronous jobs
* event streaming
* observability

Use modular boundaries first.

Introduce independently deployable services only where there is a strong reason such as:

* independent scaling
* independent operational lifecycle
* workload isolation
* data ownership
* security isolation
* failure isolation
* latency requirements
* team ownership
* specialized infrastructure

Do not create microservices solely for architectural appearance.

---

# SYSTEM ARCHITECTURE

Define a concrete high-level architecture containing, where appropriate:

* web clients
* mobile clients
* public API entry point
* authentication subsystem
* application/backend modules
* background workers
* event brokers
* databases
* cache infrastructure
* search infrastructure
* object storage
* media-processing workers
* CDN
* payment provider
* notification providers
* analytics infrastructure
* administrative interfaces
* observability infrastructure

Explicitly identify which components are:

* stateless
* stateful
* horizontally scalable
* asynchronously processed
* latency-sensitive
* throughput-sensitive
* durable
* ephemeral

Define which components may scale independently.

Define which communication paths are:

* synchronous
* asynchronous
* event-driven
* request/response
* streaming
* real-time

---

# DOMAIN BOUNDARIES

Define explicit bounded contexts.

At minimum, evaluate the following domains:

## Identity and Access

Responsible for:

* accounts
* credentials
* sessions
* identity providers
* authentication
* authorization
* roles
* permissions
* account lifecycle
* security events
* device/session management

## User Profile

Responsible for:

* profile data
* preferences
* locale
* privacy settings
* personalization settings
* account metadata

## Music Catalog

Responsible for:

* artists
* albums
* tracks
* releases
* genres
* labels
* credits
* catalog metadata
* content availability
* explicit-content classification

## Media Assets

Responsible for:

* audio assets
* artwork
* audio variants
* processing state
* derivative assets
* storage references
* media lifecycle

## Playlists

Responsible for:

* playlists
* playlist membership
* ordering
* ownership
* collaboration
* playlist visibility
* playlist metadata

## Listener Library

Responsible for:

* liked tracks
* saved albums
* followed artists
* followed playlists where applicable
* personal collections

## Playback

Responsible for:

* playback authorization
* playback sessions
* device state
* queue state where server persistence is required
* progress synchronization
* entitlement checks
* content availability checks

## Search

Responsible for:

* indexing
* querying
* autocomplete
* relevance
* filtering
* search analytics

The search system must not become the canonical transactional source of truth.

## Recommendations

Responsible for:

* candidate generation
* ranking
* personalization signals
* recommendation surfaces
* recommendation experiments
* model/version metadata

The architecture must permit recommendation algorithms to evolve without changing transactional domains.

## Subscriptions and Billing

Responsible for:

* plans
* subscriptions
* entitlements
* billing state
* provider references
* invoices where applicable
* lifecycle transitions
* payment events

## Notifications

Responsible for:

* notification preferences
* templates
* delivery attempts
* delivery status
* in-app notifications
* email
* push notifications

## Analytics

Responsible for:

* playback telemetry
* behavioral events
* aggregated metrics
* analytical pipelines
* reporting datasets

Analytics infrastructure must not become a dependency for latency-critical transactional flows.

## Administration and Moderation

Responsible for:

* administrative workflows
* moderation
* reports
* review state
* audit operations
* operator actions
* policy enforcement

Explicitly identify cross-domain relationships and prevent uncontrolled domain coupling.

---

# SERVICE BOUNDARY STRATEGY

For each major domain, determine whether it should initially exist as:

* a module inside a modular monolith
* an independently deployable service
* an asynchronous worker
* a specialized data subsystem
* a managed infrastructure component

Document the reason.

The architecture should favor an incremental path from modular application architecture toward independent scaling where required.

Define stable internal interfaces so future service extraction does not require rewriting business logic.

Avoid shared mutable state between domains.

Avoid uncontrolled direct database access between bounded contexts.

---

# DATA OWNERSHIP

Create a data-ownership matrix.

For every major entity, define:

* owning domain
* storage system
* lifecycle owner
* read consumers
* write authority
* deletion authority
* event source
* caching strategy
* search representation if applicable
* analytics representation if applicable

Core entities should include at least:

* User
* Account
* Session
* Device
* Artist
* Album
* Track
* Release
* Genre
* Playlist
* PlaylistItem
* LibraryEntry
* Follow
* Like
* PlaybackSession
* PlaybackProgress
* Subscription
* Plan
* PaymentCustomer
* Notification
* MediaAsset
* MediaVariant
* SearchDocument
* RecommendationProfile
* AnalyticsEvent
* AuditEvent

Entity names may be refined, but ownership must remain unambiguous.

---

# DATABASE ARCHITECTURE

Use PostgreSQL as the primary transactional datastore.

Design a relational model suitable for high-scale operation.

The architecture must define:

* logical schema boundaries
* major tables/entities
* relationships
* primary keys
* foreign keys
* unique constraints
* check constraints
* indexes
* high-cardinality access paths
* pagination strategies
* retention strategies
* deletion semantics
* auditing requirements
* migration strategy

Use normalized relational modeling for authoritative transactional data unless denormalization has a measurable architectural purpose.

Define where read models or materialized views may be justified.

Do not turn every domain into a separate database without justification.

Where separate database ownership becomes necessary, document:

* data ownership
* synchronization mechanism
* consistency expectations
* failure behavior
* migration strategy

---

# IDENTIFIER STRATEGY

Define the platform-wide identifier strategy.

Identifiers must support:

* distributed generation
* uniqueness
* API exposure
* database indexing
* event correlation
* safe external use

Avoid identifiers that unnecessarily expose internal sequential counts when public identifiers require stronger opacity.

Define identifier conventions consistently across:

* users
* content
* playlists
* media
* subscriptions
* events
* jobs

---

# CONSISTENCY MODEL

Document consistency requirements for each major workflow.

Classify operations as:

* strongly consistent
* transactionally consistent
* eventually consistent
* best-effort

At minimum evaluate:

* account creation
* authentication
* playlist editing
* likes
* follows
* library changes
* subscription entitlement
* playback authorization
* playback progress
* search indexing
* recommendations
* analytics
* notifications
* media-processing state

Do not use eventual consistency where users could receive unauthorized access or incorrect financial entitlement.

Do not force strong consistency on workloads where eventual consistency is operationally preferable.

---

# TRANSACTION BOUNDARIES

Define transaction ownership.

A transaction should remain within an authoritative data boundary whenever possible.

Document workflows requiring atomicity, such as:

* account state transitions
* playlist mutations
* subscription entitlement transitions
* catalog publishing
* media-processing status transitions
* authorization state changes

Where cross-system transactions are unavoidable, define:

* transactional outbox
* saga/orchestration
* compensating actions
* idempotency
* retry strategy
* recovery procedure

Do not rely on distributed database transactions unless there is an explicit, defensible requirement.

---

# CONCURRENCY MODEL

Define concurrency expectations for:

* playlist edits
* collaborative playlists
* library updates
* likes
* follows
* subscription transitions
* playback-state updates
* media-processing state
* administrative edits

Specify where to use:

* optimistic concurrency
* version numbers
* unique constraints
* atomic updates
* database locking
* idempotency keys
* last-write-wins behavior
* conflict detection

Collaborative functionality must not silently overwrite unrelated user changes.

---

# REDIS ARCHITECTURE

Define Redis usage explicitly.

Potential responsibilities include:

* API caching
* session-related ephemeral state
* rate limiting
* playback presence
* playback coordination
* temporary state
* distributed locks where justified
* counters
* BullMQ infrastructure

For each usage define:

* key namespace
* TTL
* invalidation
* maximum value size
* failure behavior
* fallback behavior
* memory considerations

The architecture must remain functional when noncritical Redis data is unavailable.

---

# EVENT ARCHITECTURE

Define the Kafka/Redpanda architecture.

Establish event categories for domains such as:

* identity
* catalog
* media
* playlists
* library
* playback
* subscriptions
* notifications
* analytics
* moderation

Define event envelope requirements:

* event ID
* event type
* event version
* aggregate ID
* producer
* occurred-at timestamp
* correlation ID
* causation ID where useful
* trace context
* schema metadata
* payload

Define:

* topic naming
* partition strategy
* key selection
* retention
* ordering guarantees
* replay policy
* consumer groups
* retry handling
* dead-letter handling
* schema evolution
* compatibility rules

Do not assume global ordering.

Document ordering guarantees per aggregate or partition key where required.

---

# TRANSACTIONAL OUTBOX

Define where transactional outbox patterns are required.

At minimum evaluate:

* catalog publishing
* playlist mutations producing external events
* subscription state transitions
* user lifecycle events
* moderation decisions
* media lifecycle transitions

The architecture must ensure that a successful transactional state change cannot silently lose its corresponding event.

Define:

* outbox record lifecycle
* publishing worker
* retry policy
* deduplication
* cleanup
* monitoring
* idempotency

---

# QUEUE ARCHITECTURE

Define BullMQ or equivalent queues for workloads that do not belong in request/response execution.

Potential job families include:

* media processing
* transcoding
* artwork processing
* search indexing
* notification delivery
* analytics aggregation
* recommendation generation
* catalog maintenance
* cleanup
* subscription maintenance

For each queue define:

* producer
* worker responsibility
* job payload
* priority
* concurrency
* timeout
* retries
* backoff
* deduplication
* idempotency
* failure policy
* dead-letter strategy
* observability

Critical workflows must have a recoverable failure path.

---

# SEARCH ARCHITECTURE

Design Elasticsearch or OpenSearch as a specialized read/search subsystem.

Define searchable documents for:

* artists
* albums
* tracks
* playlists
* genres
* curated content

Define:

* indexing source
* indexing triggers
* document schema
* analyzers
* normalization
* autocomplete
* typo handling
* ranking
* filtering
* pagination
* freshness expectations
* reindexing
* alias/version strategy
* failure recovery

Search indexing must be asynchronous where appropriate.

A search-index outage must not corrupt transactional catalog data.

Define stale-search behavior.

---

# RECOMMENDATION ARCHITECTURE

Define a layered recommendation architecture that can evolve.

Separate:

1. signal collection
2. candidate generation
3. filtering
4. ranking
5. personalization
6. serving
7. experimentation
8. feedback/measurement

Candidate sources may include:

* recent listening
* liked tracks
* followed artists
* playlist behavior
* similar content
* popularity
* editorial curation
* contextual behavior
* explicit preferences

Define how recommendation requests interact with transactional and analytical systems.

Do not make a slow analytical pipeline a synchronous dependency for basic playback.

Define recommendation freshness expectations.

Define model/version identifiers where algorithmic components exist.

---

# MEDIA INGESTION ARCHITECTURE

Define the complete media lifecycle:

1. authorization
2. upload initiation
3. object-storage upload
4. upload finalization
5. validation
6. metadata extraction
7. malware/security scanning where applicable
8. transcoding
9. derivative generation
10. quality validation
11. publication
12. CDN availability
13. lifecycle management
14. deletion or retention

Clearly separate:

* source asset
* processed asset
* delivery variant
* artwork
* waveform/metadata derivatives

Define processing states and failure states.

Media processing must be asynchronous.

Do not expose incomplete media as playable content.

---

# MEDIA STORAGE ARCHITECTURE

Use S3-compatible object storage for durable media assets.

Define bucket/storage boundaries for:

* source uploads
* processed audio
* artwork
* derivatives
* temporary processing assets
* restricted administrative assets

Define:

* access controls
* lifecycle policies
* encryption
* object naming
* metadata
* signed-access strategy
* retention
* deletion
* orphan cleanup

Protected media must not rely on unrestricted public object URLs.

---

# CDN ARCHITECTURE

Define CDN responsibilities for:

* audio delivery
* artwork
* public catalog assets
* static web assets where appropriate

Define:

* cache keys
* cache-control strategy
* signed access
* origin protection
* invalidation
* regional considerations
* failure behavior

Media origin infrastructure must not be directly exposed unnecessarily.

---

# PLAYBACK ARCHITECTURE

Design playback as a dedicated platform capability.

A playback request must be able to evaluate:

* user identity
* authentication state
* subscription entitlement
* content availability
* geographic restrictions
* content policy
* account/device limits where applicable
* track/media state
* playback authorization

Define the lifecycle of a playback session:

1. request authorization
2. validate entitlement and availability
3. create or update playback session
4. issue secure media access
5. deliver content through CDN
6. receive playback telemetry
7. update resumable state where appropriate
8. terminate or expire session

Do not route audio bytes through ordinary API endpoints.

Define how playback failures are handled when:

* API is degraded
* Redis is unavailable
* CDN is unavailable
* search is unavailable
* analytics is unavailable
* subscription provider is unavailable

Noncritical analytics must not prevent playback when authorization can still be safely determined.

---

# REAL-TIME ARCHITECTURE

Use WebSockets only where real-time communication provides meaningful product value.

Potential responsibilities include:

* synchronized playback state
* collaborative playlist changes
* live device/session state
* real-time notifications
* administrative monitoring where justified

Define:

* connection authentication
* authorization
* connection lifecycle
* heartbeat
* reconnection
* message validation
* rate limiting
* fan-out
* presence
* ordering
* duplicate handling
* backpressure

Never trust client-supplied real-time authorization state.

---

# AUTHENTICATION ARCHITECTURE

Define an authentication system supporting:

* account registration
* login
* session/token lifecycle
* refresh
* logout
* device/session revocation
* password management
* email verification where appropriate
* external identity providers where applicable

Define:

* access-token strategy
* refresh-token strategy
* token rotation
* expiration
* revocation
* session storage
* device identification
* suspicious-login handling
* rate limiting
* account-lockout or progressive protection strategy

Do not expose credential secrets to clients beyond what is required.

---

# AUTHORIZATION ARCHITECTURE

Define server-side authorization boundaries for:

* listener resources
* private playlists
* collaborative playlists
* artist resources
* catalog management
* moderation
* administration
* support functions
* financial data
* analytics
* media assets

Evaluate RBAC and resource-level authorization.

Authorization decisions must consider resource ownership and privacy state where relevant.

Prevent:

* IDOR
* privilege escalation
* cross-tenant access where applicable
* unauthorized media access
* unauthorized administrative operations

---

# SUBSCRIPTION ARCHITECTURE

Define the relationship among:

* plans
* subscriptions
* customers
* invoices
* payments
* entitlements
* account status

Separate payment-provider state from application entitlement state.

A payment webhook must not directly mutate unrelated domain data without validation and idempotency.

Define:

* webhook verification
* idempotency
* event ordering
* subscription state machine
* cancellation
* renewal
* failed payment
* grace period
* expiration
* plan changes
* entitlement propagation

Financial state transitions require strong auditability.

---

# NOTIFICATION ARCHITECTURE

Design notifications as an asynchronous subsystem.

Define:

* notification event
* preference evaluation
* template selection
* channel selection
* delivery scheduling
* provider integration
* retries
* deduplication
* delivery status
* suppression
* user preferences

Separate:

* notification creation
* notification delivery
* notification provider state

Provider failure must not corrupt source business events.

---

# ANALYTICS ARCHITECTURE

Separate operational analytics from transactional application state.

Define an event pipeline for:

* playback
* discovery
* search
* recommendation interaction
* subscription behavior
* content engagement
* application behavior

Define:

* event collection
* validation
* buffering
* event transport
* processing
* aggregation
* retention
* privacy filtering
* access controls

Analytics loss should be observable and bounded without corrupting critical transactions.

---

# ADMINISTRATION AND MODERATION ARCHITECTURE

Define separate operator capabilities for:

* user administration
* catalog administration
* media review
* artist verification
* reports
* moderation decisions
* subscription support
* security investigation
* audit review

Administrative operations must:

* require explicit authorization
* be auditable
* expose only necessary data
* support operator identity attribution
* avoid accidental destructive actions
* support appropriate confirmation workflows

Sensitive administrative endpoints must have stronger security controls where appropriate.

---

# FAILURE DOMAINS

Identify failure domains across:

* web
* API
* database
* Redis
* event broker
* queues
* search
* object storage
* CDN
* payment provider
* email provider
* push provider
* media-processing workers
* recommendation infrastructure

For each dependency, define:

* criticality
* timeout
* retry strategy
* fallback
* degradation mode
* observability
* recovery path

Explicitly separate fatal dependencies from nonfatal dependencies.

---

# ARCHITECTURAL SECURITY BOUNDARIES

Define trust boundaries among:

* public clients
* API edge
* application services
* workers
* databases
* caches
* event brokers
* search
* object storage
* CDN
* external payment systems
* external notification providers
* administration systems

Identify:

* untrusted inputs
* privileged components
* secrets
* sensitive data
* high-impact operations

Specify where validation and authorization must occur.

---

# ARCHITECTURAL DOCUMENTATION REQUIRED

Produce a coherent architecture package containing at least:

* system context
* container/component architecture
* bounded-context definitions
* service/module boundaries
* data-ownership matrix
* transactional data architecture
* event architecture
* queue architecture
* search architecture
* media architecture
* playback architecture
* authentication architecture
* authorization architecture
* subscription architecture
* notification architecture
* analytics architecture
* failure model
* consistency model
* scalability strategy
* security boundaries

Include architecture diagrams in a repository-friendly format such as Mermaid where useful.

Diagrams must represent actual architecture decisions rather than decorative visuals.

---

# IMPLEMENTATION BOUNDARIES

This architecture volume is responsible for defining the system-level foundation.

It must establish enough architectural detail to allow later implementation prompts to define concrete backend, frontend, mobile, infrastructure, and QA work without contradicting one another.

Do not implement:

* application source code
* database migrations
* production infrastructure manifests
* frontend components
* mobile screens
* backend controllers
* production worker code

Those are implementation concerns.

This prompt defines the architecture that those implementations must realize.

---

# ARCHITECTURAL VALIDATION

Before completing the architecture work, verify that the design addresses:

* domain ownership
* transactional integrity
* scalability
* playback latency
* high concurrency
* media delivery
* asynchronous processing
* search
* recommendations
* subscriptions
* notifications
* analytics
* administration
* security
* privacy
* observability
* failure recovery
* deployment
* disaster recovery

Identify and resolve contradictions before finalizing the architecture.

Do not leave mutually incompatible architecture decisions unresolved.

---

# REQUIRED ARCHITECTURE DELIVERABLES

The architecture implementation agent must produce and maintain, as appropriate:

* architecture documentation
* domain-boundary documentation
* service/module boundary definitions
* data-ownership documentation
* entity relationship documentation
* event contract documentation
* queue documentation
* API boundary documentation
* media lifecycle documentation
* playback lifecycle documentation
* security-boundary documentation
* failure/degradation documentation
* architecture diagrams
* important architecture decision records

All documentation must describe the actual intended architecture.

Do not create speculative sections that have no architectural purpose.

---

# COMPLETION CRITERIA

This architecture task is complete only when:

* the system boundaries are explicit
* domain ownership is explicit
* service/module boundaries are explicit
* authoritative storage is explicit
* event flows are explicit
* queue responsibilities are explicit
* search architecture is explicit
* media architecture is explicit
* playback architecture is explicit
* authentication is explicit
* authorization is explicit
* subscriptions are explicit
* notification architecture is explicit
* analytics architecture is explicit
* failure behavior is explicit
* scaling strategy is explicit
* security boundaries are explicit
* observability requirements are explicit
* disaster-recovery considerations are explicit
* important consistency decisions are documented
* architecture contradictions have been resolved

Do not declare completion merely because documentation files exist.

The architecture must be internally coherent and detailed enough to guide real implementation.

---

# IMPLEMENTATION REPORT

At completion, report:

* architecture documents created
* architecture documents modified
* major architectural decisions
* domain boundaries defined
* service/module boundaries defined
* data ownership decisions
* database architecture decisions
* event architecture decisions
* queue architecture decisions
* media architecture decisions
* playback architecture decisions
* security decisions
* observability decisions
* scalability decisions
* reliability decisions
* unresolved architectural issues, if any
* validation performed

Do not claim architectural decisions were validated unless they were actually reviewed.

---

# FINAL INSTRUCTION

Design one coherent production-grade architecture for an original global music streaming platform.

The architecture must make the system understandable before implementation begins while remaining practical to implement incrementally.

Favor explicit boundaries over accidental coupling.

Favor authoritative transactional ownership over duplicated mutable state.

Favor asynchronous processing for workloads that do not belong in latency-sensitive request paths.

Favor CDN-based media delivery over application-server media streaming.

Favor secure-by-default access to protected content.

Favor resilient behavior over fragile happy paths.

Favor clear evolution paths over premature infrastructure complexity.

The resulting architecture must support the long-term convergence of web, mobile, backend, media, search, recommendation, analytics, subscription, administration, infrastructure, and QA implementations into one coherent production system.
