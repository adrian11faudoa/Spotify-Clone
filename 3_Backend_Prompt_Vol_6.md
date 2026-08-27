You are operating in Senior Engineering Team Mode.

Build the production-ready backend for search, discovery, recommendations, personalization, radio, stations, charts, trending content, and discovery feeds for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must follow the approved Spotify-like architecture, domain boundaries, catalog architecture, playback architecture, playlist architecture, library architecture, entitlement model, event architecture, Redis strategy, API conventions, security model, and Project Index.

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

• Track search
• Artist search
• Album search
• Playlist search
• Podcast search integration
• Episode search integration
• Genre search
• Search autocomplete
• Search suggestions
• Typo tolerance
• Language-aware search
• Search ranking
• Search filters
• Personalized discovery
• Home feed
• New releases
• Trending music
• Popular content
• Similar tracks
• Similar artists
• Genre discovery
• Personalized playlists
• Radio
• Artist radio
• Track radio
• Genre radio
• Personalized stations
• Charts
• Global charts
• Regional charts
• Genre charts
• Time-windowed rankings
• Recommendation events
• Recommendation caching
• Discovery analytics

The implementation must support:

• Hundreds of millions of users
• Millions of tracks
• Millions of artists/albums/playlists
• Large search traffic
• Large recommendation traffic
• High discovery traffic
• Global operations
• Multiple languages
• Regional content
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

Search:

• Elasticsearch or OpenSearch

Event Streaming:

• Kafka or Redpanda

Background Processing:

• BullMQ

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

Keep business logic outside controllers.

Use repositories for persistence.

Use DTOs for API contracts.

Use centralized validation.

Use centralized error handling.

Use structured logging.

Use the established observability infrastructure.

Recommendation failures must never block playback, product/content access, playlists, or core account functionality.

────────────────────────────────────────

DOMAIN OWNERSHIP

Maintain explicit boundaries between:

• Search
• Search indexing
• Search analytics
• Discovery
• Recommendations
• Personalization
• Radio
• Stations
• Charts
• Trending
• Editorial content

Do not combine:

• Search indexing with transactional catalog storage
• Recommendation state with playback state
• Radio generation with the persistent user library
• Chart aggregation with transactional catalog operations

Search and recommendation systems are derived systems.

Catalog and user-owned data remain authoritative elsewhere.

────────────────────────────────────────

SEARCH DOMAIN

Implement:

• Search tracks
• Search artists
• Search albums
• Search playlists
• Search podcasts where available
• Search episodes where available
• Search genres
• Search suggestions
• Autocomplete

Support:

• Full-text search
• Prefix search
• Typo tolerance
• Language-aware analysis
• Synonyms
• Ranking
• Filters
• Pagination
• Cursor pagination where appropriate

────────────────────────────────────────

SEARCH INDEXES

Define and implement search-index integration for:

TRACKS

• Title
• Artist
• Album
• Genre
• Tags
• Popularity
• Release date
• Explicit flag
• Region availability

ARTISTS

• Name
• Aliases
• Genres
• Popularity
• Localization

ALBUMS

• Title
• Artist
• Release date
• Genre
• Popularity

PLAYLISTS

• Name
• Description
• Public owner information
• Genre/tags
• Popularity

PODCASTS

• Show title
• Description
• Hosts
• Categories

EPISODES

• Title
• Description
• Show
• Categories

Private user data must never become publicly searchable.

────────────────────────────────────────

SEARCH INDEX OWNERSHIP

Define:

• Index owner
• Index version
• Mapping
• Analyzer
• Shards
• Replicas
• Alias strategy
• Reindex strategy

Search indexes must be rebuildable from authoritative data.

────────────────────────────────────────

SEARCH INDEXING

Consume catalog/library events such as:

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
• PlaylistCreated
• PlaylistUpdated
• PlaylistDeleted
• PodcastCreated
• EpisodeCreated
• ContentAvailabilityChanged

Indexing must be:

• Idempotent
• Retryable
• Observable

────────────────────────────────────────

SEARCH REINDEXING

Implement support for:

• Full reindex
• Incremental reindex
• Versioned indexes
• Alias switching
• Bulk indexing
• Partial failure recovery
• Failed-document retry
• Progress tracking
• Reindex cancellation where appropriate

Never block core catalog transactions while reindexing.

────────────────────────────────────────

SEARCH RANKING

Design ranking signals based on:

• Text relevance
• Popularity
• Recency
• Quality
• Regional relevance
• Availability
• User context where appropriate

Do not expose private behavioral information through public search rankings.

────────────────────────────────────────

SEARCH SUGGESTIONS

Implement autocomplete/suggestion infrastructure.

Support:

• Prefix matching
• Popularity
• Recency
• Typo tolerance
• Language
• Regionalization

Cache high-frequency suggestions where appropriate.

────────────────────────────────────────

SEARCH PRIVACY

Protect:

• Private playlists
• Private listening behavior
• Private profile information
• Private recommendation signals
• Private library state

Search results must honor:

• Publication state
• Region
• Content restrictions
• Explicit-content settings
• User permissions

────────────────────────────────────────

SEARCH ANALYTICS

Track:

• Search query
• Query timestamp
• Result count
• Clicked result
• Search abandonment
• Zero-result query
• Add-to-library after search
• Playback after search

Minimize personally identifiable information.

Define retention.

────────────────────────────────────────

DISCOVERY DOMAIN

Implement discovery feeds for:

• Home
• New releases
• Trending
• Popular music
• Personalized music
• Personalized playlists
• Genre discovery
• Similar artists
• Similar tracks
• Recently played
• Editorial collections

Define:

• Feed sections
• Ranking
• Candidate generation
• Eligibility
• Fallback
• Caching

────────────────────────────────────────

RECOMMENDATION ARCHITECTURE

Implement an extensible recommendation platform.

Support stages:

INITIAL

• Popularity
• Recency
• Genre
• Artist similarity
• Track similarity
• User history

EVOLVED

• Collaborative signals
• Behavioral features
• Candidate generation
• Ranking models

FUTURE

• ML ranking
• Real-time features
• Feature store
• Model serving
• Online experimentation

Do not require a full ML platform in the initial implementation.

────────────────────────────────────────

RECOMMENDATION CANDIDATES

Generate candidates from:

• User history
• Liked tracks
• Saved albums
• Followed artists
• Playlist activity
• Search behavior
• Similar users where privacy-safe
• Similar artists
• Similar tracks
• Trending
• Editorial content
• New releases
• Regional popularity

Apply filtering before ranking.

────────────────────────────────────────

RECOMMENDATION RANKING

Ranking may consider:

• Relevance
• User preference
• Recent activity
• Diversity
• Novelty
• Popularity
• Content availability
• Explicit-content policy
• Regional rights
• Subscription entitlement

Avoid recommending unavailable content.

────────────────────────────────────────

RECOMMENDATION DIVERSITY

Prevent recommendation feeds from becoming overly repetitive.

Support:

• Artist diversity
• Genre diversity
• Content freshness
• Exploration
• User preference balance

Define configurable diversity rules.

────────────────────────────────────────

RECOMMENDATION FALLBACKS

If personalized recommendations are unavailable, use:

• Trending
• Popular
• Regional popular
• Genre popular
• Editorial collections
• Recently played
• Similar content

Recommendation failures must not cause user-facing application failures.

────────────────────────────────────────

RECOMMENDATION CACHE

Use Redis for:

• Home feed
• Similar artists
• Similar tracks
• Trending content
• Personalized recommendations
• Radio candidate sets

Define:

• Key pattern
• TTL
• User/profile scope
• Invalidation
• Regeneration
• Cache stampede protection

Do not cache private results under shared keys.

────────────────────────────────────────

PERSONALIZATION PROFILE

Create a personalization representation based on:

• Liked tracks
• Saved albums
• Followed artists
• Playlist activity
• Listening history
• Search activity
• Recently played
• Skips
• Completions
• Genre preference
• Recency

The personalization profile is derived data.

Do not treat it as authoritative account data.

────────────────────────────────────────

PERSONALIZATION PRIVACY

Define strict access boundaries.

Personalization data must not be exposed to:

• Other users
• Artists
• Labels
• Ordinary support agents

Administrative access must be permission-controlled and auditable.

────────────────────────────────────────

RADIO DOMAIN

Implement:

• Track radio
• Artist radio
• Genre radio
• Personalized stations
• Mood stations where supported

A radio session should generate a dynamic sequence of content.

Do not permanently persist every generated radio queue unless required.

────────────────────────────────────────

RADIO CANDIDATE GENERATION

Generate radio candidates from:

• Similar artists
• Similar tracks
• Genre
• User preference
• Listening history
• Trending
• Editorial signals

Filter for:

• Rights
• Availability
• Explicit-content policy
• Region
• Subscription entitlement where applicable
• Recent-play duplication

────────────────────────────────────────

RADIO SESSION

Support:

• Radio session ID
• Seed
• Current position
• Candidate state
• Generated items
• Session expiration

Radio sessions should tolerate intermittent connectivity and client retries.

────────────────────────────────────────

RADIO DEDUPLICATION

Avoid:

• Same track repeated immediately
• Excessive same-artist repetition
• Recently played repetition

Define configurable windows for deduplication.

────────────────────────────────────────

CHARTS DOMAIN

Implement:

• Global charts
• Regional charts
• Genre charts
• Trending charts
• Time-window charts

Support periods such as:

• Daily
• Weekly
• Monthly
• Rolling windows

────────────────────────────────────────

CHART AGGREGATION

Build chart rankings from events such as:

• Playback completed
• Playback started
• Unique listener
• Save
• Follow

Define anti-abuse weighting.

Do not treat raw playback starts as automatically equivalent to valid chart activity.

────────────────────────────────────────

CHART SNAPSHOTS

Persist historical chart snapshots.

Support:

• Chart ID
• Period
• Region
• Ranking
• Score
• Content
• Generated timestamp

Historical charts must remain reproducible.

────────────────────────────────────────

TRENDING

Implement trending calculations.

Support:

• Global trends
• Regional trends
• Genre trends
• New-release trends

Define time windows and decay functions.

Use asynchronous processing.

────────────────────────────────────────

EDITORIAL CONTENT

Define an editorial-content boundary for curated experiences.

Support:

• Editorial playlists
• Featured artists
• Featured releases
• Curated collections
• Campaigns

Editorial content must be distinguishable from algorithmically generated recommendations.

────────────────────────────────────────

DISCOVERY EVENTS

Publish:

• SearchPerformed
• SearchResultClicked
• DiscoveryFeedServed
• RecommendationGenerated
• RecommendationServed
• RecommendationClicked
• RadioStarted
• RadioItemGenerated
• ChartGenerated
• TrendingUpdated

Events must contain only required information.

────────────────────────────────────────

BACKGROUND JOBS

Implement BullMQ jobs for:

• Search indexing
• Bulk reindex
• Recommendation refresh
• Personalization refresh
• Trending calculation
• Chart calculation
• Chart snapshotting
• Radio candidate preparation
• Search suggestion updates
• Cache warming
• Cache invalidation
• Failed-index retry

Every job must support:

• Retry
• Backoff
• Timeout
• Idempotency
• Dead-letter handling
• Metrics
• Structured logging

────────────────────────────────────────

DATABASE

Implement Prisma models and migrations for derived/operational data where required.

Include appropriate structures such as:

• SearchQueryReference
• SearchAnalytics
• RecommendationProfileReference
• RecommendationCacheMetadata
• RecommendationExperiment
• RecommendationResultReference
• RadioSession
• RadioSessionItem
• Chart
• ChartSnapshot
• ChartEntry
• TrendingSnapshot
• DiscoveryFeedReference
• EditorialCollection
• EditorialCollectionItem

Do not store complete search indexes in PostgreSQL.

Do not store unlimited raw behavioral telemetry transactionally.

────────────────────────────────────────

API

Implement production-ready REST APIs.

SEARCH

• Search
• Autocomplete
• Suggestions
• Search filters
• Search facets

DISCOVERY

• Home feed
• New releases
• Trending
• Popular
• Genre discovery
• Editorial collections

RECOMMENDATIONS

• Personalized feed
• Similar tracks
• Similar artists
• Related content
• Personalized playlists
• Frequently relevant content

RADIO

• Create radio session
• Get radio session
• Get next items
• Refresh radio
• End radio session

CHARTS

• List charts
• Get chart
• Get chart entries
• Historical chart period

Every endpoint must implement:

• Authentication where required
• Authorization
• Profile scoping
• Content availability validation
• Explicit-content policy
• Region validation where required
• Rate limiting
• Cursor pagination where appropriate
• OpenAPI documentation
• Consistent errors

────────────────────────────────────────

EXPLICIT CONTENT

Discovery systems must respect profile settings.

Filter or classify content according to:

• Explicit flag
• Profile restrictions
• Managed-profile rules
• Region rules
• Platform policy

Never rely solely on the client to hide restricted content.

────────────────────────────────────────

RIGHTS AND AVAILABILITY

Recommendation and search systems must filter out content that is unavailable because of:

• Expired rights
• Region
• Subscription tier
• Platform restrictions
• Content removal

Do not recommend content the user cannot legitimately access unless the product intentionally presents unavailable content as discovery.

────────────────────────────────────────

SECURITY

Protect against:

• Search scraping
• Automated recommendation harvesting
• User-profile enumeration
• Private playlist discovery
• Recommendation-data leakage
• API abuse
• Ranking manipulation
• Chart manipulation

Implement:

• Rate limiting
• Authorization
• Privacy boundaries
• Abuse detection
• Audit controls

────────────────────────────────────────

OBSERVABILITY

Instrument:

• Search latency
• Search errors
• Search zero-result rate
• Indexing lag
• Recommendation latency
• Recommendation cache hit rate
• Feed generation latency
• Radio generation latency
• Chart-generation latency
• Queue backlog

Track:

• Search success
• Recommendation availability
• Cache performance
• Search freshness
• Ranking failures

Never log private behavioral data unnecessarily.

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Search query construction
• Ranking rules
• Candidate generation
• Recommendation filters
• Diversity rules
• Radio candidate selection
• Radio deduplication
• Chart calculations
• Trending calculations
• Explicit-content filtering
• Rights filtering

INTEGRATION TESTS

Test:

• Elasticsearch/OpenSearch
• PostgreSQL
• Redis
• Kafka
• BullMQ

SEARCH TESTS

Test:

• Full-text
• Autocomplete
• Typo tolerance
• Filters
• Facets
• Ranking
• Reindexing
• Alias switching
• Index failure

RECOMMENDATION TESTS

Test:

• Personalization
• Candidate generation
• Ranking
• Diversity
• Fallback
• Cache failures
• Rights filtering
• Explicit-content filtering

RADIO TESTS

Test:

• Seed selection
• Session creation
• Deduplication
• Candidate exhaustion
• Retry
• Session expiration

CHART TESTS

Test:

• Aggregation
• Ranking
• Regionalization
• Time windows
• Snapshot consistency
• Anti-abuse weighting

PERFORMANCE TESTS

Test:

• Search throughput
• Autocomplete throughput
• Recommendation throughput
• Feed generation
• Radio generation
• Chart retrieval

SECURITY TESTS

Test:

• Private playlist leakage
• Profile-data leakage
• Search scraping
• Ranking abuse
• Recommendation endpoint abuse
• Rate-limit bypass

────────────────────────────────────────

DOCUMENTATION

Generate:

• Search architecture
• Index architecture
• Search ranking
• Search privacy
• Recommendation architecture
• Personalization
• Recommendation caching
• Discovery feeds
• Radio
• Stations
• Charts
• Trending
• Editorial content
• Rights filtering
• Explicit-content filtering
• API contracts
• Event contracts
• Queue architecture
• Database schema
• Privacy model
• Testing strategy

────────────────────────────────────────

PROJECT INDEX

Update the backend Project Index with:

• Search modules
• Search indexes
• Search analytics
• Discovery modules
• Recommendation modules
• Personalization
• Radio
• Stations
• Charts
• Trending
• Editorial content
• Database objects
• Search mappings
• Kafka topics
• BullMQ queues
• Workers
• Redis keys
• API endpoints
• Events
• Tests
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 51

Search service, search client, index mappings, analyzers, aliases, and query infrastructure.

BACKEND MILESTONE 52

Search indexing, autocomplete, suggestions, filters, facets, ranking, and reindexing.

BACKEND MILESTONE 53

Search analytics, zero-result analysis, click analytics, privacy controls, and operational tooling.

BACKEND MILESTONE 54

Recommendation domain, personalization profile, candidate generation, and recommendation APIs.

BACKEND MILESTONE 55

Recommendation ranking, diversity, fallback strategies, caching, and experimentation foundations.

BACKEND MILESTONE 56

Discovery feeds, home feed, new releases, editorial collections, trending, and popular-content systems.

BACKEND MILESTONE 57

Radio sessions, track/artist/genre radio, candidate generation, deduplication, and radio APIs.

BACKEND MILESTONE 58

Charts, regional charts, genre charts, time-window aggregation, snapshots, and anti-abuse weighting.

BACKEND MILESTONE 59

Events, background jobs, Redis optimization, observability, rights filtering, and explicit-content enforcement.

BACKEND MILESTONE 60

Integration, performance, ranking, security, privacy, resilience, and production-hardening tests.

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

• Search
• Autocomplete
• Search suggestions
• Search indexing
• Search analytics
• Discovery
• Recommendations
• Personalization
• Radio
• Stations
• Charts
• Trending
• Editorial collections
• Recommendation caching
• Discovery events
• Related background jobs

Do not implement complete:

• Podcast domain
• Audiobooks
• Notifications
• Advertising
• Long-term analytics platform
• Moderation
• Administration
• Frontend
• Mobile
• Infrastructure

Those belong to later implementation volumes.

────────────────────────────────────────

QUALITY BAR

Treat search, discovery, recommendations, radio, and charts as high-scale production systems.

Assume:

• Hundreds of millions of users
• Millions of searchable content objects
• Massive search traffic
• High recommendation traffic
• High discovery traffic
• Regional content restrictions
• Large event volumes
• Global deployment

Prioritize:

• Low latency
• Search relevance
• Recommendation quality
• Privacy
• Rights correctness
• Explicit-content enforcement
• Horizontal scalability
• Cache efficiency
• Graceful degradation
• Observability
• Security
• Production readiness
