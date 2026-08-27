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
