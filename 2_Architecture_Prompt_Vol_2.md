You are operating in Senior Engineering Team Mode.

Complete the remaining enterprise architecture for a production-ready global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

Use the architecture defined for the platform as the source of truth.

Do not restart the architecture.

Do not implement backend code.

Do not implement frontend code.

Do not implement mobile code.

Do not generate infrastructure implementation files.

Do not generate Dockerfiles.

Do not generate Kubernetes manifests.

Do not generate Terraform files.

Do not generate application source code.

Produce architecture, specifications, contracts, diagrams, engineering decisions, security models, operational strategies, and implementation guidance only.

────────────────────────────────────────

VOLUME 2 OBJECTIVE

Complete the remaining enterprise architecture for:

1. Multi-device architecture
2. Web and mobile playback architecture
3. Background audio architecture
4. Audio focus and interruption architecture
5. Content ingestion workflows
6. Artist and label workflows
7. Release management
8. Media processing pipeline
9. Audio transcoding
10. Adaptive streaming
11. CDN and global delivery
12. Content protection
13. Offline downloads
14. Device authorization
15. Subscription lifecycle
16. Billing and entitlement operations
17. Advertising architecture
18. Podcast architecture
19. Audiobook extensibility
20. Recommendation platform evolution
21. Discovery architecture
22. Radio architecture
23. Charts architecture
24. Analytics architecture
25. Data platform boundaries
26. Notification architecture
27. Localization architecture
28. Explicit-content and parental controls
29. Moderation architecture
30. Administration architecture
31. Feature flags
32. Security architecture
33. Threat model
34. Observability architecture
35. Deployment architecture
36. Kubernetes topology
37. Disaster recovery
38. Capacity planning
39. Failure scenarios
40. Data consistency strategy
41. Testing strategy
42. Architectural Decision Records
43. Backend implementation roadmap
44. Complete Project Index

────────────────────────────────────────

MULTI-DEVICE PLATFORM ARCHITECTURE

Design support for:

• Web browsers
• iOS
• Android
• Tablets
• Desktop applications where appropriate
• Smart speakers where appropriate
• Smart TVs
• Connected cars
• Future consoles
• Future embedded platforms

Define:

• Device registration
• Device identity
• Device capabilities
• Device trust
• Device limits
• Session management
• Remote logout
• Device revocation
• Playback synchronization
• Queue synchronization
• Library synchronization
• Download synchronization

Create a capability model supporting differences in:

• Audio codecs
• Maximum audio quality
• Offline support
• Background playback
• Audio output
• DRM/content-protection support
• Spatial-audio capabilities where applicable
• Input methods

Do not assume every client has identical capabilities.

────────────────────────────────────────

PLAYBACK CLIENT ARCHITECTURE

Define the client playback engine boundaries.

Support:

• Track loading
• Buffering
• Playback
• Pause
• Resume
• Seek
• Skip
• Previous
• Queue
• Repeat
• Shuffle
• Cross-device handoff where supported
• Progress synchronization
• Playback state synchronization

Clearly separate:

• UI player state
• Local playback engine state
• Server playback session state
• Historical listening events

Do not persist every playback tick transactionally to PostgreSQL.

────────────────────────────────────────

BACKGROUND AUDIO

Design background playback for mobile.

Support:

• Background playback
• Lock-screen controls
• Notification media controls
• Headset controls
• Bluetooth controls
• Interruptions
• App suspension
• Audio focus
• Audio route changes
• Resume after interruption

Define platform-specific boundaries without coupling backend services to client implementation details.

────────────────────────────────────────

AUDIO FOCUS AND INTERRUPTION

Handle:

• Phone calls
• Other audio applications
• Navigation prompts
• Bluetooth changes
• Wired headset insertion/removal
• Device audio route changes
• System interruptions

Define:

• Pause behavior
• Resume behavior
• Ducking where appropriate
• State recovery

────────────────────────────────────────

CONTENT INGESTION

Design the complete content ingestion workflow.

Support:

• Artist upload
• Label upload
• Partner upload
• Bulk ingestion
• Metadata submission
• Audio upload
• Artwork upload
• Lyrics submission
• Rights declarations
• Validation
• Review
• Approval
• Processing
• Publishing
• Scheduled publishing
• Unpublishing
• Archival
• Removal

Define lifecycle:

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

Define:

• State ownership
• Transition rules
• Retry
• Idempotency
• Audit
• Failure recovery

────────────────────────────────────────

ARTIST AND LABEL ARCHITECTURE

Design support for:

• Artist organizations
• Artist users
• Artist staff
• Labels
• Label staff
• Distribution partners
• Content administrators

Support:

• Roles
• Permissions
• Organization boundaries
• Content ownership
• Release management
• Rights management
• Analytics access
• Financial reporting access

Ensure one artist or label cannot access another organization's private data.

────────────────────────────────────────

RELEASE MANAGEMENT

Design release workflows for:

• Singles
• EPs
• Albums
• Compilations
• Deluxe releases
• Reissues

Support:

• Release metadata
• Track ordering
• Artwork
• Release date
• Territory
• Explicit-content labels
• Language
• Rights
• Contributors
• ISRC/UPC or equivalent identifiers where applicable

Define release validation.

────────────────────────────────────────

MEDIA PROCESSING PIPELINE

Design the complete audio/media pipeline:

1. Upload authorization
2. Direct object-storage upload
3. Upload completion
4. File validation
5. Malware scanning boundary
6. Metadata extraction
7. Codec validation
8. Audio quality validation
9. Loudness analysis
10. Transcoding
11. Rendition generation
12. Artwork processing
13. Lyrics processing
14. Packaging
15. Quality validation
16. Rights validation
17. Publication readiness
18. CDN availability
19. Publication

Define:

• Service ownership
• Events
• Queues
• Retry
• Dead-letter handling
• Idempotency
• Temporary storage
• Cleanup
• Failure recovery

────────────────────────────────────────

AUDIO TRANSCODING

Design a production audio-processing system.

Support:

• Multiple codecs
• Multiple containers
• Multiple bitrates
• Multiple sample rates
• Stereo
• Mono
• High-quality audio
• Lossless where supported

Define a capability abstraction rather than hard-coding one codec.

Support future:

• New codecs
• Spatial audio
• Immersive formats
• Higher-quality tiers

where architecture permits.

────────────────────────────────────────

LOUDNESS AND QUALITY

Define processing for:

• Loudness analysis
• Peak detection
• Clipping detection
• Duration validation
• Channel validation
• Sampling-rate validation
• Corruption detection

Define quality thresholds and failure handling.

────────────────────────────────────────

ADAPTIVE AUDIO STREAMING

Complete HLS or equivalent adaptive audio architecture.

Define:

• Master manifests
• Variant playlists
• Audio segments
• Segment storage
• CDN cache keys
• Signed playback access
• Token expiration
• Quality switching
• Device capability selection

Application servers must not proxy audio bytes unnecessarily.

────────────────────────────────────────

CDN AND GLOBAL DELIVERY

Design global delivery for:

• Audio manifests
• Audio segments
• Artwork
• Lyrics
• Podcasts
• Static application assets

Define cache behavior for:

• Immutable audio segments
• Public artwork
• Protected manifests
• Short-lived playback credentials
• Frequently changing metadata

Support:

• Origin protection
• Cache invalidation
• Regional failover
• Cost optimization

────────────────────────────────────────

CONTENT PROTECTION

Define abstraction boundaries for content protection.

Support future integration with:

• Platform-appropriate DRM/content protection
• License services
• Secure playback tokens
• Offline licenses

Clearly distinguish:

• Authentication
• Authorization
• Entitlement
• Playback authorization
• Content protection licensing

Do not implement custom cryptographic algorithms.

Do not claim signed URLs alone are equivalent to DRM.

────────────────────────────────────────

PLAYBACK AUTHORIZATION

Define the complete authorization process:

Client requests playback
→ Authenticate user/device
→ Validate subscription
→ Validate entitlement
→ Validate content rights
→ Validate region
→ Validate device capability
→ Validate concurrent-play limit
→ Generate short-lived playback authorization
→ CDN delivers media

Define:

• Token lifetime
• Revocation
• Replay mitigation
• Failure behavior
• Regional routing

────────────────────────────────────────

OFFLINE DOWNLOADS

Complete offline architecture.

Support:

• Download authorization
• Device authorization
• Entitlement validation
• Download manifest
• Encrypted local storage
• Offline license issuance
• License renewal
• Expiration
• Device revocation
• Download limits
• Storage management

Define failure behavior when:

• License renewal fails
• Subscription expires
• Device is revoked
• Content rights expire
• Region changes

Do not store downloadable audio as unprotected files.

────────────────────────────────────────

SUBSCRIPTION OPERATIONS

Complete subscription architecture.

Support:

• Trial
• Free
• Premium
• Family
• Student
• Regional plans
• Upgrade
• Downgrade
• Cancellation
• Renewal
• Grace period
• Payment failure
• Recovery

Define:

• Billing state
• Payment state
• Subscription state
• Entitlement state

────────────────────────────────────────

ENTITLEMENT OPERATIONS

Define entitlement refresh and recovery.

Support:

• Provider event processing
• Cache refresh
• Grace periods
• Temporary payment-provider outages
• Subscription cancellation
• Expiration
• Region changes
• Plan changes

Entitlement systems must be resilient to delayed external payment events.

────────────────────────────────────────

ADVERTISING ARCHITECTURE

Complete advertising architecture for free/ad-supported plans.

Support:

• Advertisers
• Campaigns
• Creatives
• Targeting
• Inventory
• Audio ad breaks
• Ad decisions
• Impression events
• Completion events
• Frequency capping
• Consent
• Fraud detection
• Reporting

Advertising failures should degrade gracefully.

Playback must remain operational when the advertising system is temporarily unavailable, according to the approved product policy.

────────────────────────────────────────

PODCAST PLATFORM

Complete podcast architecture.

Support:

• Shows
• Episodes
• Episode artwork
• Descriptions
• Hosts
• Categories
• Publishing schedules
• Playback progress
• Downloads
• Follows
• Search
• Recommendations
• Analytics

Define podcast-specific ingestion and content rules.

────────────────────────────────────────

AUDIOBOOK EXTENSIBILITY

Complete the architecture boundary for future audiobooks.

Support conceptual models for:

• Book
• Chapter
• Narrator
• Author
• Progress
• Entitlement
• Download
• Rights
• Playback

Do not force all audiobook functionality into the initial implementation.

────────────────────────────────────────

DISCOVERY ARCHITECTURE

Design discovery experiences including:

• Home
• New releases
• Trending
• Personalized playlists
• Daily mixes
• Similar artists
• Similar tracks
• Genre discovery
• Mood/curated collections
• Editorial content
• Radio

Define:

• Candidate sources
• Ranking
• Personalization
• Editorial overrides
• Business rules
• Fallback behavior

────────────────────────────────────────

RECOMMENDATION PLATFORM EVOLUTION

Define an evolution path:

Stage 1:

• Deterministic rules
• Popularity
• Recency
• Content metadata

Stage 2:

• Collaborative signals
• Behavioral features
• Candidate generation

Stage 3:

• ML ranking
• Feature stores
• Model serving

Stage 4:

• Real-time personalization
• Online experimentation
• Advanced ranking

Do not require a complete ML platform before the first production release.

────────────────────────────────────────

RADIO ARCHITECTURE

Complete:

• Track radio
• Artist radio
• Genre radio
• Personalized stations
• Mood stations

Define:

• Candidate generation
• Ranking
• Session continuity
• Deduplication
• Personalization
• Fallback

Radio generation must not depend on a single synchronous downstream service.

────────────────────────────────────────

CHARTS ARCHITECTURE

Support:

• Global charts
• Regional charts
• Genre charts
• Trending
• Time-window rankings
• Historical charts

Define:

• Aggregation windows
• Data sources
• Fraud controls
• Update frequency
• Snapshotting
• Ranking consistency

────────────────────────────────────────

ANALYTICS ARCHITECTURE

Complete analytics architecture.

Separate:

Operational data
→ events
→ stream processing
→ aggregation
→ analytical storage
→ dashboards

Track:

• Streams
• Unique listeners
• Listening hours
• Completion
• Skips
• Saves
• Follows
• Search
• Recommendations
• Subscription conversion
• Churn
• Advertising metrics
• Artist performance

Do not overload PostgreSQL with raw telemetry.

────────────────────────────────────────

DATA PLATFORM BOUNDARIES

Define the boundary between:

• Transactional PostgreSQL
• Kafka/Redpanda
• Operational analytics
• Long-term analytical storage
• Search indexes
• Recommendation features

Define retention and ownership for each.

────────────────────────────────────────

NOTIFICATION ARCHITECTURE

Complete:

• Push
• Email
• In-app notifications

Support:

• New release alerts
• Artist-follow notifications
• Playlist notifications
• Subscription events
• Payment failures
• Download completion
• Security events
• Recommendations

Define:

• Preferences
• Scheduling
• Deduplication
• Rate limiting
• Retry
• Provider fallback

────────────────────────────────────────

LOCALIZATION

Support:

• Multiple languages
• Localized artist metadata
• Localized album metadata
• Localized descriptions
• Localized editorial content
• Audio language
• Lyrics language
• Regional pricing
• Regional availability

Define:

• Locale model
• Fallback strategy
• Translation workflow
• Client negotiation

────────────────────────────────────────

EXPLICIT CONTENT AND PARENTAL CONTROLS

Design:

• Explicit-content labels
• Content restrictions
• Family plans
• Managed profiles
• Age restrictions
• Playback restrictions
• Search restrictions
• Download restrictions

Enforcement must occur at:

• API
• Domain
• Discovery
• Search
• Playback authorization

Do not rely solely on client-side filtering.

────────────────────────────────────────

MODERATION

Support moderation for:

• Artist profiles
• Catalog metadata
• Playlists
• Podcasts
• User-generated content where supported
• Abuse reports
• Malicious uploads

Define:

• Automated checks
• Manual review
• Appeals
• Policy versioning
• Audit

────────────────────────────────────────

ADMINISTRATION

Design an enterprise administration platform.

Support:

• Users
• Accounts
• Subscriptions
• Content
• Artists
• Labels
• Rights
• Moderation
• Advertising
• Payments
• Analytics
• Feature flags
• System configuration
• Audit

Define:

• Administrative roles
• Permissions
• Sensitive operations
• Approval workflows
• Audit requirements

High-risk administrative actions must be traceable.

────────────────────────────────────────

FEATURE FLAGS

Support:

• Global rollout
• Percentage rollout
• User targeting
• Region targeting
• Device targeting
• Plan targeting
• Experimental features
• Kill switches
• Feature expiration

Define:

• Evaluation
• Caching
• Propagation
• Ownership
• Audit
• Cleanup

────────────────────────────────────────

SECURITY ARCHITECTURE

Complete platform security.

Identity:

• Password security
• MFA
• Passkeys
• Session protection
• Token rotation
• Device trust

Application:

• Input validation
• Rate limiting
• Abuse prevention
• Secure headers
• CORS
• CSRF where applicable
• XSS protection

Content:

• Playback authorization
• Rights enforcement
• Offline protection
• Content protection boundaries

Infrastructure:

• IAM
• Least privilege
• Network segmentation
• Encryption
• Secrets management
• Kubernetes security
• Audit logging

────────────────────────────────────────

THREAT MODEL

Create a threat model covering:

• Account takeover
• Credential stuffing
• Session hijacking
• Playback token theft
• Unauthorized streaming
• Download abuse
• Subscription fraud
• Payment fraud
• Fake listening
• Stream manipulation
• Bot activity
• Malicious content uploads
• Webhook spoofing
• Supply-chain attacks
• Data leakage
• Insider threats
• DDoS
• Kubernetes compromise
• Secret exposure

For each define:

• Attack vector
• Affected systems
• Mitigation
• Detection
• Response
• Recovery

────────────────────────────────────────

OBSERVABILITY ARCHITECTURE

Complete observability for:

• APIs
• Playback authorization
• Playback sessions
• Search
• Recommendations
• Media processing
• Downloads
• Subscriptions
• Payments
• Notifications
• Advertising
• Analytics

Use:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Define:

• Metrics
• Structured logs
• Tracing
• Correlation IDs
• Trace propagation
• Dashboards
• Alerts
• SLOs
• SLIs

────────────────────────────────────────

DEPLOYMENT ARCHITECTURE

Design:

• Development
• Testing
• Staging
• Production
• Disaster Recovery

Support:

• Kubernetes
• Helm
• Container registry
• GitHub Actions
• Rolling deployments
• Canary deployments
• Blue-green where appropriate
• Automatic rollback
• Health verification

Define deployment boundaries for:

• APIs
• Playback services
• Workers
• Media processing
• Search
• Kafka
• Redis
• PostgreSQL
• Observability

────────────────────────────────────────

KUBERNETES TOPOLOGY

Define:

• Cluster structure
• Namespaces
• Node pools
• API workloads
• Playback workloads
• Worker workloads
• Media workloads
• Search workloads
• Observability workloads

Use:

• Autoscaling
• Resource limits
• Resource requests
• PDB
• Network policies
• RBAC
• Pod security
• Dedicated node pools where appropriate

────────────────────────────────────────

DISASTER RECOVERY

Define:

• RTO
• RPO
• PostgreSQL recovery
• S3 recovery
• Search recovery
• Kafka recovery
• Redis recovery
• Kubernetes recovery
• Regional failover

Create recovery procedures for:

• Database failure
• Region failure
• CDN failure
• Search failure
• Payment failure
• Media-processing failure
• Event-stream failure

────────────────────────────────────────

CAPACITY STRATEGY

Design for:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of content assets
• Massive CDN traffic
• High playback authorization traffic
• High recommendation traffic
• High analytics traffic

Analyze scaling for:

• API Gateway
• Authentication
• Catalog
• Playback authorization
• CDN
• Redis
• Kafka
• Search
• Recommendation systems
• Audio workers
• Notification systems
• Analytics systems

Identify bottlenecks and mitigation strategies.

────────────────────────────────────────

FAILURE SCENARIOS

Define graceful behavior when:

• Database unavailable
• Redis unavailable
• Kafka unavailable
• Search unavailable
• Recommendation unavailable
• Payment provider unavailable
• S3 unavailable
• CDN degradation
• Audio processing backlog
• Notification provider unavailable
• Ad decision service unavailable
• Region unavailable

For every scenario define:

• Detection
• Retry
• Timeout
• Fallback
• Degraded operation
• Recovery
• Reconciliation

────────────────────────────────────────

DATA CONSISTENCY STRATEGY

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
• Advertising
• Analytics

Identify:

• Strong consistency
• Eventual consistency
• Idempotency
• Optimistic concurrency
• Distributed locks
• Transactional outbox
• Saga patterns where justified

────────────────────────────────────────

TESTING STRATEGY

Define:

UNIT TESTING

• Domain rules
• Entitlements
• Playback authorization
• Playlist logic
• Subscription logic
• Recommendation rules

INTEGRATION TESTING

• PostgreSQL
• Redis
• Kafka
• BullMQ
• Search
• S3
• Payments
• Notification providers

CONTRACT TESTING

• REST
• Playback APIs
• Events
• Webhooks

END-TO-END

• Registration
• Subscription
• Search
• Playback
• Queue
• Playlist
• Library
• Download
• Multi-device
• Notifications

PERFORMANCE

• Playback authorization
• Search
• Recommendations
• Event ingestion
• Audio processing
• CDN

RESILIENCE

• Database failure
• Redis failure
• Kafka failure
• Search failure
• Regional failure

SECURITY

• Authentication
• Authorization
• Playback protection
• Download protection
• Abuse prevention
• Webhook security

────────────────────────────────────────

ARCHITECTURAL DECISION RECORDS

Generate ADRs for:

• Multi-device architecture
• Background playback
• Audio processing
• Adaptive streaming
• CDN architecture
• Content protection
• Offline downloads
• Rights architecture
• Subscription and entitlement architecture
• Advertising architecture
• Podcast architecture
• Recommendation evolution
• Analytics platform
• Multi-region deployment
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

BACKEND IMPLEMENTATION ROADMAP

At the end of this architecture volume, define the exact backend implementation order.

BACKEND MILESTONE 1

Monorepo foundation and shared backend infrastructure.

BACKEND MILESTONE 2

Configuration, observability, validation, error handling, authentication foundations.

BACKEND MILESTONE 3

Identity, accounts, profiles, sessions, and devices.

BACKEND MILESTONE 4

Subscriptions, billing, payments, and entitlements.

BACKEND MILESTONE 5

Content catalog, artists, albums, tracks, releases, and metadata.

BACKEND MILESTONE 6

Artist/label workflows, rights, availability, and localization.

BACKEND MILESTONE 7

Media uploads, audio processing, renditions, artwork, and content ingestion.

BACKEND MILESTONE 8

Playback authorization, playback sessions, progress, queue, and synchronization.

BACKEND MILESTONE 9

Offline downloads and offline licensing.

BACKEND MILESTONE 10

Search, discovery, and indexing.

BACKEND MILESTONE 11

Recommendations, personalization, radio, and charts.

BACKEND MILESTONE 12

Playlists, libraries, likes, follows, and listening history.

BACKEND MILESTONE 13

Podcasts and future audiobook boundaries.

BACKEND MILESTONE 14

Notifications and advertising.

BACKEND MILESTONE 15

Analytics and reporting.

BACKEND MILESTONE 16

Moderation, parental controls, administration, feature flags, and audit.

BACKEND MILESTONE 17

Security hardening, abuse prevention, and privacy.

BACKEND MILESTONE 18

Integration testing, performance testing, resilience testing, reconciliation, and production readiness.

Adjust the sequence only when implementation dependencies require it.

────────────────────────────────────────

PROJECT INDEX

Update the Project Index with:

• Architecture Volume 1 status
• Architecture Volume 2 status
• Service boundaries
• Domain ownership
• Data architecture
• Media architecture
• Playback architecture
• Rights architecture
• Subscription architecture
• Search architecture
• Recommendation architecture
• Advertising architecture
• Analytics architecture
• Security architecture
• Infrastructure decisions
• ADRs
• Backend implementation roadmap
• Remaining project phases

────────────────────────────────────────

ARCHITECTURE VOLUME 2 OUTPUT

Produce:

1. Multi-Device Architecture
2. Playback Client Architecture
3. Background Audio Architecture
4. Audio Focus and Interruption Architecture
5. Content Ingestion Architecture
6. Artist and Label Architecture
7. Release Management Architecture
8. Media Processing Pipeline
9. Audio Transcoding Architecture
10. Audio Quality Architecture
11. Adaptive Audio Streaming Architecture
12. CDN and Global Delivery
13. Content Protection Architecture
14. Playback Authorization
15. Offline Download Architecture
16. Subscription Operations
17. Entitlement Operations
18. Advertising Architecture
19. Podcast Platform
20. Audiobook Extensibility
21. Discovery Architecture
22. Recommendation Platform Evolution
23. Radio Architecture
24. Charts Architecture
25. Analytics Architecture
26. Data Platform Boundaries
27. Notification Architecture
28. Localization Architecture
29. Explicit Content and Parental Controls
30. Moderation Architecture
31. Administration Architecture
32. Feature Flag Architecture
33. Security Architecture
34. Threat Model
35. Observability Architecture
36. Deployment Architecture
37. Kubernetes Topology
38. Disaster Recovery
39. Capacity Strategy
40. Failure Scenario Analysis
41. Data Consistency Strategy
42. Testing Strategy
43. Architectural Decision Records
44. Backend Implementation Roadmap
45. Complete Project Index

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
• Strong entitlement enforcement
• Secure playback authorization
• Horizontal scaling
• Graceful degradation
• Observable operations

Avoid:

• Unnecessary microservices
• Shared database ownership
• Distributed transactions where avoidable
• Tight coupling
• Single points of failure
• Redis as a system of record
• PostgreSQL as a raw telemetry store
• Application servers proxying high-bandwidth audio
• Proprietary cryptography
• Frontend-only security
• Unnecessary cross-region synchronous dependencies
• Premature ML infrastructure
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
• Service boundaries
• Ownership rules
• State machines
• Media workflows
• Playback workflows
• Rights workflows
• Subscription workflows
• API contracts
• Event contracts
• Queue definitions
• Security models
• Threat models
• Scalability strategies
• Deployment architecture
• Disaster recovery
• Testing strategy
• ADRs
• Backend implementation roadmap
• Project Index

The resulting architecture must be sufficiently detailed that separate backend, frontend, mobile, infrastructure, DevOps, and QA teams can implement the complete music streaming platform without making major architectural decisions themselves.
