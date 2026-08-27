You are operating in Senior Engineering Team Mode.

Build the production-ready backend for podcasts, episodes, audiobook extensibility, notifications, customer communications, advertising, analytics, reporting, moderation, administration, feature flags, system configuration, and audit for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must follow the approved Spotify-like architecture, domain boundaries, database ownership, authentication model, authorization model, catalog architecture, playback architecture, subscription architecture, playlist architecture, library architecture, search architecture, recommendation architecture, event architecture, queue architecture, security model, and Project Index.

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

• Podcasts
• Podcast shows
• Podcast episodes
• Podcast categories
• Podcast creators
• Podcast follows
• Podcast playback progress
• Podcast downloads where supported
• Podcast search integration
• Podcast recommendations integration
• Audiobook extensibility
• Notifications
• Notification preferences
• Push notifications
• Email notifications
• In-app notifications
• Customer communications
• Advertising
• Ad campaigns
• Ad creatives
• Ad inventory
• Ad decisioning
• Ad impressions
• Ad completion events
• Analytics event ingestion
• Analytics aggregation
• Reporting
• Moderation
• Administration
• Feature flags
• Dynamic system configuration
• Audit
• Privacy workflows

The implementation must support:

• Hundreds of millions of users
• Millions of podcast episodes
• Large notification volumes
• Large advertising event volumes
• Large analytics event volumes
• Global audiences
• Multiple languages
• Regional availability
• Free/ad-supported plans
• Premium plans
• Strict privacy
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

Search:

• Elasticsearch or OpenSearch

Object Storage:

• AWS S3-compatible object storage

CDN:

• CloudFront or equivalent CDN

Notifications:

• Firebase Cloud Messaging
• Apple Push Notification Service
• Email provider abstraction

Payments:

• Stripe or approved payment abstraction

Observability:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Testing:

• Jest
• Supertest
• Integration and contract testing tools

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

Keep business logic outside controllers.

Use repositories for persistence.

Use DTOs for API contracts.

Use centralized validation.

Use centralized error handling.

Use structured logging.

Use idempotency for notifications, advertisements, reports, and administrative mutations.

────────────────────────────────────────

DOMAIN OWNERSHIP

Maintain explicit boundaries between:

• Podcasts
• Podcast creators
• Podcast shows
• Podcast episodes
• Podcast playback
• Podcast follows
• Audiobook extensibility
• Notifications
• Customer communications
• Advertising
• Analytics
• Reporting
• Moderation
• Administration
• Feature flags
• System configuration
• Audit

Do not combine:

• Podcast content with music catalog entities where different lifecycle rules are required
• Notification state with business state
• Advertising delivery with subscription state
• Analytics with transactional storage
• Administrative configuration with authorization logic

────────────────────────────────────────

PODCAST DOMAIN

Implement:

• Podcast show
• Podcast creator
• Podcast host
• Podcast episode
• Categories
• Genres
• Languages
• Artwork
• Descriptions
• Publication state
• Release scheduling
• Explicit-content metadata
• Availability
• Follows
• Playback progress

Support show states:

• Draft
• Submitted
• Review
• Approved
• Published
• Suspended
• Archived

────────────────────────────────────────

PODCAST CREATOR

Support:

• Creator account
• Creator profile
• Creator staff
• Show ownership
• Content management
• Analytics access
• Publishing permissions

Creators must only access authorized shows and episodes.

────────────────────────────────────────

PODCAST EPISODES

Implement:

• Episode creation
• Episode metadata
• Duration
• Audio asset reference
• Artwork
• Description
• Episode number
• Season
• Explicit-content state
• Publication state
• Availability
• Release date

Support:

• Draft
• Processing
• Scheduled
• Published
• Unpublished
• Archived

────────────────────────────────────────

PODCAST PLAYBACK

Integrate podcasts with the approved playback architecture.

Support:

• Playback authorization
• Episode entitlement
• Playback progress
• Resume position
• Completion
• Skip
• Recently played
• Download eligibility where supported

Do not duplicate the entire music playback engine.

Reuse the established playback abstractions where possible.

────────────────────────────────────────

PODCAST FOLLOWS

Implement:

• Follow show
• Unfollow show
• Check follow
• List followed shows

Publish events for:

• PodcastFollowed
• PodcastUnfollowed

Use uniqueness constraints to prevent duplicate follows.

────────────────────────────────────────

PODCAST SEARCH

Integrate:

• Shows
• Episodes
• Creators
• Categories

with the established search architecture.

Respect:

• Publication
• Region
• Explicit-content restrictions
• Privacy
• Moderation state

────────────────────────────────────────

PODCAST RECOMMENDATIONS

Provide signals to the established recommendation architecture.

Events may include:

• PodcastViewed
• PodcastFollowed
• EpisodePlayed
• EpisodeCompleted
• EpisodeSkipped

Recommendations must respect availability and content restrictions.

────────────────────────────────────────

AUDIOBOOK EXTENSIBILITY

Create bounded architectural interfaces for future audiobook support.

Support conceptual entities:

• Audiobook
• Chapter
• Narrator
• Author
• Series
• Playback progress
• Entitlement
• Rights
• Availability
• Download

Do not implement unnecessary audiobook complexity.

Do not mix audiobook accounting with standard music subscription rules unless explicitly required.

────────────────────────────────────────

NOTIFICATION DOMAIN

Implement:

• Notification creation
• Notification routing
• Notification templates
• Notification preferences
• Notification channels
• Notification delivery
• Notification read state
• Notification deduplication
• Notification scheduling

Channels:

• Push
• Email
• In-app

────────────────────────────────────────

NOTIFICATION TYPES

Support:

• New release
• Followed artist release
• Playlist update
• Podcast episode release
• Subscription event
• Payment failure
• Download completion
• Security event
• Account event
• Recommendation
• System notification

Security-critical notifications must remain protected by backend rules.

────────────────────────────────────────

NOTIFICATION PREFERENCES

Support:

• Global settings
• Channel settings
• Category settings
• Promotional settings
• Security notifications
• Artist notifications
• Podcast notifications
• Subscription notifications

Preferences must be profile/account scoped according to the approved architecture.

────────────────────────────────────────

PUSH NOTIFICATIONS

Implement:

• Device token registration
• FCM
• APNS
• Token rotation
• Invalid-token cleanup
• Retry
• Backoff
• Delivery state
• Provider failures

Support multiple devices.

Avoid duplicate delivery when deterministic deduplication is possible.

────────────────────────────────────────

EMAIL NOTIFICATIONS

Implement an email-provider abstraction.

Support:

• Templates
• Localization
• Retry
• Delivery status
• Failure
• Bounce handling where provider capabilities allow it

Do not hard-code a single email vendor into domain logic.

────────────────────────────────────────

IN-APP NOTIFICATIONS

Implement:

• Notification list
• Read state
• Unread count
• Mark read
• Mark all read
• Categories
• Deep-link targets
• Expiration

Persist notification state authoritatively in PostgreSQL.

Use Redis only for acceleration.

────────────────────────────────────────

NOTIFICATION QUEUES

Use BullMQ for:

• Push delivery
• Email delivery
• Notification retry
• Scheduled notifications
• Notification cleanup
• Token cleanup

Every worker must support:

• Retry
• Backoff
• Timeout
• Idempotency
• Dead-letter handling
• Metrics
• Structured logging

────────────────────────────────────────

CUSTOMER COMMUNICATIONS

Support approved communications such as:

• System messages
• Creator notifications
• Subscription communications
• Account security
• Service announcements

Do not create an uncontrolled generic messaging system.

Customer-to-seller messaging belongs to another project architecture.

────────────────────────────────────────

ADVERTISING DOMAIN

Implement a production advertising foundation for ad-supported plans.

Support:

• Advertiser
• Campaign
• Ad group
• Creative
• Targeting
• Placement
• Audio ad
• Impression
• Completion
• Click where applicable
• Frequency cap
• Budget
• Schedule
• Campaign status

────────────────────────────────────────

ADVERTISING CAMPAIGN LIFECYCLE

Support:

• Draft
• Review
• Approved
• Scheduled
• Active
• Paused
• Completed
• Rejected
• Archived

Define state ownership and authorization.

────────────────────────────────────────

AD CREATIVES

Support:

• Audio creatives
• Companion assets where appropriate
• Metadata
• Duration
• Destination
• Content validation
• Processing state

Validate:

• File type
• Duration
• Size
• Policy compliance
• Malware boundary

────────────────────────────────────────

AD TARGETING

Support architecture for:

• Region
• Language
• Device
• Subscription tier
• Context
• Time window
• Content category
• Frequency

Do not use sensitive personal information for targeting unless explicitly permitted and appropriately governed.

────────────────────────────────────────

AD DECISIONING

Design a low-latency ad-decisioning boundary.

Support:

• Eligible campaign selection
• Frequency capping
• Budget checks
• Targeting
• Consent
• Content policy
• Regional availability
• Campaign pacing

Ad decisioning must not block core user authentication, library, or account functions.

────────────────────────────────────────

AD DELIVERY FAILURE

Define fallback behavior when:

• Ad decisioning unavailable
• Campaign unavailable
• Creative unavailable
• Tracking unavailable

Follow product policy for whether playback:

• Continues without ad
• Retries
• Uses fallback inventory

Do not allow an ad-system failure to corrupt playback state.

────────────────────────────────────────

AD EVENT TRACKING

Publish:

• AdRequested
• AdSelected
• AdStarted
• AdImpression
• AdCompleted
• AdSkipped
• AdClicked where applicable
• AdFailed

Events must be idempotently processed for billing/reporting purposes.

────────────────────────────────────────

FREQUENCY CAPPING

Implement frequency-capping state.

Support caps by:

• User/profile
• Device
• Campaign
• Time window

Use Redis for low-latency counters where appropriate, with a durable analytics trail.

Define behavior during Redis failure.

────────────────────────────────────────

ANALYTICS DOMAIN

Implement analytics ingestion foundations.

Support events for:

• Playback
• Search
• Discovery
• Recommendations
• Playlist activity
• Likes
• Follows
• Downloads
• Subscription
• Payments
• Advertising
• Notifications
• Podcasts

Analytics ingestion must be asynchronous.

Do not block customer requests on analytical processing.

────────────────────────────────────────

ANALYTICS PIPELINE

Design:

Event
→ Kafka
→ Validation
→ Processing
→ Aggregation
→ Analytical storage
→ Reporting

Separate:

• Operational state
• Event stream
• Aggregated metrics
• Long-term analytical storage

────────────────────────────────────────

ANALYTICS RETENTION

Define retention for:

• Raw events
• Aggregated metrics
• User-level analytics
• Product metrics
• Creator analytics
• Advertising metrics

Respect privacy requirements.

────────────────────────────────────────

CREATOR ANALYTICS

Support analytics such as:

• Streams
• Unique listeners
• Listening hours
• Completion
• Saves
• Follows
• Geography where permitted
• Demographics only where legitimately available and governed
• Release performance
• Playlist appearances

Creators must never see data belonging to unrelated creators.

────────────────────────────────────────

BUSINESS ANALYTICS

Support:

• MAU
• DAU
• Retention
• Conversion
• Churn
• ARPU
• Subscription revenue
• Ad revenue
• Ad impressions
• Ad completion
• Listening hours
• Playback quality

Do not calculate high-volume business dashboards directly from operational tables if the workload would harm transactional systems.

────────────────────────────────────────

REPORTING

Implement asynchronous reporting.

Support:

• Report type
• Parameters
• Filters
• Date ranges
• Generation status
• Progress
• Completion
• Failure
• Secure download
• Expiration

Use BullMQ.

Store generated reports in secure object storage.

────────────────────────────────────────

MODERATION

Implement moderation for:

• Artist profiles
• Podcast shows
• Podcast episodes
• Playlists where applicable
• Ad creatives
• User-generated content
• Malicious uploads

Support:

• Reports
• Cases
• Assignment
• Investigation
• Action
• Appeal
• Resolution
• Audit

────────────────────────────────────────

MODERATION STATES

Support:

• Open
• Assigned
• Investigating
• Action Required
• Action Taken
• Appealed
• Resolved
• Reopened
• Closed

Store:

• Policy
• Subject
• Priority
• Evidence references
• Action
• Actor
• Timestamp

────────────────────────────────────────

ADMINISTRATION

Implement controlled administrative backend APIs for:

• Users
• Profiles
• Subscriptions
• Payments
• Content
• Artists
• Labels
• Podcasts
• Advertising
• Moderation
• Reports
• Analytics
• Feature flags
• System configuration
• Audit

Administrative actions must respect granular permissions.

────────────────────────────────────────

SENSITIVE ADMINISTRATIVE OPERATIONS

Require stronger authorization for:

• Subscription changes
• Refunds
• Financial adjustments
• Content removal
• Rights overrides
• Campaign activation
• Feature-flag kill switches
• System configuration changes
• Permission changes

Support:

• Reason capture
• Confirmation
• Re-authentication where required
• Audit trail
• Dual approval where appropriate

────────────────────────────────────────

FEATURE FLAGS

Implement:

• Global rollout
• Percentage rollout
• User/profile targeting
• Region targeting
• Plan targeting
• Device targeting
• App version targeting
• Kill switches
• Experiments

Support:

• Evaluation
• Caching
• Propagation
• Ownership
• Audit
• Expiration
• Cleanup

Feature flags must not replace authorization.

────────────────────────────────────────

SYSTEM CONFIGURATION

Implement typed dynamic configuration.

Support settings for:

• Recommendation thresholds
• Notification limits
• Playback limits
• Trial configuration
• Subscription policy
• Advertising controls
• Moderation thresholds
• Rate limits
• Content policies
• Feature defaults

Configurations must be:

• Typed
• Validated
• Versioned
• Audited
• Rollback-capable

Never allow arbitrary executable configuration.

────────────────────────────────────────

AUDIT

Implement immutable audit records.

Audit:

• Administrative actions
• Subscription changes
• Financial operations
• Content moderation
• Rights actions
• Advertising actions
• Feature flags
• System configuration
• Permission changes
• Privacy requests

Audit records include:

• Actor
• Role
• Action
• Resource
• Resource ID
• Reason
• Request ID
• Correlation ID
• Timestamp
• Result

Never store secrets.

────────────────────────────────────────

PRIVACY REQUESTS

Implement backend foundations for:

• Data export
• Data access request
• Deletion request
• Retention enforcement

Separate:

• User-owned data
• Analytics data
• Financial records
• Audit records
• Legal-retention data

Do not delete mandatory financial/audit records merely because an account deletion request exists.

────────────────────────────────────────

EVENTS

Publish:

PODCASTS

• PodcastCreated
• PodcastUpdated
• EpisodeCreated
• EpisodePublished
• EpisodeUnpublished
• PodcastFollowed
• PodcastUnfollowed
• EpisodePlayed
• EpisodeCompleted

NOTIFICATIONS

• NotificationCreated
• NotificationQueued
• NotificationDelivered
• NotificationFailed
• NotificationRead

ADVERTISING

• CampaignCreated
• CampaignApproved
• CampaignActivated
• CampaignPaused
• AdSelected
• AdImpression
• AdCompleted
• AdFailed

MODERATION

• ReportCreated
• ModerationCaseOpened
• ModerationActionTaken
• AppealSubmitted
• AppealResolved

ADMINISTRATION

• AdministrativeActionTaken
• FeatureFlagChanged
• SystemConfigurationChanged
• AuditLogCreated

PRIVACY

• DataExportRequested
• DataExportCompleted
• DataDeletionRequested
• DataDeletionCompleted

Events must only contain information required by consumers.

────────────────────────────────────────

DATABASE

Implement Prisma models and migrations for:

• Podcast
• PodcastCreator
• PodcastMember
• PodcastEpisode
• PodcastCategory
• PodcastLocalization
• PodcastFollow
• PodcastPlaybackProgress
• AudiobookReference where appropriate
• Notification
• NotificationPreference
• NotificationDelivery
• PushToken
• Advertiser
• AdCampaign
• AdGroup
• AdCreative
• AdTargetingRule
• AdImpression
• AdDeliveryReference
• ModerationCase
• ModerationAction
• ModerationAppeal
• Report
• RiskEvaluationReference where appropriate
• FeatureFlag
• FeatureFlagRule
• SystemConfiguration
• SystemConfigurationVersion
• AuditLog
• PrivacyRequest
• DataExportJob
• DataDeletionJob
• ReportJob

Use:

• Primary keys
• Foreign keys
• Unique constraints
• Composite indexes
• Status constraints
• Version fields
• Effective timestamps
• Expiration timestamps

Do not store raw high-volume analytics events in ordinary transactional tables.

────────────────────────────────────────

API

Implement production-ready APIs.

PODCASTS

• Create
• Get
• Update
• Publish
• Unpublish
• Follow
• Unfollow
• List followed shows

EPISODES

• Create
• Get
• Update
• Publish
• Unpublish
• Progress

NOTIFICATIONS

• List
• Mark read
• Mark all read
• Preferences
• Register device token

ADVERTISING

• Campaigns
• Creatives
• Targeting
• Reporting
• Campaign state

REPORTING

• Create report
• Get report
• Download report

ADMINISTRATION

• Manage content
• Manage subscriptions
• Manage advertising
• Manage moderation
• Manage feature flags
• Manage configuration
• Search audit

PRIVACY

• Request export
• Get export status
• Request deletion
• Get deletion status

Every endpoint must implement:

• Authentication
• Authorization
• Profile scoping
• Validation
• Rate limiting
• Idempotency where appropriate
• OpenAPI documentation
• Consistent errors
• Audit where required

────────────────────────────────────────

SECURITY

Protect against:

• Notification abuse
• Push-token abuse
• Advertising fraud
• Campaign manipulation
• Analytics-data leakage
• Creator cross-tenant access
• Podcast content access bypass
• Administrative privilege escalation
• Feature-flag abuse
• Configuration injection
• Audit manipulation

Apply:

• Least privilege
• RBAC
• Resource ownership
• Rate limiting
• Signed media access
• Audit logging

────────────────────────────────────────

OBSERVABILITY

Instrument:

• Podcast ingestion
• Episode publication
• Notification delivery
• Push failures
• Email failures
• Ad decisioning
• Ad delivery
• Analytics ingestion
• Report generation
• Moderation
• Administrative operations
• Privacy jobs

Track:

• Notification latency
• Delivery rate
• Ad decision latency
• Ad fill/failure
• Analytics processing lag
• Queue backlog
• Report generation time
• Moderation backlog
• Privacy-job status

Never log:

• Passwords
• Tokens
• Secrets
• Payment credentials
• Private user analytics unnecessarily

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Podcast state
• Episode state
• Follow/unfollow
• Notification routing
• Notification preferences
• Ad eligibility
• Frequency caps
• Campaign state
• Moderation state
• Feature flags
• Configuration validation
• Privacy workflows

INTEGRATION TESTS

Test:

• PostgreSQL
• Redis
• Kafka
• BullMQ
• S3
• Notification providers
• Payment abstraction
• Search integration

NOTIFICATION TESTS

Test:

• FCM
• APNS
• Token rotation
• Retry
• Provider failure
• Deduplication

ADVERTISING TESTS

Test:

• Targeting
• Frequency caps
• Budget constraints
• Campaign state
• Duplicate event processing
• Ad decision failures

ANALYTICS TESTS

Test:

• Event ingestion
• Schema validation
• Aggregation
• Retention
• Creator isolation

ADMINISTRATION TESTS

Test:

• RBAC
• Sensitive operations
• Audit generation
• Feature flag changes
• Configuration changes

SECURITY TESTS

Test:

• Creator isolation
• Notification authorization
• Ad-abuse paths
• Admin privilege escalation
• Analytics data leakage
• IDOR

PERFORMANCE TESTS

Test:

• Notification throughput
• Ad decision latency
• Event ingestion
• Report generation
• Podcast search integration

────────────────────────────────────────

DOCUMENTATION

Generate:

• Podcast architecture
• Creator architecture
• Audiobook boundaries
• Notification architecture
• Advertising architecture
• Analytics architecture
• Reporting
• Moderation
• Administration
• Feature flags
• System configuration
• Audit
• Privacy workflows
• API contracts
• Event contracts
• Queue architecture
• Database schema
• Security model
• Testing strategy

────────────────────────────────────────

PROJECT INDEX

Update the backend Project Index with:

• Podcast modules
• Episode modules
• Creator modules
• Notification modules
• Advertising modules
• Analytics modules
• Reporting modules
• Moderation modules
• Administration modules
• Feature-flag modules
• Configuration modules
• Audit modules
• Privacy modules
• Database objects
• Migrations
• APIs
• Events
• Queues
• Workers
• Search integrations
• Tests
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 61

Podcast shows, creators, episodes, categories, metadata, follows, and APIs.

BACKEND MILESTONE 62

Podcast playback progress, search integration, recommendation integration, and content availability.

BACKEND MILESTONE 63

Audiobook extensibility boundaries and future content-model abstractions.

BACKEND MILESTONE 64

Notification domain, preferences, device tokens, in-app notifications, and notification APIs.

BACKEND MILESTONE 65

FCM/APNS integration, email abstraction, notification queues, retries, and deduplication.

BACKEND MILESTONE 66

Advertising domain, advertisers, campaigns, creatives, targeting, scheduling, and lifecycle.

BACKEND MILESTONE 67

Ad decisioning, frequency caps, delivery tracking, impressions, completions, and reconciliation.

BACKEND MILESTONE 68

Analytics ingestion, event processing, aggregation, creator analytics, and business analytics foundations.

BACKEND MILESTONE 69

Reporting, moderation, administration, feature flags, system configuration, audit, and privacy workflows.

BACKEND MILESTONE 70

Security hardening, integration tests, performance tests, abuse tests, reconciliation, and production readiness.

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

• Podcasts
• Podcast creators
• Podcast episodes
• Podcast follows
• Podcast playback-progress integration
• Audiobook extensibility
• Notifications
• Push notifications
• Email notifications
• In-app notifications
• Advertising
• Ad decisioning
• Ad delivery
• Analytics
• Reporting
• Moderation
• Administration
• Feature flags
• System configuration
• Audit
• Privacy workflows

Do not implement:

• New core music playback architecture
• New playlist architecture
• New search architecture
• New recommendation architecture
• Infrastructure
• Frontend
• Mobile

Use the approved existing systems.

────────────────────────────────────────

QUALITY BAR

Treat podcasts, notifications, advertising, analytics, administration, and privacy systems as enterprise-scale production systems.

Assume:

• Hundreds of millions of users
• Large notification traffic
• Large podcast catalogs
• High advertising throughput
• Billions of analytics events
• Large creator ecosystems
• Strict privacy requirements
• Multiple regions
• Strict security requirements

Prioritize:

• Privacy
• Security
• Reliability
• Idempotency
• Scalability
• Auditability
• Graceful failure
• Data isolation
• Observability
• Maintainability
• Production readiness
