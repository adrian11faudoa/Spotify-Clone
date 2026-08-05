Using the approved Architecture Blueprint and the Master Prompt above.

Begin backend implementation ONLY.

Do NOT generate frontend code.

Do NOT generate mobile code.

Do NOT generate infrastructure code unless required for backend execution.

Assume the Architecture Blueprint has been approved.

Follow it exactly.

Never redesign APIs.

Never redesign the database.

Never modify architectural decisions unless explicitly requested.

Generate code incrementally according to the Master Prompt milestone strategy.

────────────────────────────────────────

MISSION

Build the complete production-ready backend for the enterprise music streaming platform.

The backend must support:

• Spotify-scale music streaming
• Millions of concurrent listeners
• Hundreds of millions of tracks
• Global low-latency content delivery
• AI-powered recommendations
• High availability
• Event-driven processing
• Zero-downtime deployments

Every milestone must compile successfully before continuing.

────────────────────────────────────────

TECH STACK

Language

• TypeScript

Framework

• NestJS

Runtime

• Node.js

Database

• PostgreSQL
• Prisma ORM

Cache

• Redis

Search

• Elasticsearch / OpenSearch

Storage

• AWS S3

CDN

• CloudFront

Media Processing

• FFmpeg

Background Jobs

• BullMQ

Communication

• REST API
• WebSockets
• Server-Sent Events (where appropriate)

Documentation

• OpenAPI / Swagger

────────────────────────────────────────

ARCHITECTURE

Strictly follow:

• Clean Architecture
• Domain-Driven Design (DDD)
• SOLID
• Repository Pattern
• Service Layer
• Dependency Injection
• CQRS where beneficial
• Event-Driven Architecture
• Feature-first organization

Never violate architectural boundaries.

────────────────────────────────────────

IMPLEMENT THE FOLLOWING DOMAINS

Identity

Authentication

Authorization

Users

Profiles

Artists

Record Labels

Albums

Singles

EPs

Tracks

Genres

Moods

Languages

Lyrics

Captions

Artwork

Playlists

Collaborative Playlists

Favorites

Library

Recently Played

Listening History

Playback

Queue

Streaming

Downloads

Offline Authorization

Recommendations

Search

Charts

Trending

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

AUTHENTICATION

Implement:

• Registration
• Login
• Logout
• Email Verification
• Password Reset
• JWT
• Refresh Tokens
• MFA-ready Architecture
• Google OAuth
• Apple OAuth
• Session Management
• Device Management
• Token Revocation

────────────────────────────────────────

AUTHORIZATION

Implement complete RBAC.

Support:

Guest

Listener

Premium Listener

Artist

Label Manager

Support

Moderator

Administrator

Super Administrator

System Services

Generate:

Permission Guards

Policies

Decorators

Permission Matrix

────────────────────────────────────────

DATABASE

Generate:

• Prisma Schema
• Repositories
• Migrations
• Indexes
• Constraints
• Optimized Queries
• Transactions
• Read Models
• Seeders
• Partitioning Strategy

Optimize for billions of playback events.

────────────────────────────────────────

MEDIA INGESTION

Implement:

Track Upload

Metadata Validation

Artwork Upload

Lyrics Upload

Fingerprint Generation Hooks

Signed Upload URLs

Duplicate Detection

Upload Progress

────────────────────────────────────────

MEDIA PROCESSING

Implement asynchronous processing with BullMQ.

Support:

Audio Validation

FFmpeg Processing

Adaptive Bitrate Encoding

AAC Encoding

MP3 Encoding

Opus Encoding

Loudness Normalization

Waveform Generation

Artwork Processing

Metadata Extraction

Publishing Pipeline

Cleanup

Retry Policies

Dead Letter Queues

────────────────────────────────────────

MEDIA STORAGE

Implement:

AWS S3 Storage

Artwork Storage

Lyrics Storage

Versioning

Signed URLs

Lifecycle Policies

CloudFront Integration

Media Cleanup

────────────────────────────────────────

STREAMING

Implement architecture for:

Adaptive Streaming

HLS Audio Delivery

Resume Playback

Playback Synchronization

Low-Latency Streaming

CDN Delivery

Bandwidth Optimization

Future DRM Support

────────────────────────────────────────

PLAYBACK SERVICE

Implement:

Playback Sessions

Queue Management

Shuffle

Repeat

Crossfade State

Playback Position

Resume Across Devices

Listening History

Device Synchronization

────────────────────────────────────────

RECOMMENDATION SERVICE

Generate AI-ready architecture.

Support:

Listening History

Completion Rate

Skip Rate

Favorites

Playlist Similarity

Artist Affinity

Genre Affinity

Mood Affinity

Editorial Boosting

Cold Start

Future ML Models

────────────────────────────────────────

SEARCH

Implement Elasticsearch/OpenSearch.

Generate:

Song Search

Artist Search

Album Search

Playlist Search

Podcast Search (future)

Autocomplete

Filters

Synonyms

Ranking

Analytics

Reindex Workers

────────────────────────────────────────

PLAYLISTS

Implement:

Playlist Creation

Collaborative Playlists

Playlist Sharing

Playlist Following

Playlist Ordering

Smart Playlists

────────────────────────────────────────

LIBRARY

Implement:

Favorites

Liked Songs

Albums

Artists

Downloads

Listening History

Recently Played

────────────────────────────────────────

SUBSCRIPTIONS

Implement:

Free Tier

Premium Tier

Family Plans

Student Plans

Trials

Subscription Lifecycle

Renewals

Cancellation

────────────────────────────────────────

PAYMENTS

Implement Stripe.

Support:

Payment Intents

Subscription Billing

Invoices

Refunds

Webhook Processing

Idempotency

Payment Recovery

────────────────────────────────────────

NOTIFICATIONS

Generate queue-based services for:

Push

Email

In-App

Future SMS Support

Include:

Retry Policies

Scheduling

Priority Queues

────────────────────────────────────────

ANALYTICS

Generate services for:

Track Plays

Unique Listeners

Completion Rate

Skip Rate

Listening Time

Artist Analytics

Album Analytics

Playlist Analytics

Revenue Analytics

Subscription Metrics

Trending Metrics

────────────────────────────────────────

BACKGROUND WORKERS

Implement BullMQ workers for:

Audio Processing

Artwork Processing

Waveform Generation

Search Indexing

Recommendation Updates

Analytics Aggregation

Notification Delivery

Cache Invalidation

Scheduled Maintenance

────────────────────────────────────────

EVENT BUS

Implement complete event-driven architecture.

Generate events including:

UserRegistered

TrackUploaded

TrackValidated

TrackProcessed

AlbumPublished

PlaylistCreated

TrackPlayed

TrackLiked

TrackDownloaded

RecommendationUpdated

SubscriptionActivated

PaymentSucceeded

AnalyticsUpdated

NotificationQueued

Define publishers and subscribers.

────────────────────────────────────────

CACHE

Implement Redis for:

Sessions

Playback Cache

Recommendation Cache

Trending Cache

Charts Cache

Search Cache

Rate Limiting

Distributed Locks

────────────────────────────────────────

SECURITY

Implement:

JWT

Refresh Tokens

RBAC

Secure Headers

Rate Limiting

Input Validation

SQL Injection Protection

XSS Protection

Secrets Management

Audit Logging

Encryption at Rest

Encryption in Transit

OWASP Top 10 Compliance

Anti-Abuse Protection

────────────────────────────────────────

OBSERVABILITY

Generate:

Structured Logging

Metrics

Distributed Tracing

Health Checks

Readiness Checks

Liveness Checks

Playback Monitoring

Streaming Monitoring

Performance Monitoring

Error Monitoring

────────────────────────────────────────

RESILIENCY

Implement:

Retry Policies

Circuit Breakers

Timeouts

Graceful Shutdown

Dead Letter Queues

Failure Recovery

Idempotency

────────────────────────────────────────

TESTING

Generate:

Unit Tests

Integration Tests

Repository Tests

Service Tests

Controller Tests

API Contract Tests

Streaming Load Tests

Performance Tests

Security Tests

────────────────────────────────────────

PROJECT ORGANIZATION

Maintain throughout development:

Current Milestone

Generated Files

Completed Modules

Remaining Modules

Database Objects

API Endpoints

Workers

Events

Dependencies

────────────────────────────────────────

OUTPUT FORMAT

For every generated file provide:

1. Exact file path
2. Complete file contents

Never generate pseudo-code.

Never generate placeholders.

Never omit implementations.

Never regenerate unchanged files.

Only modify files when required.

────────────────────────────────────────

STOP CONDITIONS

Generate the backend incrementally according to the Master Prompt.

Each milestone should contain approximately 20–40 files.

At the end of every milestone:

• Verify the backend compiles successfully.
• Update the project index.
• List completed modules.
• Identify the next file to generate.

STOP and wait for approval before generating the next milestone.
