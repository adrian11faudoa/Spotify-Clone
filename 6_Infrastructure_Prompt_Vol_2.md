# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — INFRASTRUCTURE VOLUME 2

## ROLE

Act as the complete senior infrastructure engineering organization responsible for implementing the advanced production deployment, autoscaling, media-delivery, workload isolation, observability, security, disaster-recovery, and operational reliability capabilities of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

Operate as:

* Principal Software Architect
* DevOps Engineer
* Cloud Architect
* Distributed Systems Engineer
* Security Engineer
* Reliability Engineer
* Performance Engineer
* Database Architect
* QA Engineer
* Technical Writer

This prompt defines an independent infrastructure implementation task.

Do not provide a tutorial.

Do not provide pseudo-code.

Do not create placeholder infrastructure.

Do not create fake cloud resources.

Do not leave TODO/FIXME infrastructure gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and integrate the infrastructure implementation with the actual repository state.

Implement the requested infrastructure completely, with production-grade deployment safety, scalability, reliability, security, observability, backup/recovery, disaster recovery, testing, and documentation.

---

# PROJECT

Build the advanced production infrastructure capabilities for an original global music streaming platform.

The platform operates a web application, mobile clients, NestJS backend services, asynchronous workers, media-processing workloads, search, recommendations, subscriptions, notifications, analytics, administration, and high-scale audio delivery.

This infrastructure volume is responsible for:

* production Kubernetes workload deployment
* Helm release architecture
* application autoscaling
* queue-driven worker autoscaling
* media-processing workload isolation
* secure CDN/media delivery
* advanced object-storage lifecycle
* database scaling and operational hardening
* Redis workload isolation
* Kafka/Redpanda operational hardening
* search-cluster operations
* observability dashboards and alerts
* centralized logging and tracing
* deployment strategies
* progressive delivery
* rollback
* security hardening
* backup verification
* disaster recovery
* operational runbooks
* resilience testing
* capacity planning
* infrastructure cost controls

The implementation must integrate with the actual infrastructure already present in the repository.

Do not replace functioning infrastructure merely to introduce a different style.

---

# TECHNOLOGY DIRECTION

Use:

## Cloud

Use AWS as the baseline when the repository does not already establish an equivalent provider.

## Infrastructure as Code

* Terraform

## Containers

* Docker

## Orchestration

* Kubernetes

## Kubernetes Packaging

* Helm

## CI/CD

* GitHub Actions

## Observability

* OpenTelemetry
* Prometheus
* Grafana
* Loki or an equivalent log aggregation system
* Tempo or an equivalent tracing system
* cloud-native monitoring where useful

## Delivery

Use a CDN for production media delivery.

Use managed infrastructure for durable state whenever operationally justified.

Use the repository's existing versions and resource conventions whenever compatible.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect Terraform modules and environment roots.
3. Inspect Kubernetes manifests.
4. Inspect Helm charts.
5. Inspect Dockerfiles.
6. Inspect GitHub Actions.
7. Inspect application health endpoints.
8. Inspect backend deployment configuration.
9. Inspect worker deployment configuration.
10. Inspect media-processing configuration.
11. Inspect Redis/BullMQ configuration.
12. Inspect Kafka/Redpanda configuration.
13. Inspect search configuration.
14. Inspect object storage and CDN configuration.
15. Inspect observability configuration.
16. Inspect backup and recovery configuration.
17. Inspect infrastructure documentation.

The repository defines what currently exists.

This prompt defines what this infrastructure volume must achieve.

Do not assume that previous AI-generated prompts or conversations are available.

Preserve compatible resources and deployment behavior.

Do not destroy or recreate production resources unnecessarily.

---

# INFRASTRUCTURE RESPONSIBILITY

This volume owns:

* Kubernetes application workloads
* workload-specific Helm charts
* backend deployments
* worker deployments
* media-processing deployments
* search/indexing workers
* notification workers
* analytics workers
* autoscaling
* queue-aware scaling
* pod disruption strategy
* rollout strategy
* CDN hardening
* media origin protection
* storage lifecycle
* production database operational configuration
* Redis workload isolation
* event-broker operational configuration
* search-cluster operations
* observability dashboards
* alerts
* logging
* tracing
* security policies
* backup validation
* disaster recovery
* resilience testing
* capacity planning
* cost optimization

---

# KUBERNETES WORKLOAD ARCHITECTURE

Deploy production workloads using clearly separated workload classes.

At minimum evaluate:

* web application
* API application
* real-time/WebSocket application where needed
* general background workers
* media-processing workers
* event consumers
* search-indexing workers
* notification workers
* analytics workers
* scheduled maintenance jobs

Each deployment must define:

* replicas
* resource requests
* resource limits
* health probes
* termination grace period
* security context
* service account
* configuration
* secret references
* topology behavior
* autoscaling policy

Do not create a single generic deployment for materially different workloads.

---

# HELM ARCHITECTURE

Create maintainable Helm charts or chart structures for production application workloads.

Charts must support:

* environment-specific values
* immutable application image references
* resource configuration
* autoscaling
* secrets integration
* config maps
* service accounts
* ingress
* probes
* PodDisruptionBudgets
* topology constraints
* security contexts
* network-policy integration

Avoid duplicating complete charts for every environment.

Use values and overlays where practical.

Do not place production secrets directly into committed Helm values.

---

# APPLICATION DEPLOYMENTS

Deploy the backend as a production workload.

Configure:

* multiple replicas
* rolling deployment
* readiness probes
* liveness probes
* startup probes where appropriate
* graceful termination
* pod disruption protection
* anti-affinity or topology spread
* autoscaling
* secure service account
* network policy

Do not expose internal ports unnecessarily.

Ensure WebSocket-capable services have appropriate load-balancing and timeout behavior.

---

# WEB DEPLOYMENT

Deploy the web application using the repository's selected Next.js hosting architecture.

If Next.js runs in Kubernetes, support:

* multiple replicas
* readiness/liveness
* rolling deployment
* CDN-compatible static delivery
* caching
* secure environment configuration

If the repository uses a managed web-hosting platform instead, preserve that architecture and integrate it with the rest of the infrastructure rather than moving it without justification.

---

# WORKER ARCHITECTURE

Deploy worker classes independently.

At minimum separate workloads with materially different operational profiles:

* lightweight event consumers
* notification workers
* search-indexing workers
* analytics processing
* general jobs
* media processing

Define per-worker:

* concurrency
* resource profile
* queue/topic assignment
* autoscaling
* retry/failure behavior
* graceful shutdown

A media-processing backlog must not prevent the API from receiving requests.

---

# MEDIA-PROCESSING INFRASTRUCTURE

Provide dedicated infrastructure for FFmpeg/media-processing workloads.

Support:

* CPU-intensive node pools
* sufficient ephemeral storage
* memory limits
* job-level resource requests
* controlled concurrency
* queue-driven autoscaling
* graceful termination
* temporary storage cleanup

Prevent untrusted media from exhausting node resources through uncontrolled processing.

Use resource limits and workload quotas.

---

# QUEUE-BASED AUTOSCALING

Implement autoscaling for asynchronous workloads where useful.

Scale workers using signals such as:

* queue depth
* queue age
* processing latency
* CPU/memory
* event-consumer lag

Do not use CPU-only autoscaling for workloads whose primary bottleneck is backlog.

Scale down conservatively enough to avoid thrashing.

Do not allow autoscaling to overwhelm:

* PostgreSQL
* Redis
* Kafka/Redpanda
* search
* external providers

---

# POD DISRUPTION STRATEGY

Configure PodDisruptionBudgets for critical workloads.

Ensure planned infrastructure events do not remove all healthy replicas.

Combine:

* PodDisruptionBudgets
* topology spread
* anti-affinity
* rolling deployment limits

Do not create PDBs so restrictive that cluster maintenance becomes impossible.

---

# NETWORK POLICIES

Implement Kubernetes network policies where supported.

Restrict communication between:

* public-facing workloads
* backend
* workers
* media processors
* search consumers
* administrative workloads
* observability components

Allow only required connectivity.

Do not create an all-to-all cluster network as the production default.

---

# SERVICE ACCOUNTS AND IAM

Every workload must use an appropriate service account.

Map workload identities to cloud permissions.

Permissions must follow least privilege.

Examples:

* backend may access selected secrets
* media workers may access specific object-storage prefixes
* indexing workers may access search and event topics
* notification workers may access notification secrets
* analytics workers may access analytics destinations

Do not grant every workload the same cloud role.

---

# SECRET DELIVERY

Integrate Kubernetes with the selected secret-management system.

Support:

* secret rotation
* versioning
* controlled access
* workload-specific permissions
* auditability

Where possible, avoid storing long-lived secret material as ordinary Kubernetes Secret data.

Applications must not require image rebuilds to rotate secrets.

---

# CONFIGURATION PROMOTION

Separate configuration from image artifacts.

Promote the same immutable application artifact through:

* development
* staging
* production

Inject environment-specific:

* endpoints
* feature settings
* resource settings
* secrets
* logging levels

Do not rebuild code solely to change environment configuration.

---

# DEPLOYMENT STRATEGY

Implement safe rolling deployments.

Support:

* max unavailable
* max surge
* readiness gates
* startup protection
* rollback
* failed-deployment detection

A deployment must not be considered successful merely because Kubernetes accepted the manifest.

Verify:

* healthy replicas
* readiness
* error rate
* application smoke tests

---

# PROGRESSIVE DELIVERY

Where production risk warrants it, support progressive rollout strategies such as:

* canary
* blue/green
* weighted traffic

Use progressive delivery especially for:

* backend
* playback authorization
* media-processing changes
* critical worker changes

Do not introduce complex progressive deployment tooling without operational justification.

---

# ROLLBACK

Implement deterministic rollback procedures.

Rollback must restore:

* application image
* compatible configuration
* relevant Helm release
* traffic routing where progressive delivery is used

Database migrations must be designed separately because application rollback cannot automatically undo incompatible data migrations.

Document migration compatibility requirements.

---

# DATABASE OPERATIONAL HARDENING

Harden PostgreSQL infrastructure for production workloads.

Support:

* multi-AZ
* automated backups
* point-in-time recovery
* monitoring
* maintenance windows
* failover
* read replicas where justified
* connection pooling
* parameter tuning based on measured workloads

Do not create replicas solely for appearance.

Document which workloads may use replicas and their consistency expectations.

---

# DATABASE CAPACITY

Monitor:

* CPU
* memory
* storage
* IOPS
* connections
* locks
* replication lag
* transaction age
* slow queries

Define scaling triggers.

Avoid reacting to one transient metric without contextual evidence.

---

# DATABASE CONNECTION GOVERNANCE

Coordinate connection counts across:

* API replicas
* worker replicas
* admin jobs
* migration jobs

Autoscaling must account for the database connection ceiling.

Use managed pooling/proxy infrastructure where appropriate.

Do not allow every new pod to create an unlimited connection pool.

---

# REDIS OPERATIONAL HARDENING

Separate or logically isolate Redis workloads for:

* cache
* playback state
* BullMQ
* rate limiting

Where one Redis cluster is used, enforce:

* key namespaces
* memory limits
* TTLs
* eviction policy suited to workload
* monitoring

Where workload contention becomes unsafe, use separate Redis deployments.

Do not allow large queue backlogs to evict latency-sensitive application state without mitigation.

---

# REDIS CAPACITY MONITORING

Monitor:

* memory
* hit ratio
* evictions
* command latency
* connections
* replication
* failovers
* fragmentation
* queue-related pressure

Create alerts for conditions that threaten critical application behavior.

---

# KAFKA/REDPANDA OPERATIONS

Harden the event platform for production.

Support:

* replication
* partition planning
* retention
* consumer groups
* producer/consumer authentication
* encryption
* monitoring
* lag detection
* controlled topic configuration

Define operational topic classes for:

* domain events
* analytics
* playback telemetry
* system events

Do not put unrelated high-volume workloads into one unbounded topic.

---

# EVENT BROKER CAPACITY

Monitor:

* broker CPU
* disk
* network throughput
* partition distribution
* producer latency
* consumer lag
* under-replicated partitions

Define alert thresholds appropriate to the workload.

Plan partition growth deliberately.

Do not over-partition without a scaling reason because it increases operational complexity.

---

# SEARCH OPERATIONS

Harden Elasticsearch/OpenSearch.

Support:

* node redundancy
* shard/replica strategy
* storage scaling
* snapshot lifecycle
* index lifecycle management
* health monitoring
* controlled upgrades

Avoid oversized shards.

Do not place every document type into one giant index if isolation and lifecycle requirements materially differ.

---

# SEARCH REINDEXING INFRASTRUCTURE

Provide operational infrastructure for full and partial reindexing.

Support:

* versioned indexes
* aliases
* rebuild
* backfill
* validation
* controlled alias switching
* rollback

Reindexing must not require stopping transactional catalog operations.

---

# OBJECT-STORAGE LIFECYCLE

Implement lifecycle policies for:

* abandoned uploads
* temporary processing artifacts
* old media variants
* old source files where policy permits
* deleted assets
* stale derivatives

Lifecycle rules must not accidentally delete active production media.

Test lifecycle assumptions against object naming/versioning strategy.

---

# CDN HARDENING

Harden CDN behavior for protected audio and artwork.

Support:

* TLS
* origin access control
* signed requests/cookies/URLs where required
* appropriate cache policies
* cache-key controls
* origin failover where appropriate
* access logging
* invalidation policy

Do not cache personalized or authorization-sensitive responses under publicly shared cache keys.

---

# MEDIA DELIVERY PERFORMANCE

Optimize media delivery for high concurrency.

Consider:

* edge caching
* regional origins
* correct content headers
* byte-range requests where supported
* connection reuse
* origin scaling
* cache-hit ratio
* bitrate/variant strategy

Do not route high-volume media bytes through Kubernetes API pods unnecessarily.

---

# MEDIA ORIGIN PROTECTION

Ensure protected media cannot be downloaded directly from object storage.

Validate:

* private bucket policies
* origin access
* signed-access enforcement
* access expiration
* policy boundaries

Attempt to identify bypass paths during infrastructure validation.

---

# OBSERVABILITY

Expand the observability platform into a production operational system.

Provide:

* service dashboards
* infrastructure dashboards
* SLO dashboards
* alert rules
* log aggregation
* trace collection
* capacity dashboards
* deployment telemetry

Dashboards must be actionable.

---

# SERVICE LEVEL OBJECTIVES

Define SLOs for critical capabilities such as:

* API availability
* API latency
* playback authorization
* search availability
* search latency
* notification processing
* media-processing completion
* event-consumer lag
* queue latency

Define:

* target
* measurement
* window
* alerting threshold
* error-budget interpretation

Do not define unrealistic targets that cannot be supported by the architecture.

---

# PLAYBACK OBSERVABILITY

Provide infrastructure dashboards/alerts for:

* playback authorization latency
* authorization failures
* CDN origin failures
* media-access generation errors
* active sessions where observable
* playback backend errors
* regional degradation

Time-sensitive playback signals must be distinguishable from low-priority analytics problems.

---

# QUEUE OBSERVABILITY

Provide dashboards for:

* queue depth
* oldest job age
* throughput
* retries
* failed jobs
* worker utilization
* processing duration

Create alerts for sustained backlog rather than momentary queue spikes.

---

# EVENT-LAG OBSERVABILITY

Track:

* consumer lag
* dead-letter volume
* processing latency
* retry rate
* partition health

Identify consumers whose lag threatens user-visible correctness.

---

# DEPLOYMENT OBSERVABILITY

Every deployment should expose:

* version
* environment
* rollout state
* replica health
* error rate
* latency
* rollback status

Correlate deployments with production incidents.

---

# LOG RETENTION

Define environment-specific log retention.

Production logs should support:

* incident investigation
* security investigation
* troubleshooting

Do not retain unlimited logs by default.

Avoid deleting logs so aggressively that meaningful operational debugging becomes impossible.

---

# SECURITY OBSERVABILITY

Monitor:

* authentication abuse
* WAF events
* unusual traffic
* privileged infrastructure changes
* IAM changes
* secret access
* failed deployments
* unexpected public exposure
* storage-policy changes

Integrate cloud audit logs into centralized security monitoring where appropriate.

---

# VULNERABILITY MANAGEMENT

Implement:

* container image scanning
* dependency scanning
* Terraform scanning
* Kubernetes configuration scanning
* secret scanning

Define:

* severity classes
* blocking thresholds
* remediation ownership
* exception process

Do not permanently suppress findings without an explicit documented reason.

---

# SUPPLY-CHAIN SECURITY

Harden build and deployment provenance.

Where supported, implement:

* signed container images
* provenance metadata
* immutable artifacts
* restricted CI permissions
* protected branches/environments
* dependency lockfiles
* reusable trusted workflows

CI must not receive unrestricted production credentials.

---

# CI/CD SECURITY

GitHub Actions must:

* use least-privilege permissions
* protect production environments
* avoid long-lived cloud secrets where OIDC is available
* isolate untrusted pull-request workflows
* prevent secret exposure in logs
* verify deployment artifacts

Do not permit arbitrary pull-request code to deploy to production.

---

# BACKUP VALIDATION

Backups must be tested.

Implement or document automated verification for:

* database restore
* search restore
* object-storage recovery
* Terraform-state recovery
* critical configuration recovery

A successful backup job alone is insufficient evidence of recoverability.

---

# DISASTER RECOVERY

Implement a practical disaster-recovery architecture.

Cover:

* regional failure
* database failure
* object-storage corruption
* Kubernetes-cluster failure
* event-broker failure
* Redis loss
* search loss
* CI/CD failure
* compromised infrastructure credentials

Define which components are:

* recreated
* restored
* replicated
* rebuilt from source

Do not treat Redis cache data as irreplaceable durable state.

---

# DR DATABASE STRATEGY

Define production database recovery with explicit:

* RPO
* RTO
* backup
* replication
* failover
* restore

Where cross-region replication is used, document consistency and failover semantics.

Do not fail over blindly without understanding application compatibility.

---

# DR OBJECT-STORAGE STRATEGY

For critical media assets, evaluate:

* cross-region replication
* versioning
* lifecycle
* delete protection
* recovery procedures

Distinguish:

* source assets
* processed delivery assets
* temporary assets

Temporary artifacts need not necessarily receive identical DR guarantees as canonical source media.

---

# DR EVENT-PLATFORM STRATEGY

Define recovery for Kafka/Redpanda.

Support appropriate:

* retention
* replication
* snapshots/backup where supported
* topic recreation
* consumer recovery
* offset recovery

Do not make unrecoverable ephemeral events a hidden requirement for transactional correctness.

---

# DR SEARCH STRATEGY

Search indexes are derived state.

Design recovery so they can be:

* restored from snapshots
* rebuilt from authoritative catalog data
* recreated through event/backfill pipelines

Do not require search backups to be the only path to recovery.

---

# INCIDENT RESPONSE

Provide production incident runbooks for:

* API outage
* database degradation
* Redis outage
* event-broker outage
* search outage
* media origin outage
* CDN outage
* payment-provider outage
* notification-provider outage
* bad deployment
* Kubernetes node failure
* region failure
* security incident

Runbooks must contain actionable steps and rollback/recovery commands appropriate to the actual infrastructure.

Do not document commands that are not compatible with the repository's tooling.

---

# RESILIENCE TESTING

Implement safe infrastructure resilience tests where the environment permits.

Test scenarios such as:

* pod termination
* node disruption
* worker crash
* Redis failover
* broker restart
* search-node failure
* database failover
* CDN/origin degradation

Use controlled nonproduction environments before production experiments.

Do not conduct destructive tests against production without explicit safeguards and approval mechanisms.

---

# CAPACITY PLANNING

Define capacity models for:

* API requests
* WebSocket connections
* concurrent playback authorization
* playback telemetry
* search queries
* event throughput
* queue jobs
* media processing
* database connections
* Redis memory
* object storage
* CDN bandwidth

Document assumptions.

Use measurable signals for scaling decisions.

Avoid using arbitrary infrastructure sizes without workload justification.

---

# COST OPTIMIZATION

Optimize cost without compromising production requirements.

Consider:

* autoscaling
* spot capacity for interruptible media workloads where safe
* storage lifecycle
* CDN cache hit rate
* database sizing
* worker scheduling
* log retention
* nonproduction scheduling
* unused resource detection

Do not use spot instances for workloads where interruption could cause unacceptable data loss without a recovery strategy.

---

# ENVIRONMENT GOVERNANCE

Enforce:

* required tags
* naming standards
* owner metadata
* environment metadata
* cost allocation
* security classification

Prevent accidental creation of production resources without required metadata.

---

# OPERATIONAL DOCUMENTATION

Update documentation for:

* Helm deployment
* autoscaling
* workload classes
* media workers
* queue scaling
* deployment/rollback
* database operations
* Redis operations
* event-broker operations
* search operations
* CDN/media delivery
* observability
* SLOs
* backup/restore
* DR
* incident response
* resilience testing
* capacity planning
* cost controls

Documentation must describe actual infrastructure.

---

# IMPLEMENTATION BOUNDARIES

This infrastructure volume owns advanced production operations.

Implement:

* Kubernetes workloads
* Helm
* autoscaling
* worker isolation
* queue scaling
* network policies
* workload IAM
* secret integration
* media-delivery hardening
* CDN configuration
* database operations
* Redis operations
* event-broker operations
* search operations
* observability
* SLOs
* security scanning
* supply-chain security
* backup verification
* disaster recovery
* incident runbooks
* resilience testing
* capacity planning
* cost controls

Do not implement:

* application business logic
* frontend features
* mobile features
* database schema migrations
* media-processing application code

Provide only the infrastructure required to operate those workloads reliably.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before modifying files:

1. inspect current infrastructure
2. inspect Terraform modules
3. inspect Helm charts
4. inspect Kubernetes resources
5. inspect CI/CD
6. inspect application and worker containers
7. inspect cloud resources
8. inspect observability
9. inspect backup/recovery
10. identify production constraints

Then:

1. implement workload Helm architecture
2. implement deployments and scaling
3. isolate heavy workloads
4. harden storage and CDN
5. harden databases and stateful platforms
6. implement observability and SLOs
7. implement security/supply-chain controls
8. implement backup verification
9. implement DR capabilities
10. implement runbooks and resilience testing
11. validate deployments
12. update documentation

Do not duplicate resources unnecessarily.

Do not destroy production state merely to simplify Terraform.

---

# COMPLETION CRITERIA

This infrastructure task is complete only when:

* application workloads are deployable through reproducible Helm releases
* resource and scaling policies are defined
* workload classes are appropriately isolated
* queue-based workers can scale
* media-processing capacity is isolated
* network policies restrict unnecessary communication
* workload IAM is least privilege
* secrets are securely delivered
* deployments support controlled rollback
* progressive delivery is available where justified
* database operations are production-hardened
* Redis operations are production-hardened
* Kafka/Redpanda operations are production-hardened
* search operations are production-hardened
* CDN/media origin security is enforced
* observability supports operational diagnosis
* SLOs and alerts are defined
* vulnerability/supply-chain controls are active
* backup restoration is validated
* disaster recovery is documented and operationally credible
* incident runbooks exist
* resilience testing is implemented where appropriate
* capacity planning is documented
* cost controls are implemented
* infrastructure validation succeeds
* no required operational capability is intentionally incomplete

Do not declare completion when infrastructure validation, deployment testing, recovery testing, or other required checks fail.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* Helm charts/releases created or modified
* Kubernetes workload changes
* autoscaling changes
* worker-isolation changes
* network-policy changes
* IAM changes
* secret-management changes
* database operational changes
* Redis changes
* event-broker changes
* search changes
* object-storage changes
* CDN changes
* observability changes
* SLOs/alerts created
* security/supply-chain changes
* backup/restore validation
* disaster-recovery validation
* resilience tests performed
* deployment/rollback tests performed
* capacity-planning changes
* cost-control changes
* documentation changes
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified infrastructure from planned or unverified behavior.

Do not claim that failover, restoration, rollback, autoscaling, or resilience tests succeeded unless they were actually performed and verified.

---

# FINAL INSTRUCTION

Implement the advanced production infrastructure required to operate the music-streaming platform safely at large scale.

Deploy workloads according to their actual operational profiles.

Keep media processing isolated from latency-sensitive workloads.

Scale workers according to backlog as well as resource utilization.

Protect stateful systems through private networking, backups, monitoring, and controlled access.

Protect media origins behind secure CDN access.

Make deployments observable, reversible, and compatible with database migration realities.

Make SLOs and alerts actionable.

Make backup and disaster recovery testable rather than theoretical.

Make supply-chain security part of CI/CD.

Make resilience testing part of operational engineering.

Make capacity and cost decisions measurable rather than arbitrary.

Do not create superficial Helm/Terraform configuration and call it production infrastructure.

The resulting infrastructure must provide a resilient, secure, observable, recoverable, and economically sustainable operating platform for the music-streaming system, capable of supporting large-scale web traffic, concurrent playback, media processing, asynchronous events, search, recommendations, subscriptions, notifications, and analytics without fragile single points of failure.
