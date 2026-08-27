You are operating in Senior Engineering Team Mode.

Build the production-ready backend for identity, accounts, profiles, authentication, authorization, sessions, devices, subscriptions, billing, payments, and entitlements for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The backend must follow the approved Spotify-like architecture, domain boundaries, service ownership, database architecture, API conventions, security model, event architecture, and Project Index.

Do not redesign the architecture.

Do not generate frontend code.

Do not generate mobile code.

Do not generate infrastructure implementation code.

Do not generate Terraform.

Do not generate Kubernetes manifests.

Do not generate CI/CD workflows.

────────────────────────────────────────

MISSION

Implement the production-ready backend domains for:

• Identity
• Users
• Accounts
• Profiles
• Authentication
• Authorization
• Sessions
• Devices
• Account security
• Subscription plans
• Subscriptions
• Billing accounts
• Payment methods
• Payments
• Invoices
• Refunds
• Entitlements
• Regional plan availability
• Subscription lifecycle
• Payment-provider webhooks
• Subscription reconciliation

The implementation must support:

• Hundreds of millions of users
• Multiple profiles where supported
• Multiple devices per account
• Multiple concurrent sessions
• Free plans
• Premium plans
• Family plans
• Student plans
• Regional pricing
• Trials where approved
• Upgrades
• Downgrades
• Cancellations
• Grace periods
• Payment failures
• Renewals
• Entitlement recovery

────────────────────────────────────────

TECHNOLOGY STACK

Backend:

• Node.js
• NestJS
• TypeScript

Database:

• PostgreSQL
• Prisma ORM

Cache:

• Redis

Event Streaming:

• Kafka or Redpanda

Background Jobs:

• BullMQ

Payments:

• Stripe or approved payment abstraction

Notifications:

• Firebase Cloud Messaging
• Apple Push Notification Service
• Email provider abstraction

Testing:

• Jest
• Supertest
• Integration testing tools

Observability:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

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

Use dependency injection.

Keep controllers thin.

Keep business logic outside controllers.

Use repositories for persistence.

Use DTOs for external contracts.

Use centralized validation.

Use centralized error handling.

Use structured logging.

Use the existing observability infrastructure.

Use idempotency for security- and payment-sensitive operations.

────────────────────────────────────────

DOMAIN OWNERSHIP

Maintain explicit boundaries between:

Identity

Accounts

Profiles

Authentication

Authorization

Sessions

Devices

Subscriptions

Billing

Payments

Entitlements

Notifications

Audit

Do not combine:

• Payment state with subscription state
• Subscription state with entitlement state
• Session state with account state
• Device state with authentication credentials

────────────────────────────────────────

IDENTITY

Implement:

• User creation
• User lookup
• User status
• Identity lifecycle
• Account association
• Account activation
• Account suspension
• Account deactivation
• Account deletion workflow

Support states such as:

• Pending
• Active
• Suspended
• Disabled
• Deactivated
• Deleted

Use stable public identifiers.

Do not expose internal database IDs unnecessarily.

────────────────────────────────────────

ACCOUNT

Implement:

• Account creation
• Account retrieval
• Account settings
• Account status
• Security settings
• Account recovery
• Account deletion request
• Account suspension
• Account reactivation where permitted

Separate:

• Identity
• Account
• Profile
• Session
• Device
• Subscription

Account-level operations must be auditable.

────────────────────────────────────────

PROFILE

Implement:

• Profile creation
• Profile retrieval
• Profile update
• Profile deletion where supported
• Display name
• Avatar reference
• Language preference
• Content preferences
• Explicit-content preference
• Autoplay preference
• Notification preferences

Support account models containing multiple profiles where the approved architecture allows it.

Profile-specific recommendation and listening state must remain isolated.

────────────────────────────────────────

PROFILE SECURITY

Support:

• Profile PIN where appropriate
• Managed/kids profile boundaries where supported
• Explicit-content restrictions
• Search restrictions
• Playback restrictions

Restrictions must be enforced server-side.

────────────────────────────────────────

AUTHENTICATION

Implement:

• Registration
• Login
• Logout
• Refresh
• Session creation
• Session revocation
• Email verification
• Password reset
• Password change

Prepare architecture for:

• OAuth
• MFA
• Passkeys
• Social login providers

Do not implement unsupported providers as fake placeholders.

────────────────────────────────────────

PASSWORD SECURITY

Implement:

• Industry-standard password hashing
• Password verification
• Password change
• Password reset
• Reset-token expiration
• Single-use reset tokens
• Login-attempt protection
• Account lockout/rate limiting where appropriate

Never:

• Store plaintext passwords
• Log passwords
• Return password hashes
• Include passwords in events

────────────────────────────────────────

EMAIL VERIFICATION

Implement:

• Verification token generation
• Token expiration
• Single-use verification
• Resend limits
• Verification state
• Replay prevention

Integrate with the established notification abstraction.

────────────────────────────────────────

SESSION MANAGEMENT

Implement:

• Session creation
• Session retrieval
• Session listing
• Session refresh
• Session expiration
• Session revocation
• Logout-all-sessions

Track appropriate metadata:

• Device
• Platform
• Application version
• Created timestamp
• Last activity
• Expiration
• Revocation state
• Security metadata where appropriate

Do not store unnecessary secrets.

────────────────────────────────────────

DEVICE MANAGEMENT

Implement:

• Device registration
• Device identification
• Device platform
• Application version
• Capabilities reference
• Push token association
• Session association
• Device revocation
• Remote logout

Prepare device capabilities needed later for:

• Audio quality
• Offline downloads
• DRM/content protection
• Background playback
• Maximum supported codec

Do not collect unnecessary device information.

────────────────────────────────────────

DEVICE AUTHORIZATION

Define:

• Device ownership
• Device registration trust
• Device revocation
• Maximum device counts where applicable
• Active device limits
• Download device limits

Ensure revoked devices cannot silently continue privileged operations.

────────────────────────────────────────

AUTHORIZATION

Implement RBAC and permission infrastructure.

Roles may include:

• Listener
• Premium Listener
• Family Manager
• Student Subscriber
• Artist
• Artist Staff
• Label Staff
• Content Moderator
• Support Agent
• Administrator
• Super Administrator
• System Service

Implement:

• Guards
• Permission decorators
• Policies
• Resource ownership
• Account scoping
• Profile scoping
• Organization scoping

────────────────────────────────────────

PROFILE-LEVEL AUTHORIZATION

Ensure profile-specific data is isolated.

This includes:

• Listening history
• Recommendations
• Playlists where private
• Likes
• Saved albums
• Follow relationships
• Downloads
• Preferences

One profile must not automatically gain access to another profile's private state.

────────────────────────────────────────

SUBSCRIPTION PLAN DOMAIN

Implement:

• Plan creation
• Plan retrieval
• Plan activation
• Plan deactivation
• Regional availability
• Currency
• Billing interval
• Feature definitions
• Device limits
• Offline limits
• Audio-quality limits
• Family/Student eligibility rules

Support plan types such as:

• Free
• Premium
• Family
• Student

Use configuration rather than hard-coding plan behavior throughout the domain.

────────────────────────────────────────

REGIONAL PLAN AVAILABILITY

Support:

• Region
• Currency
• Local pricing
• Tax behavior
• Availability period
• Plan eligibility

Prevent unavailable plans from being purchased in unsupported regions.

────────────────────────────────────────

SUBSCRIPTION DOMAIN

Implement:

• Subscription creation
• Activation
• Upgrade
• Downgrade
• Renewal
• Cancellation
• Expiration
• Grace period
• Payment failure
• Recovery

Subscription states may include:

• Trialing
• Active
• Past Due
• Grace Period
• Canceled
• Expired
• Suspended

Define valid state transitions.

────────────────────────────────────────

SUBSCRIPTION STATE CONSISTENCY

Separate:

• Subscription state
• Payment state
• Billing state
• Entitlement state

Do not assume these states always transition simultaneously.

Define eventual-consistency behavior for delayed provider events.

────────────────────────────────────────

TRIALS

Support trials where the approved plan allows them.

Implement:

• Trial start
• Trial end
• Trial eligibility
• Trial conversion
• Trial cancellation
• Trial expiration

Prevent repeated abuse of trial eligibility.

────────────────────────────────────────

UPGRADE AND DOWNGRADE

Implement:

• Immediate upgrade where appropriate
• Scheduled downgrade where appropriate
• Proration through the payment provider where supported
• Entitlement changes
• Billing-period handling

Never calculate provider-specific financial behavior incorrectly in the core domain.

Use provider abstraction boundaries.

────────────────────────────────────────

CANCELLATION

Support:

• Immediate cancellation where allowed
• End-of-period cancellation
• Cancellation reason
• Cancellation timestamp
• Entitlement expiration

Do not silently remove entitled access before the configured cancellation period ends.

────────────────────────────────────────

BILLING ACCOUNT

Implement billing-account state separate from the user/account domain.

Support:

• Billing customer reference
• Billing region
• Currency
• Tax metadata
• Provider references
• Billing state

Never store unnecessary raw payment information.

────────────────────────────────────────

PAYMENT DOMAIN

Implement a payment abstraction.

Support:

• Payment method reference
• Payment intent
• Payment attempt
• Payment status
• Payment confirmation
• Payment failure
• Refund
• Payment provider reference

Use provider tokens and references.

────────────────────────────────────────

STRIPE INTEGRATION

Implement the approved Stripe abstraction.

Support:

• Customer creation
• Payment intent
• Subscription-related billing where appropriate
• Payment methods
• Webhooks
• Refunds
• Provider metadata

Do not allow Stripe-specific models to become the core business-domain model.

────────────────────────────────────────

PAYMENT STATE MACHINE

Implement states such as:

• Created
• Requires Action
• Processing
• Succeeded
• Failed
• Canceled
• Refunded
• Partially Refunded

Define valid transitions.

Never mark payment successful solely from a client request.

────────────────────────────────────────

WEBHOOK PROCESSING

Implement secure payment webhook handling.

Support:

• Signature verification
• Event persistence
• Event ID uniqueness
• Duplicate detection
• Idempotent processing
• Retry
• Failure recording
• Unknown-event handling
• Reconciliation

Persist provider event IDs.

Never process unverified webhook payloads.

────────────────────────────────────────

INVOICES

Implement:

• Invoice reference
• Invoice state
• Amount
• Currency
• Billing period
• Provider reference
• Created date
• Due date where appropriate
• Paid date
• Void state

Historical invoice data must remain auditable.

────────────────────────────────────────

REFUNDS

Implement:

• Full refund
• Partial refund
• Refund reason
• Refund state
• Provider reference
• Refund timestamps

Prevent duplicate refund effects.

────────────────────────────────────────

ENTITLEMENTS

Implement an entitlement domain.

Support entitlement decisions for:

• Streaming
• Offline downloads
• Premium audio quality
• Ad-free experience
• Family benefits
• Student benefits
• Regional content
• Other subscription features

Define entitlement sources:

• Subscription
• Plan
• Promotional grant where supported
• Administrative grant where explicitly authorized

────────────────────────────────────────

ENTITLEMENT STATE

Support:

• Active
• Grace
• Expiring
• Expired
• Revoked

Define:

• Effective time
• Expiration
• Source
• Subscription reference
• Region
• Profile/account scope

────────────────────────────────────────

ENTITLEMENT CACHING

Use Redis for low-latency entitlement reads where appropriate.

Define:

• Key pattern
• TTL
• Invalidation
• Refresh
• Failure behavior

If Redis is unavailable, entitlement evaluation must fall back to authoritative sources where possible.

Do not allow stale entitlements to persist beyond configured safety boundaries.

────────────────────────────────────────

PAYMENT / ENTITLEMENT RECOVERY

Define behavior for:

• Payment succeeds but webhook is delayed
• Webhook arrives multiple times
• Payment provider temporarily unavailable
• Subscription expires
• Payment fails during renewal
• Refund issued
• Subscription canceled
• Region changes

Reconciliation must eventually converge subscription and entitlement state.

────────────────────────────────────────

FAMILY PLANS

Design backend boundaries for:

• Family account
• Family manager
• Family members/profiles
• Shared subscription
• Profile-specific personalization
• Device limits
• Entitlement inheritance

Define who controls:

• Billing
• Plan
• Family membership
• Payment method

────────────────────────────────────────

STUDENT PLANS

Support architecture for:

• Student eligibility
• Verification provider abstraction
• Student plan activation
• Verification expiration
• Re-verification
• Downgrade after eligibility expires

Do not hard-code one verification provider into the domain layer.

────────────────────────────────────────

SUBSCRIPTION EVENTS

Publish:

• SubscriptionCreated
• SubscriptionActivated
• SubscriptionUpgraded
• SubscriptionDowngraded
• SubscriptionRenewed
• SubscriptionCancellationRequested
• SubscriptionCanceled
• SubscriptionExpired
• SubscriptionGracePeriodStarted
• PaymentSucceeded
• PaymentFailed
• RefundIssued
• EntitlementGranted
• EntitlementChanged
• EntitlementRevoked
• DeviceRegistered
• DeviceRevoked
• SessionCreated
• SessionRevoked

Events must contain only information consumers need.

Never include:

• Passwords
• Access tokens
• Refresh tokens
• Raw payment credentials

────────────────────────────────────────

BACKGROUND JOBS

Implement BullMQ jobs for:

• Verification-token cleanup
• Password-reset cleanup
• Session cleanup
• Device cleanup
• Trial expiration
• Subscription renewal reconciliation
• Entitlement expiration
• Provider reconciliation
• Invoice synchronization
• Payment reconciliation
• Refund reconciliation

Each job must support:

• Retry
• Exponential backoff
• Timeout
• Idempotency
• Dead-letter handling
• Metrics
• Structured logs

────────────────────────────────────────

DATABASE

Implement Prisma models and migrations for the domains covered by this volume.

Include appropriate models such as:

• User
• Account
• Profile
• Session
• Device
• VerificationToken
• PasswordResetToken
• Role
• Permission
• RolePermission
• UserRole
• ProfileRestriction
• SubscriptionPlan
• PlanRegion
• Subscription
• SubscriptionChange
• BillingAccount
• PaymentMethodReference
• Payment
• PaymentAttempt
• PaymentWebhookEvent
• Invoice
• Refund
• Entitlement
• EntitlementGrant
• SubscriptionProviderReference where appropriate
• Audit/SecurityEvent references where appropriate

Use:

• Primary keys
• Foreign keys
• Unique constraints
• Composite indexes
• Check constraints
• Status constraints
• Effective timestamps
• Expiration timestamps

Do not create music catalog tables in this volume.

────────────────────────────────────────

DATABASE TRANSACTIONS

Use transactions for local consistency such as:

• User/account creation
• Session creation where appropriate
• Role assignment
• Subscription state transitions
• Entitlement persistence
• Payment record creation
• Refund record creation
• Webhook-event persistence

Do not use distributed transactions with external payment providers.

Use:

• Idempotency
• Outbox events
• Reconciliation
• Provider references

────────────────────────────────────────

API

Implement production-ready REST APIs.

AUTHENTICATION

• Register
• Login
• Logout
• Refresh
• Verify
• Password reset
• Password change

ACCOUNT

• Get account
• Update account
• Account security

PROFILE

• Create profile
• List profiles
• Get profile
• Update profile
• Delete profile where supported

SESSIONS

• List sessions
• Revoke session
• Revoke all sessions

DEVICES

• Register device
• List devices
• Revoke device

SUBSCRIPTIONS

• List plans
• Get plan
• Create subscription
• Get subscription
• Change plan
• Cancel subscription
• Resume where supported

BILLING

• Get billing account
• List invoices
• Get invoice
• List payment methods where supported

PAYMENTS

• Create payment intent
• Get payment state
• Payment history

ENTITLEMENTS

• Get current entitlements

ADMINISTRATION

• Manage plans
• Manage plan regions
• Manage subscription state with appropriate permissions
• Inspect payments
• Inspect entitlements
• Reconcile provider state

Every endpoint must implement:

• Authentication
• Authorization
• DTO validation
• Rate limiting
• OpenAPI documentation
• Consistent error responses
• Idempotency where appropriate

────────────────────────────────────────

SECURITY

Protect against:

• Account takeover
• Credential stuffing
• Session theft
• Token replay
• Subscription abuse
• Trial abuse
• Payment abuse
• Refund abuse
• Privilege escalation
• Unauthorized entitlement access
• Seller/artist/admin data leakage

Implement:

• Rate limiting
• Strong authentication
• Secure session management
• Resource ownership
• RBAC
• Provider webhook verification
• Audit logging

────────────────────────────────────────

PRIVACY

Minimize sensitive data.

Protect:

• Account information
• Billing information
• Payment references
• Device information
• Security events
• Profile restrictions

Do not expose billing or security information to unauthorized profiles or users.

────────────────────────────────────────

OBSERVABILITY

Instrument:

• Registration
• Login
• Authentication failures
• Session creation/revocation
• Device operations
• Subscription changes
• Payment operations
• Webhook processing
• Entitlement evaluation
• Reconciliation
• Administrative subscription changes

Track:

• Login failure rate
• Authentication latency
• Subscription conversion
• Renewal success
• Payment failure rate
• Entitlement latency
• Webhook processing latency
• Reconciliation mismatches

Never log:

• Passwords
• Tokens
• Payment credentials
• Secrets

────────────────────────────────────────

TESTING

UNIT TESTS

Test:

• Authentication rules
• Password policies
• Session state
• Device policies
• Authorization
• Subscription state machine
• Plan eligibility
• Trial eligibility
• Entitlement calculation
• Refund rules

INTEGRATION TESTS

Test:

• PostgreSQL
• Prisma
• Redis
• Kafka
• BullMQ
• Stripe abstraction

WEBHOOK TESTS

Test:

• Signature verification
• Duplicate events
• Delayed events
• Out-of-order events
• Retry
• Unknown event types
• Malformed payloads

SECURITY TESTS

Test:

• Account takeover
• Session invalidation
• Token replay
• IDOR
• Privilege escalation
• Subscription manipulation
• Entitlement bypass

CONCURRENCY TESTS

Test:

• Concurrent subscription changes
• Duplicate payment requests
• Duplicate webhook delivery
• Concurrent cancellation
• Concurrent renewal processing

FINANCIAL TESTS

Test:

• Payment success
• Payment failure
• Refund
• Partial refund
• Subscription renewal
• Provider reconciliation

PERFORMANCE TESTS

Test:

• Login
• Subscription lookup
• Entitlement lookup
• Payment webhook throughput
• Session operations

────────────────────────────────────────

DOCUMENTATION

Generate:

• Identity architecture
• Authentication flows
• Session lifecycle
• Device lifecycle
• Authorization model
• Profile model
• Subscription plans
• Subscription lifecycle
• Billing architecture
• Payment architecture
• Webhook processing
• Entitlement model
• Family-plan architecture
• Student-plan architecture
• Regional plan architecture
• Reconciliation
• API contracts
• Database schema
• Event contracts
• Queue architecture
• Testing strategy
• Security model

────────────────────────────────────────

PROJECT INDEX

Update the backend Project Index with:

• Identity modules
• Account modules
• Profile modules
• Authentication
• Authorization
• Session modules
• Device modules
• Subscription modules
• Billing modules
• Payment modules
• Invoice modules
• Refund modules
• Entitlement modules
• Database objects
• Migrations
• API endpoints
• Webhooks
• Events
• Queues
• Workers
• Tests
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

BACKEND MILESTONE 11

Identity, users, accounts, profiles, and database models.

BACKEND MILESTONE 12

Authentication, password handling, email verification, sessions, and device management.

BACKEND MILESTONE 13

Authorization, RBAC, permissions, profile restrictions, and security hardening.

BACKEND MILESTONE 14

Subscription plans, regional availability, pricing metadata, and trial eligibility.

BACKEND MILESTONE 15

Subscriptions, lifecycle transitions, upgrades, downgrades, cancellation, and grace periods.

BACKEND MILESTONE 16

Billing accounts, payment methods, payment intents, payment persistence, and secure provider integration.

BACKEND MILESTONE 17

Webhooks, invoices, refunds, reconciliation, and provider-state synchronization.

BACKEND MILESTONE 18

Entitlements, entitlement caching, family/student boundaries, and entitlement recovery.

BACKEND MILESTONE 19

Events, background jobs, notifications integration, observability, and administrative operations.

BACKEND MILESTONE 20

Integration testing, concurrency testing, security testing, financial testing, performance testing, and production hardening.

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

This volume covers only:

• Identity
• Accounts
• Profiles
• Authentication
• Authorization
• Sessions
• Devices
• Subscription plans
• Subscriptions
• Billing
• Payments
• Invoices
• Refunds
• Entitlements
• Family-plan boundaries
• Student-plan boundaries
• Regional plan availability
• Payment webhooks
• Reconciliation

Do not implement complete:

• Artists
• Albums
• Tracks
• Releases
• Audio assets
• Audio processing
• Rights
• Availability
• Playback
• Downloads
• Playlists
• Library
• Search
• Recommendations
• Radio
• Charts
• Podcasts
• Notifications
• Advertising
• Analytics
• Moderation
• Administration UI
• Infrastructure

Those belong to later backend implementation volumes.

────────────────────────────────────────

QUALITY BAR

Treat identity, subscriptions, payments, and entitlements as mission-critical backend infrastructure.

Assume:

• Hundreds of millions of users
• Large concurrent login volume
• Millions of subscription records
• High payment traffic
• High webhook volume
• Multiple devices per account
• Multiple profiles
• Regional plans
• Strict security requirements
• Strict privacy requirements
• Global deployment

Prioritize:

• Authentication security
• Authorization correctness
• Subscription correctness
• Payment idempotency
• Entitlement accuracy
• Auditability
• Reconciliation
• Scalability
• Observability
• Fault tolerance
• Maintainability
• Production readiness
