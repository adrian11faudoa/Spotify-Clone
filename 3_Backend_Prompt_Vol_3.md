# Spotify-Style Music Streaming Platform

## Backend Implementation Prompt — Volume 3

### User Library, Likes, Follows, Playlists & Collaborative Playlists

You are the backend engineering team for an original, production-grade global music streaming platform inspired by the capabilities and user experience of services such as Spotify, Apple Music, YouTube Music, and similar platforms.

This prompt is fully standalone. Do not assume that another prompt, architecture document, specification, previous AI response, or prior conversation is available. The repository itself is the implementation source of truth. If compatible backend functionality already exists, inspect and reuse it rather than creating competing implementations.

Your mission in this volume is to implement the backend functionality for:

* User library
* Liked tracks
* Saved albums
* Saved playlists
* Follow relationships
* User-created playlists
* Playlist items
* Playlist ordering
* Playlist visibility
* Playlist ownership
* Playlist permissions
* Collaborative playlists
* Playlist mutation concurrency
* Library synchronization
* Related domain events
* Required caching and invalidation
* Required authorization, auditing, testing, migrations, and documentation

Do **not** implement the complete playback/media-delivery, recommendation, search, subscription/payment, notification, or analytics systems in this volume.

---

# 1. Engineering Role

Act as a senior production engineering organization consisting of:

* Principal Software Architect
* Staff Backend Engineer
* Database Architect
* Security Engineer
* Distributed Systems Engineer
* QA Engineer
* DevOps Engineer
* Technical Writer

Do not behave as a teacher.

Inspect the repository first and determine:

* Existing project structure
* Existing NestJS modules
* Existing domain/application/infrastructure layers
* Existing Prisma schema
* Existing migrations
* Existing authentication and authorization
* Existing Redis infrastructure
* Existing API conventions
* Existing DTO conventions
* Existing error handling
* Existing event/outbox infrastructure
* Existing queue infrastructure
* Existing testing infrastructure
* Existing logging and observability
* Existing naming conventions

Integrate with the implementation already present.

Do not blindly overwrite existing code.

Do not create duplicate models, modules, repositories, services, controllers, infrastructure abstractions, or utilities when compatible implementations already exist.

If repository implementation differs from the assumptions in this prompt, preserve working behavior and make the smallest safe changes necessary to satisfy the requirements.

---

# 2. Technology Baseline

Use the technology already established by the repository.

The intended backend stack is:

* Node.js
* NestJS
* TypeScript
* PostgreSQL
* Prisma ORM
* Redis
* REST APIs
* BullMQ where asynchronous processing is justified
* Kafka or Redpanda where durable domain/event streaming is justified
* OpenAPI/Swagger
* Docker
* OpenTelemetry
* Prometheus
* Grafana
* Loki
* Tempo

Do not introduce unnecessary infrastructure.

Do not replace existing technology merely for stylistic reasons.

---

# 3. Scope of This Volume

Implement the complete backend foundation for the following domains:

## User Library

Users must be able to manage their personal music library, including:

* Liked tracks
* Saved albums
* Saved playlists
* Followed artists
* Followed users where supported by the existing product model
* Library retrieval
* Library pagination
* Library mutation
* Library synchronization metadata where required

## Playlists

Implement:

* Playlist creation
* Playlist editing
* Playlist deletion
* Playlist ownership
* Playlist visibility
* Playlist description
* Playlist artwork reference
* Playlist item management
* Playlist ordering
* Playlist metadata
* Playlist sharing
* Playlist collaboration
* Playlist permissions
* Playlist item removal
* Playlist item insertion
* Playlist item reordering

## Follows

Implement appropriate follow relationships for:

* Artists
* Users, if supported by the domain model

Do not create relationships that are not justified by the actual product model.

---

# 4. Domain Modeling

Design the database and domain model carefully.

Potential entities include:

* User
* Artist
* Album
* Track
* Playlist
* PlaylistItem
* LikedTrack
* SavedAlbum
* SavedPlaylist
* Follow
* PlaylistCollaborator
* PlaylistPermission
* LibraryMutation or synchronization metadata where justified

Use the existing repository schema when possible.

Do not blindly create every entity listed above if the existing architecture already models the concept differently.

Every relationship must have:

* Clear ownership
* Appropriate foreign keys
* Referential integrity
* Appropriate uniqueness constraints
* Appropriate indexes
* Explicit lifecycle behavior

---

# 5. User Library

Implement a durable user library.

The library must support efficient access to:

* Liked tracks
* Saved albums
* Saved playlists
* Followed artists
* Relevant followed users

Implement APIs for adding and removing library items.

Operations must be:

* Authenticated
* Authorized
* Idempotent where appropriate
* Safe under concurrent requests
* Efficient for large libraries

Do not rely exclusively on Redis for library persistence.

PostgreSQL must remain the authoritative source of truth.

---

# 6. Liked Tracks

Implement a robust liked-track system.

Requirements:

* User can like a track
* User can unlike a track
* Repeated like requests must not create duplicates
* Repeated unlike requests must be safe
* Authorization must ensure users can only modify their own library
* Queries must support pagination
* Ordering should be deterministic
* The system should preserve a meaningful saved/liked timestamp
* Database uniqueness must prevent duplicate relationships

Expose appropriate REST endpoints according to repository conventions.

Possible semantics include:

```text
PUT    /v1/me/tracks/{trackId}
DELETE /v1/me/tracks/{trackId}
GET    /v1/me/tracks
```

Adapt paths to the repository's existing API conventions rather than blindly copying these examples.

---

# 7. Saved Albums

Users must be able to:

* Save an album
* Remove an album
* List saved albums
* Paginate through saved albums
* Determine whether an album is saved

Implement efficient database queries.

Avoid N+1 queries.

Use database constraints to prevent duplicate saved-album relationships.

Preserve deterministic ordering, normally based on when the album was saved unless the existing product model specifies another ordering.

---

# 8. Saved Playlists

Users must be able to:

* Save playlists created by other users
* Remove saved playlists
* Retrieve saved playlists
* Determine whether a playlist is saved

Clarify the distinction between:

* Playlist owner
* Playlist collaborator
* Playlist viewer
* Playlist saved by another user

A user saving a playlist must not automatically gain editing permissions.

Do not allow saved-playlist functionality to bypass playlist visibility or authorization rules.

---

# 9. Follow System

Implement artist and, where supported, user follow relationships.

Requirements:

* Follow
* Unfollow
* Follow status
* Followers pagination
* Following pagination
* Duplicate prevention
* Authorization
* Consistent timestamps
* Safe concurrent mutations

For artist follows, enforce the correct relationship between the authenticated user and the artist.

For user follows, prevent invalid self-follow behavior if the product rules prohibit it.

Avoid exposing private user information through follower/following APIs.

---

# 10. Playlist Creation

Implement complete playlist creation.

A playlist should support appropriate fields such as:

* ID
* Owner
* Name
* Description
* Visibility
* Artwork reference
* Collaborative flag
* Created timestamp
* Updated timestamp
* Version/revision where needed

Playlist names and descriptions must be validated.

Do not allow:

* Empty required names
* Oversized fields
* Invalid identifiers
* Unauthorized ownership manipulation
* Arbitrary media URLs
* Arbitrary storage paths

Artwork must reference the platform's controlled media/storage abstraction rather than allowing arbitrary external storage access.

---

# 11. Playlist Visibility

Support the repository's appropriate visibility model.

Possible states include:

* Public
* Private
* Unlisted/shareable

Do not introduce visibility modes without a clear product or architectural reason.

Visibility must be enforced server-side.

A private playlist must never become accessible merely because a user knows or guesses its identifier.

Every playlist retrieval path must evaluate:

* Authentication state
* Owner status
* Collaboration permissions
* Visibility
* Resource existence

Avoid leaking the existence of private resources through authorization errors.

---

# 12. Playlist Ownership

The playlist owner has authority over playlist-level administrative operations.

Implement authorization rules for:

* Editing metadata
* Changing visibility
* Enabling/disabling collaboration
* Managing collaborators
* Deleting playlists
* Managing artwork
* Managing permissions

Never trust a client-provided owner identifier.

Ownership must come from authenticated server-side identity and database relationships.

---

# 13. Playlist Items

Implement playlist track membership.

A playlist item should support appropriate information such as:

* Playlist ID
* Track ID
* Stable item ID where useful
* Position/order
* Added by user
* Added timestamp
* Optional snapshot/version information if justified

Do not duplicate the complete Track entity inside PlaylistItem.

Reference the authoritative catalog Track entity.

The system must support:

* Add track
* Remove track
* Retrieve playlist tracks
* Retrieve item metadata
* Reorder tracks
* Bulk mutations where justified

Avoid inefficient per-item queries.

---

# 14. Playlist Ordering

Playlist ordering is a concurrency-sensitive operation.

Design it carefully.

The implementation must handle:

* Concurrent inserts
* Concurrent removals
* Concurrent reorders
* Multiple devices modifying the same playlist
* Stale clients
* Retry requests
* Duplicate requests

Choose an ordering strategy appropriate for PostgreSQL and the expected scale.

Possible approaches include:

* Integer positions with transactional resequencing
* Fractional ordering
* Lexicographic ordering keys
* Explicit revision-based mutation

Choose the strategy based on the repository architecture and scalability requirements.

Do not implement a fragile ordering mechanism merely because it is simpler.

---

# 15. Playlist Revision and Optimistic Concurrency

Where playlist mutation conflicts are possible, implement optimistic concurrency.

A playlist or playlist mutation model should have a safe revision/version mechanism where justified.

Clients may submit the revision they last observed.

If the playlist has changed since that revision:

* Detect the conflict
* Do not silently overwrite newer changes
* Return a deterministic conflict response
* Provide enough information for the client to refresh

Do not allow last-write-wins behavior to silently destroy playlist changes when stronger concurrency protection is appropriate.

---

# 16. Collaborative Playlists

Implement collaborative playlist support.

Requirements include:

* Owner enables/disables collaboration
* Authorized collaborators can add tracks
* Authorized collaborators can remove tracks
* Authorized collaborators can reorder tracks where permitted
* Owner can manage collaborators
* Collaborator permissions are server-enforced
* Non-collaborators cannot mutate collaborative playlists
* Read access still follows playlist visibility rules

Define a clear authorization model.

Potential roles:

* OWNER
* EDITOR
* VIEWER

Only introduce roles that are actually needed.

Do not allow users to grant themselves collaboration privileges.

---

# 17. Collaborator Management

Implement appropriate APIs for:

* Add collaborator
* Remove collaborator
* List collaborators
* Update collaborator permission where supported

Authorization must be checked for every operation.

The server must verify:

* Authenticated user
* Playlist ownership
* Existing collaborator status
* Playlist collaboration state
* Target user/resource validity

Prevent:

* Self-escalation
* Unauthorized collaborator insertion
* IDOR
* Permission bypass
* Modification of playlists the user does not control

---

# 18. Playlist Deletion

Implement safe playlist deletion.

Determine the correct lifecycle strategy based on the repository architecture.

Consider:

* Referential integrity
* Saved playlists
* Collaborators
* Playlist items
* Events
* Caches
* Search projections
* Future recommendation consumers

If hard deletion is safe, use it.

If a lifecycle state is necessary, implement it explicitly.

Do not leave orphaned playlist items or broken relationships.

Deletion must be transactional.

---

# 19. Cache Strategy

Use Redis only for appropriate acceleration and ephemeral state.

Potential cache targets:

* Public playlist metadata
* Frequently accessed playlist summaries
* Follow state
* Library summaries
* Permission lookups where justified

Every cache must define:

* Key format
* TTL
* Invalidation trigger
* Stale-data behavior
* Failure behavior

Database remains authoritative.

Playlist mutation must invalidate or update affected cache entries.

Library mutations must not leave indefinitely stale library state.

Never make correctness depend exclusively on Redis availability.

---

# 20. Events and Outbox Integration

Where the repository uses an event-driven architecture, emit durable domain events for relevant mutations.

Potential events include:

```text
TrackLiked
TrackUnliked
AlbumSaved
AlbumUnsaved
PlaylistCreated
PlaylistUpdated
PlaylistDeleted
PlaylistTrackAdded
PlaylistTrackRemoved
PlaylistReordered
PlaylistCollaboratorAdded
PlaylistCollaboratorRemoved
ArtistFollowed
ArtistUnfollowed
UserFollowed
UserUnfollowed
```

Use the actual event naming/versioning conventions established in the repository.

Events should include appropriate metadata such as:

* Event ID
* Event type
* Event version
* Aggregate ID
* Actor/user ID where appropriate
* Timestamp
* Correlation ID
* Trace context where supported
* Safe domain payload

Do not publish sensitive information unnecessarily.

If PostgreSQL state and event publication must remain consistent, use the existing transactional outbox mechanism or implement one if this repository lacks the necessary foundation and it is required by the architecture.

Do not rely on an unsafe pattern where a database transaction commits successfully but event publication silently fails.

---

# 21. Idempotency

Library and playlist mutations must be safe under retries.

Consider duplicate requests caused by:

* Mobile network retries
* HTTP client retries
* User double taps
* Multiple devices
* Worker retries
* Connection failures after server-side success

Use:

* Unique constraints
* Idempotency keys where appropriate
* Transactional checks
* Version checks
* Deterministic mutation semantics

Do not create duplicate library relationships or duplicate playlist operations because of retry behavior.

---

# 22. Transactions

Use PostgreSQL transactions for operations that require atomicity.

Examples:

* Creating playlist and initial metadata
* Adding/removing playlist items when ordering must remain consistent
* Reordering playlist items
* Collaborator changes
* Playlist deletion
* Library mutation plus required durable event/outbox record

Keep transactions appropriately scoped.

Do not hold transactions open while performing slow external operations.

---

# 23. Database Design

Update Prisma models and migrations as necessary.

Requirements:

* Foreign keys
* Appropriate cascading behavior
* Unique constraints
* Composite indexes
* Query-oriented indexes
* Timestamp indexes where useful
* Efficient pagination support
* Deterministic ordering
* Referential integrity

Design for users with:

* Thousands of liked tracks
* Thousands of saved albums
* Hundreds/thousands of playlists
* Large playlists
* Large follower/following graphs

Do not optimize only for toy datasets.

---

# 24. Pagination

Implement production-grade pagination.

Prefer cursor-based pagination for large, mutable collections where appropriate.

Pagination must be:

* Deterministic
* Stable
* Efficient
* Resistant to duplicates
* Resistant to skipped records

Apply this to:

* Liked tracks
* Saved albums
* Saved playlists
* Followers
* Following
* Playlist items
* Collaborators

Follow existing repository pagination conventions.

---

# 25. API Contracts

Implement complete REST APIs following existing repository conventions.

Every endpoint must define:

* Request DTO
* Response DTO
* Validation
* Authentication requirements
* Authorization rules
* Error semantics
* Pagination semantics
* OpenAPI documentation

Do not expose Prisma entities directly as API responses.

Map internal persistence/domain structures into stable API contracts.

Do not leak:

* Password hashes
* Session secrets
* Internal identifiers that should remain private
* Storage credentials
* Internal database details
* Private user information

---

# 26. Error Handling

Use explicit domain/API errors.

Examples:

* Playlist not found
* Track not found
* Album not found
* Unauthorized
* Forbidden
* Invalid playlist name
* Invalid visibility
* Collaboration disabled
* Insufficient playlist permission
* Revision conflict
* Invalid pagination cursor
* Duplicate mutation where relevant

Do not return vague internal errors to clients.

Do not expose stack traces or database internals in production responses.

---

# 27. Security

Perform a security review of every new endpoint.

Specifically defend against:

* IDOR
* Broken access control
* Privilege escalation
* Unauthorized playlist modification
* Unauthorized library modification
* User enumeration
* Private playlist disclosure
* Mass assignment
* Parameter tampering
* SQL injection
* XSS through playlist metadata
* Malicious identifiers
* Rate-limit bypass
* Abuse of collaboration endpoints
* Oversized request bodies
* Resource exhaustion

Authorization must always be enforced server-side.

Never trust:

* User IDs
* Owner IDs
* Collaborator IDs
* Permission values
* Playlist visibility
* Track ownership claims
* Client-generated authorization decisions

---

# 28. Rate Limiting and Abuse Prevention

Apply appropriate rate limits to mutation-heavy endpoints.

Pay particular attention to:

* Playlist creation
* Bulk playlist mutations
* Track likes
* Saves
* Follows
* Collaborator management
* Reordering
* Public playlist retrieval if abuse risk exists

Do not use one arbitrary global rate limit for every endpoint.

Follow existing Redis-based rate-limiting infrastructure.

---

# 29. Privacy

Respect privacy requirements across:

* Private playlists
* User libraries
* Follow relationships
* Collaborator lists
* User profile data
* Audit logs
* Events
* Caches

Do not expose private library state through:

* Public APIs
* Search indexes
* Events
* Logs
* Analytics payloads
* Error responses

Any future search/recommendation integration must receive only data that is authorized and appropriate to expose.

---

# 30. Observability

Instrument important operations.

Capture:

* Request latency
* Error rates
* Database latency
* Redis latency
* Transaction failures
* Playlist mutation conflicts
* Library mutation failures
* Authorization failures
* Event/outbox failures
* Cache hit/miss rates where useful

Use the repository's observability stack.

Logs must contain useful structured context without exposing:

* Passwords
* Tokens
* Session secrets
* Sensitive private library contents
* Credentials
* Unnecessary personal data

---

# 31. Testing

Add comprehensive tests.

At minimum include:

## Unit tests

Test:

* Library services
* Playlist services
* Authorization policies
* Permission evaluation
* Ordering logic
* Revision/conflict logic
* Validation
* Event construction

## Integration tests

Test:

* PostgreSQL persistence
* Prisma transactions
* Redis behavior
* Cache invalidation
* Outbox behavior

## API tests

Test:

* Authentication
* Authorization
* Validation
* Pagination
* Error responses
* Mutation semantics

## Security tests

Explicitly test:

* IDOR
* Private playlist access
* Unauthorized playlist mutation
* Unauthorized collaborator changes
* Library access between users
* Permission escalation
* User enumeration behavior

## Concurrency tests

Test:

* Simultaneous playlist mutations
* Simultaneous reorder operations
* Duplicate like requests
* Duplicate save requests
* Concurrent collaborator updates
* Stale revision mutations

## Regression tests

Ensure existing authentication, user, catalog, and other previously implemented backend functionality remains functional.

---

# 32. Performance

Review database queries for:

* N+1 behavior
* Missing indexes
* Excessive joins
* Inefficient count operations
* Large offset pagination
* Unnecessary payloads
* Repeated permission queries

Use:

* Proper indexes
* Cursor pagination
* Batched queries
* Prisma transactions
* Redis caching where justified

Do not prematurely optimize without understanding actual access patterns.

---

# 33. Documentation

Update backend documentation as necessary.

Document:

* Library API
* Playlist API
* Follow API
* Collaboration permissions
* Visibility rules
* Pagination
* Concurrency/revision behavior
* Error semantics
* Events
* Cache behavior
* Database migrations
* Testing procedures

Update OpenAPI/Swagger definitions.

Documentation must describe actual implemented behavior.

Do not document functionality that does not exist.

---

# 34. Explicitly Deferred Scope

Do NOT implement the following as complete systems in this volume:

* Audio streaming
* HLS generation
* FFmpeg transcoding
* S3 media processing
* CloudFront delivery
* Playback sessions
* Playback authorization
* Offline downloads
* Search
* Elasticsearch/OpenSearch indexing
* Recommendation engine
* Personalized recommendations
* Subscription billing
* Stripe/payment integration
* Advertising
* Push notifications
* Full analytics pipeline
* Artist royalty calculations
* Full music licensing workflows
* Social feed
* Real-time chat

Only create integration boundaries/events if required for the currently implemented domains.

Do not create fake implementations for deferred systems.

---

# 35. Repository Integrity

Before modifying anything:

1. Inspect the repository.
2. Identify existing implementations.
3. Determine the correct integration points.
4. Reuse compatible abstractions.
5. Make minimal safe changes.
6. Preserve backward compatibility.
7. Avoid regenerating unchanged files.

Never create a parallel architecture merely to satisfy this prompt.

---

# 36. Validation

Before declaring the volume complete:

* Run formatting.
* Run linting.
* Run TypeScript compilation/type checking.
* Run relevant unit tests.
* Run integration tests where available.
* Run API tests.
* Run database migration validation.
* Verify Prisma schema consistency.
* Verify OpenAPI generation.
* Verify Docker/build compatibility where applicable.
* Verify no secrets were introduced.
* Verify no TODO/FIXME placeholders were introduced.
* Verify no pseudo-code remains.
* Verify existing functionality has not regressed.

Fix discovered problems before completion.

Do not report tests as passing unless they actually ran successfully.

---

# 37. Completion Report

At the end, provide a factual implementation report containing:

## Implemented

List the functionality actually implemented.

## Files Changed

List files created or modified.

## Database Changes

Describe:

* Models
* Relationships
* Constraints
* Indexes
* Migrations

## APIs Added or Changed

List the actual endpoints.

## Events

List implemented domain events/outbox changes.

## Security

Summarize authorization and security controls.

## Tests

Report the actual commands executed and their real results.

## Validation

Report actual:

* Type-check result
* Lint result
* Test result
* Build result
* Migration result

## Deferred

List functionality intentionally left for later volumes.

Never claim something was implemented if it was not actually implemented.

---

# 38. Final Engineering Rule

The result must be production-grade backend software, not a demonstration.

Every implementation must be:

* Complete
* Typed
* Tested
* Secure
* Observable
* Transactionally correct
* Concurrency-aware
* Maintainable
* Scalable
* Compatible with the existing repository
* Ready for integration with future playback, search, recommendation, notification, subscription, and analytics systems

Never use:

* Pseudo-code
* Placeholders
* TODO comments
* FIXME comments
* Fake integrations
* Fake provider responses
* Hardcoded secrets
* Incomplete implementations
* “Implement similarly”
* “For brevity”
* “Remaining code omitted”
* “Left as an exercise”

Do not stop after creating scaffolding.

Implement the actual functionality required by this volume, validate it, and report the factual repository state.
