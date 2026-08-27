You are operating in Senior Engineering Team Mode.

Complete the remaining production-ready infrastructure, DevOps, deployment automation, multi-region architecture, observability, security operations, disaster recovery, scalability, cost optimization, infrastructure testing, and operational tooling for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The infrastructure must integrate with the established backend, web frontend, mobile applications, music catalog, audio processing, playback, CDN, subscriptions, payments, playlists, libraries, search, recommendations, podcasts, notifications, advertising, analytics, moderation, and administration systems.

Do not redesign the approved application architecture.

Do not implement backend business logic.

Do not implement frontend code.

Do not implement mobile code.

Do not generate unrelated application code.

────────────────────────────────────────

MISSION

Complete the production infrastructure required for:

• Production Kubernetes workloads
• Helm deployment
• Backend service deployment
• Web deployment
• Background workers
• Audio-processing workers
• Search workers
• Recommendation workers
• Analytics workers
• Notification workers
• Global CDN delivery
• Global DNS
• WAF
• TLS
• CI/CD
• GitHub Actions
• Container security
• Image scanning
• SBOM
• Image signing
• Secret rotation
• Multi-region deployment
• Regional failover
• Database operations
• Redis operations
• Kafka operations
• OpenSearch operations
• Observability
• SLOs
• Alerting
• Backup validation
• Disaster recovery
• Capacity planning
• Cost optimization
• Incident response
• Operational runbooks
• Production smoke testing
• Infrastructure testing
• Release management

────────────────────────────────────────

PRIMARY TECHNOLOGY STACK

Cloud:

• AWS

Orchestration:

• Kubernetes
• Amazon EKS

Packaging:

• Helm

Infrastructure as Code:

• Terraform

Containers:

• Docker
• Amazon ECR

CI/CD:

• GitHub Actions

Database:

• PostgreSQL
• Amazon RDS or Aurora PostgreSQL where justified

Cache:

• Redis
• Amazon ElastiCache

Event streaming:

• Kafka or Redpanda

Search:

• OpenSearch or approved Elasticsearch deployment

Object storage:

• Amazon S3

CDN:

• Amazon CloudFront

DNS:

• Amazon Route 53

TLS:

• AWS Certificate Manager

Security:

• IAM
• KMS
• WAF
• Security Groups
• Network ACLs
• Kubernetes RBAC
• NetworkPolicies
• Pod Security Standards

Secrets:

• AWS Secrets Manager
• Approved Kubernetes secret-management integration

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

Never omit required implementation.

Never say:

- "implement similarly"
- "left as an exercise"
- "for brevity"
- "remaining configuration omitted"

Every generated infrastructure file must be complete.

Never regenerate unchanged files.

Only modify existing files when required.

Never hard-code secrets.

Never hard-code production credentials.

Use reusable Terraform and Helm patterns.

Keep environment-specific configuration separate from reusable modules.

────────────────────────────────────────

KUBERNETES PRODUCTION WORKLOADS

Complete production Kubernetes architecture for:

• Web application
• API Gateway
• Identity services
• Catalog services
• Playback services
• Search services
• Recommendation services
• Playlist services
• Subscription services
• Notification services
• Podcast services
• Advertising services
• Analytics workers
• Media-processing workers
• Search-index workers
• Background workers
• Administrative services

Define:

• Deployments
• Services
• ServiceAccounts
• ConfigMaps
• Secrets references
• Ingress
• HorizontalPodAutoscaler
• PodDisruptionBudget
• NetworkPolicy
• Resource limits
• Resource requests
• Probes
• Topology spread
• Affinity
• Anti-affinity

────────────────────────────────────────

HELM

Create reusable production Helm architecture.

Support:

• Common chart patterns
• Backend service charts
• Worker charts
• Web application charts
• Media-worker charts
• Search-worker charts
• Environment-specific values

Support:

• Development
• Testing
• Staging
• Production

Define:

• Resource templates
• Autoscaling
• Health probes
• ServiceAccounts
• Ingress
• NetworkPolicy
• PDB
• ConfigMaps
• Secret references
• Deployment strategies

Avoid duplicating identical templates across services.

────────────────────────────────────────

DEPLOYMENT STRATEGY

Implement:

• Rolling deployments
• Canary deployments
• Blue-green deployments where justified
• Graceful termination
• Connection draining
• Readiness verification
• Automatic rollback

Define deployment strategies separately for:

• Web
• API
• Playback authorization
• Media workers
• Search workers
• Analytics workers
• Notification workers

High-risk services should have stricter deployment gates.

────────────────────────────────────────

ZERO-DOWNTIME DEPLOYMENT

Ensure:

• Readiness probes
• Startup probes
• Liveness probes
• PodDisruptionBudgets
• Graceful shutdown
• Minimum available replicas
• Connection draining
• Backward-compatible schema changes

Do not deploy database migrations that break the currently running version during rolling deployments.

────────────────────────────────────────

DATABASE MIGRATION DEPLOYMENTS

Use:

• Expand-and-contract
• Backward-compatible schema evolution
• Staged migration
• Production prechecks
• Migration validation
• Post-migration validation

Define how application versions N and N+1 can coexist safely.

────────────────────────────────────────

CI/CD ARCHITECTURE

Implement GitHub Actions workflows for:

PULL REQUESTS

• Formatting
• Linting
• Type checking where applicable
• Unit tests
• Integration tests
• Contract tests
• Security scanning
• Secret scanning
• Dependency scanning
• Docker build validation
• Terraform formatting
• Terraform validation
• Helm validation
• Kubernetes validation

BUILD

• Docker image creation
• ECR publishing
• SBOM
• Vulnerability scanning
• Image signing where appropriate

DEPLOYMENT

• Development
• Staging
• Production

────────────────────────────────────────

GITHUB ACTIONS SECURITY

Use:

• OIDC
• Short-lived AWS credentials
• Protected environments
• Branch protections
• Required approvals
• Minimal workflow permissions

Separate:

• Development deployment
• Staging deployment
• Production deployment

Never use long-lived AWS access keys when OIDC can provide federated credentials.

────────────────────────────────────────

RELEASE MANAGEMENT

Implement:

• Versioning
• Git tags
• Release metadata
• Artifact traceability
• Environment promotion
• Change tracking
• Rollback

Every production artifact must be traceable to:

• Git commit
• Build
• Docker image
• Deployment
• Configuration version

────────────────────────────────────────

CONTAINER SECURITY

Implement:

• Minimal runtime images
• Non-root execution
• Immutable image references
• Dependency scanning
• Vulnerability scanning
• SBOM generation
• Image signing
• Registry lifecycle policies

Define deployment blocking rules for critical vulnerabilities.

────────────────────────────────────────

MULTI-REGION ARCHITECTURE

Complete global production architecture.

Support:

• Multiple AWS regions
• Regional EKS clusters
• Regional APIs
• Regional workers
• Regional playback authorization
• Regional search where appropriate
• Regional observability
• Regional data services where required
• Global routing
• Regional health checks
• Regional failover

Use:

• Route 53 latency routing
• Route 53 failover routing
• Weighted routing where appropriate

Avoid unnecessary synchronous cross-region dependencies.

────────────────────────────────────────

REGIONAL TRAFFIC MANAGEMENT

Support:

• Regional health
• Traffic shifting
• Region draining
• Controlled failover
• Recovery routing
• Failback

Do not automatically route traffic to a partially recovered region.

────────────────────────────────────────

MULTI-REGION DATABASE STRATEGY

Complete infrastructure for:

PostgreSQL:

• Primary region
• Recovery region
• Replication
• Backup replication
• PITR
• Failover

S3:

• Cross-region replication
• Versioning
• Lifecycle

Kafka/Redpanda:

• Recovery/replication strategy

OpenSearch:

• Snapshots
• Restore
• Rebuild

Redis:

• Regional isolation
• Failover

────────────────────────────────────────

POSTGRESQL OPERATIONS

Configure monitoring for:

• CPU
• Memory
• Connections
• Disk
• IOPS
• Query latency
• Lock contention
• Deadlocks
• Replica lag
• Transaction rate

Support:

• Automated backups
• PITR
• Read replicas
• Multi-AZ
• Maintenance
• Failover

────────────────────────────────────────

REDIS OPERATIONS

Monitor:

• Memory
• Connections
• Command latency
• Evictions
• Replication
• Failover
• Hit rate
• Hot keys

Support:

• Multi-AZ
• Automatic failover
• Encryption
• Authentication

Redis must remain non-authoritative for persistent business data.

────────────────────────────────────────

KAFKA / REDPANDA OPERATIONS

Monitor:

• Broker health
• Partition distribution
• Consumer lag
• Disk utilization
• Throughput
• Rebalances
• Under-replicated partitions

Support:

• Multi-AZ
• Replication
• TLS
• Authentication
• Topic retention
• Recovery

Prevent hot partitions through appropriate partitioning.

────────────────────────────────────────

OPENSEARCH OPERATIONS

Monitor:

• Cluster health
• CPU
• Memory
• JVM pressure
• Disk
• Shard balance
• Search latency
• Indexing latency
• Failed indexing

Support:

• Snapshots
• Restore
• Index aliases
• Versioned indexes
• Reindexing

Search must always remain rebuildable from authoritative catalog sources.

────────────────────────────────────────

MEDIA PROCESSING INFRASTRUCTURE

Create dedicated infrastructure for:

• Audio validation
• Metadata extraction
• Loudness analysis
• Transcoding
• Rendition generation
• Packaging
• Artwork processing
• Podcast processing

Support:

• CPU-intensive worker nodes
• Queue-based autoscaling
• Temporary processing storage
• Failure isolation
• Retry
• Cleanup

Do not run resource-heavy media jobs on latency-sensitive API nodes.

────────────────────────────────────────

QUEUE-BASED AUTOSCALING

Autoscale workers using relevant signals:

• Queue depth
• Job latency
• Kafka consumer lag
• CPU
• Memory

Apply to:

• Audio processing
• Search indexing
• Recommendations
• Notifications
• Analytics
• Reports

Do not rely only on CPU when workloads are queue-driven.

────────────────────────────────────────

OBSERVABILITY

Complete production observability.

Use:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Create dashboards for:

APPLICATION

• Requests
• Errors
• Latency
• Saturation

PLAYBACK

• Authorization latency
• Session count
• Playback failures
• Token failures

MEDIA

• Processing throughput
• Processing latency
• Processing failures
• Queue depth

SEARCH

• Search latency
• Indexing lag
• Search errors

RECOMMENDATIONS

• Generation latency
• Cache hit rate
• Failure rate

SUBSCRIPTIONS

• Payment failures
• Renewal failures
• Entitlement errors

INFRASTRUCTURE

• EKS
• Nodes
• Pods
• CPU
• Memory
• Disk
• Network

────────────────────────────────────────

SLO / SLI

Define measurable SLOs for:

• API availability
• Authentication
• Playback authorization
• Search
• Recommendations
• Playlist APIs
• Subscription operations
• Payment processing
• Media processing
• Notification delivery
• Content publication

For each define:

• SLI
• Data source
• Target
• Alert threshold
• Error budget

────────────────────────────────────────

ALERTING

Create alerts for:

• API errors
• API latency
• Authentication failures
• Playback authorization failures
• Search failures
• Search indexing lag
• Media-processing backlog
• Queue backlog
• Kafka consumer lag
• PostgreSQL failures
• PostgreSQL replica lag
• Redis memory pressure
• OpenSearch cluster issues
• Payment failures
• Notification failures
• Backup failures
• Deployment failures
• Certificate expiration
• WAF anomalies
• Region health

Use severity:

• Warning
• Critical
• Emergency

────────────────────────────────────────

LOGGING

Complete centralized logging.

Support:

• Structured JSON
• Loki
• Correlation IDs
• Request IDs
• Trace IDs
• Retention
• Access controls
• Sensitive-data filtering

Never log:

• Passwords
• API keys
• AWS credentials
• Payment secrets
• Playback credentials
• Private keys
• Authentication tokens

────────────────────────────────────────

SECRET ROTATION

Automate or document rotation for:

• PostgreSQL credentials
• Redis credentials
• Kafka credentials
• Stripe secrets
• Webhook secrets
• OAuth secrets
• Notification credentials
• Search credentials

Support:

• Rotation
• Revocation
• Validation
• Audit
• Emergency rotation

Applications must handle rotated credentials safely.

────────────────────────────────────────

WAF AND EDGE SECURITY

Complete WAF policies for:

• Web
• APIs
• Creator APIs
• Admin APIs
• Webhooks

Support:

• Rate limiting
• OWASP rules
• Request-size limits
• IP blocking
• Bot controls
• DDoS integration

Administrative APIs should use stricter controls.

────────────────────────────────────────

BACKUP OPERATIONS

Implement:

• Scheduled backups
• Retention
• Encryption
• Cross-region replication
• Backup monitoring
• Restore validation

Validate backups for:

• PostgreSQL
• S3
• OpenSearch
• Terraform state
• Critical configuration

────────────────────────────────────────

DISASTER RECOVERY

Implement recovery procedures for:

• EKS failure
• Node-group failure
• PostgreSQL failure
• Redis failure
• Kafka failure
• OpenSearch failure
• S3 failure
• CDN failure
• Region failure

Define:

• Detection
• Failover
• Recovery
• Validation
• Reconciliation
• Failback

────────────────────────────────────────

RTO / RPO

Define infrastructure objectives for:

• Authentication
• Catalog
• Playback
• Subscriptions
• Payments
• Playlists
• Library
• Search
• Recommendations
• Podcasts
• Analytics

Differentiate:

• Mission-critical transactional services
• Derived services
• Ephemeral services

────────────────────────────────────────

DISASTER-RECOVERY TESTING

Test:

• PostgreSQL restore
• PITR
• Regional failover
• S3 recovery
• Search recovery
• Kafka recovery
• Redis recovery
• EKS reconstruction
• Terraform reconstruction

Measure actual:

• RTO
• RPO

Compare against targets.

────────────────────────────────────────

CAPACITY PLANNING

Create capacity models for:

• Users
• API requests
• Concurrent listeners
• Playback authorization
• Audio traffic
• Search
• Recommendations
• Playlist operations
• Subscription traffic
• Payment traffic
• Notification traffic
• Media processing
• Analytics events

For each define:

• Baseline
• Peak
• Burst
• Headroom
• Autoscaling threshold
• Expansion procedure

────────────────────────────────────────

COST OPTIMIZATION

Evaluate:

• EKS node utilization
• Right-sizing
• Autoscaling
• Savings Plans
• Reserved capacity
• Spot workloads where safe
• S3 lifecycle
• CloudFront caching
• Database sizing
• Redis sizing
• OpenSearch sizing
• Data transfer
• NAT costs
• Log retention

Do not compromise reliability or data durability solely to reduce cost.

────────────────────────────────────────

INCIDENT RESPONSE

Define:

• Incident severity
• On-call ownership
• Escalation
• Communication
• Containment
• Recovery
• Validation
• Postmortem
• Corrective action

Create incident workflows for:

• Playback outage
• Authentication outage
• Subscription outage
• Payment outage
• Database outage
• Kafka outage
• Search outage
• CDN outage
• Region outage
• Secret compromise

────────────────────────────────────────

OPERATIONAL RUNBOOKS

Create runbooks for:

• Deployment failure
• Rollback
• Database failure
• Redis failure
• Kafka failure
• Search failure
• Media backlog
• Notification backlog
• Region failover
• Region recovery
• Certificate failure
• Secret rotation
• Backup failure
• EKS outage

Each runbook must include:

• Detection
• Diagnosis
• Mitigation
• Recovery
• Validation
• Escalation

────────────────────────────────────────

PRODUCTION SMOKE TESTING

After every production deployment validate:

• Web availability
• API availability
• Authentication
• Catalog
• Search
• Playback authorization
• Playlist operations
• Subscription state
• Payment-provider connectivity where safe
• Podcast access
• Notifications
• Creator APIs
• Administrative APIs

Use only safe, non-destructive tests.

────────────────────────────────────────

INFRASTRUCTURE TESTING

Validate:

• Terraform
• Helm
• Kubernetes
• Docker
• IAM
• Security Groups
• NetworkPolicies
• WAF
• Autoscaling
• Load balancing
• Backup configuration
• Restore procedures
• Deployment
• Rollback
• Health checks

────────────────────────────────────────

SECURITY OPERATIONS

Complete:

• IAM review
• Access review
• KMS review
• Secret rotation
• Security-group review
• NetworkPolicy review
• Container scanning
• Dependency scanning
• Image signing
• WAF review
• Audit review

Prepare controls for:

• SOC 2
• ISO 27001
• GDPR
• PCI DSS scope minimization

Do not claim certification without formal assessment.

────────────────────────────────────────

RELEASE READINESS

A production deployment is ready only when:

• Required tests pass
• Infrastructure validation passes
• Security checks pass
• Monitoring is operational
• Alerts are operational
• Rollback is available
• Backup status is healthy
• Required approvals are complete
• Known risks are documented

────────────────────────────────────────

DOCUMENTATION

Generate:

• Production deployment guide
• Kubernetes operations guide
• Helm guide
• Terraform operations guide
• CI/CD guide
• GitHub Actions security guide
• Multi-region guide
• Global routing guide
• Database operations
• Redis operations
• Kafka operations
• OpenSearch operations
• Media-worker operations
• CDN operations
• Backup and restore guide
• Disaster-recovery guide
• Observability guide
• Security operations guide
• Incident-response guide
• Runbooks
• Capacity-planning guide
• Cost-management guide

────────────────────────────────────────

PROJECT INDEX

Update the infrastructure Project Index with:

• AWS accounts
• Regions
• EKS clusters
• Node pools
• Namespaces
• Helm charts
• Terraform modules
• Docker images
• ECR repositories
• PostgreSQL
• Redis
• Kafka/Redpanda
• OpenSearch
• S3
• CloudFront
• Route 53
• ACM
• WAF
• IAM
• KMS
• Secrets
• CI/CD
• Monitoring
• Logging
• Alerts
• SLOs
• Backups
• Disaster recovery
• Runbooks
• Security controls
• Infrastructure tests
• Generated files
• Remaining work
• Current milestone

────────────────────────────────────────

IMPLEMENTATION MILESTONES

INFRASTRUCTURE MILESTONE 11

Production Helm charts, application deployments, worker deployments, resource policies, health checks, and deployment configuration.

INFRASTRUCTURE MILESTONE 12

Autoscaling, workload-specific node pools, queue-based worker scaling, media workers, search workers, analytics workers, and notification workers.

INFRASTRUCTURE MILESTONE 13

Ingress, load balancing, CloudFront, Route 53, ACM, WAF, global routing, traffic management, and regional failover.

INFRASTRUCTURE MILESTONE 14

GitHub Actions, OIDC, CI/CD pipelines, ECR, image scanning, SBOM, image signing, release management, and rollback.

INFRASTRUCTURE MILESTONE 15

Multi-region deployment, regional clusters, regional recovery, database replication, S3 replication, search recovery, and failover procedures.

INFRASTRUCTURE MILESTONE 16

Prometheus, Grafana, Loki, Tempo, OpenTelemetry, dashboards, SLOs, alerts, and observability validation.

INFRASTRUCTURE MILESTONE 17

Database operations, Redis operations, Kafka operations, OpenSearch operations, backup automation, restore validation, and operational reconciliation.

INFRASTRUCTURE MILESTONE 18

Security hardening, IAM reviews, secret rotation, KMS, WAF, container security, dependency scanning, and compliance preparation.

INFRASTRUCTURE MILESTONE 19

Disaster-recovery testing, capacity planning, load validation, chaos/resilience testing, cost optimization, incident-response workflows, and runbooks.

INFRASTRUCTURE MILESTONE 20

Production smoke testing, final deployment validation, rollback validation, recovery validation, documentation, infrastructure certification, and final Project Index.

Each milestone should contain approximately 20–40 files where practical.

Every milestone must be validated before proceeding.

────────────────────────────────────────

OUTPUT FORMAT

For every generated file provide:

1. Exact file path
2. Complete file contents

Never truncate files.

Never summarize files instead of generating them.

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

This volume completes the production infrastructure and DevOps implementation.

It covers:

• Kubernetes
• Helm
• Production deployments
• Autoscaling
• CI/CD
• GitHub Actions
• ECR
• Container security
• Global routing
• CloudFront
• Route 53
• ACM
• WAF
• Multi-region infrastructure
• PostgreSQL operations
• Redis operations
• Kafka operations
• OpenSearch operations
• Media-worker infrastructure
• Observability
• SLOs
• Alerts
• Backups
• Disaster recovery
• Capacity planning
• Cost optimization
• Incident response
• Runbooks
• Infrastructure testing
• Production smoke testing
• Production readiness

Do not implement:

• Backend business logic
• Frontend code
• Mobile code
• Application-domain features

────────────────────────────────────────

QUALITY BAR

Treat this infrastructure as mission-critical global infrastructure supporting:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Massive CDN traffic
• Large audio-processing workloads
• High playback authorization traffic
• Large search traffic
• Large recommendation traffic
• Large analytics traffic
• Multiple subscription plans
• Multiple devices
• Offline-capable mobile applications
• Global rights and availability

Prioritize:

• Availability
• Security
• Scalability
• Reliability
• Recoverability
• Observability
• Zero-downtime deployment
• Automation
• Operational simplicity
• Cost efficiency
• Production readiness
