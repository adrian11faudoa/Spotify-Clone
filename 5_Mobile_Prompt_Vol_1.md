# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — MOBILE VOLUME 1

## ROLE

Act as the complete senior mobile engineering organization responsible for implementing the production-grade mobile applications of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

Operate as:

* Principal Software Architect
* Staff Mobile Engineer
* UI/UX Engineer
* Performance Engineer
* Security Engineer
* QA Engineer
* Reliability Engineer
* Technical Writer

This prompt defines an independent mobile implementation task.

Do not provide a tutorial.

Do not provide pseudo-code.

Do not create fake backend integrations.

Do not create placeholder screens.

Do not leave TODO/FIXME implementation gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and integrate the implementation with the actual repository state.

Implement the requested functionality completely, with production-grade navigation, authentication, state management, networking, playback, offline resilience, accessibility, security, performance, testing, observability, and documentation.

---

# PROJECT

Build the production iOS and Android mobile applications for an original global music streaming platform.

The mobile applications must provide a coherent listener experience supporting:

* account registration
* login
* logout
* session restoration
* profile management
* personalized home
* discovery
* search
* autocomplete
* artist pages
* album pages
* track pages
* playlists
* library
* likes
* follows
* saved albums
* playback
* queue
* playback history
* recommendations
* notifications
* subscription status
* account settings
* privacy controls
* device/session management

The applications must be designed for real-world mobile conditions:

* intermittent connectivity
* variable bandwidth
* background/foreground transitions
* application termination
* device storage limits
* changing audio focus
* Bluetooth/headset controls
* platform-specific permission behavior
* OS resource constraints
* screen-size differences
* accessibility settings
* battery constraints

Use an original mobile experience and visual system.

Do not reproduce proprietary source code, copyrighted assets, or exact visual implementations from any existing commercial streaming application.

---

# TECHNOLOGY DIRECTION

Use:

## Mobile

* React Native
* Expo
* TypeScript

Use Expo modules and native platform capabilities where appropriate.

Use the repository's existing React Native/Expo version and configuration when compatible.

Do not perform unrelated dependency upgrades.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect the existing mobile application structure.
3. Inspect Expo configuration.
4. Inspect navigation.
5. Inspect API integration.
6. Inspect authentication/session handling.
7. Inspect state-management conventions.
8. Inspect playback implementation if present.
9. Inspect secure-storage integration.
10. Inspect notification configuration.
11. Inspect tests.
12. Inspect assets and design-system conventions.
13. Identify existing reusable components.

The repository defines what currently exists.

This prompt defines what this mobile volume must achieve.

Do not assume previous AI-generated prompts are available.

Consume actual backend contracts from the repository.

Do not invent incompatible endpoints.

---

# MOBILE RESPONSIBILITY

This volume is responsible for establishing:

* React Native/Expo application foundation
* navigation
* mobile design-system foundation
* authentication UX
* secure session persistence
* API client
* server-state management
* client-state management
* home/discovery
* search
* artist/album/track screens
* playlist screens
* library
* basic playback architecture
* queue
* notifications foundations
* profile/account settings
* subscription status
* accessibility foundations
* mobile error handling
* analytics foundations
* automated testing

---

# APPLICATION ARCHITECTURE

Implement a scalable feature-oriented React Native architecture.

Separate:

* navigation
* feature modules
* reusable UI
* API/data-access
* server state
* client state
* playback
* device services
* storage
* analytics
* validation

Avoid putting business logic directly inside screen components.

Use clear boundaries between:

* presentation
* application logic
* data fetching
* platform integrations

Do not create a single global state store containing every application concern.

Use server-state management for remote backend data.

Use a focused client-state store for concerns such as:

* playback
* queue
* UI preferences
* transient global state

---

# NAVIGATION

Implement navigation supporting:

* authentication flow
* listener application
* account/settings
* catalog detail screens
* library
* search
* playlist management
* subscription screens
* notification screens

Support:

* protected navigation
* deep links
* nested navigation
* modal workflows where appropriate
* restoration after application restart
* notification/deep-link routing

Do not rely solely on hidden client screens for security.

Backend authorization remains authoritative.

---

# MOBILE DESIGN SYSTEM

Create reusable accessible primitives for:

* buttons
* text
* inputs
* forms
* cards
* lists
* list rows
* dialogs
* bottom sheets
* menus
* tabs
* badges
* avatars
* artwork
* skeletons
* empty states
* error states
* toast/feedback surfaces

Maintain consistent:

* typography
* spacing
* sizing
* icons
* focus/pressed states
* disabled states
* loading behavior

Support both iOS and Android platform conventions without creating incompatible product behavior.

---

# RESPONSIVE MOBILE LAYOUT

Account for:

* small phones
* large phones
* tablets where supported
* portrait
* landscape where appropriate
* safe areas
* notches
* system navigation
* keyboard appearance

Use safe-area handling throughout the application.

Do not place critical controls underneath system UI.

---

# ACCESSIBILITY

Implement:

* screen-reader labels
* accessible roles
* accessible states
* logical traversal order
* dynamic text sizing support
* sufficient contrast
* touch target sizes
* reduced-motion awareness where applicable
* accessible forms
* accessible playback controls

Do not rely on visual color alone to communicate status.

---

# API CLIENT

Implement a centralized typed API client.

Support:

* authentication
* request configuration
* serialization
* response typing
* error normalization
* cancellation where applicable
* safe retries
* request IDs/correlation where appropriate

Do not scatter raw networking logic across screens.

Do not expose internal backend errors directly to users.

---

# SERVER STATE

Use the repository's established server-state solution, preferably TanStack Query when compatible.

Manage:

* current user
* profile
* catalog
* artist
* album
* track
* playlist
* library
* search
* recommendations
* playback session
* notifications
* subscription

Define:

* query keys
* stale times
* cache policy
* invalidation
* retry behavior
* pagination
* optimistic updates where appropriate

Never cache private user data under shared/public keys.

---

# CLIENT STATE

Use centralized client state only for genuinely client-owned data.

Potential state includes:

* player status
* queue
* current track
* volume
* repeat
* shuffle
* temporary UI state
* onboarding state
* network indicators

Do not store server-authoritative subscription or authorization state as an independent long-lived source of truth.

---

# AUTHENTICATION

Implement:

* registration
* login
* logout
* session restoration
* token/session refresh
* password reset
* password change
* verification where supported
* device/session management

Handle:

* invalid credentials
* expired session
* revoked session
* account suspension
* account deletion
* network failure
* backend outage

Do not create infinite refresh loops.

Prevent simultaneous refresh requests from creating race conditions.

---

# SECURE SESSION STORAGE

Store sensitive authentication material using platform-secure storage rather than ordinary unencrypted application storage.

Use the appropriate Expo/native secure-storage mechanism selected by the repository.

Protect:

* access credentials
* refresh credentials
* session secrets

Do not store secrets in:

* AsyncStorage without encryption
* application logs
* analytics
* URLs
* crash reports

Clear secure credentials on logout or account switch when appropriate.

---

# AUTHENTICATION RACE CONDITIONS

Handle concurrent requests during token refresh.

Prevent:

* multiple refresh calls
* stale token overwrite
* request storms
* unauthorized retry loops

Queue or coordinate pending requests where appropriate.

If refresh fails permanently:

* clear session
* clear private server-state cache
* return to authentication
* avoid leaking private screen data

---

# PROTECTED NAVIGATION

Protect:

* private library
* private playlists
* account settings
* subscription
* notifications
* user profile editing
* device/session management

Render authorization-aware UI without treating client state as security enforcement.

When server authorization changes, update the mobile UI accordingly.

---

# HOME AND DISCOVERY

Implement a mobile home experience containing applicable:

* personalized recommendations
* recently played
* featured content
* popular content
* curated playlists
* related artists
* discovery sections

Use performant vertical and horizontal lists where appropriate.

Every data-driven section must support:

* loading
* empty
* partial failure
* retry
* stale content

Do not let one failed section crash the whole screen.

---

# LIST PERFORMANCE

Use appropriate React Native list primitives.

Optimize large collections with:

* FlatList/SectionList or the repository-approved equivalent
* stable keys
* controlled rendering
* memoized list items
* pagination
* incremental fetching

Avoid rendering thousands of track rows simultaneously.

---

# ARTIST SCREEN

Implement artist screens showing:

* artist identity
* artwork
* verification/status where public
* popular tracks
* albums
* releases
* related content
* follow state

Support:

* follow/unfollow
* play artist
* navigation to albums
* navigation to tracks

Respect backend content availability and privacy state.

---

# ALBUM SCREEN

Implement:

* artwork
* title
* artist
* release metadata
* track list
* explicit markers
* save state
* play-all
* track navigation

Support large albums without excessive memory usage.

---

# TRACK SCREEN

Implement track detail presentation where applicable.

Support:

* artwork
* title
* artist
* album
* duration
* explicit state
* playback
* like
* add to playlist
* related recommendations

---

# PLAYLIST SCREEN

Implement:

* playlist artwork
* title
* description
* owner
* visibility
* tracks
* playback
* add/remove
* reorder where authorized
* save/follow where applicable
* collaboration state where available

Prevent unauthorized mutations at the UI layer while still relying on backend authorization.

---

# LIBRARY

Implement:

* liked tracks
* saved albums
* followed artists
* playlists
* recently played

Support:

* pagination
* refresh
* loading
* empty state
* error recovery
* optimistic low-risk mutations

Synchronize state with authoritative backend responses.

---

# SEARCH

Implement mobile search with:

* search input
* debounce
* autocomplete
* result categories
* track results
* artist results
* album results
* playlist results
* empty state
* pagination
* loading state
* retry

Support keyboard submission behavior.

Cancel obsolete requests.

Do not perform unbounded searches.

---

# AUTOCOMPLETE

Implement keyboard-accessible autocomplete behavior.

Support:

* debounced requests
* result selection
* loading state
* no-results state
* request cancellation
* stale-response prevention

Do not let a slower previous search overwrite a newer query.

---

# PLAYER FOUNDATION

Implement a centralized mobile playback subsystem.

Support:

* current track
* play
* pause
* resume
* seek
* previous
* next
* volume
* mute
* buffering
* duration
* progress
* playback errors
* queue
* shuffle
* repeat
* loading
* authorization state

Do not implement playback controls independently in each screen.

---

# AUDIO PLAYBACK

Use the appropriate Expo/native audio capability compatible with the project.

The playback flow must:

1. request backend playback authorization
2. receive secure media access
3. load the audio
4. manage playback state
5. report progress/telemetry
6. handle authorization expiration
7. handle interruptions
8. handle network changes
9. handle track completion

Do not embed object-storage credentials.

Do not persist signed URLs longer than necessary.

---

# MOBILE AUDIO LIFECYCLE

Handle:

* app foreground
* app background
* app suspension
* app termination
* headphones
* Bluetooth audio
* audio focus changes
* phone calls where supported
* other audio sessions
* interruption
* route changes

Use platform-appropriate audio-session behavior.

Do not assume iOS and Android lifecycle behavior is identical.

---

# MEDIA CONTROLS

Integrate device-level playback controls where supported.

Support:

* play
* pause
* previous
* next
* seek where supported
* metadata
* artwork

The controls must update application/player state correctly.

---

# PLAYER UI

Implement:

* mini player
* full-screen player
* progress
* seek
* artwork
* title
* artist
* play/pause
* next/previous
* shuffle
* repeat
* queue access

The mini player must persist appropriately across navigation.

Avoid unnecessary player remounting.

---

# QUEUE

Implement client-side queue management.

Support:

* add
* remove
* reorder
* clear
* play next
* play later
* previous
* current index

When tracks become unavailable:

* detect the condition
* display appropriate state
* skip safely where permitted
* preserve the rest of the queue

---

# PLAYBACK SYNCHRONIZATION

Integrate with backend playback sessions.

Support:

* session creation
* heartbeat
* pause/resume
* seek
* skip
* completion
* termination
* reconnect

Throttle high-frequency network activity.

Do not make every progress tick a database request.

---

# OFFLINE-RESILIENT PLAYBACK STATE

The application must gracefully handle temporary connectivity loss.

Preserve:

* current safe player state
* queue
* local preferences

Where offline playback is not implemented yet, do not falsely imply that media remains available without authorization.

Do not use stale subscription state as proof of entitlement.

---

# PUSH NOTIFICATIONS FOUNDATION

Integrate push-notification registration where supported.

Support:

* permission request
* device-token registration
* token refresh
* notification reception
* deep-link handling
* notification navigation

Respect user preferences and backend authorization.

Do not put private content unnecessarily into notification payloads.

---

# NOTIFICATION CENTER

Implement:

* notification list
* unread count
* read
* mark-all-read
* navigation
* pagination
* loading
* empty
* retry

Synchronize with backend state.

Handle notification arrival while the application is foregrounded and backgrounded.

---

# DEEP LINKS

Implement deep links for supported entities:

* artist
* album
* track
* playlist
* notification destination
* subscription pages

Validate incoming parameters.

Do not trust deep-link data as authorization.

Resolve entities through the backend.

Handle expired/deleted destinations gracefully.

---

# SUBSCRIPTION STATUS

Implement subscription screens supporting:

* current plan
* entitlement
* renewal
* payment state
* cancellation status
* available plans where mobile checkout is supported

The mobile client must consume authoritative backend state.

Do not calculate plan entitlement locally.

---

# PROFILE AND ACCOUNT

Implement:

* profile display
* profile editing
* settings
* privacy
* session/device management
* password/security actions
* account deletion initiation

Sensitive actions must require suitable confirmation and backend authorization.

---

# PRIVACY

Support applicable settings for:

* profile visibility
* listening activity
* social activity
* personalization
* notifications
* marketing
* account deletion

Do not expose private history or activity through UI shortcuts or cached data.

---

# LOGOUT AND ACCOUNT SWITCHING

On logout:

* clear private query cache
* clear user-scoped client state
* clear player authorization
* clear private notifications
* revoke/clear secure credentials
* cancel private requests where practical
* return to authentication

On account switch:

* treat the new user as a new security context
* prevent stale data from the previous account appearing in the new session

---

# NETWORK RESILIENCE

Handle:

* no connectivity
* slow connectivity
* timeout
* server errors
* expired authentication
* partial API failures

Use:

* bounded retries
* exponential backoff
* request cancellation
* stale data where safe
* clear retry controls

Do not retry destructive mutations automatically without idempotency.

---

# MOBILE SECURITY

Protect against:

* insecure credential storage
* deep-link abuse
* token leakage
* sensitive logging
* unauthorized navigation
* unsafe file handling
* malicious remote content
* certificate/network issues where applicable
* screenshot/data leakage for sensitive screens where business requirements justify platform controls

Do not ship secrets inside the application bundle.

Do not treat application-side authorization as sufficient.

---

# FILE HANDLING

For any user or artist uploads:

* validate file type
* enforce size limits
* use secure temporary handling
* avoid permanent local copies unless required
* clean up temporary files
* never execute arbitrary uploaded content
* use backend authorization for uploads

Large media must not be unnecessarily loaded entirely into JavaScript memory.

---

# PERFORMANCE

Optimize for mobile constraints.

Pay particular attention to:

* initial startup
* navigation latency
* JavaScript bundle size
* memory
* battery use
* list rendering
* image memory
* network traffic
* player resource usage
* background processing

Avoid unnecessary re-renders.

Memoize carefully.

Use appropriate image sizing and caching.

---

# IMAGE HANDLING

Implement efficient artwork/image loading.

Support:

* remote image caching
* correct dimensions
* placeholders
* fallback images
* error handling
* memory-conscious sizing

Do not download oversized source artwork when smaller delivery variants are available.

---

# ANALYTICS

Implement mobile analytics through a controlled abstraction.

Track appropriate events such as:

* app open
* screen view
* search
* play
* pause
* skip
* completion
* like
* follow
* playlist actions
* recommendation exposure
* notification interaction
* subscription interaction

Do not transmit:

* credentials
* tokens
* unnecessary private data
* secrets

Respect backend privacy and retention policies.

---

# CRASH AND ERROR OBSERVABILITY

Integrate approved mobile error/crash monitoring.

Capture useful diagnostics for:

* startup crashes
* navigation errors
* API failures
* playback errors
* notification failures
* background-processing issues

Avoid collecting sensitive data unnecessarily.

Include safe correlation identifiers where useful.

---

# ACCESSIBILITY

Validate:

* screen readers on iOS and Android
* dynamic text sizes
* touch targets
* focus/navigation order
* labels
* playback state announcements
* form errors
* dialogs
* bottom sheets
* notification controls

Do not rely solely on automated accessibility tooling.

---

# TESTING

Implement comprehensive mobile tests.

Cover:

* authentication
* protected navigation
* session restoration
* catalog screens
* search
* playlists
* library
* player
* queue
* notifications
* deep links
* subscription state
* privacy
* logout/account switching
* network errors
* token refresh
* playback interruption

Use:

* unit tests
* component tests
* integration tests
* device/emulator E2E tests where appropriate

---

# END-TO-END TESTING

Validate critical journeys such as:

* fresh installation
* registration
* login
* session restoration
* browse catalog
* search
* open artist
* open album
* play track
* use player controls
* modify queue
* like track
* create/edit playlist
* receive notification
* navigate from push notification
* inspect subscription state
* logout
* re-authenticate

Test both iOS and Android-specific behavior where feasible.

---

# DOCUMENTATION

Document:

* mobile architecture
* navigation
* API client
* authentication
* secure storage
* state management
* player architecture
* background/foreground behavior
* push notifications
* deep links
* testing
* environment configuration
* build configuration
* local development

Documentation must represent the actual implementation.

---

# IMPLEMENTATION BOUNDARIES

This mobile volume owns the mobile foundation and core listener experience.

Implement:

* React Native/Expo foundation
* navigation
* design system
* authentication
* secure storage
* API integration
* state management
* home/discovery
* search
* catalog screens
* playlists
* library
* player
* queue
* notifications
* account/settings
* subscription status
* mobile analytics
* accessibility
* mobile tests

Do not implement:

* complete artist administration dashboard
* backend services
* database migrations
* media-processing workers
* Kubernetes/Terraform infrastructure

Only implement mobile-specific integrations required to consume existing backend capabilities.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before changing files:

1. inspect the existing mobile application
2. inspect Expo configuration
3. inspect navigation
4. inspect API and authentication
5. inspect secure storage
6. inspect player/audio implementation
7. inspect notification setup
8. inspect tests
9. identify reusable components and platform abstractions

Then:

1. establish mobile application structure
2. implement navigation
3. implement authentication
4. implement API/state foundations
5. implement catalog/discovery
6. implement search
7. implement playlists/library
8. implement player/queue
9. implement notifications/deep links
10. implement account/subscription surfaces
11. implement accessibility
12. implement analytics/error monitoring
13. add tests
14. validate iOS and Android behavior
15. update documentation

Do not rewrite unrelated mobile functionality.

---

# COMPLETION CRITERIA

This mobile task is complete only when:

* the Expo application builds
* navigation is coherent
* authentication works
* secure session storage is implemented
* protected navigation works
* catalog browsing works
* search works
* playlists work
* library works
* player works
* queue works
* playback lifecycle is handled
* notifications work
* deep links work
* subscription state is displayed authoritatively
* privacy/account flows work
* network failures are handled
* mobile accessibility is implemented
* analytics/error monitoring is integrated
* performance has been validated
* automated tests cover critical mobile behavior
* iOS and Android-specific lifecycle behavior has been addressed
* no required mobile functionality is intentionally incomplete

Do not declare completion when required builds, tests, type checking, device/emulator validation, or runtime checks fail.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* navigation changes
* authentication changes
* secure-storage changes
* API/state-management changes
* catalog/search changes
* playlist/library changes
* player/queue changes
* notification changes
* deep-link changes
* subscription/account changes
* privacy/security changes
* accessibility changes
* analytics/error-monitoring changes
* platform-specific changes
* tests added or updated
* iOS validation performed
* Android validation performed
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified results from assumptions.

Do not claim successful device/emulator workflows unless they were actually executed.

---

# FINAL INSTRUCTION

Implement the production mobile foundation and core listener experience for the music-streaming platform.

Treat mobile as a real production client rather than a smaller web application.

Use platform-secure credential storage.

Design around foreground/background lifecycle transitions.

Make playback resilient to audio interruptions and temporary connectivity loss.

Keep server-authoritative state authoritative.

Protect private data during logout and account switching.

Optimize network, memory, CPU, battery, and media usage for real mobile devices.

Build real screens, real navigation, real backend integration, real playback behavior, real notification handling, real security, real accessibility, and real tests.

The resulting iOS and Android applications must integrate cleanly with the existing backend and provide a maintainable foundation for advanced mobile playback, offline capabilities, push notifications, and platform-specific functionality without requiring incompatible rewrites later.
