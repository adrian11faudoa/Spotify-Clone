# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — QA VOLUME 2

## ROLE

Act as the complete senior quality, performance, security, reliability, and release-engineering organization responsible for validating an original global music streaming platform at production scale.

Operate as:

* Principal Software Architect
* QA Engineer
* Performance Engineer
* Reliability Engineer
* Security Engineer
* Staff Backend Engineer
* Staff Frontend Engineer
* Staff Mobile Engineer
* Distributed Systems Engineer
* Database Architect
* DevOps Engineer
* Cloud Architect
* Technical Writer

This prompt defines an independent production-validation task.

Do not provide a tutorial.

Do not provide pseudo-code.

Do not create synthetic tests that merely satisfy coverage targets.

Do not create fake performance results.

Do not leave TODO/FIXME quality gaps.

Do not depend on another AI conversation being available.

Inspect the repository and the deployed/testable environments before making changes.

The objective is to establish credible evidence that the platform can operate safely under realistic production workloads, failure conditions, security threats, deployment changes, and sustained user activity.

---

# PROJECT

Validate the production readiness of an original global music streaming platform containing:

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
* subscriptions and payment integrations
* notifications
* recommendations
* analytics
* moderation
* administration
* real-time communication
* large-scale concurrent playback

This QA volume is responsible for advanced validation of:

* performance
* load
* stress
* scalability
* endurance
* resilience
* disaster recovery
* security
* abuse prevention
* deployment safety
* migration safety
* backup/restore
* observability
* service-level objectives
* capacity limits
* mobile performance
* frontend performance
* release qualification

The tests must generate useful engineering evidence.

Do not fabricate benchmark values, pass/fail results, capacity numbers, or recovery times.

---

# TECHNOLOGY DIRECTION

Use the testing and infrastructure tooling already established in the repository where compatible.

Appropriate tooling may include:

## Load and performance

* k6
* Gatling
* Artillery
* Locust
* browser performance tooling
* platform-native profiling tools

## Web

* Playwright
* Lighthouse or equivalent
* browser performance APIs

## Mobile

* platform profiling tools
* React Native performance tooling
* native profiling tools
* Detox/Maestro where applicable

## Security

* OWASP-oriented automated testing
* dependency scanners
* SAST/DAST tooling
* container and infrastructure scanners
* targeted authorization/security test suites

## Infrastructure

* Terraform validation
* Kubernetes validation
* Helm validation
* controlled fault-injection tooling
* cloud/provider-native monitoring

Do not introduce multiple overlapping tools without a concrete reason.

---

# SOURCE OF TRUTH

Before modifying or creating tests:

1. Inspect the repository.
2. Inspect existing test suites.
3. Inspect service boundaries.
4. Inspect API contracts.
5. Inspect database schema and migrations.
6. Inspect Redis usage.
7. Inspect event topics and consumers.
8. Inspect queues.
9. Inspect media-processing workers.
10. Inspect search infrastructure.
11. Inspect playback APIs.
12. Inspect subscription/payment integrations.
13. Inspect notification providers.
14. Inspect Kubernetes and Helm.
15. Inspect Terraform.
16. Inspect observability dashboards and metrics.
17. Inspect CI/CD workflows.
18. Inspect existing performance/security tests.

The repository defines current implementation reality.

This prompt defines the advanced validation requirements.

Do not assume a previous AI-generated prompt is available.

Do not design tests around functionality that does not exist merely because it is listed in an architectural document.

When a test reveals a production defect, fix the production implementation where appropriate rather than weakening the test.

---

# QA RESPONSIBILITY

This volume is responsible for production-scale validation.

It must establish:

* baseline performance
* load profiles
* stress profiles
* endurance profiles
* scalability validation
* concurrency testing
* database performance validation
* cache performance validation
* event/queue throughput validation
* media-processing capacity validation
* search performance validation
* recommendation performance validation
* playback authorization performance validation
* frontend performance validation
* mobile performance validation
* security validation
* abuse testing
* resilience testing
* disaster-recovery validation
* backup/restore validation
* deployment validation
* migration validation
* observability validation
* release gates

---

# TEST ENVIRONMENT

Performance, resilience, and destructive validation must run in controlled environments.

Use:

* isolated load environment
* staging
* dedicated performance environment where required
* dedicated recovery environment

Do not point destructive or high-load tests at production unless the test has a documented production-safe design and explicit operational controls.

Never use real customer payment data or production private user data in destructive tests.

---

# WORKLOAD MODEL

Define realistic workload profiles before executing tests.

Model traffic classes such as:

* anonymous browsing
* authentication
* catalog browsing
* search
* autocomplete
* playlist reads
* playlist mutations
* library operations
* playback authorization
* playback session updates
* playback telemetry
* recommendations
* notifications
* subscription APIs
* administration
* media uploads
* media processing
* event consumers

Traffic must reflect realistic relative proportions.

Do not benchmark only the easiest endpoint.

---

# BASELINE PERFORMANCE

Establish repeatable baseline measurements.

Measure at minimum:

* request throughput
* latency percentiles
* error rate
* database latency
* Redis latency
* event publication latency
* queue latency
* search latency
* recommendation latency
* playback authorization latency
* media-processing duration

Report:

* p50
* p90
* p95
* p99
* maximum where useful
* throughput
* resource utilization

Do not rely on averages alone.

---

# API LOAD TESTING

Load-test critical APIs including:

* authentication
* catalog
* search
* playlists
* library
* recommendations
* playback authorization
* playback session operations
* notifications
* subscription status
* administration

Validate:

* latency
* throughput
* error rates
* resource use
* rate limiting
* graceful degradation

Do not generate unrealistic traffic patterns that cannot inform capacity planning.

---

# AUTHENTICATION LOAD TESTING

Test realistic authentication traffic.

Evaluate:

* login bursts
* token refresh
* session restoration
* password-reset traffic
* concurrent refresh behavior

Monitor:

* CPU
* database load
* Redis load
* rate-limit behavior
* latency

Verify that authentication spikes do not destabilize unrelated public catalog traffic.

---

# SEARCH LOAD TESTING

Test:

* common queries
* autocomplete
* high-frequency popular queries
* diverse queries
* result filtering
* pagination

Measure:

* p50/p95/p99 latency
* cluster CPU
* memory
* cache behavior
* shard behavior
* indexing lag

Include mixed read/index workloads.

---

# RECOMMENDATION LOAD TESTING

Test recommendation-serving workloads under:

* cold cache
* warm cache
* high concurrency
* recommendation-service degradation
* fallback behavior

Measure:

* recommendation latency
* cache hit ratio
* downstream dependency pressure
* fallback frequency
* API error rate

Verify that recommendation failures do not cascade into core playback failures.

---

# PLAYBACK AUTHORIZATION LOAD TESTING

Treat playback authorization as a critical latency-sensitive workload.

Test:

* large concurrent authorization bursts
* steady-state concurrency
* subscription-entitlement lookup
* Redis availability
* database load
* repeated session creation

Measure:

* authorization latency
* error rate
* database load
* Redis load
* CPU/memory
* autoscaling response

Verify that playback authorization remains isolated from noncritical analytics workloads.

---

# PLAYBACK TELEMETRY LOAD TESTING

Generate realistic high-volume playback telemetry.

Test:

* start
* pause
* resume
* seek
* skip
* buffering
* completion
* errors

Measure:

* ingestion throughput
* queue/event lag
* processing latency
* storage pressure
* consumer lag

Verify telemetry load does not degrade:

* authentication
* playback authorization
* catalog APIs
* subscriptions

---

# WEBSOCKET LOAD TESTING

Where WebSockets are implemented, test:

* concurrent connections
* connection establishment
* heartbeat
* reconnect
* message fan-out
* collaborative playlist activity
* device-state updates
* notification updates

Measure:

* active connections
* memory
* CPU
* connection latency
* disconnect rate
* message latency
* event-loop pressure

Test reconnect storms.

Do not assume normal connection counts are the only difficult case.

---

# QUEUE THROUGHPUT TESTING

Test worker queues under:

* normal load
* burst load
* sustained backlog
* downstream dependency slowdown
* worker restarts
* scaling events

Measure:

* queue depth
* oldest-job age
* throughput
* retry rate
* worker utilization
* completion latency

Verify queue backlogs recover after load returns to normal.

---

# MEDIA-PROCESSING PERFORMANCE

Use representative media fixtures to test:

* validation
* metadata extraction
* transcoding
* derivative generation
* cleanup

Measure:

* processing duration
* CPU
* memory
* temporary storage
* worker concurrency
* queue age
* throughput

Determine practical worker concurrency without exhausting node resources.

Do not infer production capacity from one media file.

Use a representative sample of media sizes and codecs.

---

# MEDIA ABUSE PERFORMANCE

Test malicious or pathological media scenarios such as:

* oversized files
* malformed containers
* extreme metadata
* unsupported codecs
* unexpectedly long duration
* files engineered to consume disproportionate processing resources

Verify:

* resource limits
* timeouts
* queue controls
* rejection
* cleanup

Media-processing security and performance must be validated together.

---

# DATABASE PERFORMANCE

Evaluate PostgreSQL under representative application workloads.

Measure:

* query latency
* CPU
* memory
* IOPS
* connections
* locks
* transaction duration
* replication lag
* slow queries

Identify:

* N+1 patterns
* full-table scans
* inefficient pagination
* missing indexes
* excessive connection creation
* write amplification

Do not optimize based solely on application-level latency without inspecting database behavior.

---

# DATABASE CONCURRENCY

Stress:

* collaborative playlist edits
* library mutations
* subscription transitions
* media state transitions
* catalog publishing

Validate:

* transaction correctness
* lock contention
* deadlocks
* serialization failures
* retry behavior
* consistency

The system must preserve correctness under concurrency, not merely maintain low latency.

---

# REDIS PERFORMANCE

Test Redis under:

* cache traffic
* playback state traffic
* rate limiting
* BullMQ
* concurrent clients

Measure:

* command latency
* memory
* hit ratio
* evictions
* connections
* replication
* failover behavior

Where separate Redis workloads are architecturally required, prove the isolation materially improves failure behavior.

---

# EVENT-BROKER PERFORMANCE

Test Kafka/Redpanda under representative:

* domain-event volume
* playback telemetry
* analytics volume
* consumer concurrency

Measure:

* producer throughput
* consumer throughput
* partition utilization
* lag
* broker resource usage
* replication health

Test burst traffic.

Verify that analytics traffic cannot starve critical domain-event processing.

---

# SEARCH PERFORMANCE AND CAPACITY

Test:

* query throughput
* index throughput
* mixed read/write
* shard allocation
* recovery after node failure

Measure:

* p95/p99 latency
* CPU
* memory
* heap where applicable
* disk
* segment/index growth
* queue/indexing delay

Perform reindex performance tests using realistic catalog size.

---

# FRONTEND PERFORMANCE

Validate the web client using production-like builds.

Measure:

* startup
* route navigation
* LCP
* INP
* CLS
* JavaScript payload
* memory
* image cost
* API waterfall
* search interaction
* player startup

Test on:

* high-end desktop
* average desktop
* constrained mobile browser
* slower network profiles

Do not optimize only for a high-end developer workstation.

---

# WEB PLAYBACK PERFORMANCE

Measure:

* time from play action to first audio
* media authorization latency
* CDN latency
* buffering
* startup failure
* recovery time

Separate:

* API latency
* media-access generation
* CDN delivery
* browser media startup

This decomposition is required to identify the actual bottleneck.

---

# MOBILE PERFORMANCE

Test representative iOS and Android devices.

Measure:

* cold startup
* warm startup
* navigation
* scrolling
* memory
* CPU
* battery impact where practical
* playback startup
* notification handling
* background behavior
* download performance where applicable

Test both recent and realistically constrained devices.

---

# MOBILE PLAYBACK PERFORMANCE

Measure:

* time to first audio
* buffering
* memory
* CPU
* audio interruptions
* recovery
* background behavior
* battery consumption

Verify that high-frequency telemetry does not materially degrade playback.

---

# STRESS TESTING

Push individual systems beyond expected normal load until controlled degradation occurs.

Stress:

* API
* search
* Redis
* database
* event broker
* queues
* workers
* WebSockets
* media processing

Record:

* saturation point
* failure mode
* recovery behavior
* data integrity
* user-visible behavior

Do not define "pass" as surviving infinite load.

The objective is to identify controlled capacity boundaries and safe degradation.

---

# SOAK / ENDURANCE TESTING

Run sustained workloads over a meaningful period.

Monitor for:

* memory leaks
* connection leaks
* queue growth
* event lag
* cache degradation
* database bloat
* file descriptor exhaustion
* log growth
* resource fragmentation
* progressive latency increases

Compare beginning and end-of-test metrics.

A system that survives a short spike may still fail during prolonged operation.

---

# AUTOSCALING VALIDATION

Validate scaling behavior for:

* API pods
* workers
* media processors
* event consumers
* search-related workloads where supported
* Kubernetes nodes

Test:

* scale-up latency
* scale-down behavior
* load redistribution
* cold-start effects
* resource limits
* database connection pressure

Verify autoscaling does not create a feedback loop that worsens an overload.

---

# RATE-LIMIT TESTING

Validate that rate limits:

* trigger at the intended boundaries
* distinguish clients appropriately
* recover after cooldown
* cannot be bypassed trivially
* do not block legitimate traffic unnecessarily

Test:

* authentication
* search
* autocomplete
* playback authorization
* uploads
* telemetry
* administration

Validate behavior when Redis/rate-limit infrastructure is degraded.

---

# SECURITY TESTING

Perform structured security validation across the application.

Test:

* authentication bypass
* authorization bypass
* IDOR
* privilege escalation
* injection
* XSS
* CSRF where applicable
* SSRF-sensitive features
* command injection-sensitive features
* unsafe uploads
* path traversal
* token leakage
* session abuse
* replay
* rate-limit bypass
* webhook forgery
* malicious deep links

Use both automated scanning and targeted functional tests.

---

# API FUZZ TESTING

Fuzz suitable API boundaries with:

* malformed JSON
* unexpected types
* boundary values
* oversized strings
* nested structures
* invalid identifiers
* invalid enum values
* large arrays
* duplicate fields where applicable

Verify the server:

* rejects invalid input
* remains stable
* does not leak internal errors
* does not consume unbounded resources

Do not fuzz endpoints against production data stores.

---

# MEDIA SECURITY TESTING

Attempt to bypass media protection.

Test:

* direct bucket access
* expired signed URLs
* modified signed URLs
* reused media credentials
* access from unauthorized accounts
* cross-user resource access
* withdrawn media
* expired subscription
* revoked session

Verify protected media cannot be obtained through alternate infrastructure paths.

---

# WEB SECURITY TESTING

Test:

* reflected XSS
* stored XSS through user-controlled metadata
* unsafe HTML
* open redirect
* malicious deep links
* sensitive data in local storage
* sensitive information in URL parameters
* cache leakage
* authorization UI bypass

Test using both browser automation and API-level requests.

---

# MOBILE SECURITY TESTING

Test:

* insecure credential storage
* token leakage
* deep-link manipulation
* notification data leakage
* unauthorized private screen access
* unsafe local files
* downloaded-media access
* logout data remnants
* account-switching leakage

Inspect release builds rather than debug builds where possible.

---

# DEPENDENCY AND SUPPLY-CHAIN TESTING

Run:

* package vulnerability scans
* dependency lockfile validation
* container scans
* infrastructure scans
* secret scans
* license/policy checks where required

Prioritize exploitable production-impacting findings.

Do not suppress vulnerabilities permanently without documented justification.

---

# WEBHOOK SECURITY TESTING

Test external webhooks using:

* invalid signatures
* missing signatures
* stale timestamps
* replayed events
* duplicate events
* malformed payloads
* incorrect event types
* oversized payloads

Verify:

* invalid requests are rejected
* duplicates are harmless
* business state remains correct
* abuse is rate limited
* security events are observable

---

# DISASTER-RECOVERY TESTING

Validate practical recovery paths for:

* PostgreSQL
* Redis loss
* Kafka/Redpanda failure
* search loss
* object storage recovery
* Kubernetes cluster loss
* regional failure where infrastructure supports it

Measure actual:

* recovery time
* restoration completeness
* data loss
* manual intervention
* dependency ordering

Compare results with declared RPO/RTO targets.

Do not claim DR readiness based solely on written runbooks.

---

# BACKUP RESTORE TESTING

Perform scheduled restoration tests.

Validate:

* database backups restore
* point-in-time recovery where configured
* object storage recovery
* search snapshot restoration
* infrastructure state recovery
* configuration recovery

Verify restored systems can actually serve representative application functionality.

---

# DATABASE FAILOVER TESTING

Where managed PostgreSQL failover exists:

* trigger or simulate controlled failover
* observe application behavior
* verify connection recovery
* verify transaction behavior
* verify read/write routing
* measure downtime
* inspect errors and retries

Verify applications do not cache stale database endpoints indefinitely.

---

# REDIS FAILOVER TESTING

Validate:

* connection recovery
* cache degradation
* playback state behavior
* rate limiting
* queue continuity where supported

Critical business state must remain correct through Redis failure.

---

# EVENT-BROKER FAILURE TESTING

Simulate:

* broker unavailability
* producer failure
* consumer restart
* partition issue
* lag
* replay

Verify:

* outbox records remain recoverable
* consumers resume
* duplicate processing remains safe
* critical transactional state remains correct

---

# SEARCH FAILURE TESTING

Destroy or isolate search availability in controlled environments.

Verify:

* catalog writes continue
* APIs return predictable failure/degraded states
* indexing catches up after recovery
* no authorization bypass occurs
* search consumers recover

---

# DEPLOYMENT VALIDATION

Test production deployment processes using realistic release candidates.

Validate:

* immutable artifacts
* image verification
* migrations
* rollout
* readiness
* smoke tests
* observability
* rollback

Do not declare a deployment successful solely because Kubernetes reports successful pods.

---

# ROLLBACK TESTING

Perform controlled rollback tests.

Test:

* application rollback
* configuration rollback
* failed rollout
* progressive rollout reversal
* worker rollback

Explicitly evaluate database migration compatibility.

Never perform an application rollback across an incompatible database schema without a deliberate migration strategy.

---

# MIGRATION SAFETY

For every production database migration category, evaluate:

* lock behavior
* execution time
* backward compatibility
* rolling-deployment compatibility
* rollback feasibility
* replication implications

For large-table changes, validate using representative data volumes.

Avoid assuming development-scale migration timing is representative.

---

# OBSERVABILITY VALIDATION

Verify that observability can actually detect failures.

Intentionally trigger controlled test failures and confirm:

* metrics change
* logs appear
* traces connect
* dashboards show impact
* alerts fire
* correlations are usable

Test:

* API failure
* database latency
* queue backlog
* search failure
* media-processing failures
* authentication abuse

An alert that exists but cannot reliably detect the intended failure is not complete.

---

# SLO VALIDATION

For each declared SLO:

* identify the source metric
* verify calculation
* verify aggregation
* verify alerting
* verify error-budget behavior

Do not define an SLO that cannot be measured accurately.

---

# CAPACITY LIMITS

Determine practical limits for:

* API throughput
* concurrent playback authorization
* WebSocket connections
* search QPS
* recommendation QPS
* queue throughput
* media-processing concurrency
* database connections
* Redis memory
* event throughput

Document:

* tested capacity
* observed bottleneck
* safe operating range
* degradation point
* scaling action

Do not extrapolate linearly without engineering evidence.

---

# RELEASE QUALITY GATES

Define release gates appropriate to the repository.

A production release should require, as applicable:

* type checking
* unit tests
* integration tests
* API contract tests
* critical E2E tests
* security scans
* migration validation
* container scans
* infrastructure validation
* performance regression checks
* accessibility checks
* mobile build validation

High-risk releases should receive stronger gates.

Do not make every test equally mandatory if cost and signal differ; classify gates according to risk.

---

# PERFORMANCE REGRESSION GATES

Establish thresholds for critical paths based on measured project baselines.

Guard against material regressions in:

* API latency
* search latency
* playback authorization
* web startup
* mobile startup
* time to first audio
* queue processing
* media-processing duration

Do not introduce arbitrary thresholds before collecting credible baselines.

---

# SECURITY RELEASE GATES

Block releases for critical security findings such as:

* known exploitable dependency vulnerabilities
* authentication bypass
* authorization bypass
* secret exposure
* unsafe production configuration
* public access to protected media
* invalid webhook verification
* critical infrastructure exposure

Exceptions must be documented, time-bounded, and approved through the project's operational process.

---

# TEST DATA SAFETY

Performance, security, and resilience tests must not accidentally expose:

* real user data
* credentials
* payment information
* private listening history
* private playlists
* production media credentials

Use synthetic or appropriately sanitized datasets.

---

# TEST REPORTING

Generate reproducible engineering reports containing:

* test objective
* environment
* software version
* infrastructure configuration
* workload profile
* duration
* concurrency
* dataset size
* metrics
* findings
* bottlenecks
* failures
* recovery behavior
* recommendations
* pass/fail status

Do not report a test as passing when it merely completed without crashing.

---

# DEFECT CLASSIFICATION

Classify discovered defects by impact, considering:

* security
* data integrity
* financial correctness
* availability
* user experience
* performance
* recoverability
* observability

Critical defects should block production release unless a formally approved mitigation exists.

---

# FLAKY PERFORMANCE TESTS

Do not hide performance variability by averaging away anomalies.

Investigate:

* infrastructure noise
* garbage collection
* network variance
* cold starts
* autoscaling
* cache state
* external providers

Use repeated runs where appropriate.

Document environmental variance.

---

# RESILIENCE TESTING RULES

Resilience experiments must:

* use controlled environments
* have clear stop conditions
* have rollback/recovery procedures
* preserve test data integrity
* avoid uncontrolled customer impact
* produce actionable telemetry

Do not intentionally cause destructive production failures without explicit safeguards.

---

# QA CI/CD INTEGRATION

Integrate advanced quality validation into CI/CD in staged form.

Examples:

## Pull request

* lint
* unit tests
* targeted integration tests
* static security checks
* schema validation

## Main branch

* broader integration
* contract tests
* critical E2E
* migration validation

## Release candidate

* comprehensive E2E
* security suite
* performance regression
* build validation
* infrastructure validation

## Production qualification

* release smoke tests
* deployment verification
* rollback readiness
* observability verification

The exact pipeline must reflect actual repository capabilities.

---

# QUALITY DASHBOARD

Create or maintain a quality dashboard showing:

* test success
* flaky tests
* coverage where useful
* security findings
* performance regressions
* failed deployments
* SLO state
* open critical defects
* release qualification status

Do not optimize the dashboard for vanity metrics.

---

# DOCUMENTATION

Document:

* performance methodology
* workload models
* benchmark execution
* capacity testing
* security testing
* DR testing
* backup restoration
* resilience testing
* release gates
* SLO validation
* defect classification
* test environments
* operational safety rules

Documentation must include exact commands/tools supported by the repository.

Do not document tests that cannot actually be run.

---

# IMPLEMENTATION BOUNDARIES

This QA volume owns advanced production validation.

Implement:

* load tests
* stress tests
* soak tests
* scalability tests
* capacity tests
* WebSocket load tests
* playback performance tests
* media-processing performance tests
* frontend performance tests
* mobile performance tests
* API fuzzing
* security tests
* webhook security tests
* media-access security tests
* resilience tests
* backup/restore validation
* disaster-recovery validation
* deployment/rollback validation
* migration safety tests
* observability validation
* SLO validation
* release quality gates
* quality reporting

Do not invent benchmark results.

Do not modify production behavior simply to make a performance test pass.

When a real performance, resilience, or security defect is discovered, fix the underlying implementation or infrastructure according to the repository's architecture.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before changing files:

1. inspect existing QA tooling
2. inspect CI/CD
3. inspect performance tests
4. inspect security tests
5. inspect infrastructure validation
6. inspect observability
7. inspect deployment automation
8. identify available staging/test environments
9. identify current metrics and SLOs
10. identify missing release gates

Then:

1. establish baseline benchmarks
2. build representative workloads
3. implement load/stress/soak testing
4. implement performance regression checks
5. implement security validation
6. implement resilience testing
7. implement backup/DR validation
8. implement deployment/rollback checks
9. implement observability validation
10. define release gates
11. integrate CI/CD where appropriate
12. execute tests
13. analyze findings
14. remediate genuine defects
15. re-run affected validation
16. update documentation

Do not skip execution and claim validation based only on test definitions.

---

# COMPLETION CRITERIA

This QA task is complete only when:

* realistic workload models exist
* baseline performance is measured
* critical APIs have load coverage
* playback authorization has scale testing
* search has scale testing
* recommendation serving has scale testing
* telemetry and queues have throughput testing
* media processing has capacity testing
* frontend performance is measured
* mobile performance is measured
* stress testing is implemented
* endurance testing is implemented
* autoscaling is validated
* security testing covers critical threats
* media protection is tested
* webhook security is tested
* dependency failures are tested
* backup restoration is verified
* disaster recovery is exercised
* database failover is tested where supported
* event-broker recovery is tested where supported
* deployments are validated
* rollback is validated
* migration safety is validated
* observability can detect controlled failures
* SLO calculations are verified
* practical capacity limits are documented
* release gates are integrated
* quality reports are reproducible
* no critical quality capability is intentionally incomplete

Do not declare production readiness merely because the tests exist.

Production readiness requires execution, evidence, analysis, and remediation of material failures.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* workload profiles created
* benchmark suites created
* baseline results actually measured
* load/stress/soak tests executed
* scalability findings
* capacity findings
* database performance findings
* Redis findings
* event-broker findings
* queue findings
* media-processing findings
* search findings
* recommendation findings
* web performance findings
* mobile performance findings
* security findings
* resilience findings
* backup/restore results
* disaster-recovery results
* deployment/rollback results
* migration validation results
* observability validation results
* SLO validation results
* release gates added
* defects discovered
* defects remediated
* remaining risks
* compatibility considerations
* unresolved issues, if any

The report must distinguish:

* measured results
* inferred results
* unexecuted validation
* environmental limitations

Never invent numbers.

Never claim a performance target was met without measured evidence.

Never claim disaster recovery works without an actual restoration or controlled validation.

---

# FINAL INSTRUCTION

Validate the music-streaming platform as a production system under realistic pressure and failure.

Performance must be measured rather than assumed.

Capacity must be demonstrated rather than guessed.

Security must be tested at both functional and infrastructure boundaries.

Playback must remain reliable under high concurrency.

Media processing must remain controlled under pathological inputs.

Search and recommendations must degrade safely.

Financial and entitlement systems must preserve correctness under retries and provider failures.

Infrastructure must recover from realistic component failures.

Backups must actually restore.

Deployments must actually roll out and roll back safely.

Observability must actually detect controlled failures.

Release gates must use evidence rather than arbitrary checkboxes.

When validation exposes a genuine defect, fix the underlying production implementation or infrastructure and re-run the affected tests.

The resulting QA system must provide credible, reproducible evidence that the global music-streaming platform is secure, scalable, resilient, observable, and suitable for production operation at large scale.

Prompt sequence complete.
