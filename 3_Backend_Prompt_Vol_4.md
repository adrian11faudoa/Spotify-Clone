You are operating in Senior Engineering Team Mode.

Build the production-ready backend for audio processing, transcoding, adaptive audio streaming, playback authorization, playback sessions, playback progress, queue synchronization, multi-device playback synchronization, and CDN delivery for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must follow the approved Spotify-like architecture, domain boundaries, database ownership, media architecture, rights architecture, entitlement architecture, API conventions, event architecture, queue architecture, security model, and Project Index.

Do not redesign the architecture.

Do not generate frontend code.

Do not generate mobile code.

Do not generate infrastructure implementation code.

Do not generate Terraform.

Do not generate Kubernetes manifests.

Do not generate CI/CD workflows.

────────────────────────────────────────

MISSION

Implement the production-ready backend required for:

• Audio processing
• Audio transcoding
• Audio rendition generation
• Loudness analysis
• Audio quality validation
• Adaptive audio streaming
• HLS manifests
• Audio segments
• Playback authorization
• Entitlement validation
• Rights validation
• Regional availability validation
• Device capability validation
• Concurrent playback limits
• Playback sessions
• Playback progress
• Resume playback
• Queue synchronization
• Multi-device playback synchronization
• Playback state
• CDN delivery authorization
• Signed playback credentials
• Playback event ingestion

The implementation must support:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Large-scale audio processing
• Global CDN delivery
• Multiple audio quality levels
• Multiple codecs
• Multiple devices
• Premium and free plans
• Regional content rights
• Offline architecture integration
• High availability
• Horizontal scaling

────────────────────────────────────────

TECHNOLOGY STACK

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

Audio Processing:

• FFmpeg
• Approved media-processing infrastructure

Storage:

• AWS S3-compatible object storage

CDN:

• CloudFront or equivalent CDN

Observability:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Testing:

• Jest
• Supertest
• Integration and performance testing tools

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

Keep domain rules outside controllers.

Use repositories for persistence.

Use DTOs for API contracts.

Use centralized validation.

Use centralized error handling.

Use structured logging.

Use idempotency for processing and playback authorization operations.

────────────────────────────────────────

DOMAIN OWNERSHIP

Maintain explicit boundaries between:

• Audio processing
• Audio renditions
• Playback authorization
• Playback sessions
• Playback progress
• Queue
• Device synchronization
• CDN delivery
• Entitlements
• Rights

Do not combine:

• Media-processing state with playback state
• CDN state with subscription state
• Playback progress with raw analytics
• Device presence with authoritative account data

────────────────────────────────────────

AUDIO PROCESSING

Implement audio-processing orchestration.

Support:

• Source validation
• Metadata extraction
• Loudness analysis
• Duration validation
• Sample-rate validation
• Channel validation
• Codec validation
• Clipping detection
• Transcoding
• Rendition generation
• Packaging
• Quality verification

Use BullMQ for asynchronous media workloads.

────────────────────────────────────────

PROCESSING STATE

Support:

• Uploaded
• Validation Pending
• Validating
• Validation Failed
• Processing
• Processed
• Quality Check
• Ready
• Failed
• Reprocessing

Define valid state transitions.

Every transition must be idempotent.

────────────────────────────────────────

AUDIO QUALITY VALIDATION

Validate:

• Duration
• Sample rate
• Bit depth
• Channels
• Codec
• Container
• Loudness
• Peak level
• Corruption

Define configurable quality thresholds.

Reject or quarantine invalid media.

────────────────────────────────────────

AUDIO TRANSCODING

Implement a configurable rendition system.

Support conceptual quality tiers such as:

• Low
• Standard
• High
• Lossless where supported

Support multiple:

• Codecs
• Containers
• Bitrates
• Sample rates
• Channel configurations

Do not hard-code business logic around one codec.

Create an audio-capability abstraction.

────────────────────────────────────────

RENDITION MODEL

Each rendition should have metadata such as:

• Track
• Codec
• Container
• Bitrate
• Sample rate
• Channels
• Quality tier
• Duration
• Object key
• Processing version
• Status

A track may have many renditions.

────────────────────────────────────────

MEDIA STORAGE

Implement storage organization for:

• Source audio
• Processing intermediates
• Final renditions
• Manifests
• Segments
• Artwork references

Use deterministic object-key strategies.

Do not expose internal storage paths directly to clients unless explicitly authorized.

────────────────────────────────────────

MEDIA CLEANUP

Implement jobs for:

• Failed-upload cleanup
• Temporary processing cleanup
• Obsolete-rendition cleanup
• Orphaned-segment cleanup
• Retired-source handling

Cleanup must be idempotent.

Do not delete content still referenced by active releases or playback.

────────────────────────────────────────

ADAPTIVE STREAMING

Implement the backend architecture for adaptive audio streaming.

Support:

• Master playlist
• Variant playlists
• Audio segments
• Segment metadata
• Quality variants
• Manifest generation
• Packaging state
• CDN publication

Do not stream audio bytes through the application API.

────────────────────────────────────────

MANIFEST AUTHORIZATION

Implement a secure playback-manifest authorization flow.

Client requests playback
→ Authenticate
→ Validate entitlement
→ Validate rights
→ Validate region
→ Validate device
→ Validate concurrent streams
→ Generate short-lived playback authorization
→ Return authorized playback information

Define:

• Token lifetime
• Scope
• Resource binding
• Device binding where appropriate
• Expiration
• Replay mitigation
• Revocation behavior

────────────────────────────────────────

PLAYBACK CREDENTIALS

Implement short-lived playback credentials.

Support binding credentials to appropriate:

• User
• Profile
• Device
• Track/content
• Region
• Session

Credentials must not grant broader access than required.

Do not use long-lived media URLs as the primary authorization mechanism.

────────────────────────────────────────

CONTENT PROTECTION

Implement integration boundaries for approved content-protection mechanisms.

Support future integration with:

• DRM/content protection services
• License services
• Device-specific protections
• Offline licenses

Do not implement custom cryptography.

Do not claim signed URLs are equivalent to DRM.

────────────────────────────────────────

ENTITLEMENT VALIDATION

Before playback authorization verify:

• Subscription
• Entitlement
• Content type
• Plan restrictions
• Promotional grants where applicable
• Account status

Use the entitlement domain established previously.

Define cache and fallback behavior.

────────────────────────────────────────

RIGHTS VALIDATION

Validate:

• Content rights
• Territory
• Start date
• End date
• Platform restrictions
• Device restrictions
• Subscription restrictions

A technically valid media file must still be denied if rights are not active.

────────────────────────────────────────

DEVICE CAPABILITY VALIDATION

Support:

• Device ID
• Platform
• Application version
• Supported codecs
• Maximum audio quality
• Background playback capability
• Offline capability
• Content-protection capability

Select an appropriate rendition according to device capabilities and entitlement.

────────────────────────────────────────

CONCURRENT PLAYBACK

Implement configurable concurrent-stream limits.

Track active playback sessions.

Support:

• Session creation
• Session heartbeat
• Session timeout
• Session termination
• Remote logout
• Device revocation
• Subscription-plan limits

Do not assume concurrent sessions always disappear cleanly.

Use TTL-based state with authoritative reconciliation.

────────────────────────────────────────

PLAYBACK SESSION

Implement:

• Session creation
• Session state
• Current track
• Device
• Profile
• Started timestamp
• Last heartbeat
• End timestamp
• Status

Support:

• Active
• Paused
• Stopped
• Expired
• Terminated

Do not store raw high-frequency playback telemetry here.

────────────────────────────────────────

PLAYBACK SESSION REDIS

Use Redis for low-latency active-session coordination.

Support:

• Active session registry
• Heartbeat
• TTL
• Session conflict detection
• Stream limit enforcement

PostgreSQL may persist summarized or auditable session records as required.

Redis is not the permanent source of truth.

────────────────────────────────────────

PLAYBACK PROGRESS

Implement:

• Current position
• Track completion state
• Last played timestamp
• Resume position
• Device
• Profile

Progress updates must be optimized for high frequency.

Do not write every second of playback directly to PostgreSQL.

Use throttling, batching, or event-driven persistence.

────────────────────────────────────────

LISTENING HISTORY INTEGRATION

Publish playback events for downstream analytics/history.

Events may include:

• PlaybackStarted
• PlaybackProgressed
• PlaybackCompleted
• PlaybackSkipped
• PlaybackStopped

Do not make listening-history persistence block playback.

────────────────────────────────────────

PLAYBACK QUEUE

Implement server synchronization for:

• Current track
• Upcoming tracks
• Queue order
• Repeat mode
• Shuffle mode
• Playback position

Define:

• Queue ownership
• Version
• Optimistic concurrency
• Conflict resolution
• Multi-device synchronization

────────────────────────────────────────

QUEUE CONCURRENCY

Support concurrent queue updates from multiple devices.

Use:

• Queue version
• Optimistic concurrency
• Conflict detection
• Server-authoritative reconciliation

Do not silently overwrite a newer queue state.

────────────────────────────────────────

MULTI-DEVICE PLAYBACK SYNCHRONIZATION

Support:

• Multiple signed-in devices
• Current playback device
• Queue synchronization
• Playback position synchronization
• Remote pause
• Remote play
• Track change
• Device handoff where supported

Define:

• Authoritative state
• Event propagation
• Conflict resolution
• Latency tolerance
• Offline device behavior

────────────────────────────────────────

DEVICE HANDOFF

Create architecture boundaries for:

• Transfer playback
• Device selection
• Resume on another device
• Queue transfer
• Session termination on the previous device where configured

Require authentication and device authorization.

────────────────────────────────────────

PLAYBACK EVENTS

Publish appropriate events:

• PlaybackSessionCreated
• PlaybackSessionHeartbeat
• PlaybackSessionEnded
• PlaybackStarted
• PlaybackPaused
• PlaybackResumed
• PlaybackStopped
• PlaybackCompleted
• PlaybackSkipped
• PlaybackPositionUpdated
• QueueUpdated
• DevicePlaybackChanged

Do not place excessive raw telemetry inside durable transactional event streams without clear retention strategy.

────────────────────────────────────────

AUDIO PROCESSING EVENTS

Publish:

• AudioValidationStarted
• AudioValidationCompleted
• AudioValidationFailed
• AudioProcessingStarted
• AudioProcessingCompleted
• AudioProcessingFailed
• AudioRenditionCreated
• AudioPackagingStarted
• AudioPackagingCompleted
• AudioPackagingFailed

Consumers must be idempotent.

────────────────────────────────────────

BACKGROUND JOBS

Implement queues for:

• Audio validation
• Metadata extraction
• Loudness analysis
• Transcoding
• Rendition generation
• Packaging
• Manifest generation
• CDN publication
• Temporary-file cleanup
• Orphan cleanup
• Playback-state reconciliation

Every job must support:

• Retry
• Backoff
• Timeout
• Concurrency
• Idempotency
• Dead-letter handling
• Metrics
• Structured logging

────────────────────────────────────────

CDN INTEGRATION

Implement the backend integration needed for CDN delivery.

Support:

• Origin path generation
• Cache-safe object naming
• Signed access
• Manifest authorization
• Token expiration
• Cache invalidation where required
• Regional origin selection where appropriate

Immutable audio segments should use long-lived cache policies.

Short-lived authorization data must not be cached as immutable content.

────────────────────────────────────────

CDN FAILURE HANDLING

Define behavior for:

• CDN degradation
• Origin failure
• Manifest failure
• Segment failure
• Regional failure

Playback APIs must distinguish between:

• Authorization failure
• Content unavailable
• CDN failure
• Rights failure

Do not expose internal storage errors directly to clients.

────────────────────────────────────────

API

Implement production-ready APIs.

PLAYBACK

• Authorize playback
• Get playback context
• Create playback session
• Heartbeat
• End session
• Get playback state

PROGRESS

• Update progress
• Get progress
• Resume track

QUEUE

• Get queue
• Update queue
• Add item
• Remove item
• Reorder
• Set current item
• Set repeat mode
• Set shuffle mode

DEVICES

• List playback devices
• Get device
• Transfer playback
• Stop device playback

MEDIA

• Processing status
• Rendition status
• Manifest status

Every endpoint must implement:

• Authentication
• Authorization
• Entitlement validation
• Rights validation where required
• Device validation
• Rate limiting
• Idempotency where appropriate
• OpenAPI documentation
• Consistent error handling

────────────────────────────────────────

DATABASE

Implement Prisma models and migrations for:

• PlaybackSession
• PlaybackState where appropriate
• PlaybackProgress
• PlaybackQueue
• PlaybackQueueItem
• PlaybackDeviceReference
• AudioProcessingJobReference
• AudioRendition
• AudioPackagingJob
• PlaybackAuthorizationReference where persistence is required
• PlaybackEventReference where necessary

Use:

• Primary keys
• Foreign keys
• Composite indexes
• Unique constraints
• Version fields
• Timestamps
• Expiration metadata where appropriate

Identify high-growth data and ensure raw telemetry is not unnecessarily persisted transactionally.

────────────────────────────────────────

REDIS

Use Redis for:

• Active playback sessions
• Session heartbeats
• Concurrent stream limits
• Playback-state cache
• Queue synchronization
• Short-lived playback authorization state
• Rate limiting
• Distributed locks
• Processing coordination

Define:

• Key patterns
• TTL
• Invalidation
• Failure behavior

────────────────────────────────────────

SECURITY

Protect against:

• Playback-token theft
• Credential replay
• Unauthorized track access
• Cross-profile access
• Device spoofing
• Session hijacking
• Concurrent-stream bypass
• CDN URL reuse
• Rate-limit abuse

Implement:

• Short-lived credentials
• Resource binding
• Device binding where appropriate
• Authorization checks
• Rate limiting
• Audit/security events

────────────────────────────────────────

OBSERVABILITY

Instrument:

• Playback authorization
• Session creation
• Session heartbeat
• Session termination
• Queue operations
• Progress updates
• Audio processing
• Transcoding
• Manifest generation
• CDN authorization

Track:

• Authorization latency
• Playback start latency
• Session counts
• Session failures
• Processing throughput
• Processing failures
• Queue latency
• Worker utilization

Never log:

• Playback credentials
• Access tokens
• Payment credentials
• Secrets

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Playback authorization
• Entitlement evaluation
• Rights validation
• Device capability selection
• Concurrent-stream rules
• Session state machine
• Queue state
• Progress persistence
• Processing state machine

INTEGRATION TESTS

Test:

• PostgreSQL
• Redis
• Kafka
• BullMQ
• S3
• CDN authorization
• FFmpeg integration boundaries

MEDIA TESTS

Test:

• Valid audio
• Invalid audio
• Corrupt files
• Different codecs
• Different bitrates
• Multiple quality tiers
• Processing failures
• Retry
• Duplicate jobs

PLAYBACK TESTS

Test:

• Valid subscription
• Expired subscription
• Invalid rights
• Invalid region
• Unsupported device
• Concurrent-stream limit
• Expired playback token
• Duplicate authorization request
• Revoked device

QUEUE TESTS

Test:

• Concurrent updates
• Version conflict
• Device synchronization
• Reordering
• Duplicate events

PERFORMANCE TESTS

Test:

• Playback authorization throughput
• Concurrent sessions
• Heartbeat throughput
• Queue synchronization
• Audio-processing throughput

SECURITY TESTS

Test:

• Token replay
• Session hijacking
• Device spoofing
• Unauthorized playback
• Cross-profile access
• Concurrent-stream bypass

────────────────────────────────────────

DOCUMENTATION

Generate:

• Audio-processing architecture
• Transcoding architecture
• Rendition model
• Streaming architecture
• CDN integration
• Playback authorization flow
• Rights validation
• Entitlement integration
• Playback sessions
• Playback progress
• Queue synchronization
• Multi-device synchronization
• Device handoff
• Content protection boundaries
• API contracts
• Event contracts
• Queue definitions
• Database schema
• Failure handling
• Testing strategy

────────────────────────────────────────

PROJECT INDEX

Update the backend Project Index with:

• Audio-processing modules
• Transcoding modules
• Rendition modules
• Packaging modules
• Playback modules
• Playback-session modules
• Playback-progress modules
• Queue modules
• Device synchronization
• CDN integrations
• Database objects
• Migrations
• APIs
• Events
• Queues
• Workers
• Redis usage
• Security controls
• Tests
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 31

Audio-processing orchestration, validation, metadata extraction, and processing state.

BACKEND MILESTONE 32

FFmpeg integration, transcoding profiles, audio renditions, loudness analysis, and quality validation.

BACKEND MILESTONE 33

Audio packaging, HLS manifests, segment generation, object-storage integration, and CDN preparation.

BACKEND MILESTONE 34

Playback authorization, entitlement validation, rights validation, regional validation, and device capability selection.

BACKEND MILESTONE 35

Playback sessions, concurrent-stream controls, session heartbeat, and termination.

BACKEND MILESTONE 36

Playback progress, resume behavior, listening-history events, and high-frequency state handling.

BACKEND MILESTONE 37

Playback queue, queue versioning, optimistic concurrency, and multi-device synchronization.

BACKEND MILESTONE 38

Device handoff, remote playback controls, Redis coordination, and event propagation.

BACKEND MILESTONE 39

Security hardening, CDN authorization, failure recovery, observability, and operational reconciliation.

BACKEND MILESTONE 40

Integration, performance, concurrency, media, playback-security testing, and production hardening.

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

This volume covers:

• Audio processing
• Audio transcoding
• Audio rendition generation
• Loudness/quality validation
• Adaptive audio streaming
• HLS packaging
• Manifest generation
• CDN authorization
• Playback authorization
• Entitlement integration
• Rights validation
• Device capability validation
• Concurrent playback
• Playback sessions
• Playback progress
• Queue synchronization
• Multi-device playback synchronization
• Device handoff

Do not implement complete:

• Playlists
• User library
• Search
• Recommendations
• Radio
• Charts
• Podcasts
• Offline downloads
• Notifications
• Advertising
• Analytics
• Administration
• Moderation
• Frontend
• Mobile
• Infrastructure

Those belong to later implementation volumes.

────────────────────────────────────────

QUALITY BAR

Treat playback and media delivery as mission-critical infrastructure.

Assume:

• Tens of millions of concurrent listeners
• Massive CDN traffic
• High playback authorization volume
• Millions of audio assets
• Multiple audio qualities
• Multiple codecs
• Multiple device types
• Regional content rights
• Subscription-based access
• High availability requirements

Prioritize:

• Low playback latency
• Reliable authorization
• Correct entitlement enforcement
• Rights correctness
• Secure media access
• Idempotent processing
• Horizontal scaling
• Graceful failure
• CDN efficiency
• Observability
• Security
• Production readiness
