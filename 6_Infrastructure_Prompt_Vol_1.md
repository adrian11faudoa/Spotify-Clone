# SPOTIFY-STYLE GLOBAL MUSIC STREAMING PLATFORM — INFRASTRUCTURE VOLUME 1

## ROLE

Act as the complete senior infrastructure engineering organization responsible for implementing the production-grade cloud, container, networking, deployment, security, observability, and foundational platform infrastructure of a global music streaming platform comparable in capability and scale to major commercial music-streaming services.

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

Do not create placeholder Terraform resources.

Do not create fake cloud services.

Do not leave TODO/FIXME infrastructure gaps.

Do not depend on another AI conversation being available.

Inspect the repository before making changes and integrate the infrastructure implementation with the actual repository state.

Implement real infrastructure-as-code, deployment automation, security controls, observability, backup strategy, environment isolation, and operational documentation appropriate for a serious production platform.

---

# PROJECT

Build the production infrastructure foundation for an original global music streaming platform.

The platform includes:

* Next.js web application
* React Native/Expo mobile applications
* NestJS backend
* PostgreSQL
* Redis
* Kafka or Redpanda
* BullMQ workers
* Elasticsearch or OpenSearch
* S3-compatible object storage
* media-processing workers using FFmpeg
* CDN-based media delivery
* payment-provider integrations
* notification providers
* recommendation services
* analytics pipelines
* administration services

The infrastructure must support:

* local development
* automated testing
* shared development environments
* staging
* production
* disaster recovery
* horizontal scaling
* high availability
* secure secret management
* zero-downtime deployment strategies where technically appropriate
* centralized observability
* backup and restoration
* operational diagnostics
* controlled network exposure
* infrastructure reproducibility

Design the platform for a large user population, high concurrent playback, large media storage, high API traffic, high event volume, and large asynchronous workloads.

---

# TECHNOLOGY DIRECTION

Use:

## Cloud

Use a major public cloud platform with AWS as the preferred baseline unless the existing repository already establishes a compatible provider.

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
* Loki or an equivalent centralized log system
* Tempo or an equivalent trace backend
* cloud-native monitoring where useful

## Core Managed Infrastructure

Use managed services where they materially improve:

* availability
* operational reliability
* security
* backup/recovery
* scalability
* managed lifecycle

Do not self-host infrastructure merely to avoid managed services.

---

# SOURCE OF TRUTH

Before modifying anything:

1. Inspect the repository.
2. Inspect existing Terraform.
3. Inspect Dockerfiles.
4. Inspect Docker Compose/development infrastructure.
5. Inspect Kubernetes manifests.
6. Inspect Helm charts.
7. Inspect GitHub Actions.
8. Inspect environment configuration.
9. Inspect application ports and health endpoints.
10. Inspect database configuration.
11. Inspect Redis configuration.
12. Inspect Kafka/Redpanda configuration.
13. Inspect search configuration.
14. Inspect object-storage integration.
15. Inspect observability configuration.
16. Inspect existing documentation.

The repository defines what currently exists.

This prompt defines what this infrastructure volume must achieve.

Do not assume previous AI-generated prompts are available.

Preserve compatible infrastructure.

Do not replace working production-quality infrastructure without a concrete reason.

---

# INFRASTRUCTURE RESPONSIBILITY

This volume is responsible for establishing:

* cloud account/region strategy
* Terraform structure
* environment structure
* network architecture
* VPC
* subnets
* routing
* NAT strategy
* security groups
* ingress
* TLS
* DNS
* load balancing
* Kubernetes foundation
* container registry
* node/workload architecture
* workload identities
* secret-management foundations
* configuration management
* base storage
* database infrastructure
* Redis infrastructure
* event-broker infrastructure
* search infrastructure
* object storage
* CDN foundation
* foundational observability
* infrastructure CI/CD
* environment isolation
* backup foundations

Do not implement every application deployment workload in one undifferentiated infrastructure module.

---

# INFRASTRUCTURE ARCHITECTURE

Use a layered architecture separating:

* network
* security
* identity
* compute
* data
* messaging
* media
* observability
* deployment
* environment-specific configuration

Terraform modules must have clear responsibilities.

Avoid one giant Terraform file for the entire platform.

Use reusable modules for infrastructure components that are logically independent.

---

# ENVIRONMENT MODEL

Establish distinct environments for:

* local
* test
* development
* staging
* production
* disaster recovery where applicable

Production must not depend on development resources.

Avoid sharing stateful infrastructure between production and nonproduction when that creates:

* security risk
* noisy-neighbor risk
* operational coupling
* accidental data access

Environment-specific values must come from configuration rather than source-code constants.

---

# TERRAFORM STRUCTURE

Establish a maintainable Terraform structure.

Support:

* reusable modules
* environment-specific roots
* remote state
* state locking
* provider configuration
* variable validation
* outputs
* tagging
* lifecycle protections
* dependency boundaries

Remote state must use secure storage and locking appropriate to the selected AWS architecture.

Do not store Terraform state in the repository.

Do not hardcode credentials into Terraform.

---

# TERRAFORM STATE SECURITY

Protect Terraform state because it may contain:

* resource identifiers
* configuration
* sensitive infrastructure metadata
* references to secrets

Use:

* encrypted remote state
* least-privilege IAM
* state locking
* restricted access
* versioning
* auditability

Mark sensitive Terraform outputs appropriately.

Do not print secret values through CI logs.

---

# CLOUD ACCOUNT AND REGION STRATEGY

Define infrastructure boundaries for:

* primary region
* secondary disaster-recovery region where required
* production account
* nonproduction account(s)

Where organizational constraints prevent separate accounts immediately, use strong environment isolation and document the migration path.

Do not place all workloads in one availability zone.

---

# NETWORK ARCHITECTURE

Create a production-grade VPC architecture.

Use:

* multiple availability zones
* public subnets only where genuinely required
* private subnets for application workloads
* isolated/private subnets for stateful services where appropriate
* route tables
* controlled NAT
* VPC endpoints where beneficial

Minimize internet-exposed resources.

Application workloads should not require public IP addresses merely to operate.

---

# SUBNET DESIGN

Separate appropriate network tiers such as:

* public ingress
* private application
* private worker
* data/stateful

Do not over-segment the network without an operational reason.

Ensure enough address space for:

* Kubernetes nodes
* pods
* load balancers
* future scale
* multiple environments where applicable

Do not make the CIDR plan impossible to extend.

---

# INTERNET INGRES

Expose only intended public entry points.

Public infrastructure may include:

* CDN edge
* web ingress/load balancer
* public DNS

Keep:

* databases
* Redis
* Kafka/Redpanda
* search clusters
* internal workers

off the public internet.

---

# LOAD BALANCING

Use managed load-balancing infrastructure appropriate for:

* web traffic
* API traffic
* WebSocket connections
* health checks
* TLS termination

Configure:

* listener policies
* timeouts
* idle behavior
* health checks
* security groups
* access logging where appropriate

WebSocket traffic must have suitable timeout configuration.

---

# TLS

Use managed certificate services where appropriate.

Require:

* TLS for public traffic
* secure internal communication where required
* modern protocol configuration
* automatic certificate renewal
* no plaintext production APIs

Do not terminate TLS at arbitrary internal components unless there is a documented reason.

---

# DNS

Implement a production DNS strategy.

Support:

* public application domain
* API domain
* media/CDN domain
* administrative domains where appropriate
* environment-specific hostnames
* health-based or weighted routing where justified

Avoid exposing internal service endpoints through public DNS.

---

# KUBERNETES FOUNDATION

Establish a production-grade Kubernetes foundation.

Support:

* multiple nodes
* multiple availability zones
* cluster autoscaling where appropriate
* pod scheduling
* namespaces
* resource policies
* network policies
* workload identity
* ingress
* secrets/configuration integration
* health probes
* graceful termination

Do not place all workloads in one node pool.

---

# NODE POOLS

Separate workload classes where their operational profiles materially differ.

At minimum evaluate:

* general application workloads
* memory/CPU-oriented workers
* media-processing workers

Media-processing workloads may require dedicated nodes because of:

* CPU intensity
* memory usage
* FFmpeg behavior
* scaling characteristics

Do not allow media-processing workloads to starve latency-sensitive APIs.

---

# KUBERNETES NAMESPACES

Use meaningful namespace boundaries.

Consider separation for:

* application
* workers
* observability
* ingress
* platform tooling

Do not create a namespace for every microservice unless it provides concrete value.

---

# RESOURCE MANAGEMENT

All production workloads must define appropriate:

* CPU requests
* CPU limits where appropriate
* memory requests
* memory limits
* ephemeral-storage considerations

Avoid unlimited workloads.

Avoid setting identical resource values blindly across different workloads.

Media processors must receive resource profiles appropriate to their workload.

---

# AUTOSCALING FOUNDATION

Prepare Kubernetes for horizontal and workload-specific scaling.

Support:

* Horizontal Pod Autoscaler
* node scaling
* queue-depth-driven scaling where appropriate
* CPU/memory signals
* custom metrics where justified

Do not rely exclusively on CPU for workloads whose pressure is driven by:

* queue depth
* request latency
* active playback sessions
* event lag
* media-processing backlog

---

# POD AVAILABILITY

Configure:

* readiness probes
* liveness probes
* startup probes where appropriate
* PodDisruptionBudgets
* topology spread where appropriate
* anti-affinity for critical replicas

Avoid running all replicas on one availability zone.

---

# GRACEFUL TERMINATION

Every long-running workload must have an appropriate shutdown strategy.

Infrastructure must allow:

* request draining
* WebSocket connection handling
* event-consumer shutdown
* queue-worker shutdown
* database connection cleanup
* media-job completion or retry

Do not terminate workers abruptly while they are processing durable critical work.

---

# CONTAINER IMAGE STRATEGY

Build secure production Docker images.

Require:

* minimal base images where practical
* non-root processes where supported
* deterministic dependency installation
* multi-stage builds
* production-only runtime dependencies
* health-check compatibility
* no embedded secrets

Do not run development servers in production images.

---

# CONTAINER REGISTRY

Use a managed container registry.

Support:

* immutable image tagging where appropriate
* vulnerability scanning
* lifecycle policies
* private repository access
* image retention
* provenance/signing strategy where practical

Do not deploy `latest` as the sole production identifier.

Prefer immutable release references such as:

* commit SHA
* release version
* image digest

---

# WORKLOAD IDENTITY

Use cloud-native workload identities rather than long-lived cloud access keys in Kubernetes.

Applications should receive only permissions required for their responsibilities.

Examples include permissions for:

* object storage
* secrets
* queues
* metrics
* logging

Do not put cloud credentials into Kubernetes Secrets when workload identity can provide safer access.

---

# SECRET MANAGEMENT

Use a managed secret-management system.

Support secure storage for:

* database credentials
* Redis credentials
* Kafka credentials
* payment-provider secrets
* JWT/signing keys
* OAuth credentials
* email credentials
* push notification credentials
* cloud provider secrets where unavoidable

Applications should retrieve secrets through secure mechanisms.

Do not store plaintext production secrets in:

* Git
* Terraform variables committed to source
* Docker images
* Helm values
* GitHub Actions logs

---

# KUBERNETES CONFIGURATION

Separate:

* nonsecret configuration
* secret configuration
* environment configuration

Prefer external secret synchronization where appropriate.

Never store a secret value directly in a committed manifest merely because Kubernetes supports Secret resources.

---

# IAM

Apply least privilege across:

* Terraform
* CI/CD
* Kubernetes workloads
* humans
* operators
* monitoring systems

Separate permissions for:

* infrastructure deployment
* application runtime
* data administration
* observability
* support operations

Avoid wildcard policies when narrower permissions are practical.

---

# DATABASE INFRASTRUCTURE

Provision PostgreSQL using a managed high-availability service where appropriate.

Support:

* multi-AZ deployment
* automated backups
* point-in-time recovery
* encryption
* parameter configuration
* network isolation
* connection management
* maintenance strategy
* monitoring

Define:

* primary
* read replicas where required
* failover behavior
* backup retention

Do not expose PostgreSQL publicly.

---

# DATABASE CONNECTION MANAGEMENT

Design for Kubernetes horizontal scaling.

Account for:

* connection limits
* connection pooling
* pod scaling
* worker concurrency
* background jobs

Avoid allowing an autoscaling event to overwhelm PostgreSQL with thousands of direct connections.

Use an appropriate managed proxy/pooling solution if required by the selected architecture.

---

# DATABASE SECURITY

Require:

* encryption at rest
* encryption in transit
* strong credentials
* least-privilege access
* security-group restrictions
* audit/monitoring where appropriate

Separate application credentials from administrative credentials.

Do not grant application workloads schema-owner or superuser access unless strictly required.

---

# REDIS INFRASTRUCTURE

Provision managed Redis where appropriate.

Support:

* high availability
* encryption
* private networking
* authentication
* subnet isolation
* failover
* monitoring
* memory policies

Distinguish workloads such as:

* application caching
* playback state
* rate limiting
* BullMQ

Use namespacing to prevent unrelated workloads from interfering.

---

# EVENT BROKER INFRASTRUCTURE

Provision managed Kafka-compatible infrastructure where appropriate, such as Amazon MSK or another justified managed Kafka/Redpanda platform.

Support:

* high availability
* multiple brokers
* private networking
* encryption
* authentication
* topic management
* monitoring
* retention configuration

Avoid exposing the broker publicly.

---

# EVENT BROKER SECURITY

Implement:

* encryption in transit
* authentication
* least-privilege topic access
* producer permissions
* consumer permissions
* restricted administrative access

Applications should not receive unrestricted broker privileges.

---

# QUEUE INFRASTRUCTURE

BullMQ depends on Redis.

Infrastructure must provide sufficient Redis capacity and isolation for:

* background jobs
* rate limiting
* cache
* playback state

Where scale requires it, isolate job-related Redis workloads from latency-sensitive cache/playback workloads.

Do not create an architecture in which a large media-processing backlog can exhaust the same Redis resources required for critical API traffic without mitigation.

---

# SEARCH INFRASTRUCTURE

Provision Elasticsearch/OpenSearch in a private network.

Support:

* multiple nodes where required
* suitable storage
* encryption
* authentication
* backups/snapshots
* monitoring
* shard/replica planning
* index lifecycle management

Do not expose the search cluster directly to public internet clients.

---

# OBJECT STORAGE

Provision object storage for:

* source audio
* processed audio
* artwork
* thumbnails
* derivatives
* temporary processing artifacts

Configure:

* encryption at rest
* versioning where appropriate
* lifecycle policies
* access policies
* block-public-access controls
* audit/logging where justified

Protected media buckets must not be publicly readable.

---

# CDN FOUNDATION

Establish a CDN for:

* audio delivery
* artwork
* static assets

Configure:

* origin protection
* cache policies
* TLS
* custom domains
* signed access where required
* compression where appropriate
* logging
* cache invalidation strategy

Do not make object storage publicly accessible simply to simplify CDN configuration.

---

# MEDIA ORIGIN SECURITY

Protect the media origin.

Require:

* CDN-origin restrictions
* private buckets
* signed access
* controlled origin requests

The infrastructure must prevent users from bypassing the intended CDN/access-control mechanism to retrieve protected media directly.

---

# BACKUP FOUNDATION

Implement backup infrastructure for:

* PostgreSQL
* object-storage metadata where applicable
* search snapshots
* critical configuration
* Terraform state
* required operational state

Define:

* frequency
* retention
* encryption
* access control
* restore process

A backup that has never been restored should not be treated as proven recovery.

---

# DISASTER-RECOVERY FOUNDATION

Establish the infrastructure path for disaster recovery.

Support:

* secondary-region planning
* replicated or restorable databases
* object-storage replication where appropriate
* infrastructure recreation
* secret/configuration recovery
* DNS failover strategy
* operational documentation

The DR environment must not rely on undocumented manual configuration.

---

# OBSERVABILITY FOUNDATION

Provision the foundational observability platform.

Support:

* metrics collection
* log aggregation
* trace collection
* dashboards
* alerting
* retention
* access control

Use OpenTelemetry-compatible ingestion for application traces and metrics.

---

# PROMETHEUS

Configure Prometheus or an equivalent metrics system for:

* Kubernetes
* nodes
* application workloads
* PostgreSQL
* Redis
* event broker
* search
* ingress
* media-processing workers

Avoid unrestricted high-cardinality labels.

---

# GRAFANA

Provide dashboards for:

* cluster health
* API health
* Kubernetes workloads
* PostgreSQL
* Redis
* event broker
* search
* queues
* media processing
* playback authorization
* CDN/origin behavior
* infrastructure capacity

Dashboards must focus on operational signals rather than vanity metrics.

---

# LOGGING

Centralize structured logs.

Support:

* Kubernetes workload logs
* ingress logs
* infrastructure logs
* application logs
* worker logs
* security-relevant infrastructure events

Logs must include useful correlation fields when available.

Do not log:

* passwords
* tokens
* private keys
* payment credentials
* secret values
* signed URLs with long-lived validity

---

# TRACING

Provision distributed tracing infrastructure.

Support propagation across:

* web/API ingress
* backend
* database
* Redis
* event broker
* queues
* media processing
* external providers where technically feasible

Ensure asynchronous boundaries retain trace/correlation context.

---

# ALERTING

Define alerts for production-critical conditions.

At minimum consider:

* API error rate
* API latency
* failed deployments
* unhealthy pods
* insufficient replicas
* node pressure
* database CPU
* database connections
* replication lag
* Redis memory pressure
* Redis failover
* event-broker lag
* queue backlog
* media-processing failures
* search cluster health
* object-storage failures
* CDN origin failures
* certificate expiry
* backup failures

Alerts must be actionable.

Avoid alerting on every transient event.

---

# COST CONTROLS

Design infrastructure with cost visibility.

Support:

* resource tagging
* environment tagging
* service ownership tagging
* budgets
* cost alerts
* lifecycle policies
* autoscaling
* storage cleanup

Do not sacrifice production reliability for arbitrary cost minimization.

Avoid always-on oversized resources without a capacity justification.

---

# SECURITY BASELINE

Apply cloud security controls such as:

* private networking
* least-privilege IAM
* encryption
* managed secrets
* audit logging
* security groups
* network policies
* WAF where appropriate
* vulnerability scanning
* image scanning
* dependency scanning

Do not disable security controls because they complicate local development.

Use environment-specific accommodations rather than weakening production security.

---

# WAF AND EDGE PROTECTION

Where appropriate, configure WAF protections for public HTTP traffic.

Protect against common attacks such as:

* injection
* malicious request patterns
* automated abuse
* excessive request rates

Coordinate WAF behavior with application rate limiting.

Do not rely on WAF alone for authorization.

---

# DDoS AND ABUSE RESILIENCE

Use cloud-native edge protections where available.

Protect:

* public web
* API endpoints
* authentication
* search
* playback authorization
* upload initiation

Do not allow expensive backend operations to be triggered without appropriate rate limits and authorization.

---

# CI/CD FOUNDATION

Implement GitHub Actions workflows for infrastructure and application delivery foundations.

Support:

* linting
* tests
* Terraform validation
* Terraform formatting
* security scanning
* Docker builds
* image scanning
* artifact publishing
* deployment approvals
* environment separation

Do not allow production deployment from arbitrary untrusted branches.

---

# TERRAFORM CI/CD

Terraform workflows must support:

* `fmt`
* validation
* static/security analysis where appropriate
* plan
* review/approval
* apply

Production applies require appropriate protection.

Do not print sensitive Terraform output in CI logs.

---

# ENVIRONMENT PROMOTION

Establish promotion behavior such as:

* development
* staging
* production

Use immutable artifacts between environments where practical.

Do not rebuild different application binaries for each environment if that creates drift.

Environment-specific configuration should be injected separately.

---

# DEPLOYMENT SAFETY

Infrastructure and deployment processes must support:

* rolling updates
* health checks
* rollback
* readiness gates
* controlled surge
* controlled unavailability

Do not allow infrastructure changes to remove all healthy application capacity at once.

---

# INFRASTRUCTURE TESTING

Validate infrastructure through:

* Terraform validation
* static analysis
* policy checks
* Kubernetes manifest validation
* Helm linting
* container vulnerability scanning
* deployment smoke tests
* connectivity tests
* backup verification where practical

Do not treat syntactically valid Terraform as proof of a valid production architecture.

---

# OPERATIONAL DOCUMENTATION

Document:

* infrastructure architecture
* environments
* network design
* Kubernetes architecture
* IAM model
* secret-management process
* deployment process
* rollback process
* database backup/restore
* Redis recovery
* broker recovery
* search recovery
* object-storage recovery
* CDN behavior
* observability
* alert handling
* disaster recovery

Documentation must reflect actual repository configuration.

---

# IMPLEMENTATION BOUNDARIES

This infrastructure volume owns the production infrastructure foundation.

Implement:

* cloud foundation
* Terraform
* networking
* IAM
* Kubernetes foundation
* container registry
* secrets foundation
* PostgreSQL infrastructure
* Redis infrastructure
* event-broker infrastructure
* search infrastructure
* object storage
* CDN
* observability foundation
* CI/CD foundation
* backup foundation
* DR foundation

Do not implement:

* detailed application business logic
* web UI
* mobile UI
* database schema migrations
* application-level media processing code

Infrastructure should provide the platform on which those workloads run.

---

# REPOSITORY IMPLEMENTATION PROCESS

Before modifying files:

1. inspect existing Terraform
2. inspect Docker and Compose files
3. inspect Kubernetes manifests
4. inspect Helm
5. inspect GitHub Actions
6. inspect environment configuration
7. inspect service ports
8. inspect health endpoints
9. inspect existing cloud assumptions
10. identify infrastructure already provisioned

Then:

1. establish Terraform structure
2. establish environment separation
3. implement network
4. implement IAM/security
5. implement Kubernetes foundation
6. implement stateful infrastructure
7. implement object storage/CDN
8. implement observability
9. implement CI/CD
10. implement backup/DR foundation
11. validate infrastructure
12. update documentation

Do not destroy existing infrastructure without a migration strategy.

Do not create duplicate resources simply because resource names differ.

---

# COMPLETION CRITERIA

This infrastructure task is complete only when:

* Terraform is structurally maintainable
* remote state is secure
* environments are isolated
* networking is production-grade
* public exposure is minimized
* Kubernetes foundation is highly available
* workloads can scale
* stateful services are private and resilient
* PostgreSQL has backup/recovery
* Redis has high availability where required
* Kafka/Redpanda infrastructure is secure
* search infrastructure is private and recoverable
* object storage is protected
* CDN is configured for secure delivery
* secrets are centrally managed
* IAM follows least privilege
* observability foundations are operational
* CI/CD is environment-aware
* production deployments are protected
* backups are automated
* disaster-recovery foundations exist
* security scanning is integrated
* operational documentation is present
* infrastructure validation succeeds
* no required infrastructure capability is intentionally incomplete

Do not declare completion when Terraform validation, security checks, Kubernetes validation, deployment tests, or other required verification fails.

---

# IMPLEMENTATION REPORT

At completion, report:

* files created
* files modified
* Terraform modules created/modified
* environments created/modified
* cloud resources provisioned
* network changes
* IAM changes
* Kubernetes changes
* database infrastructure changes
* Redis changes
* event-broker changes
* search changes
* storage changes
* CDN changes
* observability changes
* CI/CD changes
* backup/DR changes
* security changes
* validation performed
* deployment tests performed
* compatibility considerations
* unresolved issues, if any

The report must distinguish verified infrastructure from planned or unverified resources.

Do not claim a cloud resource, deployment, failover, backup, or restore succeeded unless it was actually validated.

---

# FINAL INSTRUCTION

Implement the production infrastructure foundation for the music-streaming platform.

Build reproducible infrastructure.

Keep stateful systems private.

Keep secrets outside source control.

Use least-privilege workload identities.

Use managed services where they materially improve reliability.

Separate latency-sensitive workloads from resource-intensive media processing.

Design Kubernetes for multi-AZ availability and horizontal scaling.

Protect media origins behind controlled CDN access.

Make backup and disaster recovery real operational capabilities rather than documentation-only promises.

Make observability part of the infrastructure baseline.

Make CI/CD secure, reproducible, reviewable, and environment-aware.

Do not create superficial Terraform scaffolding and call it production infrastructure.

The resulting infrastructure foundation must provide a secure, highly available, scalable, observable platform on which the music-streaming application's web, mobile, backend, media, search, recommendation, subscription, and asynchronous workloads can operate reliably at large scale.
