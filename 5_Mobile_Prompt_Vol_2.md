# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — MOBILE VOLUME 2

## ROLE

Act as the complete senior mobile engineering organization responsible for implementing the advanced production mobile capabilities of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

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

Do not create fake integrations.

Do not create placeholder workflows.

Do not leave TODO/FIXME implementation gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and integrate the implementation with the actual repository state.

Implement the requested functionality completely, with production-grade playback, background behavior, offline capabilities, push notifications, deep links, device synchronization, artist capabilities, accessibility, security, performance, testing, observability, and documentation.

---

# PROJECT

Build the advanced production mobile capabilities for an original global music streaming platform.

This mobile volume is responsible for:

* advanced audio playback
* background playback
* lock-screen and system media controls
* audio interruption handling
* Bluetooth/headset behavior
* playback-session synchronization
* multi-device awareness
* collaborative playlist behavior
* real-time updates
* push notification workflows
* deep links
* offline-capable application behavior
* secure offline-download foundations where the product supports offline playback
* mobile subscription workflows
* artist-facing mobile capabilities where applicable
* advanced analytics
* privacy controls
* mobile security hardening
* performance and battery optimization
* production release hardening

The implementation must integrate with the existing React Native/Expo application and actual backend contracts.

Do not assume earlier AI-generated prompts exist.

Do not arbitrarily redesign backend APIs.

---

# TECHNOLOGY DIRECTION

Use:

## Mobile

* React Native
* Expo
* TypeScript

Use appropriate Expo/native modules for:

* audio
* secure storage
* notifications
* deep linking
* background execution
* filesystem/storage
* device information
* network state

Use the repository's established versions and abstractions wherever compatible.

Do not perform unrelated dependency upgrades.

Where a feature requires native configuration, implement the required iOS and Android configuration rather than leaving an architectural placeholder.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect the existing mobile application.
3. Inspect navigation.
4. Inspect authentication and secure storage.
5. Inspect the current player.
6. Inspect API and server-state handling.
7. Inspect notification registration.
8. Inspect deep-link configuration.
9. Inspect filesystem/storage integrations.
10. Inspect platform configuration.
11. Inspect tests.
12. Inspect build and release configuration.
13. Identify existing reusable components and native abstractions.

The repository defines what currently exists.

This prompt defines what this mobile volume must achieve.

Preserve compatible behavior.

Do not rewrite unrelated mobile functionality.

---

# MOBILE RESPONSIBILITY

This volume owns:

* advanced player architecture
* background playback
* operating-system media controls
* audio focus/interruption handling
* playback recovery
* real-time synchronization
* multi-device state
* collaborative playlists
* push notification integration
* deep linking
* offline behavior
* secure local media handling where supported
* subscription/payment UX where supported
* artist mobile functionality where justified
* advanced privacy/security
* analytics
* performance/battery hardening
* release-readiness validation

---

# ADVANCED PLAYER ARCHITECTURE

Implement the player as a durable application subsystem independent from individual screens.

Support:

* persistent playback across navigation
* app backgrounding
* app foregrounding
* app suspension
* app termination where platform rules permit recovery
* queue persistence
* shuffle
* repeat
* seek
* next/previous
* volume
* buffering
* playback recovery
* media-access expiration
* unavailable content
* subscription state changes
* device/session changes
* headset interactions
* Bluetooth route changes
* phone-call interruptions where platform APIs expose them
* audio-focus changes
* network transitions

Player state must survive screen unmounting.

Do not instantiate independent audio engines per screen.

---

# PLAYER STATE MODEL

Maintain explicit state for:

* current track
* queue
* queue index
* playback state
* loading
* buffering
* position
* duration
* buffered position
* volume
* muted
* repeat mode
* shuffle mode
* playback session
* authorization state
* error
* device state

Separate:

* source-of-truth backend state
* platform audio state
* client playback state
* UI-derived state

Avoid circular synchronization between stores.

---

# BACKGROUND PLAYBACK

Implement background playback using platform-supported audio capabilities.

The application must continue playback when the product and OS permit:

* screen locked
* application backgrounded
* user navigates to another application

Configure appropriate iOS and Android capabilities.

Ensure:

* audio continues correctly
* player state remains synchronized
* system controls operate correctly
* backend playback sessions remain valid
* progress/heartbeat processing is appropriately throttled
* battery consumption is controlled

Do not rely on ordinary foreground JavaScript timers for critical background playback behavior.

---

# IOS AUDIO SESSION

Implement appropriate iOS audio-session behavior.

Handle:

* background audio
* interruptions
* route changes
* headphones
* Bluetooth
* other audio sources
* phone-call interruption
* audio-session activation/deactivation

Restore playback state correctly after transient interruptions.

Do not automatically resume after every interruption if the operating system or user action indicates that playback should remain paused.

---

# ANDROID AUDIO FOCUS

Implement appropriate Android audio-focus behavior.

Handle:

* transient focus loss
* permanent focus loss
* ducking
* competing audio
* headset disconnection
* Bluetooth routing

Ensure behavior is consistent with the product's playback rules.

Do not restart playback unexpectedly after permanent focus loss.

---

# MEDIA CONTROLS

Integrate system-level media controls.

Support where available:

* play
* pause
* next
* previous
* seek
* metadata
* artwork

Ensure system commands update the central player state.

The application must remain synchronized when commands originate outside the app UI.

---

# HEADPHONES AND BLUETOOTH

Handle:

* wired-headset connection/disconnection
* Bluetooth connection/disconnection
* route changes
* accidental media interruption
* output-device changes

When a headset is disconnected, stop or pause playback according to platform-appropriate behavior and product requirements.

Do not continue playing unexpectedly through speakers after an output route disappears.

---

# PLAYBACK RECOVERY

Implement controlled recovery for:

* network interruption
* temporary CDN failure
* media decoder error
* expired media-access authorization
* backend timeout
* player initialization failure
* app lifecycle transition

Use bounded retries.

When authorization expires:

1. request fresh authorization
2. validate that entitlement still exists
3. refresh media access
4. resume only when safe
5. avoid duplicate authorization requests

Never retry permanently.

---

# PLAYBACK TELEMETRY

Integrate client telemetry with backend playback contracts.

Support appropriate events such as:

* started
* paused
* resumed
* seeked
* skipped
* buffering
* completed
* playback error
* quality/media change

Throttle high-frequency events.

Buffer events during short network interruptions where product requirements allow.

Avoid unbounded local telemetry queues.

---

# PLAYBACK PROGRESS

Synchronize durable playback position appropriately.

Do not write to the backend on every frame.

Use throttled progress checkpoints.

Ensure:

* local position remains smooth
* server updates are eventually synchronized
* delayed responses cannot overwrite newer local state
* app termination does not unnecessarily lose a large amount of progress

---

# MULTI-DEVICE PLAYBACK

Implement device/session awareness.

Support:

* current device
* active devices
* device list
* device revocation
* playback session state
* session expiration

Where product requirements support playback transfer, implement a safe device handoff workflow.

Never authorize another device solely from a client-provided device ID.

---

# REAL-TIME MOBILE SYNCHRONIZATION

Integrate real-time communication for relevant features.

Potential use cases:

* collaborative playlist changes
* playback/device state
* notification updates
* account/session events

Implement:

* authentication
* reconnect
* backoff
* stale-message protection
* duplicate handling
* connection lifecycle
* state reconciliation

When disconnected, fall back to ordinary API synchronization.

---

# COLLABORATIVE PLAYLISTS

Implement mobile collaboration UX supporting:

* collaborator list
* owner/editor distinctions
* add/remove collaborators where authorized
* real-time item changes
* ordering changes
* conflict handling
* activity feedback

Do not silently overwrite concurrent changes.

When the backend reports a revision conflict:

* preserve local intent where possible
* refresh authoritative state
* clearly communicate the conflict
* retry only when safe

---

# PUSH NOTIFICATIONS

Implement production push notification support.

Support:

* permission request
* registration
* token submission
* token refresh
* invalid token handling
* notification receipt
* notification interaction
* foreground notifications
* background notifications
* deep-link routing

Do not request notification permission at application launch without a meaningful product context when the platform experience allows a better timing.

---

# PUSH TOKEN SECURITY

Treat push tokens as device-associated identifiers.

Store them server-side through authorized APIs.

Do not expose them through analytics unnecessarily.

Handle token rotation and invalidation.

When a user logs out:

* revoke/unregister the device token where appropriate
* remove private notification context
* prevent another account on the same device from receiving private notifications

---

# NOTIFICATION ROUTING

A notification may route to:

* track
* album
* artist
* playlist
* subscription
* account/security page
* moderation/support destination where authorized

Validate the destination.

Resolve protected resources through normal authorization-aware API flows.

Do not embed sensitive data directly into notification payloads.

---

# DEEP-LINK SECURITY

Validate all deep-link parameters.

Do not trust:

* user IDs
* resource IDs
* action parameters
* authorization claims embedded in URLs

Deep links identify destinations; the backend determines whether the user may access them.

Handle:

* deleted content
* withdrawn tracks
* private playlists
* expired subscriptions
* invalid IDs
* malformed URLs

---

# OFFLINE ARCHITECTURE

Implement a robust offline/degraded mobile architecture.

At minimum support safe offline behavior for:

* previously loaded catalog metadata
* user interface state
* queue state
* low-risk player preferences
* recently viewed non-sensitive data where appropriate

Do not claim that media is playable offline merely because metadata is cached.

Offline authorization must never be inferred from stale subscription data.

---

# OFFLINE PLAYBACK

Where offline playback is part of the implemented product scope, build it as a secure entitlement-driven subsystem.

Support:

* download authorization
* encrypted/local protected media storage
* download manifests
* device binding
* expiration
* entitlement renewal
* revocation
* download progress
* interrupted downloads
* storage management
* playback validation
* post-offline telemetry synchronization

Downloaded media must not become unrestricted files accessible to other applications.

Never store premium media as ordinary publicly readable files.

---

# DOWNLOAD MANAGEMENT

If offline playback is enabled, provide a download manager supporting:

* queued downloads
* active download
* paused
* completed
* failed
* canceled
* expired
* removed

Support:

* retry
* progress
* storage accounting
* Wi-Fi preferences where supported
* user cancellation
* cleanup

Avoid downloading entire large files into JavaScript memory.

Use native/streaming filesystem mechanisms appropriate to the platform.

---

# OFFLINE ENTITLEMENT

Offline playback must verify entitlement using a secure mechanism.

Support:

* authorization issuance
* expiration
* renewal
* device binding
* revocation

Do not rely exclusively on a timestamp stored locally without cryptographic/server-authoritative validation.

When offline entitlement expires, block protected playback until authorization is renewed where product policy requires it.

---

# OFFLINE DATA SECURITY

Protect local sensitive data.

Do not store in ordinary unencrypted storage:

* access tokens
* refresh tokens
* subscription credentials
* private user data unnecessary for offline use

Encrypt or protect sensitive offline media and metadata appropriately.

Clear protected data when:

* account is removed
* device authorization is revoked
* user logs out where required
* downloaded media expires

---

# STORAGE MANAGEMENT

Implement user-visible storage information where downloads exist.

Show:

* downloaded size
* available storage
* per-playlist/album usage
* failed downloads
* expired downloads

Do not continuously poll filesystem statistics.

Perform expensive storage operations asynchronously.

---

# NETWORK-AWARE DOWNLOADS

Respect:

* connectivity
* metered networks
* user preferences
* battery state where platform APIs support it

Support configuration such as:

* Wi-Fi only
* cellular allowed
* automatic download disabled

Do not silently consume large amounts of mobile data.

---

# SUBSCRIPTION MOBILE EXPERIENCE

Implement mobile subscription workflows compatible with the backend.

Support:

* current plan
* entitlement
* billing state
* renewal
* cancellation state
* upgrade/downgrade where supported
* plan availability

When app-store billing is used for a platform-specific product, use the repository's selected compliant billing architecture.

Keep entitlement decisions server-authoritative.

Do not assume a successful client-side purchase equals a durable subscription until backend verification completes.

---

# MOBILE PAYMENT SECURITY

Never store or transmit raw payment credentials through application logic unless the selected compliant payment architecture explicitly requires it.

Where platform billing is required:

* validate receipts/purchase tokens server-side
* handle duplicate purchase events
* handle refunds
* handle cancellations
* handle restored purchases

Do not grant permanent entitlement solely on local purchase state.

---

# ARTIST MOBILE FEATURES

Where artist mobile access is part of the product scope, support appropriate functionality such as:

* artist dashboard
* release status
* track processing status
* content overview
* basic analytics
* notifications
* upload-status monitoring
* moderation status

Do not attempt to duplicate every desktop administration workflow on mobile.

Prioritize operationally useful workflows.

---

# ARTIST UPLOAD MONITORING

Where uploads are initiated or monitored from mobile:

* show upload state
* show progress
* show processing state
* show validation errors
* show retry options
* allow cancellation where safe

Do not keep large file contents in React state.

Use native streaming/upload mechanisms where appropriate.

---

# PRIVACY

Implement mobile privacy controls for:

* profile
* listening activity
* social visibility
* recommendations
* notifications
* marketing
* data deletion

Clear private cached data when privacy state changes require it.

Do not expose sensitive history through offline caches after account logout or switching.

---

# SECURITY HARDENING

Protect against:

* insecure local storage
* token leakage
* deep-link abuse
* notification-data leakage
* unauthorized screen access
* insecure file handling
* certificate/network attacks where applicable
* reverse-engineering exposure of secrets
* debug logging in production

Do not include:

* private signing keys
* backend secrets
* provider secret keys
* privileged API credentials

inside the mobile bundle.

---

# NETWORK SECURITY

Use secure transport.

Where certificate pinning or additional transport protection is appropriate and compatible with the deployment model, evaluate and implement it carefully.

Do not introduce brittle security mechanisms that prevent legitimate certificate rotation without an operational strategy.

Never disable TLS verification in production.

---

# APP STATE AND LIFECYCLE

Handle:

* active
* inactive
* background
* suspended
* terminated
* restarted

Persist only state that is safe and necessary.

On resume:

* validate authentication state
* reconcile critical server state
* refresh expiring authorization
* restore player state
* reconnect real-time systems
* process pending telemetry

Do not blindly replay every pending operation.

---

# BACKGROUND WORK

Use platform-supported background execution selectively.

Potential workloads include:

* playback telemetry
* download management
* notification processing
* token refresh where permitted
* synchronization

Respect iOS and Android background execution limits.

Do not design critical workflows around indefinite background execution.

---

# BATTERY OPTIMIZATION

Minimize:

* wakeups
* polling
* high-frequency network requests
* background JavaScript execution
* unnecessary location/device polling
* redundant analytics

Playback and downloads must use native/platform-efficient capabilities where possible.

---

# MEMORY OPTIMIZATION

Monitor:

* audio buffers
* image caches
* download queues
* lists
* large metadata responses
* navigation stacks
* WebSocket connections

Prevent:

* unbounded queue growth
* duplicate audio resources
* leaked listeners
* unreleased file handles
* unreleased object/native resources

---

# IMAGE AND MEDIA PERFORMANCE

Use appropriately sized artwork.

Avoid loading full-resolution source artwork when variants exist.

Manage image cache behavior to prevent excessive memory usage.

For media:

* stream where appropriate
* download only when authorized
* release resources after use
* avoid duplicate concurrent downloads

---

# MOBILE ANALYTICS

Implement privacy-aware analytics for:

* playback
* search
* discovery
* recommendations
* notifications
* subscriptions
* downloads
* offline playback
* errors
* app lifecycle

Analytics must distinguish:

* online
* offline
* synchronized-later

Do not queue unlimited analytics events locally.

---

# ERROR AND CRASH OBSERVABILITY

Implement production crash/error reporting for:

* startup
* navigation
* playback
* downloads
* authentication
* notifications
* deep links
* networking

Capture enough context to diagnose failures while avoiding sensitive-data leakage.

Include:

* app version
* platform
* OS version
* safe feature context
* correlation identifiers where appropriate

---

# TESTING

Implement comprehensive tests for:

## Playback

* background playback
* interruption
* audio focus loss
* headset disconnect
* Bluetooth changes
* expiration
* retry
* recovery
* completion
* progress synchronization

## Offline

* download authorization
* download success/failure
* interrupted download
* expiration
* revocation
* storage cleanup
* offline playback validation

## Notifications

* permission
* registration
* token refresh
* foreground message
* background message
* deep-link routing

## Deep Links

* valid links
* invalid links
* private resources
* deleted resources
* authorization failures

## Multi-device

* device registration
* revocation
* session synchronization
* conflicting playback state

## Subscriptions

* purchase initiation
* server verification
* restoration
* cancellation
* refund
* entitlement expiration

## Security

* secure logout
* account switching
* token clearing
* private-data clearing
* unauthorized navigation

Use:

* unit tests
* component tests
* integration tests
* device/emulator E2E tests

---

# PLATFORM-SPECIFIC TESTING

Validate on:

## iOS

* background audio
* lock screen controls
* audio interruptions
* route changes
* push notification permissions
* deep links
* secure storage
* dynamic type
* app lifecycle

## Android

* audio focus
* background playback
* media notification
* Bluetooth
* push notification permissions
* deep links
* secure storage
* back navigation
* lifecycle

Document platform-specific deviations.

Do not force identical implementation details where operating-system behavior differs.

---

# PERFORMANCE VALIDATION

Measure:

* cold startup
* warm startup
* navigation latency
* playback startup
* time to first audio
* memory usage
* battery impact where measurable
* download throughput
* scroll performance
* notification handling

Identify regressions.

Do not claim performance improvements without measurements.

---

# RELEASE CONFIGURATION

Harden mobile release configuration.

Support:

* development
* test
* staging
* production

Configure:

* bundle identifiers/package names
* environment values
* permissions
* app icons
* splash behavior
* deep-link schemes
* push-notification configuration
* background modes
* platform capabilities
* release logging behavior

Do not commit production secrets.

---

# BUILD AND CI VALIDATION

Ensure mobile builds are reproducible through the repository's selected CI/CD approach.

Validate:

* TypeScript
* linting
* tests
* production build
* native configuration
* platform-specific configuration

Do not disable checks merely to make a build pass.

---

# DOCUMENTATION

Update documentation for:

* advanced player
* background audio
* iOS audio session
* Android audio focus
* push notifications
* deep links
* offline architecture
* downloads
* storage handling
* multi-device synchronization
* mobile subscriptions
* release configuration
* platform-specific behavior
* testing
* debugging
* troubleshooting

Documentation must reflect the actual implementation.

---

# IMPLEMENTATION BOUNDARIES

This mobile volume owns advanced mobile capabilities.

Implement:

* advanced playback
* background playback
* system controls
* audio interruptions
* device synchronization
* real-time behavior
* collaborative playlist UX
* push notifications
* deep links
* offline/degraded behavior
* secure offline playback where supported
* mobile subscription flows
* artist operational features where appropriate
* privacy/security hardening
* performance/battery optimization
* release hardening
* advanced mobile testing

Do not implement:

* backend business logic
* database migrations
* web UI
* Kubernetes/Terraform infrastructure
* server-side media processing

Use existing backend contracts.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before making changes:

1. inspect the mobile repository
2. inspect current audio implementation
3. inspect navigation
4. inspect secure storage
5. inspect push notifications
6. inspect deep links
7. inspect filesystem/download support
8. inspect backend API contracts
9. inspect subscription implementation
10. inspect tests
11. inspect native configuration
12. identify compatibility constraints

Then:

1. harden the player
2. implement background/audio-session behavior
3. implement system controls
4. implement real-time synchronization
5. implement collaborative functionality
6. implement push notifications and deep links
7. implement offline/degraded behavior
8. implement download/offline playback where supported
9. implement subscription flows
10. implement security/privacy hardening
11. optimize performance and battery behavior
12. add platform-specific tests
13. validate production builds
14. update documentation

Do not rewrite unrelated mobile code.

---

# COMPLETION CRITERIA

This mobile task is complete only when:

* background playback works according to platform rules
* system controls work
* interruptions are handled correctly
* Bluetooth/headset transitions are handled
* playback recovery is bounded and reliable
* progress synchronization is resilient
* multi-device behavior is implemented where supported
* collaborative playlist updates reconcile correctly
* push notifications work
* notification routing works
* deep links work safely
* offline/degraded behavior is implemented
* secure offline playback is implemented where included
* local protected data is handled securely
* subscription flows are verified server-side
* privacy controls work
* security hardening is complete
* performance has been measured
* battery-sensitive behavior has been addressed
* iOS-specific behavior has been validated
* Android-specific behavior has been validated
* automated tests cover advanced functionality
* production builds succeed
* no required mobile functionality is intentionally incomplete

Do not declare completion when required build, test, device/emulator, or runtime validation fails.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* player architecture changes
* background playback changes
* iOS audio-session changes
* Android audio-focus changes
* system media-control changes
* multi-device changes
* real-time synchronization changes
* collaboration changes
* push notification changes
* deep-link changes
* offline/download changes
* subscription changes
* artist-mobile changes
* security/privacy changes
* performance/battery changes
* native configuration changes
* tests added or updated
* iOS validation performed
* Android validation performed
* production build validation
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified results from assumptions.

Do not claim device validation, offline playback, background playback, or production builds were successful unless they were actually executed and verified.

---

# FINAL INSTRUCTION

Implement the advanced production mobile capabilities required for a serious music-streaming platform.

Treat playback as a long-lived native/mobile subsystem.

Treat background execution and audio focus as platform-specific production concerns.

Treat offline media as protected content rather than ordinary files.

Treat device synchronization and real-time updates as eventually consistent distributed state.

Treat push notifications and deep links as untrusted entry points into the application.

Treat subscription purchases as provisional until server verification establishes authoritative entitlement.

Minimize battery, memory, network, and storage consumption.

Protect credentials and private data throughout the complete application lifecycle.

Build real background playback, real system controls, real notification handling, real offline management, real security, real platform configuration, real tests, and real validation.

The resulting mobile application must provide a production-grade iOS and Android experience that integrates cleanly with the existing backend and remains maintainable as playback concurrency, content volume, device count, and product capabilities grow.
