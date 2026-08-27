You are operating in Senior Engineering Team Mode.

Build the production-ready backend for playlists, user libraries, liked content, followed artists, listening history, queue persistence, recently played content, playlist collaboration, playlist discovery, and synchronized personal music collections for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must follow the approved Spotify-like architecture, domain boundaries, database ownership, authentication model, authorization model, playback architecture, event architecture, Redis strategy, API conventions, and Project Index.

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

• User playlists
• Playlist items
• Playlist ownership
• Public playlists
• Private playlists
• Unlisted/shared playlists where supported
• Collaborative playlists
• Playlist permissions
• Playlist invitations
• Playlist versioning
• Playlist reordering
• Playlist snapshots
• User library
• Liked songs
• Saved albums
• Saved playlists
• Followed artists
• Followed podcasts
• Recently played
• Recently added
• Listening history
• Personal collection synchronization
• Queue persistence integration
• Cross-device synchronization
• Playlist discovery
• Playlist search integration
• Playlist recommendation signals

The implementation must support:

• Hundreds of millions of users
• Millions of playlists
• Billions of playlist items
• Large listening-history volumes
• High concurrent playlist updates
• Multiple devices per user
• Collaborative editing
• Public and private content
• High read traffic
• High synchronization traffic

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

• AWS S3-compatible object storage where playlist/review artwork requires it

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

Use optimistic concurrency where collaborative editing requires it.

Use idempotency where mutation retries could otherwise duplicate state.

────────────────────────────────────────

DOMAIN OWNERSHIP

Maintain explicit boundaries between:

• Playlists
• Playlist items
• Playlist permissions
• Playlist collaboration
• Playlist discovery
• User library
• Likes
• Follows
• Listening history
• Recently played
• Queue persistence
• Playback state

Do not combine:

• Playlist state with playback state
• Listening history with temporary playback session state
• Public playlist discovery with private playlist storage
• User library with catalog ownership

────────────────────────────────────────

PLAYLIST DOMAIN

Implement:

• Playlist creation
• Playlist retrieval
• Playlist update
• Playlist deletion
• Playlist title
• Playlist description
• Playlist artwork
• Playlist visibility
• Playlist owner
• Playlist metadata
• Playlist version

Support playlist states:

• Active
• Archived
• Deleted

Do not physically destroy playlist history unnecessarily when audit or collaboration requires retention.

────────────────────────────────────────

PLAYLIST VISIBILITY

Support:

• Private
• Public
• Unlisted/shared where appropriate

Define:

• Discovery rules
• Search rules
• Share permissions
• Access control
• Cache behavior

Private playlists must never appear in public search or recommendation systems without explicit authorization.

────────────────────────────────────────

PLAYLIST OWNERSHIP

Define:

• Owner
• Collaborator
• Viewer where appropriate

Support transfer of ownership only through controlled operations.

Ownership changes must be auditable.

────────────────────────────────────────

PLAYLIST COLLABORATION

Implement collaborative playlists.

Support:

• Invite collaborator
• Accept invitation
• Remove collaborator
• Leave playlist
• Collaborator permissions
• Add item
• Remove item
• Reorder items
• Rename playlist where authorized

Roles may include:

• Owner
• Editor
• Viewer

Do not allow collaborators to escalate their own permissions.

────────────────────────────────────────

PLAYLIST INVITATIONS

Implement:

• Invitation creation
• Expiration
• Acceptance
• Rejection
• Cancellation
• Duplicate prevention

Invitation tokens must:

• Be securely generated
• Be single-use where appropriate
• Expire
• Be revocable

Do not expose sensitive playlist information before authorization.

────────────────────────────────────────

PLAYLIST ITEMS

Implement:

• Add track
• Remove track
• Reorder track
• Move track
• Duplicate detection where appropriate
• Position/order management
• Added-by metadata
• Added timestamp

Support very large playlists.

Do not rely solely on integer array indexes for ordering at massive scale.

Define an ordering strategy that minimizes costly full-list rewrites.

────────────────────────────────────────

PLAYLIST ORDERING

Design a scalable ordering system.

Evaluate:

• Integer positions
• Fractional ordering
• Lexicographic ordering
• Linked-list style ordering
• Ordered sequence tokens

Choose a strategy appropriate for:

• Large playlists
• Frequent insertions
• Concurrent edits
• Reordering
• Pagination

Define rebalancing behavior when ordering values become too dense.

────────────────────────────────────────

PLAYLIST VERSIONING

Implement optimistic concurrency.

Each playlist maintains a version.

Mutations may require:

• Expected version
• Mutation ID
• Actor
• Resulting version

Reject stale mutations safely.

Do not silently overwrite newer collaborator changes.

────────────────────────────────────────

COLLABORATIVE CONFLICT HANDLING

Define behavior when:

• Two collaborators edit simultaneously
• One collaborator removes an item another moves
• A playlist is deleted while another user edits
• Ownership changes during an edit
• Network retries submit duplicate mutations

Use:

• Version checks
• Idempotency
• Deterministic conflict responses

Do not implement full CRDT infrastructure unless the architecture explicitly requires it.

────────────────────────────────────────

PLAYLIST SNAPSHOTS

Create snapshot architecture for:

• Version history
• Recovery
• Collaboration
• Audit
• Moderation where appropriate

Do not retain every historical snapshot indefinitely without a policy.

Define retention.

────────────────────────────────────────

PLAYLIST ARTWORK

Support:

• Custom playlist artwork
• Generated artwork reference
• Multiple resolutions
• Upload authorization
• Processing state
• CDN delivery

Use S3-compatible object storage.

Do not store binary artwork inside PostgreSQL.

────────────────────────────────────────

USER LIBRARY

Implement a user library.

Support:

• Liked tracks
• Saved albums
• Saved playlists
• Followed artists
• Followed podcasts
• Library organization where appropriate

Provide fast reads for:

• Is track liked?
• Is album saved?
• Is playlist saved?
• Is artist followed?

────────────────────────────────────────

LIKED TRACKS

Implement:

• Like track
• Unlike track
• Check liked state
• List liked tracks
• Cursor pagination
• Ordering by liked date
• Optional playlist/library integration

Prevent duplicate likes.

Use database uniqueness constraints.

────────────────────────────────────────

SAVED ALBUMS

Implement:

• Save album
• Unsave album
• Check saved state
• List saved albums
• Cursor pagination

Prevent duplicates.

────────────────────────────────────────

FOLLOWED ARTISTS

Implement:

• Follow artist
• Unfollow artist
• Check follow state
• List followed artists
• Cursor pagination

Prevent duplicate follows.

Publish follow events for downstream notification and recommendation systems.

────────────────────────────────────────

FOLLOWED PODCASTS

Implement podcast-follow boundaries without implementing the complete podcast domain.

Support:

• Follow show
• Unfollow show
• Check follow state
• List followed shows

Keep ownership separate from podcast content.

────────────────────────────────────────

RECENTLY PLAYED

Implement a high-scale recently-played experience.

Support:

• Track
• Timestamp
• Profile
• Device
• Playback context where useful

Provide:

• Recent list
• Deduplication strategy
• Cursor pagination
• Time-based cleanup

Do not rely solely on PostgreSQL row-by-row writes for extremely high playback volume.

────────────────────────────────────────

LISTENING HISTORY

Design a durable listening-history pipeline.

Support:

• Track started
• Track played
• Track completed
• Track skipped
• Timestamp
• Profile
• Device
• Playback session
• Playback context

Raw listening telemetry should be processed asynchronously.

Do not block playback on history persistence.

────────────────────────────────────────

LISTENING HISTORY STORAGE

Define separate layers for:

• Raw playback events
• Operational recently-played data
• Durable user listening history
• Long-term analytics

Do not store unlimited raw playback telemetry in the transactional database.

Define:

• Retention
• Aggregation
• Archival
• Deletion

────────────────────────────────────────

HISTORY PRIVACY

Listening history is user-private unless explicitly exposed through approved features.

Do not allow:

• Other users
• Collaborators
• Artists
• Labels
• Administrators

to access private listening history without explicit authorization.

Administrative access must be auditable.

────────────────────────────────────────

LIBRARY SYNCHRONIZATION

Support synchronization across:

• Web
• iOS
• Android
• Future desktop clients

Define:

• Sync cursor
• Change sequence
• Added records
• Removed records
• Updated records
• Deleted records

Support incremental synchronization rather than requiring full library downloads.

────────────────────────────────────────

SYNC MODEL

Create a synchronization mechanism based on:

• Per-user change sequence
• Cursor
• Mutation IDs
• Server timestamps
• Entity versions

Handle:

• Device reconnect
• Offline mutations
• Duplicate mutations
• Stale mutations
• Partial synchronization

Do not assume clients are always online.

────────────────────────────────────────

OFFLINE MUTATIONS

Support mobile-created mutations such as:

• Like track
• Unlike track
• Save album
• Unsave album
• Add track to playlist
• Remove track from playlist

Each mutation should carry:

• Mutation ID
• Client timestamp
• Entity ID
• Expected version where required

Server responses must clearly indicate:

• Applied
• Already applied
• Rejected
• Conflict

────────────────────────────────────────

QUEUE PERSISTENCE INTEGRATION

Integrate playlist/library domains with playback queue architecture.

Support:

• Save current queue
• Restore queue
• Queue derived from playlist
• Queue modifications
• Queue version

Do not duplicate the entire playback-state architecture.

The playback system remains authoritative for current playback state.

────────────────────────────────────────

PLAYLIST DISCOVERY

Support discovery for public playlists.

Define:

• Search indexing
• Popularity
• Recency
• Follow counts
• Editorial curation
• Recommendation signals

Private playlists must remain excluded.

────────────────────────────────────────

PLAYLIST SEARCH

Integrate with search architecture.

Index appropriate public fields:

• Playlist name
• Description
• Owner display name where public
• Genre/tags
• Popularity signals

Do not index:

• Private playlist contents
• Private user metadata
• Private listening behavior

────────────────────────────────────────

RECOMMENDATION EVENTS

Publish events such as:

• PlaylistCreated
• PlaylistUpdated
• PlaylistDeleted
• PlaylistItemAdded
• PlaylistItemRemoved
• PlaylistShared
• PlaylistFollowed
• TrackLiked
• TrackUnliked
• AlbumSaved
• AlbumUnsaved
• ArtistFollowed
• ArtistUnfollowed
• PodcastFollowed
• PodcastUnfollowed
• TrackPlayed
• TrackCompleted
• TrackSkipped

Consumers must be idempotent.

────────────────────────────────────────

BACKGROUND JOBS

Implement jobs for:

• Playlist cleanup
• Invitation expiration
• Playlist snapshot retention
• Search indexing
• Search cleanup
• History aggregation
• Recently-played cleanup
• Library synchronization assistance
• Orphan artwork cleanup

Each job must support:

• Retry
• Backoff
• Timeout
• Idempotency
• Dead-letter handling
• Monitoring

────────────────────────────────────────

DATABASE

Implement Prisma models and migrations for:

• Playlist
• PlaylistItem
• PlaylistCollaborator
• PlaylistInvitation
• PlaylistVersion
• PlaylistSnapshot
• PlaylistArtwork
• LikedTrack
• SavedAlbum
• SavedPlaylist
• FollowedArtist
• FollowedPodcast
• ListeningHistoryReference
• RecentlyPlayed
• UserLibraryChange
• LibrarySyncCursor
• LibraryMutation

Use:

• Primary keys
• Foreign keys
• Composite indexes
• Unique constraints
• Version fields
• Cursor-friendly indexes
• Timestamps

For high-growth history tables evaluate partitioning.

────────────────────────────────────────

DATABASE CONSISTENCY

Use transactions for:

• Playlist creation
• Playlist ownership changes
• Playlist collaborator changes
• Playlist-item mutations
• Like/unlike uniqueness
• Save/unsave uniqueness
• Follow/unfollow uniqueness
• Sync cursor updates

Use optimistic concurrency for collaborative playlists.

────────────────────────────────────────

REDIS

Use Redis for:

• Playlist read caching where appropriate
• Library membership checks
• Recent-played acceleration
• Sync state
• Rate limiting
• Distributed locks
• Hot public playlists

Define:

• Key patterns
• TTL
• Invalidation
• Stampede protection
• Failure behavior

Redis remains a cache, not authoritative storage.

────────────────────────────────────────

API

Implement production-ready REST APIs.

PLAYLISTS

• Create playlist
• Get playlist
• Update playlist
• Delete playlist
• Add item
• Remove item
• Reorder items
• List items
• Change visibility
• Share
• Follow/save
• Unfollow/remove

COLLABORATION

• Invite collaborator
• List collaborators
• Accept invitation
• Reject invitation
• Remove collaborator
• Leave playlist
• Transfer ownership where supported

LIBRARY

• Get library
• Liked tracks
• Saved albums
• Saved playlists
• Followed artists
• Followed podcasts

LIKES

• Like track
• Unlike track
• Check liked state

SAVED ALBUMS

• Save
• Unsave
• Check state

FOLLOWS

• Follow artist
• Unfollow artist
• Follow podcast
• Unfollow podcast

HISTORY

• Recently played
• Listening history
• Clear history where supported

SYNC

• Get sync cursor
• Get changes since cursor
• Submit offline mutations
• Resolve mutation state

Every endpoint must implement:

• Authentication
• Authorization
• Profile scoping
• Validation
• Rate limiting
• Pagination
• Cursor pagination
• Idempotency
• OpenAPI documentation
• Consistent errors

────────────────────────────────────────

SECURITY

Protect against:

• Private-playlist disclosure
• Cross-profile access
• Unauthorized collaboration
• Playlist ownership takeover
• Invitation replay
• Playlist IDOR
• Listening-history leakage
• Library data leakage
• Spam follows
• Like manipulation

Enforce authorization server-side.

────────────────────────────────────────

OBSERVABILITY

Instrument:

• Playlist mutations
• Collaboration mutations
• Library operations
• Sync operations
• Listening-history ingestion
• Recently-played updates
• Search indexing

Track:

• Playlist mutation latency
• Conflict rate
• Sync latency
• Sync failure rate
• History ingestion lag
• Queue backlog
• Public-playlist indexing lag

Never log:

• Private playlist contents unnecessarily
• Private listening data unnecessarily
• Tokens
• Secrets

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Playlist permissions
• Collaboration permissions
• Ordering
• Version conflicts
• Invitation lifecycle
• Like/unlike
• Save/unsave
• Follow/unfollow
• History policies
• Sync conflict resolution

INTEGRATION TESTS

Test:

• PostgreSQL
• Redis
• Kafka
• BullMQ
• Search

CONCURRENCY TESTS

Test:

• Concurrent playlist edits
• Concurrent reorder
• Duplicate mutations
• Offline retries
• Invitation races
• Ownership changes

SECURITY TESTS

Test:

• Private playlist access
• Cross-profile access
• Cross-user access
• Collaborator privilege escalation
• Listening-history access
• Invitation replay
• IDOR

PERFORMANCE TESTS

Test:

• Large playlists
• Large libraries
• Library synchronization
• Recently-played retrieval
• Public playlist search
• Concurrent playlist updates

────────────────────────────────────────

DOCUMENTATION

Generate:

• Playlist architecture
• Collaboration model
• Ordering strategy
• Versioning strategy
• Library architecture
• Like/save/follow model
• Listening-history architecture
• Recently-played architecture
• Offline synchronization
• Playlist search
• Playlist discovery
• API contracts
• Event contracts
• Queue architecture
• Database schema
• Privacy model
• Security model
• Testing strategy

────────────────────────────────────────

PROJECT INDEX

Update the backend Project Index with:

• Playlist modules
• Collaboration modules
• Library modules
• Like modules
• Save modules
• Follow modules
• Listening-history modules
• Recently-played modules
• Synchronization modules
• Database objects
• Migrations
• API endpoints
• Events
• Queues
• Workers
• Redis usage
• Search integration
• Tests
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 41

Playlist domain, playlist models, CRUD, permissions, visibility, and APIs.

BACKEND MILESTONE 42

Playlist items, ordering strategy, versioning, optimistic concurrency, and reordering.

BACKEND MILESTONE 43

Collaborative playlists, invitations, collaborator permissions, snapshots, and ownership workflows.

BACKEND MILESTONE 44

User library, liked tracks, saved albums, saved playlists, followed artists, and followed podcasts.

BACKEND MILESTONE 45

Recently played, listening-history ingestion, retention, and asynchronous event processing.

BACKEND MILESTONE 46

Library synchronization, sync cursors, offline mutations, idempotency, and conflict resolution.

BACKEND MILESTONE 47

Playlist discovery, public-playlist search integration, caching, and recommendation events.

BACKEND MILESTONE 48

Redis optimization, background jobs, observability, privacy, and security hardening.

BACKEND MILESTONE 49

Integration, concurrency, security, synchronization, and performance testing.

BACKEND MILESTONE 50

Production hardening, reconciliation, documentation, and Project Index completion.

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

• Playlists
• Playlist items
• Playlist ordering
• Playlist permissions
• Playlist collaboration
• Playlist invitations
• Playlist versioning
• Playlist snapshots
• Playlist artwork
• User library
• Liked tracks
• Saved albums
• Saved playlists
• Followed artists
• Followed podcasts
• Recently played
• Listening history
• Library synchronization
• Offline library mutations
• Public playlist discovery
• Playlist search integration
• Recommendation events

Do not implement complete:

• Search query service
• Recommendations
• Radio
• Charts
• Podcasts
• Downloads
• Offline licenses
• Notifications
• Advertising
• Analytics platform
• Administration
• Moderation
• Frontend
• Mobile
• Infrastructure

Those belong to later implementation volumes.

────────────────────────────────────────

QUALITY BAR

Treat playlists, libraries, synchronization, and listening history as high-scale user-state systems.

Assume:

• Hundreds of millions of users
• Millions of playlists
• Billions of playlist items
• High concurrent collaboration
• Multiple devices per user
• Offline mutations
• Large listening-history volumes
• High read traffic
• High synchronization traffic

Prioritize:

• Correct ownership
• Privacy
• Collaboration correctness
• Optimistic concurrency
• Idempotency
• Synchronization reliability
• Scalable ordering
• High read performance
• Eventual analytics processing
• Security
• Observability
• Production readiness
