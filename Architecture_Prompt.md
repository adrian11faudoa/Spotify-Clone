Using the approved Master Prompt above.

DO NOT begin implementation.

Your only responsibility in this phase is to design the complete enterprise architecture for the platform.

This document becomes the single source of truth for every future Backend, Mobile, Web, Infrastructure, DevOps and QA implementation.

Do NOT generate source code.

Do NOT generate placeholder implementations.

Produce only architecture, engineering specifications, contracts, infrastructure decisions, domain models, scalability strategies and implementation plans.

────────────────────────────────────────

PROJECT

Build a production-ready enterprise music streaming platform comparable to:

• Spotify
• Apple Music
• YouTube Music
• Amazon Music
• TIDAL

The platform must support:

• Tens of millions of users
• Hundreds of millions of tracks
• Global music streaming
• Personalized recommendations
• Offline listening
• Artist management
• Record label management
• Premium subscriptions
• Future podcast and audiobook support

The platform must be cloud-native, event-driven, highly available, horizontally scalable and maintainable.

────────────────────────────────────────

PRIMARY TECHNOLOGY STACK

Mobile

• React Native
• Expo
• TypeScript

Web

• Next.js 15
• React 19
• TypeScript

Backend

• Node.js
• NestJS
• TypeScript

Database

• PostgreSQL
• Prisma ORM
• Redis
• Elasticsearch / OpenSearch

Media Processing

• FFmpeg

Storage

• AWS S3

Streaming

• CloudFront CDN
• HLS Adaptive Streaming

Infrastructure

• Docker
• Kubernetes
• GitHub Actions

Observability

• Prometheus
• Grafana
• Loki
• OpenTelemetry

────────────────────────────────────────

SYSTEM REQUIREMENTS

Design for:

• 50M+ registered users
• 10M+ daily active users
• Hundreds of millions of songs
• Millions of playlists
• Millions of concurrent streams
• Multi-region deployment
• Horizontal scaling
• High availability
• Zero-downtime deployments

────────────────────────────────────────

APPLICATIONS

Design complete architecture for:

• Mobile App
• Web App
• Artist Dashboard
• Label Dashboard
• Admin Dashboard
• Public API
• Internal APIs

────────────────────────────────────────

ROLES

Design RBAC for:

• Guest
• Listener
• Premium Listener
• Artist
• Label Manager
• Moderator
• Support
• Administrator
• Super Administrator
• System Services

Generate a complete permissions matrix.

────────────────────────────────────────

DOMAIN MODULES

Design domain boundaries for:

Identity

Authentication

Authorization

Profiles

Artists

Record Labels

Albums

Singles

EPs

Songs

Genres

Moods

Languages

Lyrics

Captions

Playlists

Collaborative Playlists

Favorites

Library

Recently Played

History

Queue

Playback

Streaming

Downloads

Offline Sync

Recommendations

Search

Charts

Trending

New Releases

Editorial Collections

Notifications

Subscriptions

Billing

Payments

Analytics

Advertising (future-ready)

Podcasts (future-ready)

Audiobooks (future-ready)

Administration

Audit

Feature Flags

System Configuration

────────────────────────────────────────

MICROSERVICE DECISION

Determine whether the platform should initially use:

• Modular Monolith
• Service-Oriented Architecture
• Microservices

Provide justification.

Design migration strategy for future scaling.

────────────────────────────────────────

C4 ARCHITECTURE

Generate:

• Context Diagram
• Container Diagram
• Component Diagram
• Deployment Diagram

Describe every component and responsibility.

────────────────────────────────────────

DOMAIN-DRIVEN DESIGN

Define:

• Bounded Contexts
• Aggregates
• Entities
• Value Objects
• Domain Events
• Application Services
• Policies
• Specifications
• Repositories

────────────────────────────────────────

DATABASE

Generate complete database architecture.

Include:

• ER Diagram
• Normalization Strategy
• Tables
• Indexes
• Foreign Keys
• Constraints
• Partitioning Strategy
• Read Replicas
• Backup Strategy
• Audit Tables
• Soft Deletes

Optimize for hundreds of millions of tracks and billions of playback events.

────────────────────────────────────────

MEDIA ARCHITECTURE

Design:

• Audio Upload Pipeline
• Metadata Validation
• Audio Fingerprinting
• FFmpeg Processing
• Adaptive Bitrate Encoding
• Loudness Normalization
• Album Artwork Processing
• Waveform Generation
• Lyrics Storage
• Subtitle/Caption Storage
• CDN Distribution
• Storage Lifecycle Policies

────────────────────────────────────────

STREAMING ARCHITECTURE

Design:

• Adaptive Streaming
• HLS Delivery
• Multi-bitrate Audio
• CDN Edge Caching
• Resume Playback
• Playback Synchronization
• Future DRM Support
• Streaming Analytics

────────────────────────────────────────

RECOMMENDATION ENGINE

Design AI-ready architecture supporting:

• Personalized Recommendations
• Daily Mixes
• Discover Weekly
• Release Radar
• Similar Artists
• Similar Songs
• Mood Recommendations
• Genre Recommendations
• Listening Pattern Analysis
• Cold Start Strategy
• Diversity Ranking

Design feature storage for future ML models.

────────────────────────────────────────

SEARCH

Design Elasticsearch/OpenSearch architecture.

Include:

• Song Search
• Artist Search
• Album Search
• Playlist Search
• Podcast Search
• Autocomplete
• Filters
• Synonyms
• Ranking
• Search Analytics
• Reindex Strategy

────────────────────────────────────────

PLAYBACK ARCHITECTURE

Design:

• Playback Queue
• Crossfade
• Gapless Playback
• Shuffle
• Repeat
• Equalizer Support
• Playback Synchronization
• Multi-device Handoff
• Offline Playback

────────────────────────────────────────

EVENT ARCHITECTURE

Define events including:

UserRegistered

TrackUploaded

TrackProcessed

AlbumPublished

PlaylistCreated

TrackPlayed

TrackLiked

PlaylistFollowed

RecommendationUpdated

SubscriptionActivated

PaymentSucceeded

DownloadCompleted

Generate producers and consumers.

────────────────────────────────────────

ASYNC PROCESSING

Identify all background jobs.

Examples:

• Audio Processing
• Artwork Processing
• Search Indexing
• Recommendation Updates
• Analytics Aggregation
• Loudness Normalization
• Playlist Generation
• Notification Delivery
• Cache Invalidation

────────────────────────────────────────

CACHE STRATEGY

Design Redis usage for:

• Sessions
• Playback Cache
• Recommendation Cache
• Search Cache
• Trending Cache
• Charts Cache
• Rate Limiting
• Distributed Locks

────────────────────────────────────────

SECURITY

Design:

• JWT
• Refresh Tokens
• RBAC
• DRM-ready Architecture
• Secrets Management
• Encryption
• Audit Logging
• OWASP Compliance
• Subscription Protection
• Fraud Prevention

────────────────────────────────────────

OBSERVABILITY

Design:

• Structured Logging
• Metrics
• Distributed Tracing
• Playback Metrics
• Streaming Dashboards
• Health Checks
• Alerts
• Performance Monitoring

────────────────────────────────────────

AI ARCHITECTURE

Design future-ready AI support for:

• Recommendation Engine
• Playlist Generation
• Mood Detection
• Audio Embeddings
• Semantic Search
• Trend Prediction
• Creator Insights
• Customer Support Assistant

────────────────────────────────────────

FRONTEND & MOBILE ARCHITECTURE

Define:

• Feature-first Structure
• Navigation
• Offline Support
• Audio Cache
• Background Playback
• Secure Storage
• Push Notifications
• API Layer
• Error Recovery

────────────────────────────────────────

DEVOPS ARCHITECTURE

Design:

• CI/CD
• Environment Strategy
• Container Strategy
• Kubernetes Organization
• Monitoring
• Rollback
• Disaster Recovery

────────────────────────────────────────

TESTING STRATEGY

Design:

• Unit Testing
• Integration Testing
• E2E Testing
• Contract Testing
• Load Testing
• Streaming Simulation
• Audio Quality Testing
• Security Testing

────────────────────────────────────────

DOCUMENTATION

Generate:

• Architecture Overview
• ADRs
• Folder Structure
• Coding Standards
• API Standards
• Database Standards
• Security Standards
• Deployment Standards
• Operations Runbooks
• Disaster Recovery Plan

────────────────────────────────────────

DELIVERABLE

Produce a complete enterprise engineering blueprint.

This blueprint must be detailed enough that independent engineering teams can implement:

• Backend
• Mobile App
• Web App
• Artist Dashboard
• Infrastructure
• DevOps
• QA

without making additional architectural decisions.

STOP after completing the architecture blueprint.

Wait for approval before implementation begins.
