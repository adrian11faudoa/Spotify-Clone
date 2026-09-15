# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — QA VOLUME 1

## ROLE

Act as the complete senior quality engineering organization responsible for implementing the production-grade testing, validation, security verification, reliability verification, performance testing, and release-quality controls for a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

Operate as:

* Principal Software Architect
* QA Engineer
* Staff Backend Engineer
* Staff Frontend Engineer
* Staff Mobile Engineer
* Database Architect
* Distributed Systems Engineer
* Security Engineer
* Performance Engineer
* Reliability Engineer
* DevOps Engineer
* Technical Writer

This prompt defines an independent quality-engineering implementation task.

Do not provide a tutorial.

Do not provide pseudo-code.

Do not create fake tests.

Do not create tests that merely make coverage numbers look better.

Do not leave TODO/FIXME testing gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and build the quality system around the actual implementation state.

Every test must validate meaningful behavior.

Tests must be deterministic, maintainable, observable, and appropriate for production software.

---

# PROJECT

Build and implement the comprehensive automated quality foundation for an original global music streaming platform.

The platform contains:

* Next.js web application
* React Native/Expo mobile applications
* NestJS backend
* PostgreSQL
* Redis
* Kafka or Redpanda
* BullMQ
* Elasticsearch or OpenSearch
* S3-compatible object storage
* CDN-based media delivery
* FFmpeg media processing
* subscriptions and payments
* notifications
* recommendations
* analytics
* administration
* moderation
* real-time communication
* large-scale playback workloads

The testing system must validate:

* functional correctness
* API correctness
* database correctness
* authorization
* security
* event behavior
* queue behavior
* media processing
* playback behavior
* search
* recommendations
* subscriptions
* notifications
* administration
* web behavior
* mobile behavior
* accessibility
* performance
* resilience
* deployment correctness
* migration correctness

The test strategy must reflect the fact that this is a distributed production system rather than a collection of isolated CRUD screens.

---

# TECHNOLOGY DIRECTION

Use the testing tools already established in the repository where compatible.

Use appropriate tooling for:

## Backend

* Jest or the repository's established TypeScript test framework
* Supertest or equivalent API testing
* Prisma-backed integration tests
* real Redis/infrastructure test dependencies where justified

## Web

* React Testing Library
* Playwright or the repository's established browser E2E framework
* accessibility tooling where appropriate

## Mobile

* React Native Testing Library
* Jest or repository-equivalent unit/component tooling
* Detox, Maestro, or another established mobile E2E framework where appropriate

## Infrastructure

Use appropriate validation for:

* Terraform
* Helm
* Kubernetes
* Docker
* GitHub Actions
* security configuration

Do not introduce multiple competing testing frameworks without a clear reason.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect backend tests.
3. Inspect frontend tests.
4. Inspect mobile tests.
5. Inspect E2E tests.
6. Inspect Prisma schema and migrations.
7. Inspect event contracts.
8. Inspect queue definitions.
9. Inspect media-processing workers.
10. Inspect search integration.
11. Inspect payment/webhook handling.
12. Inspect notification handling.
13. Inspect infrastructure validation.
14. Inspect CI/CD.
15. Inspect existing test utilities and fixtures.

The repository defines what currently exists.

This prompt defines the quality coverage that must be achieved.

Do not assume earlier AI-generated prompts are available.

Preserve existing useful testing infrastructure.

Do not replace working tests merely to use a preferred framework.

---

# QA RESPONSIBILITY

This volume is responsible for establishing the complete automated quality foundation.

It must cover:

* test architecture
* test environments
* test data
* fixtures
* factories
* backend unit tests
* backend integration tests
* API tests
* database tests
* event tests
* queue tests
* frontend component tests
* mobile component tests
* contract tests
* end-to-end tests
* authentication tests
* authorization tests
* security tests
* accessibility tests
* migration tests
* media-processing tests
* playback tests
* subscription tests
* notification tests
* search tests
* recommendation tests
* administration tests
* moderation tests

Later quality work may extend into dedicated performance and resilience campaigns, but this volume must establish the core quality architecture and broad functional coverage.

---

# TESTING PRINCIPLES

All tests must follow these principles:

* test behavior rather than implementation details
* prefer deterministic tests
* isolate tests appropriately
* use realistic data
* verify failure paths
* verify authorization
* verify persistence
* verify integration boundaries
* avoid excessive mocking
* avoid arbitrary sleeps
* clean up test state
* prevent test-order dependence
* make failures diagnosable

Do not write tests that simply assert that a mocked dependency was called unless that interaction itself is a meaningful contract.

---

# TEST PYRAMID

Establish a balanced testing strategy.

Use:

* unit tests for isolated business logic
* integration tests for real component boundaries
* API tests for HTTP contracts
* contract tests for external/internal interfaces
* component tests for UI behavior
* end-to-end tests for critical user journeys
* infrastructure tests for deployment/configuration behavior

Do not attempt to cover all behavior through end-to-end tests.

Do not attempt to validate complex integration behavior exclusively through mocks.

---

# TEST ENVIRONMENT

Establish reproducible test environments.

Support appropriate isolated dependencies for:

* PostgreSQL
* Redis
* Kafka/Redpanda
* Elasticsearch/OpenSearch
* object storage
* backend API
* workers

Use ephemeral or isolated environments where practical.

The test suite must not require access to production systems.

Never run automated tests against production databases, buckets, queues, or payment systems.

---

# TEST DATABASE

Use a dedicated test database strategy.

Support:

* isolated schema/database per test environment
* deterministic migrations
* fixture creation
* cleanup
* transaction isolation where suitable

Do not rely on developer-local database state.

Tests must be able to initialize required schema deterministically.

---

# TEST DATA FACTORIES

Implement reusable test factories for important entities such as:

* users
* sessions
* devices
* artists
* albums
* releases
* tracks
* playlists
* playlist items
* library entries
* media assets
* playback sessions
* subscriptions
* plans
* entitlements
* notifications
* reports
* moderation records
* audit events

Factories must produce valid default data while allowing targeted overrides.

Do not duplicate fixture construction throughout individual test files.

---

# TEST DATA ISOLATION

Prevent cross-test contamination.

Each test must be able to control:

* database state
* Redis state
* event state
* queue state
* search state
* object-storage state

Do not rely on test execution order.

Do not use one global mutable fixture for unrelated tests.

---

# BACKEND UNIT TESTS

Cover domain/application logic such as:

* authentication rules
* authorization policies
* playlist operations
* library operations
* catalog lifecycle
* media state transitions
* playback state transitions
* entitlement evaluation
* subscription transitions
* notification preferences
* moderation transitions
* retention logic
* account-deletion orchestration

Test:

* valid transitions
* invalid transitions
* boundary conditions
* duplicate operations
* concurrency-related decisions
* failure behavior

---

# AUTHENTICATION TESTING

Test:

* registration
* login
* invalid credentials
* disabled accounts
* session creation
* token refresh
* refresh-token rotation
* revoked sessions
* logout
* password change
* reset workflows
* verification flows where implemented
* concurrent refresh requests

Verify that:

* credentials are not returned
* tokens are not logged
* revoked sessions cannot authenticate
* refresh replay protections work as intended
* rate limiting applies correctly

---

# AUTHORIZATION TESTING

Authorization must be tested as a first-class security boundary.

Test:

* ordinary listener
* premium listener
* artist
* artist representative
* moderator
* support operator
* administrator
* platform operator

Test:

* ownership
* role permissions
* resource permissions
* action permissions
* cross-user access
* cross-role escalation
* private playlist access
* private history access
* protected media access
* administrative operations

Every sensitive endpoint must have negative authorization tests.

---

# IDOR TESTING

Explicitly test insecure direct object reference scenarios.

Attempt to access another user's:

* profile-private data
* playlists
* library
* history
* notifications
* subscription
* devices
* playback sessions

Attempt to modify another user's:

* playlist
* library
* profile
* subscription-related resources

Verify the server rejects unauthorized operations regardless of client behavior.

---

# API CONTRACT TESTING

Test all critical REST contracts.

Verify:

* status codes
* request validation
* response schema
* error schema
* pagination
* authentication requirements
* authorization behavior
* idempotency
* rate limiting

Do not rely exclusively on TypeScript compilation to prove API compatibility.

---

# API ERROR TESTING

For important endpoints test:

* malformed input
* missing required input
* invalid identifier
* unauthorized
* forbidden
* not found
* conflict
* rate limited
* dependency unavailable
* expired resource
* invalid state transition

Verify the API does not leak:

* stack traces
* SQL errors
* secrets
* internal network details
* provider credentials

---

# DATABASE TESTING

Use real PostgreSQL integration tests for critical persistence behavior.

Verify:

* foreign keys
* unique constraints
* indexes where behavior depends on them
* transaction boundaries
* rollback
* concurrent mutations
* optimistic locking
* state constraints
* deletion behavior
* retention behavior

Test high-risk concurrency scenarios such as:

* concurrent playlist edits
* duplicate likes
* duplicate follows
* concurrent entitlement changes
* media publication races

---

# MIGRATION TESTING

Every migration must be tested.

Validate:

* clean database bootstrap
* migration sequencing
* migration against representative prior schema
* indexes
* constraints
* data preservation
* compatibility

For migrations involving large tables, test operational behavior where practical.

Do not mark a migration safe merely because Prisma accepts the syntax.

---

# EVENT CONTRACT TESTING

Test event envelopes and schemas.

Verify:

* event ID
* event type
* version
* aggregate ID
* producer
* timestamp
* correlation metadata
* payload shape

Test:

* valid events
* invalid payloads
* version compatibility
* consumer behavior
* duplicate delivery
* replay

Do not allow consumers to fail unpredictably because of harmless additive schema changes.

---

# OUTBOX TESTING

Test transactional outbox behavior.

Verify:

* business transaction succeeds and outbox entry exists
* business transaction fails and no orphan success event is emitted
* publication retries
* publication failure remains recoverable
* duplicate publication is safe
* cleanup behavior is correct

Simulate publisher failure.

Verify the original database transaction remains correct.

---

# EVENT CONSUMER TESTING

For each important consumer, test:

* normal event
* duplicate event
* malformed event
* unsupported version
* retryable failure
* nonretryable failure
* downstream outage
* recovery

Verify idempotency.

Verify dead-letter behavior.

---

# QUEUE TESTING

Test background jobs such as:

* media processing
* search indexing
* notification delivery
* analytics processing
* cleanup
* subscription maintenance

Verify:

* successful execution
* retry
* backoff
* timeout
* duplicate jobs
* idempotency
* concurrency
* failure handling
* dead-letter behavior
* graceful shutdown

Do not use arbitrary delays to wait for workers when a deterministic job-completion signal can be used.

---

# MEDIA TESTING

Test secure media workflows.

Cover:

* authorized upload
* unauthorized upload
* oversized file
* invalid MIME
* invalid file signature
* malformed audio
* unsupported codec
* valid audio
* duplicate upload
* processing failure
* partial output
* successful processing
* publication gating
* object cleanup

Test that untrusted media cannot bypass validation.

---

# MEDIA PROCESSING TESTING

For FFmpeg/media workers verify:

* metadata extraction
* duration extraction
* codec detection
* transcoding
* derivative generation
* expected output existence
* invalid-output rejection
* retry behavior
* cleanup

Use representative valid and invalid media fixtures.

Do not commit unnecessarily large proprietary media files.

Use synthetic or appropriately licensed test fixtures.

---

# PLAYBACK AUTHORIZATION TESTING

Test:

* authenticated user
* anonymous user
* free user
* premium user
* expired subscription
* canceled subscription
* unavailable track
* unpublished track
* region restriction
* revoked session
* device restriction
* invalid session

Verify:

* authorized users receive valid access
* unauthorized users do not
* permanent storage URLs are never returned where protected delivery is required
* expired access is rejected

---

# PLAYBACK STATE TESTING

Test:

* start
* pause
* resume
* seek
* skip
* completion
* interruption
* expiration
* revocation
* termination

Test out-of-order updates.

Test duplicate progress events.

Test delayed client updates.

Verify newer state cannot be overwritten by stale state.

---

# PLAYBACK TELEMETRY TESTING

Verify:

* event validation
* throttling expectations
* duplicate handling
* authorization
* malformed events
* replayed events
* flood protection
* asynchronous processing
* privacy filtering

Telemetry failures must not corrupt core playback state.

---

# SEARCH TESTING

Test:

* indexing
* updating
* deletion
* reindexing
* search
* autocomplete
* typo handling where implemented
* filtering
* visibility
* explicit-content restrictions
* regional availability
* pagination

Test stale index behavior.

Verify search cannot bypass authoritative authorization.

---

# SEARCH FAILURE TESTING

Simulate:

* search cluster unavailable
* timeout
* partial failure
* stale index
* indexing failure
* reindexing failure

Verify:

* catalog transactions still work
* APIs degrade predictably
* errors are observable
* clients receive safe responses

---

# RECOMMENDATION TESTING

Test:

* personalized request
* anonymous fallback
* candidate filtering
* unavailable content filtering
* explicit-content filtering
* region filtering
* duplicate suppression
* recommendation fallback
* cache behavior
* experiment metadata
* recommendation-service failure

Verify no private user features are accidentally returned to clients.

---

# SUBSCRIPTION TESTING

Test:

* plan creation/retrieval
* checkout initiation
* customer mapping
* subscription activation
* renewal
* cancellation
* plan changes
* failed payment
* grace period
* expiration
* entitlement changes
* reconciliation

Test provider webhook:

* signature validation
* duplicate event
* out-of-order event
* invalid event
* provider outage
* local/provider mismatch

Verify client-supplied pricing and entitlement claims are ignored.

---

# PAYMENT SAFETY TESTING

Verify:

* no raw payment credentials enter application storage
* invalid provider signatures are rejected
* duplicate financial events are safe
* amount/currency are authoritative
* provider identifiers are validated
* unauthorized billing access is rejected
* billing audit records are created appropriately

Never point automated tests at real customer payment accounts.

Use provider test/sandbox environments when integration testing external payment behavior.

---

# NOTIFICATION TESTING

Test:

* preference evaluation
* notification creation
* channel selection
* deduplication
* queueing
* retry
* provider failure
* invalid push token
* email failure
* in-app read state
* notification expiration

Verify security-critical notifications remain governed by server policy.

---

# MODERATION TESTING

Test:

* report creation
* report authorization
* moderation state transitions
* assignment
* resolution
* escalation
* appeal where implemented
* content restriction
* restoration
* audit logging

Verify unauthorized users cannot invoke moderation actions.

---

# ADMINISTRATION TESTING

Test privileged workflows.

Verify:

* role enforcement
* resource scoping
* read-only versus mutation access
* confirmation requirements
* audit creation
* support-data minimization
* sensitive-field masking where required

Attempt privilege escalation through direct API calls, not merely UI interactions.

---

# ACCOUNT DELETION TESTING

Test:

* deletion initiation
* authorization
* confirmation
* session revocation
* account state transition
* downstream deletion event
* private-data clearing
* notification
* cache invalidation
* recommendation-profile cleanup
* analytics privacy handling

Verify deleted accounts cannot continue authenticating.

---

# PRIVACY TESTING

Test that private data is never exposed through:

* public APIs
* search
* recommendations
* analytics
* logs
* error messages
* notifications
* caches
* administrative endpoints without authorization

Test account switching and logout behavior in web and mobile clients.

---

# REDIS TESTING

Test:

* cache hit
* cache miss
* expiration
* invalidation
* Redis outage
* stale values
* key isolation
* rate limiting
* playback state
* BullMQ behavior

Verify the application does not lose authoritative business state when Redis is unavailable.

---

# RESILIENCE TESTING FOUNDATION

Establish controlled tests for dependency failure.

At minimum evaluate:

* PostgreSQL unavailable
* Redis unavailable
* Kafka/Redpanda unavailable
* search unavailable
* object storage unavailable
* payment provider unavailable
* notification provider unavailable

For each scenario verify:

* timeout
* retry
* fallback
* user-visible behavior
* observability
* recovery

Do not treat every dependency failure identically.

---

# FRONTEND COMPONENT TESTING

Test reusable web components and feature components.

Cover:

* forms
* validation
* error states
* loading states
* empty states
* buttons/actions
* search
* playlists
* library
* notifications
* player
* queue
* subscription UI
* artist workflows
* administration

Test behavior and accessibility semantics.

Avoid snapshots as the primary validation mechanism.

---

# WEB PLAYER TESTING

Test:

* play
* pause
* seek
* next
* previous
* shuffle
* repeat
* queue
* loading
* buffering
* error
* expired authorization
* route transitions
* logout
* account switching

Verify player state does not reset unexpectedly because a route component unmounted.

---

# WEB ACCESSIBILITY TESTING

Automate and manually validate:

* keyboard navigation
* accessible names
* focus management
* dialogs
* menus
* search
* playback controls
* forms
* dynamic updates

Use accessibility tooling for automated detection but do not treat automated checks as complete accessibility validation.

---

# MOBILE TESTING

Test React Native functionality including:

* authentication
* navigation
* deep links
* push notifications
* search
* playlists
* library
* playback
* queue
* subscription state
* logout
* account switching
* network failure
* secure storage behavior

Run platform-specific tests where behavior differs materially.

---

# MOBILE PLAYBACK TESTING

Validate:

* background playback
* lock-screen controls
* audio interruptions
* Bluetooth/headset events
* audio focus
* app lifecycle
* playback recovery
* progress synchronization

Do not consider a mocked audio player sufficient proof of platform playback behavior.

Where device testing is required, execute representative device/emulator tests.

---

# MOBILE OFFLINE TESTING

Where offline functionality exists, test:

* download authorization
* download progress
* interruption
* retry
* expiration
* revocation
* storage cleanup
* offline playback
* reconnection
* telemetry synchronization

Verify protected media is not accessible outside the authorized application context.

---

# END-TO-END LISTENER JOURNEY

Implement a critical browser E2E workflow covering:

1. visitor opens the platform
2. user registers or logs in
3. user searches for content
4. user opens artist
5. user opens album
6. user starts playback
7. user likes a track
8. user creates a playlist
9. user adds a track
10. user navigates library
11. user opens recommendations
12. user checks notifications
13. user opens subscription state
14. user logs out

The workflow must use real application behavior and realistic backend state.

---

# END-TO-END MOBILE JOURNEY

Where device automation is available, cover:

1. application launch
2. authentication
3. catalog navigation
4. search
5. playback
6. queue
7. playlist mutation
8. notification/deep link
9. account/settings
10. logout

Validate platform-specific behavior separately where necessary.

---

# TEST AUTHENTICATION DATA

Create dedicated test accounts with explicit roles.

Do not reuse production accounts.

Credentials must be supplied through secure test configuration.

Do not commit test passwords into source control.

---

# EXTERNAL PROVIDER TESTING

For external providers such as:

* Stripe
* email
* push notifications
* object storage
* CDN

use:

* official sandbox/test environments
* local emulators where reliable
* contract tests
* provider-specific adapters

Do not run production financial operations from automated test suites.

---

# TEST OBSERVABILITY

Make test failures diagnosable.

Capture appropriate:

* request IDs
* traces
* logs
* screenshots
* video where E2E tools support it
* network traces where safe
* worker logs
* database diagnostics where useful

Do not include secrets in test artifacts.

---

# FLAKY TEST MANAGEMENT

Identify and eliminate flaky tests.

Do not simply increase retry counts to hide instability.

For each flaky test:

* determine root cause
* fix synchronization
* remove timing assumptions
* isolate shared state
* stabilize external dependencies
* document unavoidable environmental constraints

CI should distinguish:

* deterministic failure
* infrastructure failure
* test flakiness

---

# TEST PARALLELIZATION

Parallelize safely where possible.

Tests must not conflict through:

* shared database state
* Redis keys
* queue names
* object-storage keys
* search indexes
* test accounts

Use unique test namespaces or isolated resources.

Do not sacrifice deterministic behavior merely to maximize parallelism.

---

# CI QUALITY GATES

Integrate automated tests into CI.

Require appropriate gates for:

* type checking
* linting
* unit tests
* integration tests
* API tests
* contract tests
* frontend tests
* mobile tests
* E2E tests where appropriate
* migration validation
* security tests

Do not make every expensive E2E suite block every tiny documentation-only change unless the repository's CI architecture explicitly justifies it.

Use sensible path-aware or staged validation.

---

# COVERAGE

Track coverage as a useful signal.

Prioritize coverage of:

* authorization
* financial state
* playback authorization
* data deletion
* event consumers
* critical state machines
* security boundaries

Do not chase arbitrary global percentages while leaving security-critical logic untested.

Coverage exclusions must be explicit and justified.

---

# SECURITY TESTING

Automate security validation for:

* dependency vulnerabilities
* secret leakage
* authentication bypass
* authorization bypass
* IDOR
* malformed input
* injection
* unsafe upload
* rate-limit bypass
* SSRF-sensitive features
* XSS-sensitive rendering
* insecure direct media access
* webhook forgery

Use appropriate automated scanning plus focused functional security tests.

Do not substitute a generic scanner for actual authorization tests.

---

# TEST DOCUMENTATION

Document:

* running unit tests
* running integration tests
* starting test dependencies
* test environment variables
* factory usage
* E2E execution
* mobile device testing
* external sandbox setup
* debugging failures
* CI test stages
* known environment-specific limitations

Documentation must match the actual commands and tooling.

---

# IMPLEMENTATION BOUNDARIES

This QA volume owns the broad automated quality foundation.

Implement:

* test architecture
* test fixtures/factories
* backend unit/integration/API tests
* database/migration tests
* event/outbox tests
* queue tests
* media tests
* playback tests
* search tests
* recommendation tests
* subscription/payment tests
* notification tests
* moderation/admin tests
* privacy tests
* web component tests
* web accessibility tests
* mobile tests
* critical E2E workflows
* security test foundations
* CI quality gates
* test documentation

Do not implement:

* unrelated production business functionality merely to satisfy a test
* fake implementations solely to increase test coverage
* destructive infrastructure experiments against production

When a test reveals a genuine production defect, fix the production defect rather than weakening the test.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before changing files:

1. inspect current test structure
2. inspect existing fixtures
3. inspect CI
4. inspect environment setup
5. inspect backend modules
6. inspect frontend modules
7. inspect mobile modules
8. inspect worker infrastructure
9. inspect test utilities
10. identify missing quality boundaries

Then:

1. establish test infrastructure
2. implement reusable factories
3. implement backend unit/integration/API coverage
4. implement data/migration testing
5. implement events/queues/media/playback tests
6. implement search/recommendation/subscription/notification tests
7. implement frontend tests
8. implement mobile tests
9. implement E2E workflows
10. implement security/accessibility coverage
11. integrate CI gates
12. validate full affected suites
13. update documentation

Do not rewrite existing valid tests unnecessarily.

---

# COMPLETION CRITERIA

This QA task is complete only when:

* test environments are reproducible
* test data is isolated
* factories cover major domains
* backend critical paths are tested
* API contracts are tested
* database behavior is tested
* migrations are tested
* authorization boundaries have negative tests
* event/outbox behavior is tested
* queue behavior is tested
* media processing is tested
* playback is tested
* search is tested
* recommendations are tested
* subscriptions/payments are tested safely
* notifications are tested
* moderation/admin behavior is tested
* account deletion/privacy are tested
* web components and workflows are tested
* accessibility testing exists
* mobile workflows are tested
* critical E2E journeys exist
* security testing exists
* CI quality gates are integrated
* flaky tests are addressed
* test documentation is complete
* no required quality capability is intentionally incomplete

Do not declare completion when required tests, builds, environments, or validation steps fail.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* test infrastructure changes
* fixtures/factories created
* backend test coverage
* API test coverage
* database/migration coverage
* event/outbox coverage
* queue coverage
* media/playback coverage
* search/recommendation coverage
* subscription/payment coverage
* notification coverage
* moderation/admin coverage
* privacy/security coverage
* frontend test coverage
* mobile test coverage
* E2E workflows
* accessibility testing
* CI quality gates
* security scans
* validation performed
* flaky tests discovered and resolved
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified tests from tests that could not be executed because of environmental limitations.

Do not claim a test suite passed unless it was actually executed.

---

# FINAL INSTRUCTION

Build the quality system as part of the production platform rather than as an afterthought.

Test real behavior.

Test failures.

Test authorization.

Test concurrency.

Test duplicate delivery.

Test retries.

Test data migrations.

Test media processing.

Test playback.

Test financial state.

Test privacy.

Test web and mobile behavior.

Test critical end-to-end user journeys.

Test infrastructure boundaries where appropriate.

Do not use mocks to hide integration failures.

Do not weaken tests to accommodate broken production behavior.

When a test exposes a real defect, fix the production implementation while preserving the intended architecture and contracts.

The resulting quality foundation must provide reliable evidence that the music-streaming platform behaves correctly and securely across its backend, web, mobile, media, search, recommendation, subscription, notification, analytics, and operational surfaces.
