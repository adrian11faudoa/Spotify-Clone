You are operating in Senior Engineering Team Mode.

Complete the remaining production-ready web frontend for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The frontend must consume the established backend API contracts, authentication model, authorization model, catalog architecture, media architecture, playback architecture, playlist architecture, library architecture, search architecture, recommendation architecture, subscription architecture, podcast architecture, notification architecture, advertising architecture, analytics architecture, administration architecture, and security model.

Do not redesign backend APIs.

Do not redesign the database.

Do not implement backend code.

Do not implement mobile code.

Do not implement infrastructure implementation code.

Do not generate Terraform.

Do not generate Kubernetes manifests.

Do not generate CI/CD workflows.

────────────────────────────────────────

MISSION

Complete the advanced production-ready web applications for:

• Advanced search
• Discovery
• Recommendations
• Personalized home
• Radio
• Charts
• Playlists
• Collaborative playlists
• Library
• Listening history
• Recently played
• Advanced playback
• Device switching
• Playback synchronization
• Podcasts
• Podcast creators
• Subscriptions
• Billing
• Account security
• Notifications
• Advertising-supported experiences
• Analytics dashboards
• Artist/creator portal
• Label/partner portal
• Administration
• Moderation
• CMS/editorial content
• Feature flags
• System configuration
• Audit
• Reports

The frontend must remain consistent with the established backend contracts and domain boundaries.

────────────────────────────────────────

TECHNOLOGY STACK

Framework:

• Next.js
• React
• TypeScript

Styling:

• Tailwind CSS
• shadcn/ui
• CSS variables

Server State:

• TanStack Query

Client State:

• Zustand

Forms:

• React Hook Form
• Zod

Charts:

• Recharts

Animation:

• Framer Motion

Icons:

• Lucide React

Testing:

• Jest
• React Testing Library
• Playwright
• Accessibility testing tooling

────────────────────────────────────────

ADVANCED PLAYBACK EXPERIENCE

Complete the production web playback experience.

Support:

• Persistent player
• Mini player
• Expanded player
• Play
• Pause
• Previous
• Next
• Seek
• Volume
• Mute
• Shuffle
• Repeat
• Queue
• Playback progress
• Track artwork
• Current track metadata
• Playback quality
• Device selection
• Transfer playback
• Remote controls where supported

Separate:

• Audio engine state
• UI state
• Server playback session
• Persistent progress

────────────────────────────────────────

PLAYBACK STATES

Handle:

• Loading
• Buffering
• Playing
• Paused
• Seeking
• Ended
• Authorization failure
• Rights failure
• Content unavailable
• Network failure
• CDN failure
• Device failure

Provide clear recovery actions.

Never expose internal authorization details or provider secrets.

────────────────────────────────────────

PLAYBACK QUALITY

Support the backend-defined playback-quality options.

Display appropriate options based on:

• Subscription entitlement
• Device capability
• Content availability

Do not display unavailable quality levels as selectable.

────────────────────────────────────────

DEVICE SWITCHING

Implement:

• Device list
• Current device
• Device status
• Transfer playback
• Stop playback
• Resume on another device

Handle:

• Device unavailable
• Device disconnected
• Authorization expiration
• Reconnection

────────────────────────────────────────

QUEUE EXPERIENCE

Complete:

• Queue drawer
• Current track
• Upcoming tracks
• Add to queue
• Remove from queue
• Reorder
• Clear
• Shuffle
• Repeat

Handle backend queue-version conflicts.

Do not silently overwrite newer queue state.

────────────────────────────────────────

ADVANCED SEARCH

Complete the search experience.

Support:

• Search suggestions
• Autocomplete
• Recent searches
• Trending searches
• Search history
• Tracks
• Artists
• Albums
• Playlists
• Podcasts
• Episodes
• Genres
• Filters
• Ranking
• Pagination
• Infinite scrolling

Show useful content-specific sections such as:

• Top result
• Tracks
• Artists
• Albums
• Playlists
• Podcasts

────────────────────────────────────────

SEARCH UX

Support:

• Debounced queries
• Cancelable requests
• URL state
• Search persistence
• Keyboard navigation
• No-results suggestions
• Related queries
• Error recovery

Avoid unnecessary duplicate requests.

────────────────────────────────────────

DISCOVERY EXPERIENCE

Complete:

• Personalized home
• New releases
• Trending
• Popular
• Recommended playlists
• Recommended tracks
• Recommended artists
• Genre discovery
• Editorial collections
• Recently played

Support configurable feed sections.

Recommendation failures must gracefully fall back to non-personalized content.

────────────────────────────────────────

RECOMMENDATIONS

Implement interfaces for:

• Similar tracks
• Similar artists
• Personalized mixes
• Recommended playlists
• New releases
• Related content
• Frequently relevant content

Support:

• Loading
• Empty
• Error
• Fallback

Do not make recommendation requests block the player.

────────────────────────────────────────

RADIO

Complete:

• Track radio
• Artist radio
• Genre radio
• Personalized stations

Support continuous loading.

Display:

• Current station
• Seed
• Queue
• Next items

Recover from radio-generation failures without breaking playback.

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
• Rank
• Track playback
• Artist navigation

Use server-side pagination for large chart datasets.

────────────────────────────────────────

PLAYLISTS

Complete:

• Playlist creation
• Editing
• Deletion
• Rename
• Description
• Artwork
• Visibility
• Add track
• Remove track
• Reorder
• Save
• Follow

Support collaborative playlists.

────────────────────────────────────────

COLLABORATIVE PLAYLIST UX

Support:

• Collaborator list
• Invite
• Accept
• Remove collaborator
• Leave
• Permissions
• Shared editing
• Version conflicts

When a conflict occurs:

• Inform the user
• Preserve their local work where possible
• Refresh server state
• Allow retry

Do not silently discard edits.

────────────────────────────────────────

LIBRARY

Complete:

• Liked songs
• Saved albums
• Saved playlists
• Followed artists
• Followed podcasts
• Recently played
• Listening history

Support:

• Search
• Filter
• Sort
• Infinite scrolling
• Empty states

────────────────────────────────────────

LISTENING HISTORY

Implement:

• Recently played
• History
• Clear history where backend supports it
• Date grouping
• Search/filter where appropriate

Respect profile privacy.

────────────────────────────────────────

OFFLINE-AWARE WEB EXPERIENCE

Where supported by the approved web architecture, implement safe caching for:

• Library
• Recent content
• Catalog pages
• Playlist metadata

Do not claim full offline audio streaming unless the backend/browser architecture explicitly supports it.

Never persist sensitive secrets in ordinary browser storage.

────────────────────────────────────────

PODCAST EXPERIENCE

Complete:

• Podcast home/discovery
• Show page
• Episode page
• Episode list
• Follow
• Resume playback
• Progress
• Search
• Recommendations
• Release notifications

Reuse the existing audio-player architecture.

────────────────────────────────────────

PODCAST CREATOR PORTAL

Implement creator-facing web interfaces for:

• Dashboard
• Shows
• Episodes
• Drafts
• Uploads
• Metadata
• Publishing
• Scheduling
• Analytics
• Team members
• Settings

Support states:

• Draft
• Processing
• Review
• Approved
• Scheduled
• Published
• Unpublished

Creator data must be properly isolated.

────────────────────────────────────────

ARTIST PORTAL

Implement:

• Artist dashboard
• Profile
• Releases
• Tracks
• Uploads
• Publishing status
• Rights information where authorized
• Analytics
• Audience insights
• Team members
• Settings

Support:

• Draft
• Processing
• Submitted
• Approved
• Scheduled
• Published
• Suspended

────────────────────────────────────────

LABEL/PARTNER PORTAL

Where supported, implement:

• Organization dashboard
• Releases
• Content
• Artists
• Submission status
• Rights
• Analytics
• Team management

Do not expose unrelated organizations' data.

────────────────────────────────────────

SUBSCRIPTIONS

Complete:

• Plan comparison
• Current plan
• Trial
• Upgrade
• Downgrade
• Cancellation
• Renewal state
• Grace period
• Payment failure
• Entitlement state

Clearly explain backend-provided state.

Do not independently calculate entitlement.

────────────────────────────────────────

BILLING

Support:

• Payment methods
• Billing history
• Invoices
• Payment status
• Refund status

Use approved payment-provider components where card entry is required.

Never store raw payment credentials.

────────────────────────────────────────

FAMILY PLAN

Where supported, implement:

• Family manager controls
• Member management
• Profile management
• Content restrictions
• Subscription overview

Respect backend authorization and profile boundaries.

────────────────────────────────────────

STUDENT PLAN

Implement:

• Student eligibility flow
• Verification status
• Plan status
• Re-verification where required

Keep provider-specific verification logic behind backend APIs.

────────────────────────────────────────

NOTIFICATIONS

Complete:

• Notification center
• Unread counts
• Read/unread
• Notification preferences
• Deep links
• Push-related UI state

Support:

• New releases
• Podcasts
• Playlists
• Subscription
• Payment
• Security
• Recommendations
• System announcements

────────────────────────────────────────

ADVERTISING UI

For free/ad-supported experiences, build the frontend architecture for:

• Audio ad state
• Ad indicator
• Companion content where appropriate
• Ad loading
• Ad failure
• Frequency-cap messaging where applicable

Do not expose internal ad-targeting information.

Advertising failures must not crash the player.

────────────────────────────────────────

CREATOR ANALYTICS

Implement dashboards for:

• Streams
• Unique listeners
• Listening hours
• Completion
• Skips
• Saves
• Follows
• Release performance
• Geographic summaries where authorized
• Playlist exposure

Support:

• Date ranges
• Comparisons
• Charts
• Tables
• Loading
• Empty
• Error

────────────────────────────────────────

ADMINISTRATION

Complete the administration application.

Support:

• Users
• Profiles
• Subscriptions
• Payments
• Content
• Artists
• Labels
• Podcasts
• Advertising
• Moderation
• Reports
• Analytics
• Feature flags
• System configuration
• Audit

Use permission-aware navigation.

────────────────────────────────────────

ADMIN USER MANAGEMENT

Support:

• Search
• User detail
• Profile detail
• Subscription overview
• Device/session overview where authorized
• Security events
• Account status
• Suspension/reactivation

Sensitive information must be role-restricted.

────────────────────────────────────────

ADMIN CONTENT MANAGEMENT

Support:

• Artists
• Albums
• Releases
• Tracks
• Podcasts
• Episodes
• Rights
• Availability
• Publication state
• Moderation

High-risk actions require confirmation and reason capture.

────────────────────────────────────────

MODERATION UI

Implement:

• Report queue
• Moderation queue
• Case detail
• Evidence
• Policy
• Action
• Appeal
• Resolution
• Audit trail

Only show information authorized by backend permissions.

────────────────────────────────────────

ADVERTISING ADMIN

Support:

• Advertisers
• Campaigns
• Ad groups
• Creatives
• Targeting
• Scheduling
• Approval
• Activation
• Pause
• Reporting

Mask sensitive targeting information where appropriate.

────────────────────────────────────────

FEATURE FLAGS

Implement:

• Feature list
• Creation
• Editing
• Rollout
• Percentage rollout
• Region targeting
• User targeting
• Plan targeting
• Device targeting
• Kill switch
• Rollback
• History

Backend remains the final authority.

────────────────────────────────────────

SYSTEM CONFIGURATION

Implement:

• Configuration list
• Search
• Edit
• Validation
• Version history
• Approval
• Activation
• Rollback

Never expose secrets.

Mask sensitive configuration values.

────────────────────────────────────────

AUDIT

Implement:

• Audit search
• Filters
• Actor
• Action
• Resource
• Time
• Result
• Detail

Use server-side pagination.

Do not allow ordinary administrators to modify audit logs.

────────────────────────────────────────

REPORTING

Implement:

• Report creation
• Report type
• Parameters
• Status
• Progress
• Download
• Expiration

Use secure report-download flows.

────────────────────────────────────────

ACCOUNT SECURITY

Complete:

• Password change
• Sessions
• Devices
• MFA
• Passkeys where supported
• Security notifications
• Login activity
• Account recovery

Sensitive operations should require appropriate re-authentication.

────────────────────────────────────────

PRIVACY

Implement UI for:

• Privacy settings
• Listening-data preferences
• Recommendation preferences
• Advertising preferences
• Data export
• Account deletion
• Profile visibility
• Security settings

Display backend-authoritative status.

────────────────────────────────────────

ACCESSIBILITY

Complete WCAG 2.2 AA.

Validate:

• Keyboard navigation
• Player controls
• Search
• Playlists
• Forms
• Dialogs
• Tables
• Charts
• Notifications
• Admin workflows

Provide accessible alternatives for charts and visualizations.

────────────────────────────────────────

INTERNATIONALIZATION

Complete:

• Multiple languages
• Locale selection
• Currency formatting
• Date/time
• Number formatting
• RTL
• Localized validation
• Localized notifications

Do not hard-code user-visible strings inside feature logic.

────────────────────────────────────────

SEO

Optimize public:

• Artist pages
• Album pages
• Track pages
• Public playlists
• Podcast pages
• Creator pages where appropriate

Support:

• Metadata
• Canonical URLs
• Open Graph
• Structured data
• Sitemaps
• Robots

Private pages must not be indexed.

────────────────────────────────────────

PERFORMANCE

Optimize:

• Home
• Search
• Artist pages
• Album pages
• Playlists
• Library
• Creator dashboards
• Admin dashboards
• Charts
• Analytics

Use:

• Server Components
• Streaming
• Suspense
• Code splitting
• Dynamic imports
• Virtualization
• Query caching
• Prefetching
• Image optimization

────────────────────────────────────────

SECURITY

Implement frontend protections for:

• Protected routes
• Permission-aware navigation
• Safe rendering
• Safe URLs
• Secure playback credential handling
• Sensitive-field masking
• Safe report downloads
• Secure media flows

Never expose:

• Secrets
• Provider credentials
• Payment credentials
• Password hashes
• Long-lived playback tokens

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Player state
• Queue state
• Search state
• Form validation
• Permission-aware UI
• Formatting
• Utilities

COMPONENT TESTS

Test:

• Player
• Search
• Artist
• Album
• Playlist
• Library
• Subscription
• Podcast
• Creator
• Admin
• Notifications

INTEGRATION TESTS

Test:

• API client
• Authentication
• Playback
• Search
• Playlist collaboration
• Subscription state
• Notifications
• Admin workflows

END-TO-END TESTS

CUSTOMER:

• Registration
• Search
• Playback
• Playlist
• Library
• Subscription
• Podcast
• Notifications

CREATOR:

• Login
• Upload/content workflow
• Release management
• Analytics

ADMIN:

• Login
• User management
• Content moderation
• Advertising
• Feature flags
• Configuration
• Audit

ACCESSIBILITY TESTS

• Navigation
• Player
• Search
• Forms
• Charts
• Tables
• Admin workflows

PERFORMANCE TESTS

• Home
• Search
• Large playlists
• Large library
• Creator analytics
• Admin tables

────────────────────────────────────────

DOCUMENTATION

Generate:

• Advanced frontend architecture
• Player UX
• Queue UX
• Search UX
• Discovery UX
• Playlist UX
• Library UX
• Podcast UX
• Subscription UX
• Creator portal
• Label/partner portal
• Administration
• Moderation
• Advertising UI
• Analytics
• Accessibility
• Localization
• SEO
• Performance
• Security
• Testing

────────────────────────────────────────

PROJECT INDEX

Update the frontend Project Index with:

• Customer pages
• Player
• Queue
• Search
• Discovery
• Recommendations
• Radio
• Charts
• Playlists
• Library
• Podcasts
• Subscriptions
• Notifications
• Creator portal
• Artist portal
• Label portal
• Admin application
• Moderation
• Advertising
• Analytics
• Feature flags
• Configuration
• Audit
• Components
• Hooks
• Stores
• Queries
• API integrations
• Tests
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

FRONTEND MILESTONE 11

Advanced player, queue, device switching, synchronized playback, and playback recovery.

FRONTEND MILESTONE 12

Advanced search, discovery, recommendations, radio, charts, and trending experiences.

FRONTEND MILESTONE 13

Advanced playlists, collaboration, library, listening history, and synchronization.

FRONTEND MILESTONE 14

Podcasts, creators, episodes, follow workflows, and podcast analytics.

FRONTEND MILESTONE 15

Subscriptions, billing, family plans, student plans, account security, and privacy.

FRONTEND MILESTONE 16

Artist/creator portal, label/partner portal, releases, content workflows, and analytics.

FRONTEND MILESTONE 17

Notifications, advertising-supported experiences, and customer communications.

FRONTEND MILESTONE 18

Administration, user management, content management, moderation, reports, and audit.

FRONTEND MILESTONE 19

Feature flags, system configuration, operational dashboards, accessibility, localization, and SEO.

FRONTEND MILESTONE 20

Performance optimization, security hardening, full E2E testing, accessibility validation, and production readiness.

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

This volume completes the advanced web frontend.

Do not implement:

• Backend code
• Mobile code
• Kubernetes
• Terraform
• CI/CD infrastructure

Consume the established backend contracts exactly.

Do not redesign APIs or database structures.

────────────────────────────────────────

QUALITY BAR

Treat the web platform as a global music-streaming application serving hundreds of millions of users.

Assume:

• Massive playback traffic
• Millions of tracks
• Large playlists
• High search traffic
• Large recommendation traffic
• Multiple devices
• Multiple subscription tiers
• Podcasts
• Advertising
• Creator ecosystems
• Large analytics datasets
• Multiple languages
• Global users
• Strict accessibility requirements
• Strict security requirements

Prioritize:

• Playback reliability
• UX quality
• Performance
• Accessibility
• Security
• Correct state synchronization
• Privacy
• Maintainability
• Scalability
• Production readiness
