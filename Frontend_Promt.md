Using the approved Architecture Blueprint and the Master Prompt above.

Begin frontend and mobile implementation ONLY.

Do NOT generate backend code.

Do NOT generate infrastructure code.

Do NOT redesign APIs.

Do NOT redesign the database.

Assume the backend implementation already exists and consume its published API contracts exactly as defined in the Architecture Blueprint.

The applications must achieve App Store / Google Play flagship quality comparable to:

- Spotify
- Apple Music
- YouTube Music
- Amazon Music
- TIDAL

Every implementation must be production-ready, accessible, responsive, highly performant, and maintainable.

Generate code incrementally according to the Master Prompt milestone strategy.

────────────────────────────────────────

MISSION

Build the complete production-ready client applications for the enterprise music streaming platform.

Generate:

- Mobile App (iOS & Android)
- Web Application
- Artist Dashboard
- Label Dashboard
- Admin Dashboard
- Shared Design System
- Shared UI Component Library
- Shared API SDK

The applications must provide world-class audio playback, fluid animations, offline listening, seamless synchronization, and exceptional user experience.

Optimize for:

- Instant startup
- Low memory usage
- Low battery consumption
- High-performance scrolling
- Smooth animations (60–120 FPS)
- Fast search
- Reliable offline playback
- Cross-device synchronization

────────────────────────────────────────

TECH STACK

Mobile

- React Native
- Expo
- TypeScript

Web

- Next.js 15
- React 19
- TypeScript

Navigation

- React Navigation

State Management

- Zustand

Server State

- TanStack Query

Forms

- React Hook Form
- Zod

Audio

- Expo Audio / react-native-track-player

Animations

- React Native Reanimated
- React Native Gesture Handler
- Moti
- Framer Motion (Web)

Lists

- FlashList

Storage

- MMKV
- SecureStore

Notifications

- Expo Notifications

Charts

- Recharts

────────────────────────────────────────

ARCHITECTURE

Follow:

- Feature-first organization
- Clean Architecture
- SOLID
- Strict TypeScript
- Modular design
- Shared component library
- Shared design system
- Shared API layer
- Separation of presentation and business logic

────────────────────────────────────────

APPLICATIONS

Generate:

Listener Mobile App

Web App

Artist Dashboard

Label Dashboard

Admin Dashboard

Shared UI Components

Shared Design System

Shared API SDK

Shared Hooks

Shared Utilities

────────────────────────────────────────

FOLDER STRUCTURE

Generate scalable organization including:

app/

features/

components/

screens/

navigation/

layouts/

hooks/

providers/

services/

stores/

theme/

styles/

assets/

animations/

config/

types/

utils/

────────────────────────────────────────

NAVIGATION

Implement:

Authentication Flow

Role-based Navigation

Deep Linking

Protected Routes

Bottom Tabs

Stack Navigation

Modal Navigation

Universal Links

────────────────────────────────────────

AUTHENTICATION

Generate interfaces for:

Registration

Login

Logout

Forgot Password

Reset Password

Email Verification

Session Management

Token Refresh

Biometric Authentication

────────────────────────────────────────

HOME EXPERIENCE

Generate:

Home

Recommended For You

Discover Weekly

Daily Mixes

Release Radar

Recently Played

New Releases

Trending

Charts

Genres

Moods

Editorial Collections

────────────────────────────────────────

SEARCH

Implement:

Instant Search

Autocomplete

Recent Searches

Trending Searches

Song Search

Artist Search

Album Search

Playlist Search

Filters

Search History

────────────────────────────────────────

LIBRARY

Generate:

Liked Songs

Albums

Artists

Playlists

Downloaded Music

Listening History

Recently Played

Folders

Collections

────────────────────────────────────────

PLAYLISTS

Implement:

Playlist Creation

Collaborative Playlists

Playlist Editing

Reordering

Sharing

Following

Smart Playlists

────────────────────────────────────────

PLAYER

Implement production-grade audio player supporting:

Play

Pause

Resume

Next

Previous

Queue

Shuffle

Repeat

Crossfade

Gapless Playback

Playback Speed

Sleep Timer

Equalizer-ready Architecture

Lyrics

Synced Lyrics

Album Artwork

Waveform Display

Casting-ready Architecture

────────────────────────────────────────

BACKGROUND PLAYBACK

Support:

Lock Screen Controls

Notification Controls

Background Audio

Remote Controls

Headphone Controls

Car Integration Ready

────────────────────────────────────────

DOWNLOADS

Implement:

Offline Downloads

Download Queue

Storage Management

Quality Selection

Resume Downloads

Background Downloads

Synchronization

────────────────────────────────────────

ARTIST DASHBOARD

Generate:

Overview

Track Upload

Album Management

Release Scheduling

Analytics

Audience Insights

Revenue Dashboard

Follower Growth

Playlist Performance

────────────────────────────────────────

LABEL DASHBOARD

Generate:

Catalog Management

Artist Management

Release Approval

Royalties Overview

Analytics

Revenue Reports

────────────────────────────────────────

ADMIN DASHBOARD

Generate:

Users

Artists

Labels

Tracks

Albums

Playlists

Subscriptions

Payments

Reports

Analytics

Feature Flags

Audit Logs

System Settings

────────────────────────────────────────

STATE MANAGEMENT

Implement Zustand stores for:

Authentication

Playback

Queue

Downloads

Search

Recommendations

Library

Notifications

Theme

Settings

User Preferences

────────────────────────────────────────

SERVER STATE

Implement TanStack Query.

Support:

Caching

Optimistic Updates

Background Refresh

Retries

Offline Cache

Cache Invalidation

Infinite Queries

Pagination

────────────────────────────────────────

API CLIENT

Generate:

Typed API SDK

Authentication Interceptors

Retry Logic

Request Cancellation

Streaming Helpers

Download Helpers

Pagination Helpers

────────────────────────────────────────

FORMS

Generate production-ready forms using:

React Hook Form

Zod Validation

Inline Validation

Async Validation

Loading States

Error Handling

────────────────────────────────────────

BACKGROUND SERVICES

Implement:

Background Playback

Background Downloads

Push Notification Handling

Offline Synchronization

Pending Actions Queue

Automatic Recovery

────────────────────────────────────────

OFFLINE MODE

Support:

Offline Playback

Audio Cache

Metadata Cache

Queued Updates

Synchronization

Conflict Resolution

Automatic Retry

────────────────────────────────────────

PERFORMANCE

Optimize:

FlashList

Memoization

Audio Preloading

Image Optimization

Lazy Loading

Code Splitting

Background Prefetching

Startup Optimization

Memory Usage

Battery Consumption

────────────────────────────────────────

ACCESSIBILITY

Implement:

WCAG 2.2 AA Compliance

Screen Reader Support

VoiceOver

TalkBack

Dynamic Text

Keyboard Navigation (Web)

Reduced Motion

Focus Management

────────────────────────────────────────

RESPONSIVE DESIGN

Support:

Phones

Tablets

Desktop

Large Displays

Landscape

Portrait

────────────────────────────────────────

THEMING

Support:

Light Theme

Dark Theme

System Theme

Dynamic Themes

────────────────────────────────────────

ANIMATIONS

Use Reanimated, Moti and Framer Motion for:

Page Transitions

Player Animations

Queue Animations

Bottom Sheets

Dialogs

Cards

Micro-interactions

Loading States

Artwork Transitions

────────────────────────────────────────

ERROR HANDLING

Generate:

Error Boundaries

Offline Screens

Connection Recovery

Retry Components

Maintenance Screens

────────────────────────────────────────

TESTING

Generate:

Unit Tests

Component Tests

Integration Tests

Accessibility Tests

Playback UI Tests

Performance Tests

Visual Regression Test Architecture

────────────────────────────────────────

DOCUMENTATION

Generate:

Component Documentation

Navigation Documentation

Design System Documentation

Frontend Standards

State Management Standards

API Usage Guide

────────────────────────────────────────

PROJECT ORGANIZATION

Maintain throughout development:

Current Milestone

Generated Screens

Generated Components

Generated Features

API Integrations

Remaining Work

Dependencies

────────────────────────────────────────

OUTPUT FORMAT

For every generated file provide:

1. Exact file path
2. Complete file contents

Never generate placeholders.

Never generate pseudo-code.

Never omit implementations.

Never regenerate unchanged files.

Only modify files when required.

────────────────────────────────────────

STOP CONDITIONS

Generate the frontend incrementally according to the Master Prompt.

Each milestone should contain approximately 20–40 files.

At the end of every milestone:

- Verify all applications compile successfully.
- Update the project index.
- List completed screens and features.
- Identify the next file to generate.

STOP and wait for approval before generating the next milestone.
