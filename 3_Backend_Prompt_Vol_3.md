You are operating in Senior Engineering Team Mode.

Build the production-ready backend for the music catalog, artists, labels, releases, tracks, metadata, audio assets, artwork, lyrics, content rights, availability, localization, content ingestion, and artist/partner management domains for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must follow the approved Spotify-like architecture, domain boundaries, database ownership, API conventions, security model, media architecture, rights architecture, event architecture, queue architecture, and Project Index.

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

• Artists
• Artist teams
• Labels
• Label staff
• Content partners
• Albums
• Releases
• Tracks
• Track versions
• Track credits
• Genres
• Tags
• Languages
• Lyrics metadata
• Explicit-content metadata
• Artwork
• Audio assets
• Audio processing state
• Audio renditions
• Content identifiers
• Content localization
• Content ingestion
• Release scheduling
• Publishing
• Unpublishing
• Content rights
• Regional availability
• Platform availability
• Artist/content-partner administration
• Catalog moderation integration
• Search-index integration

The implementation must support:

• Millions of tracks
• Millions of albums/releases
• Large artist ecosystems
• Labels and distribution partners
• Multiple versions of tracks
• Regional rights
• Multiple languages
• Scheduled releases
• High catalog-read traffic
• Large media metadata volumes
• Global content delivery

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

Object Storage:

• AWS S3-compatible object storage

CDN:

• CloudFront or equivalent CDN

Event Streaming:

• Kafka or Redpanda

Background Processing:

• BullMQ

Media Processing:

• FFmpeg or approved audio-processing infrastructure

Search:

• Elasticsearch/OpenSearch integration

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

Keep domain rules outside controllers.

Use repositories for persistence.

Use DTOs for API contracts.

Use centralized validation.

Use centralized error handling.

Use structured logging.

Use the established observability infrastructure.

────────────────────────────────────────

DOMAIN OWNERSHIP

Maintain explicit boundaries between:

• Artists
• Artist teams
• Labels
• Content partners
• Albums
• Releases
• Tracks
• Track credits
• Metadata
• Audio assets
• Artwork
• Lyrics
• Rights
• Availability
• Localization
• Content ingestion
• Publishing

Do not combine:

• Catalog metadata with raw media
• Rights with playback sessions
• Artist ownership with user profile data
• Audio processing with catalog publication state

────────────────────────────────────────

ARTIST DOMAIN

Implement:

• Artist creation
• Artist profile
• Artist metadata
• Artist aliases
• Artist status
• Artist verification
• Artist members
• Artist staff
• Artist permissions

Support artist states such as:

• Draft
• Pending
• Verified
• Active
• Suspended
• Archived

────────────────────────────────────────

ARTIST TEAM

Implement:

• Team creation
• Member invitation
• Member acceptance
• Role assignment
• Role removal
• Staff suspension
• Team permissions

Roles may include:

• Artist Owner
• Manager
• Editor
• Analytics Viewer
• Content Manager

Enforce artist-scoped permissions.

────────────────────────────────────────

LABEL DOMAIN

Implement:

• Label creation
• Label profile
• Label users
• Label staff
• Label permissions
• Label status

Support:

• Active
• Suspended
• Archived

Labels must only access content and analytics authorized for their organization.

────────────────────────────────────────

CONTENT PARTNERS

Support:

• Distributor
• Production partner
• Rights partner
• Content supplier

Implement:

• Partner registration
• Partner organization
• Partner staff
• Permissions
• Content submission
• Rights declarations
• Asset upload references

────────────────────────────────────────

ALBUM DOMAIN

Implement:

• Album creation
• Album metadata
• Album artwork
• Album type
• Release association
• Track ordering
• Localization
• Status

Support:

• Album
• EP
• Compilation
• Deluxe
• Reissue
• Single-related release structures

────────────────────────────────────────

RELEASE DOMAIN

Implement:

• Release creation
• Release metadata
• Release date
• Scheduled publication
• Release status
• Track order
• Artwork
• Localization
• Rights
• Territory availability

Support:

• Draft
• Submitted
• Validating
• Processing
• Review
• Approved
• Scheduled
• Published
• Unpublished
• Archived
• Removed

────────────────────────────────────────

TRACK DOMAIN

Implement:

• Track creation
• Track metadata
• Track duration
• Track version
• Track identifiers
• Explicit-content state
• Genre/tag association
• Credits
• Release association
• Audio asset association

Support different versions:

• Original
• Radio edit
• Remaster
• Live
• Acoustic
• Instrumental
• Remix

Do not assume one track corresponds to exactly one audio file.

────────────────────────────────────────

TRACK IDENTIFIERS

Support appropriate industry identifiers where applicable:

• ISRC
• UPC/EAN
• Catalog number
• Internal platform identifier

Define uniqueness rules.

Do not assume all content will contain every external identifier.

────────────────────────────────────────

TRACK CREDITS

Support:

• Primary artist
• Featured artist
• Composer
• Lyricist
• Producer
• Remixer
• Engineer
• Other configured credit roles

Define:

• Role
• Person/artist
• Ordering
• Display behavior

────────────────────────────────────────

GENRES AND TAGS

Implement:

• Genre creation
• Genre hierarchy
• Tags
• Genre assignment
• Content-tag assignment

Prevent invalid hierarchical relationships.

────────────────────────────────────────

LANGUAGES

Support:

• Language entity
• Locale
• Audio language
• Lyrics language
• Metadata language

Define fallback behavior for localized metadata.

────────────────────────────────────────

CONTENT LOCALIZATION

Support localized:

• Artist names
• Album titles
• Track titles
• Descriptions
• Genre names
• Editorial metadata
• Lyrics metadata

Do not require every locale before publication unless explicitly configured.

────────────────────────────────────────

ARTWORK

Implement artwork metadata.

Support:

• Cover artwork
• Artist artwork
• Playlist artwork references where appropriate
• Multiple resolutions
• Processing status
• Alt text
• Localization where required

Store binaries in object storage, not PostgreSQL.

────────────────────────────────────────

AUDIO ASSET DOMAIN

Implement metadata for source audio assets.

Track:

• Object key
• MIME type
• File size
• Duration
• Sample rate
• Channels
• Codec
• Bit depth
• Loudness metadata
• Processing status
• Validation status

The asset record is metadata and state.

The actual audio object belongs in object storage.

────────────────────────────────────────

AUDIO INGESTION

Implement:

• Upload initialization
• Signed upload URL
• Upload completion
• Ownership validation
• File verification
• Processing request

Do not trust client-provided:

• MIME type
• Duration
• Codec
• File size

Validate these values from the uploaded asset.

────────────────────────────────────────

CONTENT PROCESSING STATE

Track:

• Uploaded
• Validating
• Validated
• Processing
• Processed
• Failed
• Reprocessing
• Ready

Do not mark a track published before required media validation succeeds.

────────────────────────────────────────

AUDIO RENDITIONS

Implement metadata for processed renditions.

Support:

• Codec
• Container
• Bitrate
• Sample rate
• Channel count
• Quality tier
• Object key
• Duration
• Processing version

Support future quality tiers such as:

• Low
• Standard
• High
• Lossless

Do not hard-code a fixed codec list into core domain logic.

────────────────────────────────────────

MEDIA PROCESSING JOBS

Use BullMQ for:

• Audio validation
• Metadata extraction
• Loudness analysis
• Transcoding
• Rendition generation
• Artwork processing
• Lyrics processing

Every job must support:

• Retry
• Backoff
• Timeout
• Idempotency
• Failure state
• Dead-letter handling
• Monitoring

────────────────────────────────────────

CONTENT INGESTION WORKFLOW

Implement:

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
• Transition permissions
• Validation
• Moderation integration
• Rights checks
• Event generation
• Audit

────────────────────────────────────────

RELEASE SCHEDULING

Support:

• Immediate publication
• Scheduled publication
• Scheduled unpublication
• Time zones
• Territory-specific schedules where required

Use background jobs for scheduled transitions.

Do not rely on client devices to trigger publication.

────────────────────────────────────────

RIGHTS DOMAIN

Implement:

• Rights records
• Content ownership
• Licensor
• Licensee
• Territory
• Start date
• End date
• Content type
• Platform restriction
• Subscription restriction

Rights must be auditable.

────────────────────────────────────────

RIGHTS VALIDATION

Before publication, validate:

• Required rights exist
• Rights cover the target region
• Rights dates are valid
• Conflicting rights are detected
• Platform restrictions are satisfied

Before playback, the later playback service will validate active rights.

────────────────────────────────────────

CONTENT AVAILABILITY

Implement availability records for:

• Country
• Region
• Platform
• Device class
• Subscription tier
• Start date
• End date

Support states such as:

• Available
• Scheduled
• Expired
• Blocked

────────────────────────────────────────

RIGHTS EXPIRATION

Implement background jobs for:

• Rights expiration
• Availability updates
• Content unpublishing
• CDN access invalidation where required
• Search-index updates

Do not delete historical rights records merely because they expire.

────────────────────────────────────────

CATALOG PUBLICATION

Implement publication validation.

A release cannot become published unless:

• Required metadata exists
• Required tracks exist
• Required audio assets are ready
• Required artwork is ready
• Rights are valid
• Availability is configured
• Moderation requirements are satisfied

Define configurable validation policies.

────────────────────────────────────────

SEARCH INDEX INTEGRATION

Publish catalog changes to the established search infrastructure.

Events may include:

• ArtistCreated
• ArtistUpdated
• AlbumCreated
• AlbumUpdated
• ReleasePublished
• ReleaseUnpublished
• TrackCreated
• TrackUpdated
• TrackPublished
• TrackUnpublished
• RightsChanged
• AvailabilityChanged

Indexing must be idempotent.

────────────────────────────────────────

CACHE

Use Redis for appropriate catalog caching.

Cache:

• Artist profiles
• Album metadata
• Track metadata
• Release metadata
• Genre metadata
• Public availability views

Define:

• Key patterns
• TTL
• Invalidation
• Failure behavior

Redis is not authoritative.

────────────────────────────────────────

API

Implement production-ready APIs.

ARTISTS

• Create
• Get
• Update
• List
• Verify
• Suspend

ARTIST TEAMS

• Invite
• List members
• Assign role
• Remove member

LABELS

• Create
• Get
• Update
• Manage staff

RELEASES

• Create
• Get
• Update
• Submit
• Schedule
• Publish
• Unpublish
• Archive

ALBUMS

• Create
• Get
• Update
• List

TRACKS

• Create
• Get
• Update
• Associate with release
• Manage credits
• Submit
• Publish
• Unpublish

MEDIA

• Upload authorization
• Completion
• Metadata
• Processing status

RIGHTS

• Create
• Get
• Update
• Expire
• Availability

LOCALIZATION

• Get translations
• Add translation
• Update translation

Every endpoint must implement:

• Authentication
• Authorization
• Validation
• Artist/label/partner isolation
• Rate limiting
• OpenAPI documentation
• Consistent errors
• Idempotency where appropriate

────────────────────────────────────────

DATABASE

Implement Prisma models and migrations for:

• Artist
• ArtistMember
• ArtistRole
• Label
• LabelMember
• ContentPartner
• Album
• Release
• ReleaseTrack
• Track
• TrackVersion
• TrackCredit
• Genre
• GenreRelation
• ContentTag
• Language
• ArtistLocalization
• AlbumLocalization
• ReleaseLocalization
• TrackLocalization
• Artwork
• AudioAsset
• AudioRendition
• MediaProcessingJobReference
• ContentRight
• ContentAvailability
• ContentIdentifier

Use:

• Primary keys
• Foreign keys
• Unique constraints
• Composite indexes
• Check constraints
• Status fields
• Effective/expiration timestamps

────────────────────────────────────────

DATABASE CONSISTENCY

Use transactions for:

• Release-track ordering updates
• Track/release associations
• Artist-role changes
• Rights changes
• Publication state transitions
• Media readiness state changes

Do not use distributed transactions across storage or processing services.

Use events and reconciliation.

────────────────────────────────────────

EVENTS

Publish:

ARTISTS

• ArtistCreated
• ArtistUpdated
• ArtistVerified
• ArtistSuspended
• ArtistMemberAdded
• ArtistMemberRemoved

LABELS

• LabelCreated
• LabelUpdated
• LabelMemberAdded
• LabelMemberRemoved

CONTENT

• AlbumCreated
• AlbumUpdated
• ReleaseCreated
• ReleaseSubmitted
• ReleaseApproved
• ReleasePublished
• ReleaseUnpublished
• ReleaseArchived
• TrackCreated
• TrackUpdated
• TrackPublished
• TrackUnpublished

MEDIA

• AudioUploaded
• AudioValidated
• AudioProcessingStarted
• AudioProcessingCompleted
• AudioProcessingFailed
• AudioRenditionGenerated
• ArtworkUploaded
• ArtworkProcessed

RIGHTS

• RightsCreated
• RightsUpdated
• RightsExpired
• AvailabilityChanged

LOCALIZATION

• LocalizationCreated
• LocalizationUpdated

Events must contain only required consumer data.

────────────────────────────────────────

BACKGROUND JOBS

Implement:

• Audio processing
• Artwork processing
• Metadata extraction
• Publication scheduling
• Rights expiration
• Availability expiration
• Search indexing
• Cache invalidation
• Media cleanup
• Failed-processing retry

Every job must support:

• Retry
• Backoff
• Timeout
• Idempotency
• Dead-letter handling
• Monitoring

────────────────────────────────────────

SELLER/PARTNER ISOLATION

Artist, label, and partner users must only access authorized content.

Enforce isolation for:

• Artists
• Releases
• Tracks
• Media
• Rights
• Analytics references
• Submission records

Never trust organization IDs supplied by clients.

Derive organization scope from authenticated identity.

────────────────────────────────────────

ADMINISTRATION

Implement administrative access for:

• Artist management
• Label management
• Content moderation
• Release approval
• Rights investigation
• Publication overrides
• Content suspension
• Media investigation

High-risk actions must be audited.

────────────────────────────────────────

SECURITY

Protect against:

• Unauthorized content upload
• Cross-organization access
• Malicious files
• Metadata injection
• Path traversal
• Unauthorized publishing
• Rights manipulation
• Content scraping
• IDOR
• Privilege escalation

Uploaded media must be validated before processing.

────────────────────────────────────────

OBSERVABILITY

Instrument:

• Content ingestion
• Uploads
• Processing
• Publication
• Rights changes
• Availability changes
• Search indexing
• Artist administration

Track:

• Processing latency
• Processing failure rate
• Queue depth
• Publication failures
• Rights conflicts
• Indexing latency
• Media failures

Never log sensitive credentials or private content-access tokens.

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Artist permissions
• Label permissions
• Release state machine
• Track validation
• Rights validation
• Availability rules
• Publication rules
• Localization fallback
• Processing state

INTEGRATION TESTS

Test:

• PostgreSQL
• Prisma
• Redis
• Kafka
• BullMQ
• S3
• Search integration

MEDIA TESTS

Test:

• Upload
• Validation
• Metadata extraction
• Processing
• Failure
• Retry
• Duplicate processing

SECURITY TESTS

Test:

• Artist isolation
• Label isolation
• Partner isolation
• IDOR
• Unauthorized publication
• Media access

CONCURRENCY TESTS

Test:

• Concurrent publication
• Concurrent metadata updates
• Track ordering changes
• Rights changes
• Duplicate processing jobs

PERFORMANCE TESTS

Test:

• Catalog reads
• Artist pages
• Album pages
• Track retrieval
• Publication throughput
• Search indexing

────────────────────────────────────────

DOCUMENTATION

Generate:

• Artist architecture
• Label architecture
• Content partner architecture
• Album/release model
• Track model
• Credits
• Media model
• Audio processing pipeline
• Artwork processing
• Rights architecture
• Availability
• Localization
• Content ingestion
• Publication workflow
• API contracts
• Event contracts
• Queue architecture
• Database schema
• Testing strategy
• Security model

────────────────────────────────────────

PROJECT INDEX

Update the backend Project Index with:

• Artist modules
• Artist-team modules
• Label modules
• Partner modules
• Album modules
• Release modules
• Track modules
• Metadata modules
• Genre modules
• Localization modules
• Artwork modules
• Audio asset modules
• Audio rendition modules
• Rights modules
• Availability modules
• Database objects
• Migrations
• API endpoints
• Events
• Queues
• Workers
• Search integration
• Tests
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 21

Artists, artist teams, labels, content partners, roles, and permissions.

BACKEND MILESTONE 22

Albums, releases, tracks, identifiers, credits, genres, tags, and localized metadata.

BACKEND MILESTONE 23

Artwork, audio assets, upload authorization, object-storage integration, and media metadata.

BACKEND MILESTONE 24

Audio processing state, processing jobs, rendition metadata, and media workflows.

BACKEND MILESTONE 25

Content ingestion, release submission, moderation integration, publication, and scheduling.

BACKEND MILESTONE 26

Rights management, regional availability, platform restrictions, and rights expiration.

BACKEND MILESTONE 27

Search indexing integration, cache invalidation, events, and background workers.

BACKEND MILESTONE 28

Administrative workflows, security hardening, audit integration, and partner isolation.

BACKEND MILESTONE 29

Integration testing, media testing, concurrency testing, and performance testing.

BACKEND MILESTONE 30

Production hardening, reconciliation, observability validation, and Project Index completion.

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

This volume covers only:

• Artists
• Artist teams
• Labels
• Content partners
• Albums
• Releases
• Tracks
• Track versions
• Credits
• Genres
• Tags
• Languages
• Localization
• Artwork
• Audio assets
• Audio renditions
• Content ingestion
• Publication
• Rights
• Availability
• Search-index integration
• Related media-processing workflows

Do not implement complete:

• Playback
• Playback sessions
• Playback progress
• Queue
• Downloads
• Offline licenses
• Playlists
• Library
• Search query services
• Recommendations
• Radio
• Charts
• Podcasts
• Notifications
• Advertising
• Analytics
• Frontend
• Mobile
• Infrastructure

Those belong to later implementation volumes.

────────────────────────────────────────

QUALITY BAR

Treat music catalog, content rights, media processing, and publication as critical platform infrastructure.

Assume:

• Millions of tracks
• Large artist ecosystems
• Multiple releases per artist
• Multiple track versions
• Regional licensing
• Large media uploads
• Scheduled releases
• High catalog-read traffic
• Large global CDN traffic

Prioritize:

• Content correctness
• Rights correctness
• Organization isolation
• Media integrity
• Publication integrity
• Idempotency
• Auditability
• Scalability
• Security
• Observability
• Maintainability
• Production readiness
