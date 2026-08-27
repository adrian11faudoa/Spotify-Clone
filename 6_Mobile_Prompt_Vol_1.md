You are operating in Senior Engineering Team Mode.

Build the production-ready mobile customer application foundation for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The mobile application must consume the established backend API contracts, authentication model, authorization model, catalog architecture, playback architecture, subscription architecture, playlist architecture, library architecture, search architecture, recommendation architecture, notification architecture, podcast architecture, and security model.

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

Build the production-ready React Native mobile application for:

• Android
• iOS

The application must support:

• Authentication
• Account management
• Profiles
• Search
• Discovery
• Artists
• Albums
• Tracks
• Playlists
• Library
• Liked songs
• Saved albums
• Followed artists
• Podcasts
• Audio playback
• Background playback
• Queue
• Device synchronization
• Playback synchronization
• Recommendations
• Radio
• Charts
• Subscriptions
• Account security
• Push notifications
• Deep links
• Offline-aware behavior
• Accessibility
• Localization
• Secure storage

The mobile application must be:

• Fast
• Reliable
• Secure
• Accessible
• Battery-conscious
• Data-conscious
• Offline-aware
• Maintainable
• Scalable
• Production-ready

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

• Expo Secure Store or approved platform-secure storage

Local Persistence:

• SQLite or approved mobile persistence layer

Networking:

• Typed API client
• HTTPS

Audio:

• Expo-compatible audio architecture
• Approved native playback integration where required

Notifications:

• Firebase Cloud Messaging
• Apple Push Notification Service

Testing:

• Jest
• React Native Testing Library
• Detox or approved mobile E2E framework

────────────────────────────────────────

MOBILE ARCHITECTURE

Use:

• Feature-first organization
• Strict TypeScript
• Reusable components
• Separation of UI and business logic
• Server/local-state separation
• Secure-storage boundaries
• Explicit navigation boundaries
• Platform abstraction
• Dependency inversion where appropriate

Do not put business logic directly inside screen components.

Do not reproduce backend business rules in the client.

Do not use Zustand as the authoritative server-state system.

────────────────────────────────────────

APPLICATION STRUCTURE

Create a scalable mobile structure including:

src/

features/

components/

navigation/

screens/

layouts/

providers/

hooks/

services/

stores/

database/

storage/

audio/

notifications/

deep-links/

network/

lib/

config/

types/

utils/

assets/

tests/

Keep feature modules isolated.

Avoid uncontrolled shared utility modules.

────────────────────────────────────────

EXPO FOUNDATION

Implement:

• Expo application foundation
• App configuration
• Environment handling
• App metadata
• Android configuration
• iOS configuration
• Build configuration
• Development configuration
• Production configuration

Support:

• Android
• iOS

Keep platform-specific behavior isolated.

────────────────────────────────────────

NAVIGATION

Implement React Navigation.

Support:

• Authentication stack
• Onboarding
• Main application
• Search stack
• Artist pages
• Album pages
• Track pages
• Playlist pages
• Library
• Player
• Queue
• Podcasts
• Radio
• Charts
• Subscription
• Account
• Settings
• Notifications

Support:

• Stack navigation
• Tab navigation
• Modal screens
• Nested navigation
• Protected navigation
• Deep links

Navigation must never be treated as an authorization boundary.

────────────────────────────────────────

AUTHENTICATION

Implement:

• Registration
• Login
• Logout
• Email verification
• Password reset
• Password change
• Session restoration
• Session expiration
• Token refresh
• Device registration

Use secure storage for sensitive authentication state.

Never store passwords.

Never store tokens in ordinary unencrypted storage.

────────────────────────────────────────

ACCOUNT AND PROFILE

Implement:

• Account screen
• Profile screen
• Profile switching where supported
• Account settings
• Language
• Theme
• Notification preferences
• Privacy
• Security
• Session/device management

Profile-specific data must remain isolated.

────────────────────────────────────────

SECURE STORAGE

Use secure storage for:

• Authentication tokens
• Device identifiers where appropriate
• Security-sensitive preferences
• Other sensitive credentials

Keep separate storage boundaries for:

• Secrets
• Cache
• Preferences
• Offline metadata
• User-generated non-sensitive state

────────────────────────────────────────

HOME

Implement:

• Personalized home
• Recently played
• Recommended playlists
• Recommended tracks
• Recommended artists
• New releases
• Trending
• Editorial collections
• Genre discovery
• Podcast recommendations

Support:

• Skeletons
• Loading
• Empty
• Error
• Retry

Recommendation failures must not block the home screen.

────────────────────────────────────────

SEARCH

Implement:

• Search screen
• Search input
• Autocomplete
• Suggestions
• Recent searches
• Search history
• Search results
• Tracks
• Artists
• Albums
• Playlists
• Podcasts
• Episodes
• Genres
• Filters

Support:

• Debouncing
• Request cancellation
• Pagination
• Infinite loading
• Empty results
• Error states
• Retry

────────────────────────────────────────

SEARCH PERFORMANCE

Optimize:

• Input debouncing
• Network requests
• Query caching
• Result lists
• Image loading
• Virtualized lists
• Search-state restoration

Avoid duplicate requests.

────────────────────────────────────────

ARTIST EXPERIENCE

Implement:

• Artist header
• Artwork
• Follow/unfollow
• Popular tracks
• Albums
• Singles
• EPs
• Releases
• Related artists
• Artist radio
• Recommendations

Support:

• Loading
• Empty
• Error
• Offline-aware cached display where appropriate

────────────────────────────────────────

ALBUM EXPERIENCE

Implement:

• Album artwork
• Album title
• Artist
• Release date
• Track list
• Duration
• Explicit markers
• Save/unsave
• Play album
• Shuffle album
• Recommendations
• Related releases

Use optimized list rendering.

────────────────────────────────────────

TRACK EXPERIENCE

Implement:

• Track title
• Artist
• Album
• Explicit state
• Like/unlike
• Add to playlist
• Add to queue
• Share
• Play
• More actions

Handle:

• Unavailable content
• Regional restrictions
• Entitlement restrictions

────────────────────────────────────────

PLAYLIST EXPERIENCE

Implement:

• Playlist header
• Artwork
• Title
• Description
• Owner
• Visibility
• Track list
• Play
• Shuffle
• Save
• Follow
• Add/remove tracks where authorized
• Reorder where authorized

Support collaborative playlist indicators.

────────────────────────────────────────

LIBRARY

Implement:

• Liked songs
• Saved albums
• Saved playlists
• Followed artists
• Followed podcasts
• Recently played
• Listening history

Support:

• Search
• Filtering
• Sorting
• Pagination/infinite loading
• Empty states

────────────────────────────────────────

LIKED SONGS

Implement:

• Like
• Unlike
• List
• Play all
• Shuffle
• Search
• Optimistic update where safe

Server state remains authoritative.

────────────────────────────────────────

AUDIO PLAYER FOUNDATION

Build the mobile playback architecture.

Support:

• Play
• Pause
• Previous
• Next
• Seek
• Volume
• Mute
• Repeat
• Shuffle
• Progress
• Track artwork
• Track metadata
• Queue
• Playback authorization
• Playback errors

Separate:

• Player UI state
• Native audio engine state
• Backend playback session
• Persisted playback state

────────────────────────────────────────

BACKGROUND PLAYBACK

Support:

• Background playback
• Lock-screen controls
• Notification media controls
• Headset controls
• Bluetooth controls
• App suspension
• Resume
• Audio focus

Handle platform-specific differences between iOS and Android.

────────────────────────────────────────

AUDIO INTERRUPTIONS

Handle:

• Phone calls
• Other media playback
• Navigation prompts
• Bluetooth changes
• Wired headset removal
• Audio route changes
• System interruptions

Support:

• Pause
• Resume
• Ducking where appropriate
• State recovery

────────────────────────────────────────

PLAYBACK QUALITY

Display audio-quality options according to:

• Subscription entitlement
• Device capability
• Content availability

Do not expose unavailable quality levels.

────────────────────────────────────────

PLAYBACK AUTHORIZATION

Integrate with the approved playback authorization backend.

Handle:

• Authorization success
• Authorization expiration
• Rights failure
• Entitlement failure
• Regional restriction
• Device restriction
• CDN failure
• Network interruption

Never embed long-lived media credentials in the app.

────────────────────────────────────────

QUEUE

Implement mobile queue UI.

Support:

• Current track
• Upcoming tracks
• Add
• Remove
• Reorder
• Clear
• Shuffle
• Repeat

Synchronize with backend queue state where supported.

Handle queue-version conflicts without silently losing changes.

────────────────────────────────────────

MULTI-DEVICE PLAYBACK

Support:

• Device list
• Current playback device
• Transfer playback
• Remote pause
• Remote resume
• Stop playback
• Resume on another device

Validate operations through backend APIs.

────────────────────────────────────────

RADIO

Implement:

• Track radio
• Artist radio
• Genre radio
• Personalized stations

Support continuous loading.

Handle recommendation/radio failures gracefully.

────────────────────────────────────────

CHARTS

Implement:

• Global charts
• Regional charts
• Genre charts
• Trending
• Historical periods

Use performant virtualized lists.

────────────────────────────────────────

PODCASTS

Implement:

• Podcast discovery
• Show page
• Episode page
• Episode list
• Follow/unfollow
• Play
• Pause
• Resume
• Progress
• Recommendations
• Search

Reuse the approved playback architecture.

────────────────────────────────────────

SUBSCRIPTIONS

Implement:

• Current plan
• Available plans
• Trial
• Upgrade
• Downgrade
• Cancellation
• Renewal state
• Payment status
• Entitlement state

Never independently calculate subscription state.

────────────────────────────────────────

NOTIFICATIONS

Implement mobile notification foundation.

Support:

• FCM
• APNS
• Permission handling
• Token registration
• Token refresh
• Foreground notifications
• Background notifications
• Terminated-app notifications
• Badge counts
• Deep-link navigation

Notification categories:

• New releases
• Artist updates
• Playlist updates
• Podcasts
• Subscription
• Payment
• Security
• Recommendations
• System

────────────────────────────────────────

DEEP LINKING

Implement deep links for:

• Tracks
• Albums
• Artists
• Playlists
• Search
• Podcasts
• Episodes
• Charts
• Radio
• Notifications
• Subscription
• Account

Validate authorization after navigation.

Never trust sensitive values from a deep link.

────────────────────────────────────────

OFFLINE-AWARE FOUNDATION

Implement safe offline-aware behavior.

Support cached:

• Home content
• Artists
• Albums
• Playlists
• Library
• Recently played

Support:

• Offline indicator
• Stale-cache detection
• Reconnect
• Query refresh
• Retry of safe operations

Do not implement full offline music downloads in this volume.

Do not claim transactional offline playback.

────────────────────────────────────────

CONNECTIVITY

Handle:

• Online
• Offline
• Weak network
• Wi-Fi/cellular transitions
• Reconnection

When reconnecting:

• Refresh stale queries
• Revalidate playback state
• Revalidate queue
• Refresh library
• Refresh notifications

Avoid aggressive polling.

────────────────────────────────────────

FORMS

Use:

• React Hook Form
• Zod

Support:

• Registration
• Login
• Profile
• Account settings
• Playlist editing
• Search
• Subscription flows

Provide:

• Client validation
• Server validation
• Accessible errors
• Loading
• Disabled states

────────────────────────────────────────

ACCESSIBILITY

Support:

• VoiceOver
• TalkBack
• Dynamic Type
• Large text
• Screen readers
• Accessible labels
• Accessible actions
• Focus management
• Large touch targets
• Sufficient contrast
• Reduced motion

Provide accessible labels for all player controls.

────────────────────────────────────────

LOCALIZATION

Support:

• Multiple languages
• Locale persistence
• Date/time formatting
• Number formatting
• Currency formatting
• Relative time
• RTL layouts
• Localized notifications
• Localized validation

Do not hard-code user-facing strings throughout features.

────────────────────────────────────────

THEMING

Support:

• Light
• Dark
• System
• Persistent preference

Respect reduced-motion and accessibility settings.

────────────────────────────────────────

PERFORMANCE

Optimize:

• Startup
• Navigation
• Player initialization
• Search
• Large playlists
• Library
• Album pages
• Artist pages
• Image loading
• Memory
• List virtualization
• Query caching

Avoid unnecessary re-renders.

────────────────────────────────────────

BATTERY AND DATA USAGE

Optimize:

• Background work
• Network retries
• Query refetching
• Image loading
• Audio metadata requests
• Push handling

Prefer event-driven updates over unnecessary polling.

────────────────────────────────────────

SECURITY

Implement:

• Secure storage
• Protected navigation
• Safe deep links
• Safe URLs
• Secure playback authorization handling
• Secure logout
• Sensitive-data protection

Never store:

• Passwords
• API secrets
• Payment credentials
• Long-lived media credentials

────────────────────────────────────────

TESTING

UNIT TESTS

• Player state
• Queue state
• Search state
• Validation
• Formatting
• Utilities

COMPONENT TESTS

• Player controls
• Track cards
• Artist pages
• Album pages
• Playlist pages
• Library
• Search
• Subscription
• Notifications

INTEGRATION TESTS

• API client
• Authentication
• Playback authorization
• Queue synchronization
• Search
• Library
• Notifications
• Deep linking

END-TO-END TESTS

• Registration
• Login
• Search
• Playback
• Playlist
• Library
• Subscription
• Podcast
• Notifications
• Device switching

ACCESSIBILITY TESTS

• VoiceOver
• TalkBack
• Player
• Navigation
• Forms

PERFORMANCE TESTS

• Startup
• Search
• Large playlists
• Large libraries
• Artist pages
• Album pages
• Player

────────────────────────────────────────

DOCUMENTATION

Generate:

• Mobile architecture
• Navigation architecture
• Player architecture
• Audio focus
• Background playback
• Queue
• Device synchronization
• Search
• Discovery
• Playlists
• Library
• Podcasts
• Subscriptions
• Notifications
• Deep linking
• Offline-aware strategy
• Secure storage
• Accessibility
• Localization
• Performance
• Testing

────────────────────────────────────────

PROJECT INDEX

Maintain the mobile Project Index.

Track:

• Screens
• Navigation
• Components
• Features
• Hooks
• Stores
• Queries
• API integrations
• Audio engine
• Player
• Queue
• Device synchronization
• Notifications
• Deep links
• Local persistence
• Offline cache
• Tests
• Dependencies
• Generated files
• Remaining work
• Current milestone

────────────────────────────────────────

IMPLEMENTATION MILESTONES

MOBILE MILESTONE 1

Expo foundation, configuration, navigation, providers, theme, API client, secure storage, and error handling.

MOBILE MILESTONE 2

Authentication, profiles, account, sessions, devices, subscription state, and protected navigation.

MOBILE MILESTONE 3

Home, search, discovery, artists, albums, tracks, playlists, library, liked songs, saved albums, and follows.

MOBILE MILESTONE 4

Audio player, background playback, audio focus, interruptions, playback authorization, and playback errors.

MOBILE MILESTONE 5

Queue, device selection, multi-device synchronization, remote controls, radio, and charts.

MOBILE MILESTONE 6

Podcasts, podcast progress, recommendations, subscriptions, and notifications.

MOBILE MILESTONE 7

Offline-aware caching, connectivity handling, localization, accessibility, battery optimization, and data optimization.

MOBILE MILESTONE 8

Security hardening, integration testing, E2E testing, performance testing, platform-specific testing, and production readiness.

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

This volume covers the mobile customer application foundation and core streaming experience.

Do not implement complete:

• Backend code
• Web frontend code
• Full offline-download system
• Artist portal
• Label portal
• Administration
• Advertising management
• Analytics backend
• Moderation
• Infrastructure
• Terraform
• Kubernetes
• CI/CD

Consume the established backend contracts exactly.

Do not redesign APIs or database structures.

────────────────────────────────────────

QUALITY BAR

Treat the mobile applications as production streaming clients serving a global audience.

Assume:

• Hundreds of millions of users
• Large music catalogs
• Tens of millions of concurrent listeners
• Background playback
• Multiple devices
• Unreliable networks
• Android/iOS differences
• Large playlists
• Large libraries
• Multiple subscription plans
• Podcasts
• Global localization
• Strict accessibility requirements
• Strict security requirements

Prioritize:

• Playback reliability
• Startup performance
• Battery efficiency
• Data efficiency
• Secure storage
• Accessibility
• Correct state synchronization
• Offline awareness
• Maintainability
• Scalability
• Production readiness
