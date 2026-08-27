You are operating in Senior Engineering Team Mode.

Complete the remaining production-ready mobile application for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The mobile application must consume the established backend API contracts, authentication model, authorization model, catalog architecture, playback architecture, subscription architecture, playlist architecture, library architecture, search architecture, recommendation architecture, podcast architecture, notification architecture, and security model.

Do not redesign backend APIs.

Do not redesign the database.

Do not implement backend code.

Do not implement web frontend code.

Do not implement infrastructure implementation code.

Do not generate Terraform.

Do not generate Kubernetes manifests.

Do not generate CI/CD workflows.

────────────────────────────────────────

MISSION

Complete the advanced production-ready Android and iOS applications.

Implement the remaining mobile experiences for:

• Advanced audio playback
• Background playback
• Lock-screen controls
• Audio interruptions
• Bluetooth/audio-route handling
• Offline music downloads
• Offline licenses
• Download management
• Multi-device synchronization
• Device handoff
• Advanced playlists
• Collaborative playlists
• Library synchronization
• Listening history
• Podcast downloads
• Podcast playback
• Recommendations
• Radio
• Charts
• Subscriptions
• Family plans
• Student plans
• Notifications
• Deep linking
• Account security
• Privacy
• Accessibility
• Localization
• Performance
• Battery optimization
• Data optimization
• Mobile analytics
• Production hardening

The final application must support both:

• iOS
• Android

────────────────────────────────────────

TECHNOLOGY STACK

Framework:

• React Native
• Expo
• TypeScript

Navigation:

• React Navigation

State:

• Zustand

Server State:

• TanStack Query

Forms:

• React Hook Form
• Zod

Secure Storage:

• Expo Secure Store
• Approved platform-secure storage

Local Persistence:

• SQLite
• Approved mobile persistence layer

Audio:

• Expo-compatible audio architecture
• Native playback integration where required

Notifications:

• Firebase Cloud Messaging
• Apple Push Notification Service

Testing:

• Jest
• React Native Testing Library
• Detox or approved mobile E2E framework

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

Use dependency injection where appropriate.

Separate platform-specific implementations cleanly.

Do not put backend business rules in UI components.

Do not duplicate authoritative server state unnecessarily.

────────────────────────────────────────

ADVANCED PLAYER

Complete the mobile player.

Support:

• Play
• Pause
• Resume
• Previous
• Next
• Seek
• Rewind
• Fast forward
• Volume
• Mute
• Shuffle
• Repeat
• Queue
• Playback progress
• Track metadata
• Artwork
• Quality selection
• Sleep timer where supported
• Playback speed for podcasts where supported
• Cross-device transfer
• Playback recovery

Maintain clear separation between:

• UI state
• Native audio engine
• Backend playback session
• Persistent progress
• Analytics events

────────────────────────────────────────

AUDIO ENGINE

Implement robust native audio behavior.

Support:

• Streaming audio
• Adaptive quality
• Buffering
• Seeking
• Playback interruption
• Audio focus
• Route changes
• Media controls
• Background execution
• Error recovery

Use platform-appropriate abstractions.

Do not attempt to implement a custom native audio engine unless required by the approved architecture.

────────────────────────────────────────

BACKGROUND PLAYBACK

Support:

• Background playback
• Lock-screen controls
• Notification media controls
• Bluetooth controls
• Headset controls
• Car/head-unit controls where supported
• App suspension
• Resume after suspension

Handle:

• iOS background-audio requirements
• Android foreground-media requirements

Do not assume iOS and Android behave identically.

────────────────────────────────────────

AUDIO INTERRUPTIONS

Handle:

• Phone calls
• Navigation prompts
• Other media applications
• Bluetooth connection changes
• Bluetooth disconnection
• Wired headset removal
• System audio interruptions
• Focus changes

Support:

• Pause
• Resume
• Ducking where appropriate
• State restoration

────────────────────────────────────────

AUDIO ROUTING

Support:

• Device speaker
• Wired headphones
• Bluetooth headphones
• Bluetooth speakers
• Car audio where supported
• External audio routes

Update the player UI when the active route changes.

────────────────────────────────────────

PLAYBACK QUALITY

Support quality options based on:

• User setting
• Subscription entitlement
• Device capability
• Content availability
• Network conditions

Support concepts such as:

• Data saver
• Automatic
• Normal
• High
• Maximum quality

Do not expose unavailable options.

────────────────────────────────────────

NETWORK-AWARE PLAYBACK

Adapt playback to:

• Wi-Fi
• Cellular
• Weak network
• Temporary disconnect
• Reconnection

Support:

• Buffer strategy
• Retry
• Quality adaptation
• CDN retry
• Playback recovery

Never make aggressive retries that drain battery or data.

────────────────────────────────────────

OFFLINE DOWNLOADS

Implement production-ready offline music support.

Support:

• Download authorization
• Download request
• Download queue
• Download progress
• Pause download
• Resume download
• Cancel download
• Retry download
• Download completion
• Download failure
• Download expiration
• Download removal
• Storage management

Downloads must use the approved backend authorization architecture.

────────────────────────────────────────

OFFLINE CONTENT PROTECTION

Do not store downloadable media as unprotected ordinary files.

Use:

• Encrypted local storage
• Offline license
• Secure key handling
• License expiration
• Device binding where required
• Content entitlement validation

Do not implement custom cryptography.

Do not attempt to bypass platform security mechanisms.

────────────────────────────────────────

OFFLINE LICENSE LIFECYCLE

Support:

• License acquisition
• License renewal
• License expiration
• License failure
• License revocation
• Device revocation
• Subscription expiration
• Content-right expiration

When a license becomes invalid:

• Prevent unauthorized playback
• Preserve understandable user state
• Request renewal when possible

────────────────────────────────────────

DOWNLOAD MANAGER

Create a dedicated download-management system.

Track:

• Download ID
• Content ID
• State
• Progress
• Bytes
• Total bytes
• Quality
• Storage location
• License state
• Expiration
• Error

Use persistent local state.

Support app restart recovery.

────────────────────────────────────────

DOWNLOAD STORAGE MANAGEMENT

Implement:

• Storage usage
• Available storage
• Download size estimation
• User cleanup
• Remove single download
• Remove all downloads
• Automatic cleanup of invalid downloads

Warn users before storage is exhausted.

────────────────────────────────────────

OFFLINE PLAYBACK

Support playback while offline for valid downloaded content.

Handle:

• Missing license
• Expired license
• Missing segment
• Corrupt file
• Subscription expiration
• Region change

Do not allow offline mode to bypass entitlement or license rules.

────────────────────────────────────────

OFFLINE PODCASTS

Support podcast downloads with appropriate differences from music.

Implement:

• Download episode
• Pause
• Resume
• Retry
• Delete
• Offline playback
• Playback progress

Respect podcast-specific content policies.

────────────────────────────────────────

MULTI-DEVICE SYNCHRONIZATION

Complete synchronization across:

• iPhone
• iPad
• Android phone
• Android tablet
• Web client
• Desktop clients where supported

Synchronize:

• Current playback
• Queue
• Volume where appropriate
• Repeat
• Shuffle
• Playback position
• Current device
• Recently played

────────────────────────────────────────

DEVICE HANDOFF

Support:

• Device discovery
• Current-device selection
• Transfer playback
• Resume on target device
• Queue transfer
• Progress transfer
• Previous-device cleanup

Validate all operations through backend APIs.

────────────────────────────────────────

QUEUE SYNCHRONIZATION

Support:

• Local queue
• Server queue
• Queue version
• Mutation ID
• Conflict detection
• Retry
• Recovery

When conflicts occur:

• Do not silently overwrite the server
• Preserve local intent when possible
• Refresh state
• Retry against current version

────────────────────────────────────────

ADVANCED PLAYLISTS

Complete:

• Playlist creation
• Editing
• Deletion
• Artwork
• Visibility
• Add track
• Remove track
• Reorder
• Save
• Follow
• Share
• Collaborative editing

Support large playlists efficiently.

────────────────────────────────────────

COLLABORATIVE PLAYLISTS

Support:

• Invite collaborator
• Accept
• Reject
• Leave
• Remove collaborator
• Collaborator roles
• Shared editing
• Version conflicts

Display conflict states clearly.

Never silently discard a user's edits.

────────────────────────────────────────

LIBRARY SYNCHRONIZATION

Implement:

• Library sync cursor
• Incremental changes
• Local cache
• Offline mutations
• Mutation queue
• Conflict handling
• Retry
• Reconciliation

Support:

• Likes
• Saved albums
• Saved playlists
• Followed artists
• Followed podcasts

────────────────────────────────────────

OFFLINE LIBRARY MUTATIONS

Support safe offline mutations for:

• Like track
• Unlike track
• Save album
• Unsave album
• Follow artist
• Unfollow artist
• Follow podcast
• Unfollow podcast
• Playlist add/remove where supported

Each mutation requires:

• Mutation ID
• Target entity
• Operation
• Local timestamp
• Server synchronization state

────────────────────────────────────────

LISTENING HISTORY

Implement:

• Recently played
• Listening history
• Clear history where supported
• Local history cache
• Server synchronization

Do not block playback on history writes.

────────────────────────────────────────

PLAYBACK TELEMETRY

Generate efficient analytics signals for:

• Start
• Pause
• Resume
• Seek
• Completion
• Skip
• Buffering
• Quality change
• Error

Batch or throttle telemetry where appropriate.

Do not generate excessive network traffic.

────────────────────────────────────────

RECOMMENDATIONS

Complete mobile recommendation interfaces.

Support:

• Personalized home
• Daily mixes
• Similar tracks
• Similar artists
• Recommended playlists
• Trending
• New releases
• Genre discovery
• Recently played recommendations

Recommendation failures must never crash the application.

────────────────────────────────────────

RADIO

Complete:

• Track radio
• Artist radio
• Genre radio
• Personalized radio

Support:

• Dynamic queue
• Seed
• Continuous loading
• Deduplication
• Offline-aware fallback where appropriate

────────────────────────────────────────

CHARTS

Implement:

• Global
• Regional
• Genre
• Trending
• Historical

Support:

• Period selection
• Region selection
• Track playback
• Artist navigation

Use performant virtualized lists.

────────────────────────────────────────

PODCASTS

Complete:

• Podcast home
• Show pages
• Episode pages
• Categories
• Follow
• Download
• Playback
• Progress
• Search
• Recommendations
• Notifications

Support podcast-specific playback speed and resume behavior.

────────────────────────────────────────

SUBSCRIPTIONS

Complete:

• Plan list
• Current plan
• Trial
• Upgrade
• Downgrade
• Cancellation
• Renewal
• Grace period
• Payment failure
• Entitlement state

Never derive authoritative subscription state solely from local storage.

────────────────────────────────────────

FAMILY PLANS

Support where backend permits:

• Family manager
• Family member state
• Profile management
• Subscription overview
• Content restrictions

Respect backend authorization.

────────────────────────────────────────

STUDENT PLANS

Support:

• Eligibility status
• Verification status
• Verification renewal
• Plan status
• Expiration

Provider-specific verification must remain behind backend APIs.

────────────────────────────────────────

NOTIFICATIONS

Complete:

• Push permissions
• FCM
• APNS
• Token registration
• Token refresh
• Foreground notifications
• Background notifications
• Terminated-app notifications
• Badge updates
• Deep-link actions
• Notification preferences

Support:

• New releases
• Artists
• Playlists
• Podcasts
• Subscriptions
• Payments
• Security
• Recommendations
• Downloads

────────────────────────────────────────

DEEP LINKING

Complete deep links for:

• Tracks
• Albums
• Artists
• Playlists
• Podcasts
• Episodes
• Search
• Radio
• Charts
• Notifications
• Subscription
• Account
• Downloaded content

Validate authorization after navigation.

Never trust sensitive query parameters.

────────────────────────────────────────

ACCOUNT SECURITY

Implement:

• Password change
• Session management
• Device management
• MFA where supported
• Passkeys where supported
• Security events
• Logout all devices
• Account recovery

Sensitive operations should require appropriate confirmation.

────────────────────────────────────────

PRIVACY

Implement:

• Privacy preferences
• Listening-history preferences
• Recommendation preferences
• Advertising preferences
• Profile settings
• Data export
• Account deletion
• Security preferences

Display backend-authoritative status.

────────────────────────────────────────

ACCESSIBILITY

Complete:

• VoiceOver
• TalkBack
• Dynamic Type
• Large text
• Screen readers
• Accessible labels
• Accessible actions
• Focus management
• Touch targets
• Contrast
• Reduced motion

Ensure the player is fully accessible.

────────────────────────────────────────

LOCALIZATION

Complete:

• Multiple languages
• Locale switching
• Currency formatting
• Date/time
• Number formatting
• Relative time
• RTL layouts
• Localized notifications
• Localized errors

Do not hard-code user-visible strings throughout features.

────────────────────────────────────────

THEMING

Support:

• Light
• Dark
• System
• Persistent setting

Respect:

• Reduced motion
• Dynamic Type
• Accessibility preferences

────────────────────────────────────────

PERFORMANCE

Optimize:

• Cold startup
• Warm startup
• Navigation
• Player initialization
• Audio buffering
• Search
• Large playlists
• Large library
• Downloads
• Image loading
• Memory
• Local database
• Query caching

Avoid unnecessary renders.

────────────────────────────────────────

BATTERY

Minimize:

• Background processing
• Polling
• Analytics traffic
• Retry loops
• Image downloads
• Database writes

Prefer:

• Push
• Event-driven updates
• Batched telemetry
• Efficient synchronization

────────────────────────────────────────

DATA USAGE

Provide appropriate settings for:

• Streaming quality
• Download quality
• Cellular streaming
• Cellular downloads
• Artwork quality
• Podcast auto-download

Warn users before high-data operations where appropriate.

────────────────────────────────────────

MOBILE SECURITY

Implement:

• Secure storage
• Protected navigation
• Secure logout
• Safe deep links
• Secure download storage
• Authentication protection
• Sensitive-data minimization
• Clipboard safety where appropriate

Never store:

• Passwords
• Payment secrets
• Backend API secrets
• Long-lived playback credentials

────────────────────────────────────────

ERROR HANDLING

Handle:

• Authentication failure
• Subscription failure
• Playback authorization failure
• Rights restriction
• CDN failure
• Network interruption
• Download failure
• License failure
• Search failure
• Playlist synchronization failure
• Library synchronization failure
• Notification failure

Provide user-friendly recovery.

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Player state
• Download state
• Queue state
• Synchronization state
• Library mutations
• Playlist conflicts
• Subscription state
• Validation
• Formatting

COMPONENT TESTS

Test:

• Player
• Queue
• Search
• Product/content pages
• Playlists
• Library
• Downloads
• Subscriptions
• Notifications
• Settings

INTEGRATION TESTS

Test:

• API client
• Authentication
• Playback authorization
• Download authorization
• Offline storage
• Library synchronization
• Queue synchronization
• Notifications
• Deep links

END-TO-END TESTS

Test:

• Login
• Search
• Playback
• Background playback
• Lock-screen controls
• Device switching
• Playlist
• Collaboration
• Library
• Download
• Offline playback
• Podcast
• Subscription
• Notification
• Account security

OFFLINE TESTS

Test:

• Download
• Disconnect
• Playback offline
• License expiration
• Reconnect
• Sync
• Duplicate mutations
• Conflict resolution

PLATFORM TESTS

Test on supported:

• iOS versions
• Android versions
• Screen sizes
• Device capabilities

ACCESSIBILITY TESTS

• VoiceOver
• TalkBack
• Dynamic Type
• Large text
• Player controls
• Navigation

PERFORMANCE TESTS

• Startup
• Search
• Player
• Large playlists
• Large library
• Downloads
• Offline database
• Background audio

────────────────────────────────────────

DOCUMENTATION

Generate:

• Advanced mobile architecture
• Audio engine architecture
• Background playback
• Audio focus
• Device routing
• Offline-download architecture
• Offline licensing
• Download management
• Multi-device synchronization
• Queue synchronization
• Playlist collaboration
• Library synchronization
• Playback telemetry
• Podcast architecture
• Subscription UX
• Notifications
• Deep linking
• Security
• Privacy
• Accessibility
• Localization
• Performance
• Battery optimization
• Data-usage strategy
• Testing strategy
• Release-readiness guide

────────────────────────────────────────

PROJECT INDEX

Update the mobile Project Index with:

• Screens
• Navigation
• Features
• Components
• Hooks
• Stores
• Queries
• API integrations
• Audio engine
• Playback
• Queue
• Device synchronization
• Downloads
• Offline licenses
• Offline storage
• Library synchronization
• Playlists
• Podcasts
• Subscriptions
• Notifications
• Deep links
• Analytics
• Tests
• Dependencies
• Generated files
• Modified files
• Remaining work
• Current milestone

────────────────────────────────────────

IMPLEMENTATION MILESTONES

MOBILE MILESTONE 9

Advanced audio engine, background playback, audio focus, interruptions, routing, media controls, and playback recovery.

MOBILE MILESTONE 10

Adaptive playback, playback-quality selection, network-aware streaming, telemetry, and device capability handling.

MOBILE MILESTONE 11

Offline downloads, encrypted storage, download manager, offline licensing, license renewal, expiration, and storage management.

MOBILE MILESTONE 12

Offline playback, offline podcasts, connectivity recovery, synchronization, and reconciliation.

MOBILE MILESTONE 13

Advanced playlists, collaborative playlists, queue synchronization, and conflict resolution.

MOBILE MILESTONE 14

Library synchronization, offline library mutations, listening history, recently played, and playback telemetry.

MOBILE MILESTONE 15

Recommendations, radio, charts, podcasts, and personalized discovery.

MOBILE MILESTONE 16

Subscriptions, family plans, student plans, billing state, entitlement state, and account security.

MOBILE MILESTONE 17

Notifications, deep links, privacy, accessibility, localization, theming, and data/battery controls.

MOBILE MILESTONE 18

Security hardening, integration testing, offline testing, platform testing, E2E testing, performance testing, and production readiness.

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

This volume completes the advanced mobile application.

Do not implement:

• Backend code
• Web frontend code
• Kubernetes
• Terraform
• CI/CD infrastructure

Consume the established backend contracts exactly.

Do not redesign APIs or database structures.

────────────────────────────────────────

QUALITY BAR

Treat the mobile application as a globally distributed music-streaming client serving hundreds of millions of users.

Assume:

• Tens of millions of concurrent listeners
• Large audio catalogs
• Background playback
• Offline downloads
• Multiple devices
• Unreliable networks
• Subscription tiers
• Regional rights
• Podcasts
• Large playlists
• Large libraries
• Global localization
• Strict security requirements
• Strict accessibility requirements

Prioritize:

• Playback reliability
• Offline correctness
• License enforcement
• Device synchronization
• Startup performance
• Battery efficiency
• Data efficiency
• Secure storage
• Accessibility
• Maintainability
• Scalability
• Production readiness
