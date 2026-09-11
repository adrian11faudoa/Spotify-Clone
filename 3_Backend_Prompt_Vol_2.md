# Spotify-Style Music Streaming Platform — Backend Prompt — Volume 2

## ROLE

Act as the senior backend engineering team responsible for implementing the production-grade **music catalog and content domain** of an original Spotify-style music streaming platform.

Act as:

* Principal Software Architect
* Staff Backend Engineer
* Database Architect
* Domain-Driven Design Engineer
* Security Engineer
* Media Platform Engineer
* QA Engineer

You are not acting as a programming tutor.

Implement real production-quality functionality in the existing repository.

Do not produce pseudo-code, placeholders, TODOs, FIXME comments, fake APIs, fake provider behavior, incomplete implementations, or merely descriptive answers.

The repository is the source of truth.

---

# 1. PROJECT

Build the catalog/content backend for an original music streaming platform.

The platform must support a production-quality catalog containing:

* artists
* albums
* tracks
* genres
* releases
* track/artist relationships
* album/artist relationships
* artwork references
* audio-media references
* catalog availability
* publishing lifecycle
* explicit-content metadata
* identifiers
* track ordering
* multi-disc releases
* catalog administration

The implementation must be original and independent from Spotify's proprietary code, private APIs, or internal architecture.

---

# 2. TECHNOLOGY

Use the repository's compatible implementation of:

* Node.js
* NestJS
* TypeScript
* PostgreSQL
* Prisma
* Redis where useful
* REST
* OpenAPI/Swagger
* BullMQ where asynchronous processing is required

Do not introduce unnecessary technologies.

Search infrastructure, media processing, subscriptions, recommendations, playlists, playback, and other later domains should only be implemented here when required as an explicit dependency of catalog functionality.

---

# 3. REPOSITORY-FIRST REQUIREMENT

Before modifying anything:

1. Inspect the repository.
2. Inspect the existing backend.
3. Inspect NestJS modules.
4. Inspect Prisma schema and migrations.
5. Inspect existing User/Identity functionality.
6. Inspect authorization.
7. Inspect API conventions.
8. Inspect media/storage infrastructure.
9. Inspect Redis/BullMQ infrastructure.
10. Inspect event/outbox infrastructure.
11. Inspect tests.
12. Inspect documentation.

Determine what already exists.

If catalog functionality is partially implemented:

* reuse it
* complete it
* migrate it safely
* do not create duplicate models
* do not create duplicate controllers
* do not create parallel catalog services

The repository's actual implementation takes precedence over assumptions.

---

# 4. DOMAIN BOUNDARY

Establish a clear Catalog domain.

The catalog domain owns:

* artist metadata
* album metadata
* track metadata
* genre metadata
* releases
* catalog relationships
* publication state
* content visibility
* catalog identifiers
* media references
* availability metadata

It does not own:

* user authentication
* playlist ownership
* user likes
* playback sessions
* recommendation ranking
* payment processing

Those belong to other domains.

Catalog may expose contracts consumed by those domains.

---

# 5. CORE DOMAIN MODEL

Implement or safely adapt the following entities.

## Artist

Support appropriate fields such as:

* id
* name
* normalized name
* biography
* profile artwork reference
* status
* verification state where appropriate
* createdAt
* updatedAt
* publishedAt
* deletedAt where appropriate

Do not collect unnecessary personal information.

---

## Album

Support:

* id
* title
* normalized title
* album type
* release date
* artwork reference
* status
* explicit-content metadata where applicable
* createdAt
* updatedAt
* publishedAt
* deletedAt where appropriate

Album types may include:

* ALBUM
* SINGLE
* EP
* COMPILATION

Use the actual repository-compatible enum structure.

---

## Track

Support appropriate fields such as:

* id
* title
* normalized title
* duration
* track number
* disc number
* album ID where applicable
* explicit flag
* status
* release date/reference
* ISRC or equivalent identifier where legitimately available
* artwork override/reference where appropriate
* audio media reference
* createdAt
* updatedAt
* publishedAt
* deletedAt where appropriate

Do not store derived streaming data as authoritative catalog metadata unless justified.

---

## Genre

Support:

* id
* name
* normalized name
* description where useful
* status where appropriate
* timestamps

Prevent duplicate genres through database constraints.

---

# 6. ARTIST RELATIONSHIPS

Support tracks involving:

* primary artists
* featured artists
* multiple artists

Do not store a single artist ID on Track if the product needs many-to-many artist relationships.

Create an explicit relationship model where appropriate.

Relationship metadata may include:

* artist
* track
* role
* ordering

Roles may include:

* PRIMARY
* FEATURED
* REMIXER
* PRODUCER

Only implement roles actually required by the product.

---

# 7. ALBUM ARTIST RELATIONSHIPS

Support albums with multiple artists where required.

Define:

* album
* artist
* role
* ordering

Do not assume every album has exactly one artist.

---

# 8. TRACK/GENRE RELATIONSHIPS

Support tracks belonging to multiple genres when appropriate.

Enforce uniqueness at the database level.

Avoid duplicate associations.

---

# 9. RELEASE MODEL

Where the product requires a distinction between an album's conceptual metadata and a specific release/version, implement an explicit Release model.

A release may represent:

* release date
* market/territory
* format
* version
* availability
* release status

Do not create a Release entity merely for abstraction if the actual product does not require it.

If the repository already contains a release model, preserve it.

---

# 10. CONTENT LIFECYCLE

Define explicit catalog states.

Use repository-compatible states such as:

* DRAFT
* PROCESSING
* PENDING_REVIEW
* PUBLISHED
* HIDDEN
* ARCHIVED
* REMOVED

Not every entity must use every state.

Define valid transitions.

For example:

DRAFT → PROCESSING
PROCESSING → PENDING_REVIEW
PENDING_REVIEW → PUBLISHED
PENDING_REVIEW → HIDDEN
PUBLISHED → HIDDEN
PUBLISHED → ARCHIVED
HIDDEN → PUBLISHED
ARCHIVED → REMOVED

Do not permit arbitrary state mutation.

All transitions must be validated server-side.

---

# 11. PUBLIC VISIBILITY

Define what catalog content is publicly visible.

At minimum, unpublished content must not be exposed through ordinary consumer APIs.

Prevent:

* draft tracks appearing in search
* unpublished albums appearing in public endpoints
* hidden artists appearing as normal public entities
* removed media remaining playable
* administrative metadata leaking through consumer responses

Visibility must be enforced server-side.

---

# 12. ARTIST MANAGEMENT

Implement appropriate artist management APIs.

Potential operations:

* create artist
* update artist
* retrieve artist
* list artists
* publish artist
* hide artist
* archive artist

Authorization must distinguish:

* ordinary users
* authorized artist/content managers
* administrators

Do not automatically allow every authenticated user to create or modify published catalog content.

---

# 13. ALBUM MANAGEMENT

Implement appropriate APIs for:

* album creation
* album update
* album retrieval
* album listing
* album publication
* album hiding
* album archival

Validate:

* artist relationships
* album metadata
* release information
* artwork references
* track relationships

Do not permit unauthorized users to modify another organization's catalog.

---

# 14. TRACK MANAGEMENT

Implement appropriate APIs for:

* create track
* update track
* retrieve track
* list tracks
* publish track
* hide track
* archive/remove track

Validate:

* album relationships
* artists
* duration
* track/disc number
* explicit flag
* identifiers
* media references
* status

Do not expose private processing metadata through public track responses.

---

# 15. GENRE MANAGEMENT

Implement controlled genre operations.

If genres are administrator-managed:

* restrict creation
* restrict modification
* prevent deletion when referenced
* use safe lifecycle behavior

If deletion is necessary, use a controlled migration strategy rather than violating foreign-key relationships.

---

# 16. TRACK ORDERING

For album tracks support:

* disc number
* track number
* deterministic ordering

Prevent duplicate ordering within the same disc/release where the business rules require uniqueness.

Define database constraints where practical.

Do not depend solely on application validation.

---

# 17. MULTI-DISC ALBUMS

Support albums containing multiple discs.

Track ordering must be deterministic using appropriate fields such as:

* disc number
* track number
* stable identifier

The API should return tracks in canonical order.

---

# 18. METADATA VALIDATION

Validate:

* title length
* artist name length
* biography length
* genre names
* duration
* track numbers
* disc numbers
* identifiers
* dates
* enum values
* media references

Reject invalid or malicious input.

Do not accept arbitrary unvalidated JSON as catalog metadata.

---

# 19. NORMALIZATION

Implement deterministic normalization for searchable fields such as:

* artist names
* album titles
* track titles
* genre names

Normalization may include:

* trimming
* Unicode-aware normalization where appropriate
* case normalization

Do not destroy the original display value.

Store normalized representations separately where useful.

---

# 20. IDENTIFIERS

Where applicable support legitimate music identifiers such as:

* ISRC
* UPC/EAN
* catalog identifiers

Do not invent identifiers.

Validate format where reliable validation rules exist.

Define uniqueness according to the business semantics.

---

# 21. ARTWORK REFERENCES

Integrate with the repository's existing media/storage architecture.

The catalog should reference media assets rather than embedding binary files in PostgreSQL.

Support appropriate artwork references for:

* artist
* album
* track
* release

Do not expose private storage credentials.

Do not allow arbitrary object paths from clients to bypass ownership or authorization.

---

# 22. AUDIO MEDIA REFERENCES

Track records may reference processed audio/media assets.

Do not make a track playable merely because an arbitrary S3 key was supplied.

Validate:

* media asset ownership
* processing state
* content type
* availability
* catalog relationship

The actual audio-processing and adaptive streaming pipeline may be implemented in a dedicated later backend volume.

---

# 23. MEDIA PROCESSING STATE

If the existing repository already supports media processing, integrate with it.

If catalog needs a processing relationship, support explicit states such as:

* NOT_READY
* QUEUED
* PROCESSING
* READY
* FAILED
* INVALID

Do not claim audio is streamable until the required processing state is actually complete.

---

# 24. ADMINISTRATION

Implement secure administrative catalog operations.

Administrative users may need to:

* review content
* publish content
* hide content
* archive content
* remove content
* inspect processing state

Every privileged operation must:

* authenticate the actor
* authorize the permission
* validate the target
* create an audit record where appropriate

Do not create hidden administrative endpoints.

---

# 25. ARTIST CONTENT PERMISSIONS

If the product supports artist/content-owner accounts, implement ownership boundaries.

An artist/content manager may modify only catalog entities they are authorized to manage.

Prevent IDOR such as:

`PATCH /artists/{anotherArtistId}`

succeeding merely because the caller is authenticated.

Authorization must be based on server-side ownership/permission checks.

---

# 26. SOFT DELETION AND LIFECYCLE

Use soft deletion where historical references require it.

Consider references from:

* playlists
* likes
* playback history
* analytics
* search indexes
* recommendations

Deleting a track must not automatically destroy historical playback records.

Define what happens to:

* playlist references
* library references
* search documents
* cached responses
* recommendations

---

# 27. CATALOG API DESIGN

Use versioned REST APIs.

Potential API structure:

* `/api/v1/artists`
* `/api/v1/albums`
* `/api/v1/tracks`
* `/api/v1/genres`

Use the repository's actual routing conventions when they differ.

Support:

* retrieval
* listing
* filtering where justified
* sorting
* pagination
* state transitions for authorized users

Do not expose internal database structures directly.

---

# 28. PUBLIC CATALOG ENDPOINTS

Public/consumer endpoints should return only published/visible content.

Potential operations:

* artist detail
* artist albums
* artist tracks
* album detail
* album tracks
* track detail
* genre detail
* genre tracks

Implement appropriate pagination.

Avoid unrestricted track or album lists.

---

# 29. ADMIN CATALOG ENDPOINTS

Administrative endpoints may expose additional lifecycle information.

Separate administrative responses from public responses.

Do not leak:

* internal storage paths
* processing credentials
* security metadata
* private ownership data
* internal provider responses

---

# 30. RESPONSE CONTRACTS

Use explicit response DTOs.

Public track responses may include:

* ID
* title
* duration
* artists
* album
* artwork
* explicit status
* availability

They should not include:

* database internals
* raw S3 keys
* private processing logs
* secret provider metadata

---

# 31. PAGINATION

Use bounded pagination.

For potentially large collections support cursor pagination where appropriate.

Relevant collections include:

* artists
* albums
* tracks
* artist releases
* album tracks
* genre tracks

Define:

* maximum page size
* stable ordering
* cursor validation
* next cursor

Do not allow unbounded queries.

---

# 32. CACHING

Use Redis only where caching provides a measurable benefit.

Potential cache targets:

* published artist metadata
* published album metadata
* published track metadata
* genre metadata

Define:

* key format
* TTL
* invalidation
* stale behavior

Catalog mutations must invalidate or update affected cache entries.

Never allow stale private/admin content to leak through a public cache.

---

# 33. SEARCH INTEGRATION BOUNDARY

Do not fully implement the search engine in this volume unless the repository already requires it.

However, catalog mutations must expose clean events/contracts for future indexing.

Potential events:

* ArtistCreated
* ArtistUpdated
* ArtistPublished
* ArtistHidden
* AlbumCreated
* AlbumUpdated
* AlbumPublished
* AlbumHidden
* TrackCreated
* TrackUpdated
* TrackPublished
* TrackHidden
* TrackRemoved

Use the repository's actual event naming conventions.

Events must be versioned.

---

# 34. OUTBOX / EVENT CONSISTENCY

When a catalog mutation must generate an event:

Use a transactional strategy so that:

* catalog state
* outbox record

are committed consistently.

Do not create a state change successfully and silently lose the corresponding indexing/event operation.

Consumers must be able to tolerate duplicates.

---

# 35. EVENT PAYLOADS

Events should contain safe information such as:

* event ID
* event type
* version
* aggregate/entity ID
* timestamp
* producer
* correlation ID
* trace context where available
* relevant metadata

Do not place:

* secrets
* raw credentials
* private provider tokens
* unnecessary personal information

in catalog events.

---

# 36. CONCURRENCY

Protect against concurrent modifications.

Examples:

* two users modifying an artist
* simultaneous album publication
* simultaneous track ordering changes
* repeated state transitions
* duplicate catalog creation requests

Use:

* database constraints
* transactions
* optimistic concurrency where appropriate
* idempotency where necessary

Do not rely only on application-level checks.

---

# 37. IDEMPOTENCY

Mutations that can be retried should be safely repeatable where appropriate.

Consider:

* content creation
* media association
* publication
* processing-trigger requests
* event handling

Do not create duplicate records because an HTTP request was retried.

---

# 38. DATABASE CONSTRAINTS

Use PostgreSQL constraints for important invariants.

Examples:

* unique normalized genre names
* unique identifiers where required
* unique track/genre relationships
* unique album/artist relationships
* unique track/artist relationships
* valid foreign keys
* valid ordering constraints where practical

Application validation remains necessary, but database constraints must protect authoritative state.

---

# 39. TRANSACTIONS

Use transactions for multi-record mutations requiring atomicity.

Examples:

* album + artist relationships
* track + artist relationships
* track + genre relationships
* publication state changes with outbox records
* deletion/archive operations with dependent state updates

Do not perform long-running external API calls inside transactions.

---

# 40. SECURITY

Protect catalog APIs against:

* IDOR
* unauthorized publication
* unauthorized modification
* privilege escalation
* injection
* malicious metadata
* oversized payloads
* enumeration
* rate-limit bypass

Never trust:

* client-provided ownership
* client-provided publication status
* client-provided authorization roles
* client-provided media readiness

---

# 41. RATE LIMITING

Apply appropriate rate limits to:

* public catalog APIs
* catalog search-like listing operations
* administrative mutations
* publication operations
* media-association operations

Use Redis-backed distributed rate limiting if required by the deployment model.

Avoid making public read APIs unusably restrictive.

---

# 42. AUDITING

Audit important administrative/content-management operations.

Record:

* actor
* action
* entity
* timestamp
* request ID
* correlation ID
* safe metadata

Potential audited actions:

* artist publication
* album publication
* track publication
* content hiding
* archival
* removal
* ownership changes
* metadata changes by privileged users

Do not log secrets or unnecessary private data.

---

# 43. TESTING

Implement meaningful tests.

## Artist

Test:

* creation
* retrieval
* update
* authorization
* publication
* hiding
* duplicate handling

## Album

Test:

* creation
* artist relationships
* retrieval
* track association
* ordering
* publication
* authorization

## Track

Test:

* creation
* artist relationships
* album association
* genres
* duration validation
* identifiers
* publication
* visibility

## Genres

Test:

* creation
* duplicate prevention
* relationships
* authorization

---

# 44. SECURITY TESTS

Explicitly test:

* ordinary user cannot publish catalog content without permission
* user cannot modify another artist's content
* user cannot access unpublished content through public APIs
* hidden content is not exposed
* removed content cannot be accessed as normal published content
* raw storage paths are not exposed unnecessarily
* invalid IDs cannot bypass authorization
* admin endpoints reject ordinary users
* malformed metadata is rejected
* oversized requests are rejected

---

# 45. API TESTS

Test:

* authentication
* authorization
* validation
* status transitions
* pagination
* filtering
* errors
* response DTOs
* cache behavior where implemented

Verify actual HTTP behavior rather than testing only internal services.

---

# 46. MIGRATIONS

Create safe Prisma migrations.

Validate:

* clean database setup
* migration against existing repository state
* constraints
* indexes
* relationships
* enum changes
* data preservation

Never reset the production database.

Never silently delete existing catalog data.

If existing schema conflicts with the desired model, migrate deliberately.

---

# 47. DOCUMENTATION

Update documentation for:

* catalog domain
* API endpoints
* catalog lifecycle
* permissions
* database model
* media relationships
* event contracts
* development setup
* testing

Documentation must describe actual implementation.

---

# 48. PERFORMANCE

Avoid:

* N+1 artist queries
* N+1 album queries
* N+1 track queries
* unbounded catalog queries
* expensive relationship loading
* unnecessary serialization

Use appropriate:

* indexes
* joins/includes
* pagination
* caching

Measure queries where necessary.

---

# 49. FUTURE DOMAIN COMPATIBILITY

The catalog implementation must integrate cleanly with future:

* playlist
* library
* playback
* media
* search
* recommendation
* subscription
* analytics

Do not redesign those domains here.

Expose stable domain/API/event contracts.

---

# 50. DO NOT IMPLEMENT HERE

Do not fully implement:

* user playlists
* liked music
* playback sessions
* playback queue
* playback engine
* HLS delivery
* audio transcoding pipeline
* search engine implementation
* recommendation engine
* subscription billing
* notification system
* analytics platform

Only implement the boundaries necessary for clean integration.

---

# 51. PROHIBITED IMPLEMENTATION

Never:

* create fake music provider integrations
* invent external catalog APIs
* fabricate licensing information
* claim legal music rights
* use copyrighted music as production seed data
* hardcode fake production credentials
* expose private S3 credentials
* allow arbitrary S3 object access
* use client-controlled publication state
* create unrestricted admin access
* bypass authorization for convenience
* create TODO implementations
* create placeholder services
* weaken security for tests

If seed data is needed for development, make it clearly development/test data and keep it separate from production behavior.

---

# 52. VALIDATION

Before finishing:

Run the actual applicable repository commands for:

* lint
* formatting
* TypeScript
* Prisma validation
* migrations
* unit tests
* integration tests
* API tests
* build

Inspect the final diff.

Verify:

* no secrets
* no duplicate models
* no duplicate controllers
* no unrelated modifications
* no broken existing APIs
* no invalid migrations
* no failing relevant tests

---

# 53. COMPLETION REPORT

Provide a factual report containing:

## Repository Audit

What catalog-related functionality already existed.

## Implemented

Actual:

* modules
* entities
* migrations
* APIs
* authorization
* events
* caching
* tests
* documentation

## Validation

Actual commands executed and their results.

## Deferred

Catalog-adjacent functionality intentionally reserved for later volumes.

## External Configuration

Any genuinely required external configuration.

## Known Issues

Actual limitations or unresolved issues.

Do not claim production readiness unless the repository evidence supports it.

---

# 54. STANDALONE REQUIREMENT

This prompt is fully standalone.

It must not require:

* another prompt
* a previous architecture response
* a previously approved design
* hidden conversation context

The repository is the source of truth.

Inspect actual repository state before implementing.

---

# FINAL OBJECTIVE

Leave the repository with a secure, maintainable, production-quality music catalog backend supporting:

* artists
* albums
* tracks
* genres
* releases where justified
* artist relationships
* album relationships
* track relationships
* metadata
* identifiers
* artwork references
* audio-media references
* catalog lifecycle
* publication
* visibility
* authorization
* administrative management
* auditability
* cache behavior where justified
* event contracts
* database integrity
* comprehensive tests

The implementation must provide a solid authoritative catalog foundation for the later playlist, playback, media streaming, search, recommendation, subscription, analytics, and notification systems.
