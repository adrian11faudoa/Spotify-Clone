You are operating in Senior Engineering Team Mode.

Build the complete production-grade QA, testing, security validation, performance validation, resilience validation, privacy validation, accessibility validation, infrastructure validation, and production-readiness system for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The testing system must validate the established backend, web frontend, mobile applications, infrastructure, media-processing systems, playback systems, subscriptions, payments, playlists, library, search, recommendations, podcasts, notifications, advertising, analytics, administration, security, and disaster-recovery architecture.

Do not redesign the approved architecture.

Do not implement unrelated application features.

Do not replace approved technologies without explicit technical justification.

────────────────────────────────────────

MISSION

Build a complete quality-engineering system covering:

• Unit testing
• Integration testing
• API testing
• Contract testing
• Event testing
• Queue testing
• Database testing
• Cache testing
• Search testing
• Recommendation testing
• Playback testing
• Audio-processing testing
• Media testing
• CDN testing
• Subscription testing
• Payment testing
• Webhook testing
• Entitlement testing
• Rights testing
• Playlist testing
• Library testing
• Synchronization testing
• Offline testing
• Podcast testing
• Notification testing
• Advertising testing
• Analytics testing
• Administration testing
• Moderation testing
• Web frontend testing
• Mobile testing
• Accessibility testing
• Security testing
• Abuse testing
• Performance testing
• Load testing
• Stress testing
• Soak testing
• Resilience testing
• Chaos testing
• Disaster-recovery testing
• Backup restoration testing
• Infrastructure testing
• CI/CD validation
• Production smoke testing
• Regression testing
• Release validation
• Production-readiness certification

The resulting QA system must validate:

• Functional correctness
• Security
• Privacy
• Availability
• Reliability
• Scalability
• Performance
• Recoverability
• Accessibility
• Maintainability
• Operational readiness

────────────────────────────────────────

TECHNOLOGY STACK

Backend:

• Node.js
• NestJS
• TypeScript
• PostgreSQL
• Prisma
• Redis
• Kafka or Redpanda
• BullMQ
• Elasticsearch/OpenSearch
• AWS S3
• CloudFront
• Stripe or approved payment provider
• FCM
• APNS

Frontend:

• Next.js
• React
• TypeScript

Mobile:

• React Native
• Expo
• TypeScript

Infrastructure:

• Docker
• Kubernetes
• Helm
• Terraform
• GitHub Actions

Observability:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Testing:

• Jest
• Supertest
• React Testing Library
• Playwright
• React Native Testing Library
• Detox or approved mobile E2E framework
• Appropriate load-testing tools
• Accessibility testing tools
• Security scanning tools

────────────────────────────────────────

TESTING PRINCIPLES

Use a layered test strategy.

Do not rely entirely on end-to-end testing.

Use:

• Unit tests for domain logic
• Integration tests for real dependencies
• Contract tests for service boundaries
• End-to-end tests for critical customer journeys
• Performance tests for scale
• Security tests for attack resistance
• Resilience tests for failure behavior

Tests must be deterministic whenever practical.

Avoid:

• Arbitrary sleeps
• Test-order dependencies
• Shared mutable test state
• Flaky network dependencies
• Real customer data
• Real payment credentials
• Production secrets

────────────────────────────────────────

TEST PYRAMID

UNIT TESTS

Broad coverage for:

• Authentication
• Authorization
• Entitlements
• Rights
• Subscription logic
• Payment rules
• Playlist rules
• Library rules
• Playback policies
• Recommendation rules
• Search rules
• Podcast rules
• Notification routing
• Advertising rules
• Moderation policies

INTEGRATION TESTS

Validate real integrations with:

• PostgreSQL
• Prisma
• Redis
• Kafka/Redpanda
• BullMQ
• OpenSearch/Elasticsearch
• S3
• Payment abstraction
• Notification providers

END-TO-END TESTS

Validate complete user workflows.

────────────────────────────────────────

IDENTITY TESTING

Validate:

• Registration
• Login
• Logout
• Email verification
• Password reset
• Password change
• Session refresh
• Session expiration
• Session revocation
• Device registration
• Device revocation

Security cases:

• Invalid credentials
• Credential stuffing
• Brute force
• Reset-token replay
• Session reuse
• Revoked-session access
• Account takeover attempts

────────────────────────────────────────

AUTHORIZATION TESTING

Validate:

• RBAC
• Resource ownership
• Profile isolation
• Artist isolation
• Label isolation
• Administrative permissions
• Subscription access
• Playback access
• Download access
• Private playlist access

Test:

• Horizontal privilege escalation
• Vertical privilege escalation
• IDOR
• Permission bypass
• Cross-profile access
• Cross-organization access

────────────────────────────────────────

SUBSCRIPTION TESTING

Test:

• Plan retrieval
• Plan eligibility
• Trial
• Subscription creation
• Upgrade
• Downgrade
• Renewal
• Cancellation
• Grace period
• Expiration
• Payment failure
• Recovery

Validate state transitions.

Verify subscription state is not incorrectly inferred from payment state.

────────────────────────────────────────

PAYMENT TESTING

Test:

• Payment intent
• Payment confirmation
• Authentication/3DS boundaries where applicable
• Success
• Failure
• Cancellation
• Timeout
• Refund
• Partial refund
• Full refund

Never use real card credentials.

────────────────────────────────────────

WEBHOOK TESTING

Test:

• Signature validation
• Duplicate events
• Replay
• Delayed events
• Out-of-order events
• Unknown events
• Malformed payloads
• Provider retries

Verify idempotency.

────────────────────────────────────────

ENTITLEMENT TESTING

Validate entitlement decisions for:

• Premium playback
• Free playback
• Offline downloads
• High-quality audio
• Family access
• Student access
• Regional content

Test:

• Subscription changes
• Expiration
• Grace period
• Payment failures
• Region changes
• Device revocation

────────────────────────────────────────

RIGHTS TESTING

Test:

• Territory restrictions
• Start dates
• End dates
• Subscription restrictions
• Platform restrictions
• Device restrictions
• Rights expiration
• Content takedown

Verify that rights are enforced during playback authorization.

────────────────────────────────────────

CATALOG TESTING

Test:

• Artist
• Album
• Release
• Track
• Track versions
• Credits
• Genres
• Tags
• Localization
• Artwork
• Audio assets
• Publication state

Validate:

• Draft
• Submission
• Processing
• Review
• Approval
• Scheduling
• Publication
• Unpublication
• Archival

────────────────────────────────────────

MEDIA TESTING

Test:

• Upload
• Direct object storage upload
• File validation
• Metadata extraction
• Loudness analysis
• Codec detection
• Transcoding
• Rendition generation
• Packaging
• Manifest creation
• CDN publication
• Cleanup

Test:

• Corrupt files
• Unsupported codecs
• Invalid containers
• Oversized files
• Malicious uploads
• Interrupted uploads
• Duplicate jobs
• Worker failures

────────────────────────────────────────

AUDIO QUALITY TESTING

Validate:

• Duration
• Sample rate
• Channels
• Codec
• Bitrate
• Loudness
• Peak level
• Corruption

Verify each supported rendition is technically valid and corresponds to the expected source asset.

────────────────────────────────────────

PLAYBACK AUTHORIZATION TESTING

Test the full authorization path:

User
→ Device
→ Subscription
→ Entitlement
→ Rights
→ Region
→ Content
→ Playback authorization

Test:

• Valid playback
• Expired entitlement
• Expired rights
• Unsupported region
• Unsupported device
• Revoked device
• Concurrent stream limit
• Expired playback credential
• Replayed credential
• Unauthorized track

────────────────────────────────────────

PLAYBACK SESSION TESTING

Test:

• Session creation
• Heartbeat
• Pause
• Resume
• Stop
• Expiration
• Device switching
• Concurrent sessions
• Session conflict
• Session cleanup

Test stale-session behavior.

────────────────────────────────────────

PLAYBACK PERFORMANCE TESTING

Measure:

• Playback authorization latency
• Manifest retrieval
• Segment retrieval
• Session creation
• Session heartbeat
• Playback-state synchronization

Measure:

• p50
• p95
• p99
• Throughput
• Error rate

────────────────────────────────────────

QUEUE TESTING

Test:

• Add
• Remove
• Reorder
• Clear
• Shuffle
• Repeat
• Versioning
• Concurrent edits
• Multi-device synchronization
• Conflict resolution

Test:

• Duplicate mutation
• Stale version
• Offline mutation
• Retry after timeout

────────────────────────────────────────

PLAYLIST TESTING

Test:

• Creation
• Update
• Delete
• Visibility
• Collaboration
• Invitation
• Ownership
• Ordering
• Reordering
• Versioning
• Snapshot/recovery

Security:

• Private playlist disclosure
• Collaborator escalation
• Ownership takeover
• Invitation replay

────────────────────────────────────────

LIBRARY TESTING

Test:

• Like/unlike
• Save/unsave album
• Save/unsave playlist
• Follow/unfollow artist
• Follow/unfollow podcast
• Recently played
• Listening history

Verify:

• No duplicates
• Correct profile isolation
• Correct ordering
• Correct pagination

────────────────────────────────────────

SYNC TESTING

Test synchronization across:

• Web
• iOS
• Android
• Multiple devices

Test:

• Online mutation
• Offline mutation
• Reconnect
• Duplicate mutation
• Stale mutation
• Version conflict
• Partial synchronization
• Cursor recovery

Verify eventual convergence.

────────────────────────────────────────

OFFLINE TESTING

Test:

• Download authorization
• Download
• Pause
• Resume
• Cancel
• Retry
• Offline playback
• License validation
• License expiration
• License renewal
• Device revocation
• Content-right expiration
• Subscription expiration
• Storage exhaustion

Test:

• No network
• Intermittent network
• Weak network
• Wi-Fi/cellular transitions

Offline mode must fail securely.

────────────────────────────────────────

SEARCH TESTING

Test:

• Full-text search
• Prefix search
• Autocomplete
• Suggestions
• Typo tolerance
• Filters
• Facets
• Ranking
• Region filtering
• Explicit-content filtering
• Rights filtering
• Search pagination

Test:

• Zero results
• Search failure
• Index failure
• Stale index
• Reindexing
• Alias switching

────────────────────────────────────────

RECOMMENDATION TESTING

Test:

• Candidate generation
• Ranking
• Personalization
• Diversity
• Novelty
• Trending
• Similar content
• New releases
• Fallback behavior

Verify recommendations exclude unauthorized or unavailable content.

Test recommendation-cache failures.

────────────────────────────────────────

RADIO TESTING

Test:

• Track radio
• Artist radio
• Genre radio
• Personalized radio
• Seed
• Session
• Queue generation
• Deduplication
• Candidate exhaustion
• Retry
• Session expiration

────────────────────────────────────────

CHART TESTING

Test:

• Global charts
• Regional charts
• Genre charts
• Trending
• Daily
• Weekly
• Monthly
• Rolling windows
• Historical snapshots

Validate anti-manipulation logic.

────────────────────────────────────────

PODCAST TESTING

Test:

• Show creation
• Episode creation
• Publication
• Search
• Follow
• Playback
• Progress
• Downloads
• Notifications
• Recommendations

Verify podcast state remains separate where domain rules differ from music.

────────────────────────────────────────

NOTIFICATION TESTING

Test:

• FCM
• APNS
• Device token registration
• Token rotation
• Push delivery
• In-app delivery
• Email
• Notification preferences
• Deduplication
• Retry
• Provider failure
• Deep links

Verify security-critical notifications follow their required delivery policy.

────────────────────────────────────────

ADVERTISING TESTING

Test:

• Campaign creation
• Campaign state
• Targeting
• Scheduling
• Frequency caps
• Budget limits
• Creative validation
• Ad decisioning
• Impression
• Completion
• Click where applicable

Test:

• Duplicate events
• Fraud
• Redis failure
• Ad-decision failure

Verify advertising failures do not corrupt playback.

────────────────────────────────────────

ANALYTICS TESTING

Validate:

• Event schemas
• Event ingestion
• Kafka publishing
• Consumer processing
• Aggregation
• Deduplication
• Retention
• Reporting

Test:

• Playback telemetry
• Search telemetry
• Recommendation telemetry
• Subscription events
• Advertising events
• Notification events

Analytics failures must not block transactional operations.

────────────────────────────────────────

ADMINISTRATION TESTING

Test:

• User management
• Content management
• Rights management
• Subscription management
• Payment investigation
• Advertising management
• Moderation
• Feature flags
• Configuration
• Audit

Sensitive actions must require correct permissions.

────────────────────────────────────────

MODERATION TESTING

Test:

• Report creation
• Case assignment
• Investigation
• Action
• Appeal
• Resolution
• Reopening
• Audit

Test unauthorized access to moderation evidence.

────────────────────────────────────────

WEB FRONTEND TESTING

CUSTOMER:

• Registration
• Login
• Search
• Discovery
• Artist
• Album
• Track
• Playback
• Queue
• Playlist
• Library
• Subscription
• Podcast
• Notifications

CREATOR:

• Login
• Content
• Release workflow
• Analytics
• Team management

ADMIN:

• Login
• Users
• Content
• Rights
• Moderation
• Advertising
• Configuration
• Feature flags
• Audit

────────────────────────────────────────

MOBILE TESTING

Test on iOS and Android:

• Registration
• Login
• Search
• Discovery
• Playback
• Background playback
• Lock-screen controls
• Bluetooth
• Queue
• Playlist
• Library
• Download
• Offline playback
• Podcasts
• Subscriptions
• Notifications
• Deep links
• Device switching

Test across supported device classes and operating-system versions.

────────────────────────────────────────

ACCESSIBILITY TESTING

WEB

Target WCAG 2.2 AA.

Test:

• Keyboard navigation
• Screen readers
• Focus management
• Contrast
• Forms
• Player
• Sliders
• Dialogs
• Tables
• Charts

MOBILE

Test:

• VoiceOver
• TalkBack
• Dynamic Type
• Large text
• Accessibility labels
• Touch targets
• Player controls

────────────────────────────────────────

SECURITY TESTING

Test:

• Authentication
• Authorization
• IDOR
• Privilege escalation
• Session attacks
• Token replay
• Credential stuffing
• XSS
• CSRF where applicable
• SQL injection
• SSRF where applicable
• Path traversal
• Malicious uploads
• Secret exposure
• Webhook spoofing
• Playback credential theft
• Download abuse
• Subscription abuse
• Payment abuse
• Ad fraud
• Data leakage

────────────────────────────────────────

PRIVACY TESTING

Validate that:

• Private playlists remain private
• Listening history remains private
• Recommendation signals remain private
• Profile data is isolated
• Subscription information is protected
• Device information is appropriately restricted
• Analytics data is properly scoped
• Creator analytics only expose authorized data

Test data-export and account-deletion workflows where implemented.

────────────────────────────────────────

PERFORMANCE TESTING

Create benchmarks for:

• Authentication
• Catalog retrieval
• Search
• Recommendations
• Playback authorization
• Playlist reads
• Library reads
• Queue synchronization
• Subscription lookup
• Notification retrieval
• API requests
• Event processing
• Audio processing

Measure:

• p50
• p95
• p99
• Throughput
• Error rate
• CPU
• Memory
• Database load
• Redis load

────────────────────────────────────────

LOAD TESTING

Simulate:

• Normal traffic
• Peak traffic
• Burst traffic
• Major content release
• Marketing event
• High-concurrency playback
• Large search spike
• Recommendation spike

Load-test:

• Authentication
• Search
• Playback authorization
• Playlists
• Library
• Subscriptions
• Notifications
• Event ingestion

────────────────────────────────────────

STRESS TESTING

Push systems beyond expected capacity.

Find limits for:

• API throughput
• Playback authorization
• Database
• Redis
• Kafka
• Search
• Recommendation services
• Media workers
• Notification systems

Document:

• Saturation point
• Failure mode
• Recovery behavior
• Scaling strategy

────────────────────────────────────────

SOAK TESTING

Run long-duration tests for:

• API
• Workers
• Playback services
• Search
• Redis
• Kafka consumers
• Media processing

Look for:

• Memory leaks
• Connection leaks
• Queue growth
• Cache growth
• Worker instability
• Log growth
• Storage exhaustion

────────────────────────────────────────

RESILIENCE TESTING

Inject failures into:

• PostgreSQL
• Redis
• Kafka
• BullMQ workers
• OpenSearch
• S3
• CDN
• Payment providers
• Notification providers
• Recommendation services
• Media-processing workers
• Kubernetes nodes
• Availability zones
• Regions

Verify:

• Detection
• Timeout
• Retry
• Fallback
• Degraded operation
• Recovery
• Reconciliation

────────────────────────────────────────

CHAOS TESTING

Define controlled experiments for:

• Pod termination
• Node termination
• Network latency
• Packet loss
• PostgreSQL failover
• Redis failover
• Kafka broker failure
• Search failure
• Media-worker failure
• Regional outage

Begin in non-production environments.

Promote validated experiments only under controlled operational procedures.

────────────────────────────────────────

DISASTER RECOVERY TESTING

Test:

• PostgreSQL restoration
• Point-in-time recovery
• S3 recovery
• Search restoration
• Kafka recovery
• Redis recovery
• EKS reconstruction
• Terraform reconstruction
• Regional failover

Measure:

• Actual RTO
• Actual RPO

Compare against approved targets.

────────────────────────────────────────

BACKUP TESTING

Validate restoration of:

• PostgreSQL backups
• S3 replicated objects
• Search snapshots
• Terraform state
• Critical configuration

Do not consider backups reliable without successful restoration tests.

────────────────────────────────────────

INFRASTRUCTURE TESTING

Validate:

• Terraform
• Helm
• Kubernetes
• Docker
• IAM
• Security groups
• NetworkPolicies
• WAF
• Autoscaling
• Load balancing
• TLS
• Backup policies
• Disaster-recovery infrastructure

────────────────────────────────────────

CI/CD QUALITY GATES

PULL REQUEST:

• Formatting
• Linting
• Type checking
• Unit tests
• Relevant integration tests
• Contract tests
• Security scans
• Secret scans
• Dependency scans
• Docker validation
• Terraform validation
• Helm validation

RELEASE:

• Build
• Integration
• E2E smoke tests
• Container scanning
• Infrastructure validation
• Deployment health
• Post-deployment smoke tests

Production deployment must require appropriate approvals.

────────────────────────────────────────

PRODUCTION SMOKE TESTS

After every production deployment validate non-destructively:

• Web availability
• API health
• Authentication
• Catalog
• Search
• Playback authorization
• Playlist
• Library
• Subscription
• Podcast
• Notifications
• Creator APIs
• Admin APIs

Also validate:

• PostgreSQL
• Redis
• Kafka
• Search
• Object storage

────────────────────────────────────────

OBSERVABILITY TESTING

Verify that controlled failures generate the expected:

• Metrics
• Logs
• Traces
• Alerts

Validate:

• Request IDs
• Correlation IDs
• Trace IDs
• Error rates
• Latency metrics
• Queue metrics
• Playback metrics
• Search metrics
• Subscription metrics
• Infrastructure metrics

────────────────────────────────────────

SLO / SLI VALIDATION

Define and validate SLOs for:

• Authentication
• Catalog
• Search
• Playback authorization
• Playback availability
• Playlists
• Library
• Subscriptions
• Payments
• Notifications
• Media processing
• Podcast availability

For each define:

• SLI
• Measurement source
• Target
• Alert threshold
• Error budget

────────────────────────────────────────

DATA QUALITY

Validate:

• Referential integrity
• Financial consistency
• Subscription consistency
• Entitlement consistency
• Rights consistency
• Media consistency
• Search consistency
• Event consistency
• Playlist consistency
• Library consistency
• Analytics consistency
• Audit integrity

Create reconciliation tests.

────────────────────────────────────────

TEST DATA STRATEGY

Provide deterministic factories for:

• Users
• Profiles
• Devices
• Artists
• Albums
• Tracks
• Releases
• Playlists
• Library items
• Subscriptions
• Payments
• Entitlements
• Rights
• Podcasts
• Notifications
• Ad campaigns

Do not use unnecessary real customer data.

Provide:

• Small fixtures
• Medium datasets
• Large-scale synthetic datasets

────────────────────────────────────────

ENVIRONMENT STRATEGY

Define test environments for:

• Local
• Development
• Integration
• Staging
• Performance
• Security
• Disaster recovery

Use production-like staging infrastructure where practical.

────────────────────────────────────────

REGRESSION SUITE

Maintain regression coverage for:

• Authentication
• Catalog
• Media
• Playback
• Subscriptions
• Payments
• Entitlements
• Playlists
• Library
• Search
• Recommendations
• Radio
• Charts
• Podcasts
• Notifications
• Advertising
• Analytics
• Administration
• Moderation

Prevent known regressions from reaching production.

────────────────────────────────────────

RELEASE CERTIFICATION

Define objective release criteria.

A release is production-ready only when:

• Required tests pass
• No blocking critical defects remain
• Security checks pass
• Performance budgets pass
• Contract compatibility passes
• Infrastructure validation passes
• Smoke tests pass
• Backup validation is current
• Monitoring is operational
• Rollback is available
• Required approvals are complete
• Known risks are documented

────────────────────────────────────────

DOCUMENTATION

Generate:

• QA architecture
• Test strategy
• Test matrix
• Unit-test standards
• Integration-test standards
• Contract-test standards
• API-testing standards
• Event-testing standards
• Playback-testing strategy
• Media-testing strategy
• Offline-testing strategy
• Search-testing strategy
• Recommendation-testing strategy
• Security-testing guide
• Privacy-testing guide
• Accessibility-testing guide
• Performance-testing guide
• Load-testing guide
• Stress-testing guide
• Soak-testing guide
• Resilience-testing guide
• Chaos-testing guide
• Disaster-recovery testing guide
• Infrastructure-testing guide
• CI/CD quality gates
• Production smoke testing
• Release certification
• Test-data strategy
• Environment strategy

────────────────────────────────────────

PROJECT INDEX

Maintain the QA Project Index.

Track:

• Test suites
• Unit tests
• Integration tests
• Contract tests
• API tests
• Event tests
• Queue tests
• Database tests
• Media tests
• Playback tests
• Search tests
• Recommendation tests
• Playlist tests
• Library tests
• Offline tests
• Podcast tests
• Notification tests
• Advertising tests
• Analytics tests
• Frontend tests
• Mobile tests
• Accessibility tests
• Security tests
• Privacy tests
• Abuse tests
• Performance tests
• Load tests
• Stress tests
• Soak tests
• Resilience tests
• Chaos tests
• Disaster-recovery tests
• Backup tests
• Infrastructure tests
• Smoke tests
• Quality gates
• SLO/SLI
• Coverage
• Known defects
• Known risks
• Production readiness
• Generated files
• Remaining work
• Current milestone

────────────────────────────────────────

IMPLEMENTATION MILESTONES

QA MILESTONE 1

Test infrastructure, configuration, fixtures, factories, mocks, shared utilities, and coverage reporting.

QA MILESTONE 2

Identity, authentication, authorization, profiles, devices, subscriptions, payments, webhooks, and entitlements.

QA MILESTONE 3

Catalog, media processing, rights, availability, playback authorization, playback sessions, queue, and device synchronization.

QA MILESTONE 4

Playlists, library, listening history, offline synchronization, search, recommendations, radio, and charts.

QA MILESTONE 5

Podcasts, notifications, advertising, analytics, reporting, moderation, and administration.

QA MILESTONE 6

Web frontend unit, component, integration, accessibility, performance, and E2E testing.

QA MILESTONE 7

Mobile unit, component, integration, offline, accessibility, notification, playback, and E2E testing.

QA MILESTONE 8

Security testing, privacy testing, authorization testing, seller/organization isolation, abuse testing, and fraud testing.

QA MILESTONE 9

Performance, load, stress, soak, capacity, and scalability testing.

QA MILESTONE 10

Resilience, chaos, backup restoration, disaster recovery, infrastructure validation, CI/CD validation, production smoke tests, final release certification, and Project Index completion.

Each milestone should contain approximately 20–40 files where practical.

Every milestone must produce measurable and verifiable results.

────────────────────────────────────────

OUTPUT FORMAT

For every generated file provide:

1. Exact file path
2. Complete file contents

Never truncate code.

Never summarize implementation instead of generating it.

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

This prompt is dedicated to:

• QA
• Testing
• Security validation
• Privacy validation
• Abuse validation
• Performance validation
• Scalability validation
• Resilience validation
• Accessibility validation
• Infrastructure validation
• Disaster-recovery validation
• Backup validation
• CI/CD quality gates
• Production smoke testing
• Regression testing
• Release certification
• Production readiness

Do not redesign the approved architecture.

Do not implement unrelated product features.

────────────────────────────────────────

FINAL QUALITY BAR

The completed music streaming platform must provide objective evidence that it can operate as a production-grade global service supporting:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Massive audio delivery
• Large search traffic
• Large recommendation traffic
• Large playlist and library volumes
• High subscription and payment traffic
• Podcasts
• Advertising
• Analytics
• Multiple devices
• Offline playback
• Global rights
• Multi-region deployment
• High availability
• Disaster recovery
• Strong security
• Strict privacy

The final system must demonstrate:

• Correctness
• Security
• Privacy
• Performance
• Scalability
• Reliability
• Resilience
• Observability
• Recoverability
• Accessibility
• Maintainability
• Production readiness
