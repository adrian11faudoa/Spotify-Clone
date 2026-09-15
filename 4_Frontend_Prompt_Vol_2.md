# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — FRONTEND VOLUME 2

## ROLE

Act as the complete senior frontend engineering organization responsible for implementing the advanced production web application capabilities of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

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

Do not create fake integrations.

Do not create placeholder pages or unfinished workflows.

Do not leave TODO/FIXME implementation gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and integrate the implementation with the actual repository state.

Implement the requested functionality completely, with production-grade authorization-aware UX, accessibility, performance, error handling, testing, observability, and documentation.

---

# PROJECT

Build the advanced web application capabilities for an original global music streaming platform.

This frontend volume is responsible for the web experiences surrounding:

* advanced playback
* collaborative playlists
* social interactions
* personalized discovery
* recommendation surfaces
* notifications
* subscriptions
* billing
* artist experiences
* artist management
* moderation
* support
* administration
* account privacy
* security
* advanced responsive behavior
* real-time updates
* offline/degraded web behavior where applicable
* frontend performance and reliability hardening

The implementation must integrate with the existing web application and its actual backend contracts.

Do not redesign backend APIs arbitrarily.

Do not implement React Native functionality in this task.

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
* Zustand where justified
* React Hook Form
* Zod

Use Web APIs and browser capabilities appropriate to the platform.

Use the repository's established dependency versions and conventions whenever compatible.

Do not perform unrelated dependency upgrades.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect the existing web routes.
3. Inspect the player architecture.
4. Inspect search and recommendation integration.
5. Inspect authentication/session state.
6. Inspect API client abstractions.
7. Inspect query/cache configuration.
8. Inspect notification implementation.
9. Inspect subscription implementation.
10. Inspect existing artist/admin interfaces.
11. Inspect tests.
12. Inspect styling/design-system conventions.
13. Identify reusable components.

The repository defines what currently exists.

This prompt defines what the current frontend task must achieve.

Do not assume earlier AI-generated prompts are available.

Preserve compatible behavior.

Avoid unnecessary rewrites.

---

# FRONTEND RESPONSIBILITY

This volume owns:

* advanced player behavior
* collaborative playlist UX
* recommendation experiences
* personalized discovery
* social features
* notification system
* subscription and billing UX
* artist dashboard
* artist catalog-management UX
* moderation interfaces
* support interfaces
* administration interfaces
* privacy controls
* security controls
* real-time UI synchronization
* resilient data-fetching behavior
* advanced accessibility
* frontend performance hardening
* frontend operational instrumentation

---

# ADVANCED PLAYER ARCHITECTURE

Extend the player into a robust application-level subsystem.

Support:

* persistent playback across route changes
* queue management
* shuffle
* repeat modes
* gapless transition handling where the browser/media format supports it
* playback-rate controls where appropriate
* volume persistence
* mute
* seeking
* progress synchronization
* media loading state
* buffering state
* playback error state
* authorization expiration
* track unavailability
* subscription changes
* device/session changes
* browser visibility changes
* network changes
* recovery after transient failures

Player state must remain independent of route-level component lifecycles.

A route change must not unintentionally stop playback.

---

# PLAYER STATE MODEL

Define strongly typed client state for:

* current track
* previous track
* next track
* queue
* queue position
* playback status
* buffered position
* current position
* duration
* volume
* muted
* shuffle
* repeat
* loading
* buffering
* error
* authorization state
* current playback session
* device state

Separate:

* durable server state
* ephemeral browser state
* derived UI state

Avoid duplicating authoritative backend state throughout multiple stores.

---

# MEDIA SESSION INTEGRATION

Where browser support permits, integrate the Media Session API.

Support:

* play
* pause
* seek
* previous
* next
* metadata
* artwork
* action handlers

Handle unsupported browser features gracefully.

Do not make Media Session functionality a requirement for basic playback.

---

# PLAYBACK PERSISTENCE

Persist only appropriate low-risk player preferences such as:

* volume
* mute preference
* repeat
* shuffle where appropriate
* local queue where product requirements support it

Do not persist:

* authentication credentials
* signed media credentials beyond their safe lifetime
* private server responses unnecessarily
* sensitive subscription information in insecure browser storage

Reconcile persisted player state with server-authoritative catalog and authorization state.

---

# PLAYBACK RETRY AND RECOVERY

Implement controlled retry behavior.

Handle:

* temporary network loss
* expired access
* media access failure
* CDN failure
* browser media errors
* backend timeout
* track unavailability

Use bounded retries with backoff.

When a track cannot be recovered:

* stop retrying
* surface useful feedback
* skip safely when appropriate
* preserve queue integrity
* continue with another playable item when product rules allow it

Do not create infinite retry loops.

---

# REAL-TIME PLAYBACK SYNCHRONIZATION

Integrate WebSocket or another real-time backend mechanism where the repository provides one.

Support applicable:

* playback state updates
* device/session updates
* collaborative playlist changes
* notification updates
* real-time administrative information

Implement:

* connection lifecycle
* reconnect
* authentication refresh
* stale-message protection
* message validation
* duplicate prevention
* state reconciliation

A disconnected client must remain usable where real-time communication is noncritical.

---

# REAL-TIME RECONCILIATION

Never assume every WebSocket message arrives exactly once or in perfect order.

For stateful updates, use:

* server version
* sequence number
* timestamp
* revision
* another explicit ordering mechanism

When the client detects stale state:

* ignore obsolete updates
* request authoritative state when required
* reconcile local state without losing legitimate local actions

---

# COLLABORATIVE PLAYLISTS

Implement collaborative playlist UX where the backend supports it.

Support:

* collaboration status
* collaborator identity
* invitations
* collaborator removal where authorized
* concurrent item changes
* ordering updates
* conflict states
* real-time updates
* activity feedback

Do not silently overwrite concurrent changes.

Surface conflict resolution when the server reports a revision conflict.

---

# PLAYLIST COLLABORATION PERMISSIONS

The UI must distinguish:

* owner
* editor
* viewer
* non-collaborator

Render only appropriate actions.

The backend remains authoritative.

When a user's permissions change remotely, update the UI accordingly.

---

# SOCIAL FEATURES

Implement supported social experiences such as:

* follow/unfollow
* playlist sharing
* social discovery
* activity visibility
* shared playlist participation
* profile visibility where applicable

Respect privacy settings.

Do not expose private listening activity unless the backend explicitly authorizes it.

---

# SHARING

Implement share flows for supported entities:

* track
* album
* artist
* playlist

Prefer application-controlled share URLs.

Validate any dynamic route parameters.

Use browser share capabilities where supported, with safe fallback behavior.

Do not expose signed media URLs as share links.

---

# PERSONALIZED HOME

Build advanced personalized discovery experiences.

Support:

* personalized sections
* recently played
* recommendations
* related content
* contextual recommendations
* editorial/featured content
* continuation experiences

Use reusable section components.

Each section must handle:

* loading
* empty
* partial failure
* retry
* stale data

A single recommendation-service failure must not blank the entire home page.

---

# RECOMMENDATION SURFACES

Implement recommendation surfaces for:

* home
* track page
* album page
* artist page
* search/discovery
* end-of-playback
* library
* personalized playlists

Render recommendation reasons only when supplied by the backend.

Never invent personalized explanations on the client.

---

# RECOMMENDATION FEEDBACK

Where supported, provide controls such as:

* not interested
* hide recommendation
* dislike
* remove from recommendation context

Mutations must use backend-defined contracts.

Do not locally suppress content forever unless the product contract explicitly supports local suppression.

---

# RECOMMENDATION EXPERIMENTATION

Consume backend-provided experiment metadata without exposing internal experimentation details unnecessarily.

Track:

* exposure
* interaction
* conversion/outcome

Keep experiment logic centralized rather than scattering conditions throughout presentation components.

Provide safe default UI when experiment metadata is missing.

---

# SEARCH EXPERIENCE HARDENING

Extend the search experience with:

* search history where supported
* recent searches
* category tabs
* result grouping
* improved empty states
* filter controls
* keyboard navigation
* accessibility
* URL-based search state where appropriate

Do not persist sensitive queries indefinitely.

Provide user controls to clear recent searches where the product supports local or server-side history.

---

# SEARCH PERFORMANCE

Ensure:

* debounced autocomplete
* request cancellation
* stale-response protection
* bounded result sets
* virtualization for large lists where needed
* minimal duplicate network requests

Keep search interactions responsive on slower devices and networks.

---

# NOTIFICATION CENTER

Implement a complete notification experience.

Support:

* unread count
* notification list
* grouping where useful
* mark read
* mark all read
* navigation
* deletion/dismissal where supported
* loading
* pagination
* empty state
* retry
* real-time arrival where supported

Do not poll aggressively when a reliable real-time mechanism exists.

---

# NOTIFICATION PREFERENCES

Implement user controls for:

* channel preferences
* product notifications
* artist/content notifications
* promotional notifications
* security notifications where policy allows configuration

Security-critical communications must follow server-defined rules and must not be hidden merely because the user disabled ordinary notifications.

---

# SUBSCRIPTION EXPERIENCE

Implement complete subscription UI based on backend contracts.

Support:

* plans
* plan comparison
* current subscription
* entitlement summary
* checkout initiation
* billing history
* renewal information
* cancellation
* cancellation reversal
* plan changes
* payment failure state
* grace-period state
* expiration state

Never calculate entitlement solely from UI state.

---

# CHECKOUT FLOW

Implement a secure checkout experience.

Before initiating checkout:

* validate selected plan against server state
* display authoritative price/currency
* show meaningful terms
* handle unavailable plans

During checkout:

* prevent duplicate submissions
* preserve navigation state where appropriate
* handle cancellation
* handle provider errors
* handle network failures

After checkout:

* fetch authoritative subscription state
* do not assume success merely because the provider returned the user to the application

---

# BILLING HISTORY

Implement a billing-history interface.

Support:

* invoice list
* amount
* currency
* status
* date
* subscription relationship
* invoice access/download where supported

Protect billing information.

Do not expose payment credentials or provider-internal sensitive fields.

---

# PAYMENT FAILURE UX

Support clear states for:

* payment failed
* payment retrying
* subscription past due
* grace period
* cancellation pending
* subscription expired

Provide actionable recovery paths based on backend capabilities.

Do not claim payment success without authoritative confirmation.

---

# ARTIST EXPERIENCE

Implement an artist-facing web application.

Support:

* artist dashboard
* artist profile
* catalog overview
* album/release management
* track management
* media upload status
* publishing status
* audience analytics
* playback analytics
* moderation/review state
* team-member management where supported

The artist dashboard must remain isolated from listener-only state.

---

# ARTIST CATALOG MANAGEMENT

Implement forms and workflows for:

* artist metadata
* album metadata
* release metadata
* track metadata
* artwork
* publishing state
* visibility
* explicit-content classification

Use strong form validation.

Show server-side validation failures at the relevant fields.

Do not let artists bypass media-processing or moderation states.

---

# ARTIST UPLOAD UX

Implement media-upload interfaces compatible with the backend upload flow.

Support:

* upload initialization
* direct upload
* progress
* retry
* cancellation where supported
* finalization
* processing state
* validation errors
* processing errors
* completion
* replacement workflow

Do not expose storage credentials.

Do not assume upload completion until the backend confirms it.

---

# UPLOAD PROGRESS

Track upload progress using browser APIs appropriate to the chosen transfer mechanism.

Support large files without freezing the UI.

Handle:

* temporary network failures
* expired uploads
* cancelled uploads
* browser navigation
* duplicate finalization

Do not keep megabyte-scale media data in React state.

---

# ARTIST ANALYTICS

Render artist analytics supplied by the backend.

Support appropriate metrics such as:

* streams
* listeners
* completion
* skips
* saves
* playlist inclusion
* geographic aggregation where privacy policies allow
* content performance

Respect backend-defined aggregation and privacy rules.

Do not expose raw listener identities where the backend has intentionally anonymized the data.

---

# MODERATION UI

Implement moderation workflows for authorized users.

Support:

* report queue
* filters
* report details
* evidence
* target inspection
* decision
* escalation
* dismissal
* resolution
* audit information

Do not expose moderation tools to ordinary listeners.

---

# MODERATION SAFETY

Require explicit confirmation for destructive or high-impact moderation actions.

For actions such as:

* content withdrawal
* account suspension
* catalog restriction
* irreversible deletion

display:

* target
* intended effect
* relevant context
* confirmation requirements

Do not allow accidental one-click destructive actions.

---

# SUPPORT UI

Implement support-facing experiences for authorized operators.

Support:

* user lookup
* account state
* subscription state
* entitlement inspection
* device/session inspection
* security events
* controlled support actions

Display sensitive information only when necessary.

Mask sensitive values where the business workflow does not require the full value.

---

# ADMINISTRATION UI

Implement the administrative web application.

Support appropriate areas such as:

* dashboard
* users
* artists
* catalog
* moderation
* subscriptions
* notifications
* audit logs
* system health
* operational diagnostics

Use clear separation between:

* read-only inspection
* reversible actions
* destructive actions

---

# ADMIN SECURITY UX

Apply stronger UX safeguards for privileged operations.

Support:

* session awareness
* reauthentication where required
* confirmation dialogs
* reason capture
* audit-context display
* permission-aware controls
* expired-session handling

Do not cache privileged data longer than necessary.

---

# PRIVACY SETTINGS

Implement privacy controls supported by the backend.

Potential controls include:

* profile visibility
* listening activity visibility
* social activity visibility
* recommendation personalization
* marketing communications
* data export
* account deletion

Clearly distinguish controls that affect product behavior from controls required for security or legal obligations.

---

# ACCOUNT DELETION UX

Implement a deliberate account-deletion flow.

Require:

* clear warning
* consequences
* confirmation
* reauthentication where required
* final submission
* progress/state feedback

After deletion request:

* clear private client caches
* revoke local session state
* prevent further private API use
* show authoritative deletion status

Do not pretend data is immediately erased if the backend performs asynchronous cleanup.

---

# SESSION AND DEVICE MANAGEMENT

Implement interfaces for:

* active sessions
* devices
* device names
* last activity
* platform
* revoke session
* revoke device

Support bulk revocation where backend permissions allow.

Ensure revoked sessions are removed from client state promptly.

---

# REAL-TIME NOTIFICATIONS

Where WebSockets are available, support:

* notification arrival
* unread-count updates
* playlist collaboration updates
* relevant playback/device state

Fallback gracefully to refetching when the connection is unavailable.

Do not create aggressive polling loops.

---

# OFFLINE AND DEGRADED WEB BEHAVIOR

The web application is not required to provide unrestricted offline music playback.

However, support resilient degraded behavior such as:

* retaining already loaded non-sensitive catalog data during brief connectivity loss
* preserving safe local player preferences
* showing connectivity state
* retrying noncritical requests
* allowing navigation through already available route data where possible

Never treat stale entitlement or authorization data as proof of current access.

---

# NETWORK-AWARE BEHAVIOR

Detect appropriate browser online/offline signals where useful.

Do not equate `navigator.onLine` with actual backend availability.

Combine browser state with real request outcomes.

Provide useful feedback without interrupting playback unnecessarily.

---

# ERROR BOUNDARIES

Implement robust React/Next.js error boundaries for:

* route errors
* feature errors
* player errors
* administration errors
* upload errors

A failure in one recommendation section must not crash the entire home page.

A player failure must not crash the application shell.

---

# ACCESSIBILITY HARDENING

Validate advanced interfaces including:

* drag-and-drop playlist ordering
* upload progress
* dialogs
* notification menus
* autocomplete
* player controls
* data tables
* charts
* admin workflows

Provide keyboard alternatives for interactions that would otherwise require drag gestures.

Do not rely solely on color to communicate state.

---

# DATA TABLES

For artist/admin/support interfaces, build accessible reusable data-table patterns supporting:

* sorting
* filtering
* pagination
* loading
* empty state
* row actions
* selection where required
* responsive behavior

Avoid rendering enormous datasets into the DOM at once.

Use server-side pagination where datasets are large.

---

# DASHBOARDS AND CHARTS

Where analytics dashboards are required, use the project's approved charting approach.

Charts must:

* expose meaningful labels
* remain accessible
* handle missing data
* handle loading
* handle no-data states
* support responsive dimensions
* avoid misleading scales

Do not fabricate analytics data when backend data is unavailable.

---

# PERFORMANCE HARDENING

Optimize advanced application surfaces.

Focus on:

* bundle splitting
* route-level code loading
* image optimization
* virtualized lists
* memoization where measured
* query deduplication
* cache strategy
* prefetching only when useful
* minimizing re-renders
* avoiding unnecessary global-state subscriptions

Do not preload every possible application feature.

---

# MEMORY AND RESOURCE MANAGEMENT

Pay special attention to:

* audio elements
* object URLs
* file previews
* large image previews
* WebSocket connections
* event listeners
* timers
* media upload state
* query subscriptions

Clean up resources when they are no longer needed.

Prevent memory growth during long-lived playback sessions.

---

# SECURITY

Protect advanced frontend surfaces against:

* XSS
* unsafe HTML
* open redirects
* malicious share URLs
* token leakage
* unauthorized privileged UI access
* sensitive-data caching
* clickjacking-related concerns
* untrusted file previews

Never render arbitrary uploaded content directly in the browser without appropriate validation/sanitization.

Do not use client-side role checks as the only protection.

---

# FILE PREVIEWS

For artist uploads and administrative inspection:

* validate file type before preview
* enforce file-size limits
* revoke object URLs after use
* avoid executing uploaded content
* display safe image/audio previews only

Do not embed arbitrary uploaded HTML, SVG, or executable content into privileged interfaces without a deliberate sanitization strategy.

---

# ANALYTICS

Extend frontend analytics for advanced workflows:

* recommendation exposure
* recommendation interaction
* subscription funnel
* checkout interaction
* artist upload stages
* catalog publishing
* moderation action
* support action
* notification interaction
* privacy setting changes

Do not send sensitive administrative data through general product analytics.

Administrative audit events remain server-authoritative.

---

# OBSERVABILITY

Instrument advanced frontend behavior.

Capture useful telemetry for:

* player startup
* playback errors
* buffering
* search latency
* recommendation latency
* upload duration
* upload failure
* route errors
* API error rates
* WebSocket connection health
* checkout failures
* notification delivery UI failures

Correlate with backend request/correlation IDs where available.

Never transmit secrets or unnecessary private information.

---

# TESTING

Implement automated tests covering:

## Player

* route persistence
* play/pause
* seek
* queue
* shuffle
* repeat
* recovery
* authorization expiration
* media failure
* cleanup

## Collaboration

* permissions
* concurrent edits
* real-time updates
* conflict handling

## Recommendations

* rendering
* fallback
* filtering
* experiment metadata
* error isolation

## Subscription

* plan display
* checkout initiation
* billing state
* payment failure
* cancellation
* plan changes

## Artist

* uploads
* validation
* processing status
* catalog editing
* publishing flow
* analytics

## Administration

* permission gating
* user lookup
* moderation
* destructive-action confirmation
* audit display

## Privacy

* privacy changes
* logout
* account switching
* account deletion
* private-data clearing

Use:

* unit tests
* component tests
* integration tests
* end-to-end tests

---

# END-TO-END TESTING

Implement critical advanced workflows such as:

* authenticated listener starts playback
* user creates collaborative playlist
* second session observes playlist changes
* search discovers content
* recommendation surface loads
* user opens subscription page
* checkout begins
* account cancellation state is displayed
* artist uploads audio
* artist observes processing state
* authorized administrator reviews a report
* support operator inspects a user
* user changes privacy settings
* user initiates account deletion
* logout removes private client state

Do not rely on brittle selectors tied to implementation details.

---

# DOCUMENTATION

Update documentation covering:

* advanced frontend architecture
* player architecture
* real-time architecture
* subscription flows
* artist dashboard
* administration UI
* moderation UI
* upload UX
* state-management conventions
* privacy behavior
* testing strategy
* performance strategy
* local development

Documentation must describe actual behavior.

---

# IMPLEMENTATION BOUNDARIES

This frontend volume owns the advanced web experience.

Implement:

* advanced playback
* real-time synchronization
* collaborative playlists
* personalized discovery
* recommendations
* notifications
* subscriptions
* billing
* artist dashboards
* artist catalog workflows
* moderation
* support
* administration
* privacy/security UX
* performance hardening
* advanced testing

Do not implement:

* React Native mobile application
* backend business logic
* database migrations
* production infrastructure-as-code
* server-side media processing

Consume existing backend contracts.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before changing files:

1. inspect the current frontend
2. map existing routes
3. inspect player state
4. inspect query/cache configuration
5. inspect authentication
6. inspect notification/subscription features
7. inspect artist/admin surfaces
8. inspect reusable UI components
9. inspect tests
10. identify compatibility constraints

Then:

1. implement advanced player behavior
2. implement real-time synchronization
3. implement collaborative/social features
4. implement recommendations
5. implement notifications
6. implement subscription/billing UI
7. implement artist tools
8. implement moderation/support/admin tools
9. implement privacy/security UX
10. harden performance and accessibility
11. add tests
12. validate affected workflows
13. update documentation

Do not rewrite unrelated frontend code.

---

# COMPLETION CRITERIA

This frontend task is complete only when:

* advanced playback behavior is robust
* player state survives route transitions
* playback failures recover safely
* real-time synchronization is implemented where required
* collaborative playlists handle concurrent changes
* recommendations render with proper fallbacks
* notification center works
* notification preferences work
* subscription and billing UX reflects authoritative backend state
* artist workflows work
* media-upload UX works
* moderation interfaces work
* support interfaces work
* administration interfaces work
* privacy controls work
* account deletion UX is complete
* privileged interfaces are appropriately protected
* accessibility is implemented throughout advanced workflows
* performance has been validated
* frontend telemetry is implemented
* tests cover critical workflows
* end-to-end testing covers advanced user journeys
* no required frontend functionality is intentionally incomplete

Do not declare completion when required builds, tests, type checking, or browser validation fail.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* advanced player changes
* real-time changes
* collaborative playlist changes
* recommendation changes
* notification changes
* subscription/billing changes
* artist functionality
* upload functionality
* moderation functionality
* support functionality
* administration functionality
* privacy/security changes
* performance changes
* accessibility changes
* analytics/observability changes
* tests added or updated
* end-to-end workflows validated
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified results from assumptions.

Do not claim successful browser workflows or performance validation unless they were actually executed.

---

# FINAL INSTRUCTION

Implement the advanced production web experience for the music-streaming platform.

The player must behave like a durable application subsystem rather than a collection of page-level controls.

Real-time state must be recoverable.

Collaborative changes must remain consistent under concurrency.

Recommendations must degrade gracefully.

Subscription and entitlement information must remain server-authoritative.

Artist, moderation, support, and administration workflows must be strongly permission-aware.

Uploads must remain secure from browser preview through final processing state.

Private data must be cleared appropriately during logout, account switching, and deletion.

Accessibility, performance, security, observability, and testing are part of the implementation, not later polish.

Build complete real workflows that integrate with the existing backend contracts and remain maintainable as the user base, catalog, and application complexity grow.
