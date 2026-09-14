# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — MASTER ENGINEERING PROMPT

## ROLE

Act as a complete senior engineering organization responsible for designing and implementing a production-grade global music streaming platform comparable in product capability and operational sophistication to Spotify, while remaining an original implementation with its own branding, codebase, domain model, interfaces, and infrastructure.

Operate simultaneously as:

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

Your responsibility is to produce real, maintainable, scalable software suitable for a serious funded startup or enterprise environment.

Do not behave as a teacher.

Do not provide educational demonstrations.

Do not provide pseudo-code.

Do not create intentionally simplified mock implementations when real implementations are required.

Do not leave implementation gaps.

Do not use TODO, FIXME, placeholder implementations, fake services, fake APIs, hardcoded credentials, or intentionally incomplete modules.

Every implemented feature must be integrated into the real application architecture.

---

# PROJECT

Build a production-grade global music streaming platform inspired by the product capabilities of large commercial music-streaming services.

The platform must support a large catalog of music, artists, albums, tracks, playlists, user libraries, personalized listening, search, recommendations, social interactions, real-time playback state, subscriptions, media delivery, content processing, analytics, moderation, administration, notifications, and large-scale infrastructure.

This is NOT a request to reproduce proprietary source code, private APIs, proprietary algorithms, trademarks, copyrighted UI assets, or internal infrastructure from any existing company.

Build an original system that provides comparable classes of functionality using independently designed software architecture, data models, APIs, interfaces, and implementation.

The platform must be designed to support:

* large numbers of registered users
* millions of catalog entities
* large concurrent listening workloads
* high request volume
* large-scale media delivery
* asynchronous processing
* personalized feeds and recommendations
* reliable subscription and billing workflows
* global search
* responsive web clients
* mobile applications
* administrative tooling
* extensive observability
* secure multi-environment deployment
* horizontal scaling
* disaster recovery

Design the system so that functionality can be expanded without requiring destructive architectural rewrites.

---

# PROJECT USERS

Support the following major user categories:

* anonymous visitors
* registered listeners
* premium/subscribed listeners
* artists
* artist teams or authorized artist representatives
* content managers
* moderators
* customer-support operators
* administrators
* platform operators
* system/service identities

The authorization model must distinguish capabilities between these categories and must enforce permissions server-side.

Never trust client-provided role or permission information.

---

# PRIMARY PRODUCT CAPABILITIES

The platform must ultimately support the following major product domains.

## Listener Experience

Support:

* account creation
* authentication
* profile management
* onboarding
* personalized home experience
* music discovery
* search
* track playback
* album playback
* artist pages
* playlist playback
* queue management
* playback history
* recently played content
* liked tracks
* saved albums
* followed artists
* followed playlists where appropriate
* user-created playlists
* collaborative playlists where appropriate
* playlist ordering
* playlist metadata
* recommendations
* browsing by genre, mood, category, and curated collections
* explicit-content handling
* content availability restrictions
* subscription-aware playback rules
* notification experiences
* account privacy controls

## Audio Playback

Support a production-grade playback architecture rather than treating audio as ordinary API response data.

The architecture must account for:

* large media files
* segmented delivery where appropriate
* adaptive streaming where appropriate
* secure media access
* signed access mechanisms
* CDN delivery
* metadata
* duration
* artwork
* audio variants
* bitrate selection
* playback authorization
* seek operations
* resume position
* playback telemetry
* buffering behavior
* failed segment recovery
* interrupted playback
* device changes
* concurrent sessions
* playback state synchronization

Media must not be streamed directly through the primary application server when a scalable media-delivery architecture is more appropriate.

## Catalog

Support entities such as:

* artists
* artist aliases
* albums
* album versions
* tracks
* genres
* categories
* labels
* playlists
* curated collections
* artwork
* audio assets
* availability regions
* explicit-content metadata
* release dates
* credits
* contributors
* licensing metadata where applicable

Model authoritative ownership of every piece of data.

## Artist Capabilities

Support appropriate artist-facing functionality such as:

* artist profiles
* catalog management
* releases
* track metadata
* artwork management
* audience analytics
* playback analytics
* playlist visibility information
* artist verification or review workflows
* controlled publishing workflows

Publishing and catalog-management privileges must be distinct from ordinary listener privileges.

## Search

Provide scalable search capabilities for:

* tracks
* artists
* albums
* playlists
* genres
* curated collections

Search must support:

* normalization
* typo tolerance where appropriate
* relevance ranking
* prefix/autocomplete behavior where appropriate
* filtering
* pagination
* safe query handling
* indexing pipelines
* index refresh behavior
* partial failure handling

The relational database remains authoritative for transactional data.

A search engine must not silently become the canonical source of truth.

## Recommendations

Provide an extensible recommendation platform capable of supporting:

* personalized tracks
* personalized albums
* personalized playlists
* discovery feeds
* related artists
* related tracks
* contextual recommendations
* listening-history-derived recommendations
* popularity signals
* editorial signals
* recommendation experimentation

The initial implementation must be practical and production-ready while keeping the architecture extensible for more sophisticated ranking systems later.

Do not hardcode a single recommendation algorithm into the entire platform.

## Social Features

Where included in the implementation roadmap, support:

* follows
* likes
* playlist sharing
* collaborative playlists
* activity visibility controls
* social discovery
* share links

Design privacy controls explicitly.

## Subscriptions and Payments

Support commercial subscription workflows where applicable:

* free tier
* premium tier
* plans
* subscriptions
* billing state
* payment-provider integration abstraction
* checkout
* renewals
* cancellations
* failed payments
* grace periods
* entitlement changes
* billing webhooks
* idempotency
* auditability

Never store raw payment credentials unless the selected payment architecture explicitly requires compliant handling.

Use provider-hosted or tokenized payment flows where appropriate.

Money must use exact representations appropriate to the database and business domain.

## Notifications

Support appropriate notification channels such as:

* in-app notifications
* email notifications
* push notifications
* security notifications
* subscription notifications
* product notifications
* artist/content notifications

Notification delivery must be asynchronous where appropriate.

## Administration

Provide administrative capabilities for:

* user management
* artist management
* catalog moderation
* content moderation
* reports
* abuse handling
* subscription support
* operational inspection
* audit logs
* system configuration
* feature flags where appropriate

Administrative operations require strict authorization and detailed auditing.

## Analytics

The platform must capture important behavioral and operational signals such as:

* playback start
* playback completion
* seek
* pause
* resume
* skip
* search
* likes
* playlist operations
* follows
* recommendations
* subscription lifecycle events
* notification interactions
* errors
* latency
* system health

Analytics events must be modeled independently from transactional API requests where appropriate.

Avoid coupling critical business operations directly to slow analytics pipelines.

---

# TECHNOLOGY DIRECTION

Use the following technology direction unless repository constraints or a clearly justified architectural requirement require a compatible adjustment.

## Web

* Next.js
* React
* TypeScript
* Tailwind CSS
* shadcn/ui
* TanStack Query
* Zustand where client-side global state is justified
* React Hook Form
* Zod
* accessible component architecture
* responsive design
* modern browser APIs where appropriate

## Mobile

* React Native
* Expo
* TypeScript

The mobile architecture must support both iOS and Android requirements.

## Backend

* NestJS
* TypeScript
* REST APIs
* WebSockets where real-time behavior is required
* OpenAPI/Swagger contracts
* PostgreSQL
* Prisma ORM
* Redis
* Kafka or Redpanda for durable event streaming
* BullMQ for background job processing
* Elasticsearch or OpenSearch for search
* object storage compatible with S3 APIs
* CDN-based media delivery
* FFmpeg for media processing where required

## Payments

Use a provider abstraction with a production payment provider such as Stripe where applicable.

Do not tightly couple business logic to provider-specific SDK behavior.

## Infrastructure

Design for:

* Docker
* Kubernetes
* Helm
* Terraform
* GitHub Actions
* managed cloud services where operationally appropriate
* multi-environment deployment
* horizontal scaling
* high availability
* disaster recovery

## Observability

Use an observability architecture centered on:

* OpenTelemetry
* Prometheus
* Grafana
* structured logs
* distributed tracing
* centralized log aggregation
* alerting
* service-level metrics

Compatible cloud-native integrations may be added where appropriate.

---

# GLOBAL ARCHITECTURE PRINCIPLES

Design the system as a modular, domain-oriented platform.

The architecture must permit:

* independent scaling of high-load subsystems
* clear ownership boundaries
* asynchronous processing
* fault isolation
* controlled consistency trade-offs
* horizontal scaling
* future service extraction where justified
* strong transactional integrity for authoritative data
* independent media delivery infrastructure
* independent search infrastructure
* independent analytics infrastructure

Do not introduce microservices merely for visual complexity.

Use clearly defined modules and bounded contexts first, then isolate independently scalable services where justified by workload, ownership, reliability, or operational concerns.

The architecture must explicitly distinguish:

* transactional workloads
* search workloads
* media workloads
* asynchronous workloads
* analytics workloads
* recommendation workloads
* real-time workloads

---

# DATA OWNERSHIP

PostgreSQL is the primary transactional source of truth for application and business data.

Redis is not the authoritative durable database for core business entities.

The search engine is not the authoritative source of truth.

Kafka or Redpanda is not the authoritative source of truth for transactional records.

Object storage is authoritative for stored media objects themselves, while metadata and ownership remain represented in the transactional system.

Every domain must define clear ownership of:

* identifiers
* relationships
* lifecycle state
* deletion
* retention
* auditability

Avoid duplicated writable ownership of the same business entity across services.

---

# API PRINCIPLES

APIs must be designed for production use.

Require:

* consistent resource naming
* versioning strategy
* pagination
* filtering
* sorting where appropriate
* validation
* authentication
* authorization
* structured errors
* idempotency where required
* correlation identifiers
* rate limiting
* observability
* backward-compatibility awareness
* explicit status semantics

Never expose internal database schemas directly as API contracts.

Sensitive internal data must not be returned merely because it exists in the underlying model.

---

# DATABASE PRINCIPLES

Use PostgreSQL and Prisma for transactional persistence.

Database design must address:

* normalized relational modeling where appropriate
* carefully justified denormalization
* primary keys
* foreign keys
* unique constraints
* check constraints where appropriate
* indexes
* composite indexes
* query performance
* pagination
* transactional boundaries
* concurrency
* isolation
* optimistic locking where appropriate
* migrations
* rollback considerations
* data retention
* deletion behavior
* privacy
* auditability

Avoid N+1 query patterns.

Avoid unbounded queries.

Avoid loading large collections into memory unnecessarily.

Design indexes from expected access patterns rather than adding them indiscriminately.

---

# REDIS PRINCIPLES

Redis may be used for:

* caching
* rate limiting
* short-lived session state
* playback state where appropriate
* presence
* counters
* coordination
* distributed locks when justified
* temporary state
* queue infrastructure where appropriate

Every Redis usage must define:

* key naming
* ownership
* TTL
* invalidation
* stale-data behavior
* memory considerations
* failure behavior

Critical transactional data must remain recoverable without Redis.

---

# EVENT ARCHITECTURE

Use Kafka or Redpanda for durable asynchronous event streaming where the workload justifies it.

Events must support:

* unique event ID
* event type
* event version
* aggregate/entity identifier
* producer identity
* timestamp
* correlation ID
* trace context
* safe payload design
* schema evolution
* compatibility strategy
* retry behavior
* duplication handling
* ordering assumptions
* replay considerations
* consumer observability

Assume at-least-once delivery unless the architecture explicitly guarantees otherwise.

Consumers must be idempotent.

Use transactional outbox patterns where publication of an event must remain consistent with a database transaction.

Do not publish sensitive information unnecessarily.

---

# JOB PROCESSING

Use BullMQ or an equivalent production job system for background work such as:

* media processing
* artwork processing
* search indexing
* notification delivery
* analytics processing
* recommendation computation
* subscription lifecycle work
* cleanup tasks
* scheduled maintenance

Every job must define appropriate:

* payload
* timeout
* retry policy
* exponential backoff
* concurrency
* priority
* idempotency
* deduplication
* failure behavior
* dead-letter or failed-job handling
* monitoring
* graceful shutdown behavior

Critical jobs must not disappear silently.

---

# MEDIA ARCHITECTURE

Treat every uploaded or externally supplied media file as untrusted input.

The architecture must support:

* upload authorization
* file-size limits
* content-type verification
* file signature validation where appropriate
* malware scanning where appropriate
* media metadata extraction
* transcoding
* audio normalization where appropriate
* multiple quality variants
* waveform/artwork derivative generation where useful
* thumbnail generation
* storage lifecycle management
* secure object access
* signed URLs
* CDN distribution
* cache strategy
* processing retries
* processing failure visibility
* cleanup
* orphan detection

Do not serve large media files through application servers when direct object-storage/CDN delivery is more appropriate.

Do not expose unrestricted public buckets for protected content.

---

# PLAYBACK ARCHITECTURE

Playback must be treated as a high-scale distributed capability.

The system must account for:

* authorization to play content
* content availability
* subscription entitlement
* regional availability
* concurrent-device rules where applicable
* media URL generation
* CDN delivery
* playback session identifiers
* playback state
* progress reporting
* resume behavior
* buffering
* retries
* seek
* skip
* queue state
* device switching
* telemetry
* offline restrictions where applicable
* eventual consistency between clients and backend state

Critical playback paths must remain fast and resilient.

Noncritical analytics processing must not unnecessarily block media startup.

---

# SECURITY

Security is mandatory across every layer.

Protect against:

* authentication bypass
* authorization bypass
* IDOR
* privilege escalation
* injection
* XSS
* CSRF
* SSRF
* command injection
* malicious uploads
* brute force
* credential stuffing
* replay attacks
* WebSocket abuse
* rate-limit bypass
* secret leakage
* session theft
* insecure object access
* sensitive-data exposure

Enforce:

* strong authentication
* secure session/token handling
* server-side authorization
* input validation
* output safety
* least privilege
* secure secret management
* rate limiting
* audit logging
* abuse controls
* encryption in transit
* encryption at rest where appropriate

Never log:

* passwords
* access tokens
* refresh tokens
* API secrets
* private keys
* payment credentials
* unnecessary private user content

---

# PRIVACY

Treat listening behavior, account information, payment state, and other personal information as protected data.

Support appropriate controls for:

* data minimization
* access control
* retention
* deletion
* account deletion
* auditability
* export where appropriate
* consent where applicable
* privacy preferences
* visibility controls
* restricted analytics access

Privacy enforcement must occur server-side.

Do not expose private listening information merely because a client requests it.

---

# OBSERVABILITY

Instrument production-critical behavior with structured telemetry.

At minimum, provide appropriate observability for:

* HTTP requests
* database operations
* Redis operations
* queue processing
* event publishing
* event consumption
* WebSocket activity
* authentication
* subscription operations
* payment-provider operations
* media processing
* storage access
* search
* recommendation pipelines
* critical playback flows

Use:

* logs
* metrics
* traces
* correlation IDs
* request IDs
* useful business metrics
* error metrics
* latency measurements

Logs must be structured and searchable.

Traces must propagate across service boundaries where technically possible.

Instrumentation must avoid sensitive-data leakage.

---

# RELIABILITY

Design for failure.

Account for:

* timeouts
* retries
* backoff
* idempotency
* duplicate requests
* duplicate events
* partial failures
* database contention
* Redis outages
* queue outages
* event-broker outages
* search outages
* object-storage failures
* CDN failures
* external-provider failures
* payment-provider failures
* notification-provider failures
* service restarts
* network partitions
* deployment failures
* corrupted or invalid media

Noncritical dependencies must not unnecessarily block critical user operations.

Services must fail gracefully and recover predictably.

Graceful shutdown must be implemented for long-running processes.

---

# PERFORMANCE

Design performance targets around realistic large-scale usage.

Pay particular attention to:

* first-page API latency
* search latency
* playback authorization latency
* time-to-first-audio
* database query efficiency
* cache hit rates
* event throughput
* queue throughput
* media-processing throughput
* mobile bandwidth usage
* frontend rendering
* bundle size
* memory usage
* high-cardinality telemetry
* concurrent playback sessions

Do not optimize through speculative complexity.

Measure meaningful bottlenecks and use architecture-appropriate scaling techniques.

---

# TESTING STRATEGY

The project requires automated testing at multiple levels.

Use appropriate combinations of:

* unit tests
* integration tests
* API tests
* database integration tests
* contract tests
* event tests
* queue tests
* WebSocket tests
* frontend component tests
* mobile tests
* end-to-end tests
* accessibility tests
* security tests
* performance tests
* load tests
* resilience tests
* migration tests
* backup/restore tests
* deployment validation

Tests must verify real behavior.

Tests must cover:

* success paths
* validation failures
* authorization failures
* edge cases
* concurrency
* retries
* duplicates
* transaction behavior
* event delivery
* job processing
* media-processing failures
* subscription state transitions
* playback failures
* privacy enforcement
* regression scenarios

Do not create tests that merely assert mocks without validating meaningful application behavior.

---

# REPOSITORY ENGINEERING RULES

Treat the repository as the authoritative source of implementation state.

Before changing anything:

1. Inspect the repository structure.
2. Inspect the existing implementation.
3. Identify existing modules and reusable components.
4. Inspect package and build configuration.
5. Inspect database schemas and migrations.
6. Inspect API contracts.
7. Inspect tests.
8. Inspect infrastructure definitions.
9. Inspect environment configuration.
10. Determine compatibility constraints.

Preserve working functionality.

Do not regenerate the entire project unnecessarily.

Do not rewrite unrelated files.

Do not replace existing production-quality implementations merely to use a different personal preference.

When changes are required, integrate them into the existing architecture.

Repository state is more authoritative than assumptions.

---

# IMPLEMENTATION DISCIPLINE

All implementation work must be complete and production-oriented.

Never:

* omit required files
* omit implementations for brevity
* create fake integrations
* create empty methods for future work
* use TODO/FIXME comments instead of implementation
* claim a feature is complete when only its interface exists
* silently skip difficult requirements
* invent incompatible APIs
* bypass security checks for convenience
* disable tests to make builds pass
* weaken type safety without justification
* hardcode credentials or environment-specific secrets

Use typed contracts and explicit failure handling.

Keep modules cohesive.

Keep domain logic separate from transport concerns.

Keep infrastructure concerns separated from core business logic where practical.

Prefer explicit, maintainable implementations over clever abstractions.

---

# CONFIGURATION AND SECRETS

All environment-specific values must be externally configurable.

Use secure configuration management for:

* database credentials
* Redis credentials
* broker credentials
* object-storage credentials
* payment-provider credentials
* signing keys
* JWT secrets
* OAuth credentials
* email provider credentials
* push notification credentials
* observability credentials

Provide safe configuration validation at application startup.

Do not commit secrets.

Do not expose secrets through logs.

Do not hardcode environment-specific endpoints into application logic when configuration is appropriate.

---

# API AND CONTRACT COMPATIBILITY

All domain contracts must be explicit and stable.

Changes to APIs, events, schemas, and shared contracts must consider:

* backward compatibility
* versioning
* migration paths
* client impact
* event consumer impact
* rollout ordering
* rollback behavior

Do not arbitrarily redesign an existing contract because a new implementation would be easier.

When a breaking change is genuinely required, make its compatibility impact explicit and provide a controlled migration strategy.

---

# CLIENT ENGINEERING PRINCIPLES

Web and mobile clients must:

* consume explicit backend contracts
* handle loading states
* handle empty states
* handle error states
* handle offline or degraded states where applicable
* validate user input
* preserve accessibility
* avoid leaking privileged data
* handle stale server state
* handle retries carefully
* avoid unnecessary duplicate requests
* support responsive interfaces
* support keyboard and assistive technologies where applicable
* provide clear playback feedback
* preserve correct authentication state

Do not place authoritative authorization decisions only in the client.

---

# DOCUMENTATION

Maintain useful engineering documentation for implemented functionality.

Documentation should cover applicable:

* architecture decisions
* environment configuration
* database changes
* API contracts
* event contracts
* queue contracts
* operational procedures
* local development
* deployment
* debugging
* failure recovery
* monitoring
* security-sensitive behavior

Documentation must describe the actual implementation rather than an aspirational design.

---

# SCALABILITY EXPECTATIONS

Design the platform to scale horizontally.

The architecture should support large workloads through:

* stateless application processes where practical
* autoscaling
* connection management
* caching
* asynchronous processing
* partitionable workloads
* independent media delivery
* search infrastructure
* event streaming
* queue workers
* database read scaling where appropriate
* CDN delivery
* workload isolation

Avoid hidden single-node assumptions.

Avoid global in-memory state that breaks when multiple instances run simultaneously.

---

# AVAILABILITY AND DISASTER RECOVERY

Design for production availability.

The infrastructure roadmap must support:

* multiple application replicas
* health checks
* rolling deployments
* failure isolation
* database backups
* point-in-time recovery where supported
* disaster recovery
* restoration procedures
* infrastructure recreation
* regional failure planning
* recovery testing

Define explicit recovery objectives appropriate to the business criticality of each subsystem.

Critical transactional data must have stronger durability guarantees than ephemeral caches.

---

# DELIVERY MODEL

The complete project will be implemented incrementally through a sequence of independent engineering prompts.

Each implementation prompt must be independently understandable.

Each prompt must describe its own:

* project context
* relevant technology
* architectural assumptions
* scope
* implementation requirements
* integration constraints
* validation requirements
* testing requirements
* completion criteria

A prompt may instruct the coding agent to inspect the current repository and integrate with existing code.

A prompt must never require the coding agent to have access to another AI-generated prompt.

All prompts in the project must collectively converge on one coherent production-grade system.

---

# PROJECT EXECUTION PRINCIPLES

For every implementation task:

1. Inspect before modifying.
2. Understand before rewriting.
3. Reuse compatible existing functionality.
4. Implement the requested scope completely.
5. Preserve working behavior.
6. Maintain contract consistency.
7. Add appropriate automated tests.
8. Validate compilation and type checking.
9. Validate affected runtime behavior.
10. Update migrations when required.
11. Update documentation when implementation changes require it.
12. Review security implications.
13. Review observability implications.
14. Review performance implications.
15. Review failure behavior.
16. Report the exact implementation performed.

Do not modify unrelated parts of the system without a concrete integration reason.

---

# COMPLETION REQUIREMENTS FOR IMPLEMENTATION AGENTS

An implementation task is not complete merely because source files exist.

The implementation agent must verify, as applicable:

* compilation succeeds
* type checking succeeds
* linting succeeds
* affected tests pass
* migrations are valid
* database behavior is correct
* API contracts are valid
* event contracts are valid
* background jobs are valid
* authentication and authorization work correctly
* security-sensitive behavior is validated
* observability is present
* failure paths are handled
* documentation reflects reality

Do not claim completion when known required functionality remains unimplemented.

---

# REQUIRED IMPLEMENTATION REPORT

At the end of every implementation task, report:

* files created
* files modified
* major functionality implemented
* database changes
* API changes
* event changes
* queue/job changes
* infrastructure changes
* tests added or updated
* validation performed
* migrations executed or required
* important compatibility considerations
* unresolved issues, if any

The report must be factual.

Do not claim a successful validation that was not actually performed.

---

# GLOBAL DEFINITION OF DONE

The overall platform is considered production-ready only when its implemented functionality is:

* complete
* integrated
* tested
* observable
* secure
* scalable
* maintainable
* deployable
* recoverable
* operationally documented

No subsystem may be considered complete solely because its happy path works.

Production readiness includes normal behavior, invalid input, unauthorized behavior, failures, retries, concurrency, observability, and operational recovery.

---

# SOURCE OF TRUTH

During implementation, the repository is the source of truth for the system's current implementation state.

The implementation agent must inspect:

* existing source code
* schemas
* migrations
* contracts
* tests
* configuration
* infrastructure
* documentation

The requirements in the current task define what must be achieved.

The repository defines what currently exists.

When the two differ, preserve compatible existing behavior unless the current task explicitly requires a change.

Never assume that an earlier AI conversation, earlier generated response, or external document is available to the implementation agent.

---

# FINAL INSTRUCTION

Build this project as a serious production system.

Favor correctness over shortcuts.

Favor maintainability over cleverness.

Favor explicit contracts over implicit assumptions.

Favor secure defaults over convenience.

Favor observability over blind operation.

Favor real integrations over fake implementations.

Favor resilient architecture over fragile happy paths.

Never optimize for brevity at the expense of correctness, completeness, scalability, maintainability, or production readiness.

Every implementation must be complete enough to become part of a real commercially operated music-streaming platform.

The result must be an original, coherent, extensible system capable of supporting large-scale music streaming and the surrounding product ecosystem without relying on proprietary implementation details from any existing platform.
