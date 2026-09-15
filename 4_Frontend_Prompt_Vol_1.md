# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — FRONTEND VOLUME 1

## ROLE

Act as the complete senior frontend engineering organization responsible for implementing the production-grade web application of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

Operate as:

* Principal Software Architect
* Staff Frontend Engineer
* UI/UX Engineer
* Performance Engineer
* Security Engineer
* QA Engineer
* Reliability Engineer
* Technical Writer

This prompt defines an independent frontend implementation task.

Do not provide a tutorial.

Do not provide pseudo-code.

Do not create fake backend integrations.

Do not create placeholder pages.

Do not leave TODO/FIXME implementation gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and integrate the web application with the actual repository state.

Implement the requested functionality completely, with production-grade accessibility, responsiveness, security, performance, state management, API integration, testing, observability, error handling, and documentation.

---

# PROJECT

Build the production web application for an original global music streaming platform.

The web client must provide a polished, responsive, accessible experience for:

* anonymous visitors
* registered listeners
* free listeners
* premium listeners
* artists
* artist representatives
* moderators
* support operators
* administrators

The listener-facing experience must support:

* authentication
* home/discovery
* search
* artist pages
* album pages
* track pages
* playlists
* user library
* liked tracks
* saved albums
* followed artists
* playback
* queue
* playback history
* recommendations
* notifications
* account/profile management
* subscription management foundations

The application must also provide appropriately protected interfaces for artist, moderation, support, and administrative capabilities that belong in the web platform.

Build an original interface and visual system.

Do not copy proprietary source code, copyrighted assets, or exact visual implementations from any existing commercial service.

---

# TECHNOLOGY DIRECTION

Use:

## Web

* Next.js
* React
* TypeScript
* Tailwind CSS
* shadcn/ui
* TanStack Query
* Zustand where global client state is justified
* React Hook Form
* Zod
* accessible browser APIs
* responsive layout architecture

Use the repository's existing framework versions and configuration when compatible.

Do not perform unrelated dependency upgrades.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect the existing Next.js application.
3. Inspect route structure.
4. Inspect component architecture.
5. Inspect styling and design-system configuration.
6. Inspect API client code.
7. Inspect authentication integration.
8. Inspect state-management conventions.
9. Inspect tests.
10. Inspect asset handling.
11. Inspect environment configuration.
12. Identify reusable components and layouts.

The repository defines what currently exists.

This prompt defines what this frontend volume must achieve.

Do not assume that previous prompts or AI conversations are available.

Consume backend contracts exposed by the repository.

Do not invent incompatible API endpoints when an existing implementation already defines the contract.

---

# FRONTEND RESPONSIBILITY

This frontend volume is responsible for establishing:

* application shell
* routing architecture
* design system foundations
* authentication UX
* session handling
* protected routes
* shared layouts
* catalog browsing
* search experience
* artist pages
* album pages
* track presentation
* playlist pages
* library pages
* basic playback UI
* queue interface
* notifications UI
* profile/account UI
* subscription UX foundations
* global loading/error/empty states
* responsive behavior
* accessibility foundations
* client-side security practices
* frontend testing foundations

---

# APPLICATION ARCHITECTURE

Implement a scalable Next.js architecture.

Separate:

* route-level composition
* shared layouts
* feature modules
* reusable UI components
* API/data-access layer
* client-state management
* server-state management
* form logic
* validation
* analytics
* accessibility behavior

Avoid placing business logic directly into presentation components.

Avoid creating a single global state object for every application concern.

Use TanStack Query for server state.

Use Zustand only for state that genuinely benefits from client-side centralized coordination, such as:

* player state
* temporary queue state
* UI preferences
* transient global interaction state

Do not duplicate server-authoritative state unnecessarily.

---

# ROUTING

Establish clear route groups for:

* public pages
* authenticated listener pages
* artist pages
* account pages
* subscription pages
* moderation pages
* administration pages where appropriate

Support:

* route-level authorization
* loading states
* error boundaries
* not-found states
* appropriate metadata
* deep links
* browser navigation
* refresh resilience

Do not rely solely on client-side hiding to protect privileged routes.

Sensitive routes must also respect server-side authorization.

---

# APPLICATION SHELL

Implement the main web shell.

Include appropriate shared structures such as:

* top/navigation area
* primary navigation
* responsive sidebar where appropriate
* content region
* persistent playback controls
* notification access
* account controls
* responsive mobile navigation

The layout must adapt to:

* desktop
* tablet
* narrow mobile browser widths

Do not allow persistent playback UI to obscure content.

Use stable layout behavior to minimize cumulative layout shift.

---

# DESIGN SYSTEM

Establish a reusable design system using:

* shadcn/ui
* Tailwind CSS
* accessible primitives
* project-specific tokens

Define consistent patterns for:

* buttons
* inputs
* selects
* dialogs
* drawers
* dropdowns
* tabs
* tooltips
* cards
* badges
* avatars
* skeletons
* alerts
* toast notifications
* menus
* pagination/load-more controls

Use consistent:

* typography
* spacing
* radii
* sizing
* focus states
* hover states
* disabled states
* loading states
* error states

Do not duplicate equivalent components across feature folders.

---

# RESPONSIVE DESIGN

Build responsive layouts for:

* desktop
* tablet
* mobile

Account for:

* touch interactions
* pointer interactions
* keyboard navigation
* dynamic content lengths
* translated strings
* long artist/album/playlist names
* small viewport heights
* browser zoom
* reduced-motion settings

Do not assume a fixed viewport size.

---

# ACCESSIBILITY

Implement accessibility as a first-class requirement.

Support:

* semantic HTML
* keyboard navigation
* visible focus states
* accessible names
* labels
* form descriptions
* error announcements where appropriate
* dialog focus management
* menu keyboard behavior
* sufficient contrast
* reduced-motion preferences
* screen-reader-compatible controls

Interactive playback controls must have meaningful accessible labels and states.

Do not use clickable noninteractive elements where a semantic button or link is appropriate.

---

# API DATA LAYER

Implement a typed API client abstraction.

Support:

* request configuration
* authentication
* error normalization
* request cancellation
* retries only where safe
* response typing
* correlation/request identifiers where appropriate

Do not scatter raw `fetch` calls throughout components.

Map backend API errors into predictable frontend error models.

Do not expose server internals directly to users.

---

# SERVER STATE

Use TanStack Query for remote server state.

Define appropriate query keys for:

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

Configure:

* caching
* stale times
* invalidation
* refetch behavior
* optimistic updates where safe

Do not invalidate the entire application cache after every mutation.

Invalidate the smallest relevant query scopes.

---

# AUTHENTICATION UX

Implement authentication flows for:

* registration
* login
* logout
* session restoration
* refresh
* password reset
* password change
* email/account verification where supported
* session/device management where exposed

Support:

* validation
* loading states
* invalid credentials
* expired session
* locked/disabled account
* network failure
* retry behavior

Do not expose raw backend errors or security-sensitive details.

---

# TOKEN HANDLING

Follow the backend's authentication contract.

Do not store sensitive long-lived credentials in insecure browser storage merely for convenience.

Prefer secure server-supported session mechanisms when the backend architecture supports them.

When token-based access is required:

* isolate token handling
* implement refresh behavior
* handle expiration
* handle revocation
* prevent duplicate refresh requests
* prevent refresh loops

Do not place access tokens in URLs.

Do not log tokens.

---

# PROTECTED ROUTES

Implement route protection based on actual authenticated state.

Protect:

* account pages
* private playlists
* user library
* playback controls requiring authentication
* subscription pages
* artist-management pages
* moderation
* administration

Server-side authorization remains authoritative.

The frontend must never imply access that the backend will reject.

---

# AUTHORIZATION-AWARE UX

Represent permissions without duplicating server authority.

The client may conditionally render controls based on known user capabilities, but the backend remains authoritative.

Handle:

* permission denied
* account suspension
* revoked access
* resource ownership changes
* expired privileges

Gracefully recover when permissions change while a user is actively using the application.

---

# HOME AND DISCOVERY

Implement the listener home experience.

Support sections for:

* personalized recommendations
* recently played
* recommended playlists
* featured content
* popular content
* related artists
* discovery content

Sections must be data-driven.

Do not hardcode fake catalog content into production components.

Provide loading, empty, and error states for every dynamic section.

---

# CONTENT CARDS

Create reusable presentation components for:

* track
* album
* artist
* playlist
* recommendation

Cards must support:

* title
* supporting metadata
* artwork
* contextual actions
* play action where appropriate
* keyboard accessibility
* responsive behavior

Avoid unnecessary image loading.

Use appropriate image optimization.

---

# ARTIST PAGES

Implement artist pages displaying appropriate:

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
* navigation into albums/tracks

Respect unpublished and restricted content returned by the backend.

Do not infer publication state solely from cached client data.

---

# ALBUM PAGES

Implement album pages supporting:

* artwork
* title
* artist
* release metadata
* track list
* total duration
* explicit-content indicators where applicable
* save state
* play-all action

Track rows should provide:

* play
* context menu
* navigation
* like state where appropriate

Ensure large track lists remain performant.

---

# TRACK PRESENTATION

Implement reusable track-row behavior.

Support:

* play
* pause
* add to playlist where authorized
* like/unlike
* navigation
* explicit marker
* duration
* loading state
* unavailable state

Use virtualization or other performance techniques for very large collections where appropriate.

---

# PLAYLIST PAGES

Implement listener playlist functionality.

Support:

* playlist metadata
* cover
* owner
* visibility
* track list
* playback
* add/remove where authorized
* reorder where authorized
* delete where authorized
* like/save where supported
* collaboration controls where the backend exposes them

Prevent unauthorized controls from appearing as if they were valid actions.

---

# PLAYLIST EDITING

Implement form and mutation flows for:

* title
* description
* artwork
* visibility
* track membership
* ordering

Use optimistic UI only when rollback behavior is reliable.

For collaborative or concurrent editing, surface conflict/error states instead of silently overwriting changes.

---

# LIBRARY

Implement user-library pages for:

* liked tracks
* saved albums
* followed artists
* playlists
* recently played where appropriate

Support:

* sorting/filtering where supported
* pagination/infinite loading
* empty states
* optimistic like/save actions
* error recovery

Use server-authoritative state after mutations settle.

---

# SEARCH

Implement search experience with:

* search input
* debounce
* autocomplete where supported
* result categories
* tracks
* artists
* albums
* playlists
* filtering
* pagination/infinite loading
* empty results
* loading state
* search errors

Do not query the API on every keystroke without debouncing.

Cancel obsolete requests.

Do not expose raw search-engine syntax to ordinary users.

---

# SEARCH AUTOCOMPLETE

Implement low-latency autocomplete.

Support:

* debounced requests
* keyboard navigation
* mouse/touch selection
* accessible listbox behavior
* loading state
* empty state
* error fallback

Prevent stale responses from replacing newer search results.

---

# PLAYER ARCHITECTURE

Implement a centralized client-side player state.

The player must support:

* current track
* play
* pause
* resume
* seek
* skip
* previous
* volume
* mute
* progress
* duration
* buffering
* playback error
* queue
* repeat
* shuffle where supported
* loading
* authorization failure
* media unavailability

Separate:

* player UI
* player state
* backend playback session
* media element/browser playback

Do not couple every screen directly to the HTML audio element.

---

# AUDIO PLAYBACK INTEGRATION

Use the backend playback contract for media authorization.

The client must:

1. request playback authorization
2. receive permitted media access
3. load the media safely
4. begin playback
5. report playback state/telemetry according to backend expectations
6. refresh or reauthorize access when required
7. handle expired access
8. handle unavailable media

Do not expose object-storage credentials.

Do not persist signed media URLs longer than necessary.

---

# PLAYBACK STATE SYNCHRONIZATION

Synchronize relevant client state with backend state.

Handle:

* session creation
* heartbeat
* pause
* resume
* seek
* skip
* completion
* interruption
* reconnect

Avoid sending unnecessary network requests for every UI render.

Batch or throttle high-frequency progress updates appropriately.

Do not allow delayed responses to overwrite newer local playback state.

---

# QUEUE

Implement a client-side playback queue.

Support:

* add track
* remove track
* reorder
* clear
* next
* previous
* queue persistence where appropriate

Keep queue state separate from server-authoritative catalog metadata.

When queue items become unavailable:

* surface the condition
* skip safely where appropriate
* keep remaining queue entries intact

---

# PLAYBACK ERROR HANDLING

Handle:

* authorization failure
* expired media access
* network interruption
* unsupported media
* CDN failure
* playback decode failure
* unavailable content
* subscription expiration
* device/browser limitations

Do not trap the player in infinite automatic retry loops.

Provide a useful user-facing state and recover where safe.

---

# NOTIFICATIONS

Implement web notification UI for:

* notification list
* unread count
* mark read
* mark all read where supported
* notification navigation

Respect backend notification preferences.

Do not expose provider-internal notification metadata.

---

# PROFILE AND ACCOUNT

Implement:

* profile display
* profile editing
* account settings
* privacy settings where supported
* session/device management
* password changes
* account deletion initiation

Sensitive operations must require appropriate confirmation.

Do not place security-sensitive data into URLs.

---

# SUBSCRIPTION UX

Implement subscription-facing web experiences based on backend contracts.

Support:

* current plan
* entitlement status
* available plans
* checkout initiation
* billing history
* renewal information
* cancellation
* cancellation reversal where supported

Do not calculate payment status on the client.

Do not accept arbitrary pricing from URL/query parameters.

Display server-authoritative plan and entitlement information.

---

# LOADING, EMPTY, AND ERROR STATES

Every remote-data feature must define:

* initial loading
* background loading
* empty
* partial failure
* full failure
* retry

Avoid blank screens.

Use skeletons where appropriate.

Keep previously loaded data visible during safe background refetches.

Do not display stale sensitive authorization information after the session changes.

---

# FORMS

Use React Hook Form and Zod where appropriate.

Forms must provide:

* client validation
* server validation handling
* field errors
* submission state
* disabled state
* success feedback
* retry
* accessibility

Client validation is an experience optimization, not a security boundary.

The backend remains authoritative.

---

# OPTIMISTIC UPDATES

Use optimistic updates selectively for low-risk interactions such as:

* like/unlike
* follow/unfollow
* save/unsave

Every optimistic mutation must define:

* optimistic state
* rollback
* failure feedback
* reconciliation with server state

Do not use optimistic updates for sensitive financial or authorization state.

---

# FRONTEND SECURITY

Protect against:

* XSS
* unsafe HTML rendering
* token leakage
* open redirects
* malicious URL handling
* insecure client-side authorization assumptions
* sensitive-data persistence
* clickjacking-related issues where applicable

Never render untrusted HTML without controlled sanitization.

Do not put secrets in:

* client bundles
* public environment variables
* URLs
* local storage

---

# CONTENT SECURITY

Treat catalog metadata and user-generated playlist metadata as untrusted text.

Safely render:

* playlist descriptions
* artist biographies
* user-generated names
* metadata from external providers

Prevent markup injection.

Do not interpolate untrusted values directly into HTML or unsafe browser APIs.

---

# PERFORMANCE

Optimize for:

* first contentful render
* largest contentful render
* interaction responsiveness
* image loading
* bundle size
* route transitions
* search responsiveness
* player responsiveness
* memory usage

Use:

* Next.js rendering capabilities
* code splitting
* dynamic imports where appropriate
* image optimization
* memoization when justified
* virtualization for large lists
* request deduplication

Do not prematurely optimize every component.

Measure and address actual bottlenecks.

---

# MEDIA PERFORMANCE

Optimize artwork and playback UI.

Use:

* responsive image sizes
* lazy loading
* appropriate caching
* stable dimensions to reduce layout shifts

For audio:

* preload intentionally
* avoid unnecessary simultaneous downloads
* clean up previous media resources
* avoid retaining obsolete signed URLs
* respond to network conditions where appropriate

---

# ACCESSIBILITY TESTING

Test:

* keyboard-only navigation
* screen-reader labels
* focus management
* dialogs
* menus
* playback controls
* forms
* search
* dynamic updates
* responsive interactions

Fix accessibility defects rather than suppressing automated warnings without analysis.

---

# ANALYTICS

Integrate frontend analytics events through a controlled abstraction.

Track appropriate events such as:

* page view
* search
* play
* pause
* skip
* like
* follow
* playlist interaction
* recommendation exposure
* subscription interaction
* notification interaction

Do not send:

* passwords
* tokens
* secret configuration
* unnecessary private content

Respect user privacy and backend-defined analytics policies.

---

# ERROR MONITORING

Integrate frontend error reporting through the repository's approved observability architecture.

Capture useful:

* route errors
* API failures
* playback failures
* rendering failures
* JavaScript exceptions
* performance signals

Do not transmit sensitive user data unnecessarily.

Correlate client failures with backend request IDs where safely possible.

---

# ROUTE AND DATA CACHING

Define caching behavior appropriate to:

* public catalog
* authenticated user data
* recommendations
* search
* notifications
* subscription state

Private data must never be accidentally shared through public caches.

Invalidate sensitive data promptly after:

* logout
* account switching
* permission changes
* subscription changes
* account suspension
* account deletion

---

# ACCOUNT SWITCHING AND LOGOUT

On logout or account change:

* clear private query caches
* clear client-specific state
* clear player authorization state where appropriate
* cancel in-flight private requests
* remove private notifications
* prevent stale private pages from being displayed as current

Do not leak one account's information after switching users.

---

# TESTING

Implement comprehensive frontend tests.

Cover:

* route rendering
* authentication flows
* protected routes
* authorization-aware UI
* API error handling
* search
* autocomplete
* catalog pages
* playlist operations
* library mutations
* player state
* playback failures
* queue behavior
* subscription UX
* notifications
* account settings
* optimistic updates
* responsive behavior
* accessibility

Use:

* unit tests
* component tests
* integration tests
* end-to-end tests where appropriate

Test real state transitions, not only visual snapshots.

---

# END-TO-END TESTING

Provide critical browser workflows such as:

* visitor browsing catalog
* registration
* login
* search
* opening artist
* opening album
* starting playback
* liking track
* creating playlist
* adding track
* editing playlist
* navigating library
* subscription checkout initiation
* notification reading
* logout

Protect tests from relying on brittle implementation details.

---

# DOCUMENTATION

Document:

* web architecture
* route organization
* state-management conventions
* API client conventions
* player architecture
* authentication behavior
* testing strategy
* local development
* environment configuration
* accessibility conventions
* analytics integration

Documentation must reflect actual implementation.

---

# IMPLEMENTATION BOUNDARIES

This frontend volume owns the core web application foundation and listener-facing experience.

Implement:

* application shell
* routing
* design system foundation
* authentication UX
* catalog browsing
* search
* artist/album/track pages
* playlists
* library
* player
* queue
* notifications
* account
* subscription foundations
* frontend observability
* frontend testing

Do not implement:

* React Native mobile application
* backend services
* media-processing workers
* infrastructure-as-code
* database migrations

Consume backend contracts rather than redesigning them.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before making changes:

1. inspect the current web application
2. identify routing structure
3. identify existing component system
4. inspect API integration
5. inspect auth/session integration
6. inspect existing state management
7. inspect tests
8. inspect environment configuration

Then:

1. establish the application shell
2. implement design-system foundations
3. implement authentication UX
4. implement catalog/discovery
5. implement search
6. implement playlists/library
7. implement player/queue
8. implement account/notifications/subscription surfaces
9. add accessibility
10. add observability
11. add tests
12. validate the application
13. update documentation

Do not rewrite unrelated frontend functionality.

---

# COMPLETION CRITERIA

This frontend task is complete only when:

* application routing is coherent
* the shell is responsive
* authentication UX works
* protected routes behave correctly
* server state uses appropriate query management
* catalog pages work
* search works
* autocomplete works
* playlists work
* library works
* playback UI works
* queue works
* playback errors are handled
* notifications work
* account settings work
* subscription UI consumes authoritative backend state
* forms validate correctly
* loading/empty/error states are complete
* accessibility requirements are implemented
* analytics integration is controlled
* observability is implemented
* security requirements are met
* automated tests cover critical flows
* end-to-end validation covers the primary listener journey
* no required UI functionality is intentionally incomplete

Do not declare completion when required build, type-checking, tests, or runtime validation fail.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* routes added or modified
* shared components created or modified
* API client changes
* authentication changes
* state-management changes
* catalog/search changes
* playlist/library changes
* player/queue changes
* notification changes
* subscription changes
* analytics changes
* accessibility changes
* security changes
* observability changes
* tests added or updated
* validation performed
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified results from assumptions.

Do not claim successful browser workflows, builds, tests, or accessibility checks unless they were actually performed.

---

# FINAL INSTRUCTION

Implement the production web application for the music-streaming platform.

Build a polished, responsive, accessible, high-performance experience.

Keep backend authority on the backend.

Keep server state in TanStack Query.

Keep genuinely global client state in carefully scoped stores.

Keep playback state centralized and resilient.

Protect private data across navigation, caching, logout, and account switching.

Treat all external text and metadata as untrusted.

Build real components, real state transitions, real API integration, real loading/error handling, real accessibility, and real tests.

Do not create superficial page scaffolding and call it complete.

The resulting web application must provide a coherent, production-grade listener experience that integrates cleanly with the platform's backend contracts and can scale as the catalog, user base, and playback workload grow.
