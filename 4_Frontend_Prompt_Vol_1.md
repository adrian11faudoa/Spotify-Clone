You are operating in Senior Engineering Team Mode.

Build the production-ready web frontend foundation for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The frontend must consume the established backend API contracts, authentication model, authorization model, catalog architecture, playback architecture, subscription architecture, playlist architecture, library architecture, search architecture, recommendation architecture, notification architecture, advertising architecture, analytics architecture, and security model.

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

Build the production-ready customer web application foundation for:

• Home
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
• Player
• Queue
• Playback controls
• Recommendations
• Radio
• Charts
• Subscriptions
• Account
• Settings
• Notifications
• Messaging/communications where supported

The frontend must be:

• Fast
• Responsive
• Accessible
• Secure
• Maintainable
• SEO-friendly
• Performant
• Observable
• Production-ready

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

Animation:

• Framer Motion

Icons:

• Lucide React

Charts:

• Recharts

Testing:

• Jest
• React Testing Library
• Playwright
• Accessibility testing tooling

────────────────────────────────────────

FRONTEND ARCHITECTURE

Use:

• Next.js App Router
• Feature-first organization
• Strict TypeScript
• Reusable components
• Shared design system
• Separation of server state and client state
• Typed API contracts
• Clean presentation boundaries
• Server Components where appropriate
• Client Components only where interaction requires them

Do not make the entire application a Client Component.

Do not place backend business logic inside UI components.

Do not use Zustand as a replacement for TanStack Query.

────────────────────────────────────────

APPLICATION STRUCTURE

Create a scalable structure containing:

app/

features/

components/

layouts/

hooks/

providers/

services/

stores/

lib/

config/

types/

utils/

styles/

public/

assets/

tests/

Keep feature modules isolated.

Keep shared components domain-neutral.

────────────────────────────────────────

NEXT.JS FOUNDATION

Implement:

• App Router
• Route groups
• Layouts
• Loading states
• Error boundaries
• Not-found pages
• Suspense
• Metadata
• Open Graph
• Structured metadata foundations
• Middleware
• Authentication-aware routing

Support:

• Public routes
• Authenticated routes
• Profile-aware routes
• Account routes

────────────────────────────────────────

DESIGN SYSTEM

Build reusable components using shadcn/ui and Tailwind.

Include:

• Button
• Input
• Textarea
• Select
• Checkbox
• Radio
• Switch
• Dialog
• Drawer
• Popover
• Dropdown
• Tooltip
• Tabs
• Accordion
• Card
• Badge
• Avatar
• Breadcrumb
• Table
• Pagination
• Skeleton
• Alert
• Toast
• Progress
• Slider
• Command
• Separator
• Scroll area
• Empty state
• Error state
• Loading state
• Music player controls

Components must support:

• Keyboard navigation
• Focus management
• Responsive layouts
• Dark mode
• Accessibility

────────────────────────────────────────

THEMING

Support:

• Light mode
• Dark mode
• System mode
• Persistent theme preference

Respect:

• Reduced motion
• High contrast
• Accessibility preferences

Use centralized design tokens.

────────────────────────────────────────

API CLIENT

Implement a typed API client.

Support:

• Base URL
• Authentication
• Request IDs
• Correlation IDs
• Error normalization
• Timeout
• Cancellation
• Retry
• Pagination
• Cursor pagination
• Upload workflows
• Playback authorization requests

Do not implement business logic inside the client.

Use the established backend contracts.

────────────────────────────────────────

SERVER STATE

Use TanStack Query for:

• Catalog
• Search
• Artists
• Albums
• Tracks
• Playlists
• Library
• Recommendations
• Radio
• Charts
• Podcasts
• Subscription
• Account
• Notifications

Implement:

• Query keys
• Mutations
• Infinite queries
• Caching
• Background refetching
• Optimistic updates
• Invalidation
• Retry
• Error handling

────────────────────────────────────────

CLIENT STATE

Use Zustand for client-owned state such as:

• Player UI state
• Current device
• Queue UI state
• Volume
• Repeat
• Shuffle
• Theme
• Search UI state
• Sidebar state
• Notification UI
• Modal state

The backend remains authoritative for persistent playback state.

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
• Protected routing

Support:

• OAuth foundations
• MFA foundations
• Passkey-ready architecture

Never expose secrets unnecessarily to browser JavaScript.

────────────────────────────────────────

GLOBAL APPLICATION LAYOUT

Create the core layout with:

• Sidebar/navigation
• Main content area
• Persistent player
• Queue panel
• Search
• User/profile controls
• Notifications
• Responsive navigation

Desktop layouts should support persistent playback.

Mobile web layouts must remain usable.

────────────────────────────────────────

HOME

Implement:

• Personalized home
• Recently played
• Recently added
• Recommended playlists
• Recommended tracks
• Recommended artists
• New releases
• Trending
• Editorial collections
• Genre discovery
• Podcast recommendations

Support:

• Loading
• Skeleton
• Empty
• Error
• Retry

Recommendation failures must not break the home page.

────────────────────────────────────────

SEARCH

Implement:

• Search input
• Autocomplete
• Suggestions
• Recent searches
• Search results
• Tracks
• Artists
• Albums
• Playlists
• Podcasts
• Episodes
• Genres

Support:

• Typo-tolerant results
• Filters
• Sorting
• Infinite results
• Empty states
• No-results recovery
• Error states

Synchronize search state with URL parameters where appropriate.

────────────────────────────────────────

SEARCH PERFORMANCE

Optimize:

• Debouncing
• Request cancellation
• Query caching
• Prefetching
• Virtualized lists where useful
• Image loading
• Result rendering

Do not issue duplicate requests unnecessarily.

────────────────────────────────────────

ARTIST PAGES

Implement:

• Artist header
• Artist artwork
• Popular tracks
• Albums
• Singles
• EPs
• Releases
• Follow state
• Related artists
• Recommendations
• Artist radio
• About section where available

Support localized content.

────────────────────────────────────────

ALBUM PAGES

Implement:

• Album artwork
• Album title
• Artist
• Release date
• Track list
• Duration
• Explicit markers
• Save album
• Play album
• Shuffle
• Recommendations
• Related releases

Support:

• Loading
• Error
• Unavailable tracks

────────────────────────────────────────

TRACK EXPERIENCE

Implement:

• Track title
• Artist
• Album
• Explicit status
• Like button
• Add to playlist
• Share
• More actions
• Playback
• Queue actions

Support unavailable-content states.

────────────────────────────────────────

PLAYLIST PAGES

Implement:

• Playlist header
• Artwork
• Title
• Description
• Owner
• Followers
• Visibility
• Track list
• Play
• Shuffle
• Save
• Follow
• Add/remove where authorized
• Reorder where authorized

Support collaborative playlist indicators.

────────────────────────────────────────

PLAYLIST EDITING

Support authorized users with:

• Rename
• Description
• Artwork
• Add tracks
• Remove tracks
• Reorder
• Collaborator management
• Visibility
• Delete

Use optimistic concurrency and backend version handling.

Display clear conflict states when edits collide.

────────────────────────────────────────

LIBRARY

Implement library views for:

• Liked songs
• Albums
• Playlists
• Artists
• Podcasts
• Recently played

Support:

• Filtering
• Sorting
• Search
• Infinite loading
• Empty states

Keep library state synchronized with backend state.

────────────────────────────────────────

LIKED SONGS

Implement:

• Like/unlike
• List
• Play all
• Shuffle
• Search
• Sort
• Bulk operations where backend supports them

Use optimistic UI only where rollback is reliable.

────────────────────────────────────────

PERSISTENT PLAYER

Build the core web player.

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
• Queue
• Progress
• Track information
• Artwork
• Playback quality selection where supported

Separate:

• UI state
• Audio engine state
• Backend playback session
• Persistent progress

────────────────────────────────────────

PLAYER ERROR HANDLING

Handle:

• Playback authorization failure
• Expired playback credentials
• Content unavailable
• Rights restriction
• Network interruption
• CDN failure
• Unsupported format
• Track unavailable

Provide recovery without crashing the application.

────────────────────────────────────────

QUEUE

Implement:

• Queue display
• Current track
• Upcoming tracks
• Add
• Remove
• Reorder
• Clear
• Repeat
• Shuffle

Synchronize with backend queue state where supported.

Handle queue-version conflicts gracefully.

────────────────────────────────────────

DEVICE PLAYBACK

Display available playback devices where supported.

Support:

• Current device
• Device selection
• Transfer playback
• Stop playback
• Device status

Require backend authorization for device operations.

────────────────────────────────────────

RADIO

Implement:

• Track radio
• Artist radio
• Genre radio
• Personalized station

Support continuous loading.

Handle recommendation/radio failures gracefully.

────────────────────────────────────────

CHARTS

Implement:

• Global charts
• Regional charts
• Genre charts
• Trending
• Historical chart periods

Support:

• Tabs
• Ranking
• Track cards
• Artist navigation
• Playback

────────────────────────────────────────

PODCASTS

Implement:

• Show page
• Episode list
• Episode detail
• Follow
• Play
• Resume
• Search
• Recommendations
• Progress

Reuse common audio-player architecture.

────────────────────────────────────────

SUBSCRIPTIONS

Implement:

• Current plan
• Available plans
• Upgrade
• Downgrade
• Trial
• Cancellation
• Renewal status
• Payment status
• Entitlements

Display clear subscription state.

Do not calculate billing state independently from backend state.

────────────────────────────────────────

ACCOUNT

Implement:

• Profile
• Password/security
• Sessions
• Devices
• Subscription
• Billing
• Notification preferences
• Privacy
• Explicit-content settings
• Language
• Theme

────────────────────────────────────────

NOTIFICATIONS

Implement:

• Notification center
• Unread counts
• Read/unread
• Notification preferences
• Deep links

Support:

• New release
• Playlist
• Podcast
• Subscription
• Payment
• Security
• Recommendation
• System

────────────────────────────────────────

ACCESSIBILITY

Target WCAG 2.2 AA.

Implement:

• Semantic HTML
• Keyboard navigation
• Focus management
• Screen-reader support
• Accessible player controls
• Accessible sliders
• Accessible dialogs
• Accessible menus
• Accessible playlists
• Accessible tables
• High contrast
• Reduced motion

Do not rely on color alone.

────────────────────────────────────────

RESPONSIVE DESIGN

Support:

• Desktop
• Tablet
• Mobile browser
• Large displays

The persistent player must adapt appropriately to small screens.

────────────────────────────────────────

INTERNATIONALIZATION

Support:

• Multiple languages
• Locale persistence
• Currency formatting
• Date/time formatting
• Number formatting
• Relative time
• RTL

Do not hard-code customer-facing strings throughout feature modules.

────────────────────────────────────────

SEO

Implement SEO foundations for public pages:

• Artist pages
• Album pages
• Track pages
• Public playlist pages
• Podcast pages

Support:

• Metadata
• Canonical URLs
• Open Graph
• Structured data where appropriate
• Sitemap strategy
• Robots rules

Private account and library pages must not be indexed.

────────────────────────────────────────

PERFORMANCE

Optimize:

• Streaming UI
• Home
• Search
• Artist pages
• Album pages
• Playlist pages
• Images
• Code splitting
• Dynamic imports
• Server Components
• Prefetching
• Query caching
• Virtualized lists

Do not load unnecessary JavaScript on public pages.

────────────────────────────────────────

SECURITY

Implement:

• Protected routes
• Safe URL handling
• Safe HTML rendering
• Content Security Policy compatibility
• Secure playback authorization handling
• Sensitive-field masking
• Safe error messages

Never expose:

• Secrets
• Provider credentials
• Password hashes
• Payment credentials
• Long-lived playback credentials

Frontend authorization is never the final security boundary.

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Player state
• Queue state
• Search state
• Formatting
• Validation
• Utility functions

COMPONENT TESTS

Test:

• Player
• Track cards
• Album pages
• Artist pages
• Playlist pages
• Library
• Search
• Subscription components
• Notification components

INTEGRATION TESTS

Test:

• API client
• Authentication
• TanStack Query
• Playback authorization
• Queue synchronization
• Search
• Subscription state

END-TO-END TESTS

Test:

• Registration
• Login
• Search
• Artist
• Album
• Track playback
• Playlist
• Library
• Subscription
• Podcast
• Notifications

ACCESSIBILITY TESTS

Test:

• Navigation
• Player
• Forms
• Dialogs
• Playlist editing
• Search

PERFORMANCE TESTS

Test:

• Home
• Search
• Artist pages
• Album pages
• Playlist pages
• Large libraries

────────────────────────────────────────

DOCUMENTATION

Generate:

• Web frontend architecture
• Folder structure
• Design system
• API client standards
• State-management standards
• Player architecture
• Queue architecture
• Search UX
• Playlist UX
• Library UX
• Subscription UX
• Accessibility
• SEO
• Internationalization
• Performance
• Testing

────────────────────────────────────────

PROJECT INDEX

Maintain the frontend Project Index.

Track:

• Applications
• Routes
• Features
• Components
• Layouts
• Hooks
• Stores
• Queries
• API integrations
• Player
• Queue
• Search
• Playlists
• Library
• Podcasts
• Subscriptions
• Notifications
• Tests
• Dependencies
• Generated files
• Remaining work
• Current milestone

────────────────────────────────────────

IMPLEMENTATION MILESTONES

FRONTEND MILESTONE 1

Next.js foundation, routing, providers, design system, API client, error handling, and configuration.

FRONTEND MILESTONE 2

Authentication, account, profile, session/device management, subscription state, and protected routing.

FRONTEND MILESTONE 3

Home, discovery, search, autocomplete, artist pages, album pages, track pages, and content cards.

FRONTEND MILESTONE 4

Core player, audio controls, playback states, progress, persistent player, and error recovery.

FRONTEND MILESTONE 5

Queue, device selection, playback transfer, synchronized playback, and radio.

FRONTEND MILESTONE 6

Playlists, collaboration, library, liked songs, saved albums, followed artists, and recently played.

FRONTEND MILESTONE 7

Podcasts, charts, recommendations, personalized discovery, and notifications.

FRONTEND MILESTONE 8

Subscriptions, billing UI, account security, privacy, settings, and entitlement-aware UI.

FRONTEND MILESTONE 9

Accessibility, SEO, localization, performance, responsive design, and security hardening.

FRONTEND MILESTONE 10

Integration testing, E2E testing, accessibility validation, performance testing, and production hardening.

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

This volume covers the web frontend foundation and core customer music experience.

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

Treat the web application as a production streaming platform serving hundreds of millions of users.

Assume:

• Millions of tracks
• Large playlists
• High search traffic
• Large concurrent playback
• Multiple devices
• Global users
• Multiple languages
• Multiple subscription plans
• Strict accessibility requirements
• Strict security requirements

Prioritize:

• Playback UX
• Performance
• Accessibility
• Security
• Reliable state synchronization
• Responsive design
• SEO
• Maintainability
• Scalability
• Production readiness
