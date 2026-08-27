You are operating in Senior Engineering Team Mode.

Build the production-ready infrastructure foundation for an enterprise-scale global music streaming and audio entertainment platform comparable in architectural scope to Spotify.

The platform is an original implementation.

Do not copy proprietary source code, internal architecture, branding, confidential implementation details, proprietary algorithms, or private implementation details from Spotify or any other company.

This prompt is completely independent and may be executed in a separate conversation.

The infrastructure must support the established backend, web frontend, mobile applications, music catalog, audio processing, playback, CDN delivery, subscriptions, payments, playlists, search, recommendations, podcasts, notifications, advertising, analytics, administration, and security architecture.

Do not redesign the application architecture.

Do not implement backend business logic.

Do not implement frontend code.

Do not implement mobile code.

Do not generate application-domain source code.

────────────────────────────────────────

MISSION

Build the foundational cloud and DevOps infrastructure required for:

• Global music streaming
• Large-scale audio delivery
• Large-scale catalog access
• Audio processing
• Search
• Recommendations
• Playlists
• User libraries
• Subscriptions
• Payments
• Podcasts
• Notifications
• Advertising
• Analytics
• Administration
• Multi-region deployment
• High availability
• Horizontal scaling
• Disaster recovery
• Zero-downtime operations

Support environments for:

• Local development
• Development
• Testing
• Performance testing
• Staging
• Production
• Disaster recovery

────────────────────────────────────────

PRIMARY TECHNOLOGY STACK

Cloud:

• AWS

Containers:

• Docker

Container Registry:

• Amazon ECR

Orchestration:

• Kubernetes
• Amazon EKS

Package Management:

• Helm

Infrastructure as Code:

• Terraform

CI/CD:

• GitHub Actions

Database:

• PostgreSQL
• Amazon RDS or Aurora PostgreSQL where justified

Cache:

• Redis
• Amazon ElastiCache where appropriate

Event Streaming:

• Kafka or Redpanda
• Managed alternative where justified

Search:

• Amazon OpenSearch or approved Elasticsearch infrastructure

Object Storage:

• Amazon S3

CDN:

• Amazon CloudFront

DNS:

• Amazon Route 53

TLS:

• AWS Certificate Manager

Secrets:

• AWS Secrets Manager
• Kubernetes secret integration
• Approved cloud-native secret management

Encryption:

• AWS KMS

Security:

• IAM
• WAF
• Security Groups
• Network ACLs
• Kubernetes NetworkPolicies
• Kubernetes RBAC
• Pod Security controls

Observability:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

────────────────────────────────────────

INFRASTRUCTURE PRINCIPLES

Prioritize:

• Security
• Availability
• Scalability
• Reliability
• Observability
• Recoverability
• Cost efficiency
• Operational simplicity
• Least privilege
• Automation

Avoid:

• Publicly exposed databases
• Long-lived credentials
• Single points of failure
• Unnecessary cross-region dependencies
• Manual infrastructure drift
• Secrets in source control
• Mutable production containers
• Uncontrolled Kubernetes permissions

────────────────────────────────────────

AWS ACCOUNT STRATEGY

Design an enterprise account strategy.

Evaluate separate AWS accounts for:

• Security
• Logging
• Shared services
• Development
• Testing
• Staging
• Production
• Disaster recovery

Define:

• Account ownership
• IAM boundaries
• Logging boundaries
• Billing boundaries
• Network boundaries
• Cross-account access

Production credentials must never be reused in development.

────────────────────────────────────────

REGION STRATEGY

Design:

• Primary production region
• Secondary production/recovery region
• Development region strategy
• Staging region strategy

Select regions according to:

• User latency
• Service availability
• Data-residency requirements
• Cost
• Disaster-recovery requirements

Do not assume every workload needs to be active-active across every region.

────────────────────────────────────────

ENVIRONMENT STRATEGY

LOCAL

Provide local infrastructure for:

• PostgreSQL
• Redis
• Kafka/Redpanda
• OpenSearch where practical
• S3-compatible local object storage where useful

DEVELOPMENT

Provide shared cloud infrastructure.

TESTING

Provide isolated or ephemeral resources where justified.

STAGING

Keep architecture close to production.

PRODUCTION

Use:

• Multi-AZ
• High availability
• Automated backups
• Production observability

DISASTER RECOVERY

Provide:

• Backup storage
• Recovery infrastructure
• Infrastructure reconstruction capability

────────────────────────────────────────

TERRAFORM ARCHITECTURE

Create a scalable Terraform organization.

Use reusable modules for:

• AWS accounts where applicable
• VPC
• Subnets
• Route tables
• Internet Gateway
• NAT
• VPC endpoints
• Security groups
• IAM
• KMS
• EKS
• Node groups
• RDS/Aurora
• ElastiCache
• Kafka/Redpanda
• OpenSearch
• S3
• CloudFront
• Route 53
• ACM
• WAF
• ECR
• Secrets Manager
• Monitoring
• Backup

Separate:

• Reusable modules
• Environment configuration
• Shared infrastructure
• Production infrastructure

────────────────────────────────────────

TERRAFORM STATE

Implement secure Terraform state.

Support:

• Remote state
• Encryption
• Versioning
• State locking
• Restricted access
• Separate environments

Never hard-code secrets into Terraform source.

Avoid passing sensitive secrets into Terraform state unnecessarily.

────────────────────────────────────────

NETWORK ARCHITECTURE

Design production VPCs with:

• Public subnets
• Private application subnets
• Private data subnets
• Multi-AZ deployment
• Internet Gateway
• NAT Gateways
• Route tables
• Security groups
• Network ACLs
• VPC endpoints

Define traffic flows between:

Internet
→ CloudFront
→ WAF
→ Load balancer
→ EKS
→ Internal services

and:

EKS
→ PostgreSQL
→ Redis
→ Kafka
→ OpenSearch
→ S3

────────────────────────────────────────

NETWORK SEGMENTATION

Separate:

• Edge
• Application
• Worker
• Data
• Management
• Observability

Apply least-privilege network rules.

Do not allow unrestricted east-west traffic.

────────────────────────────────────────

VPC ENDPOINTS

Use private endpoints where appropriate for:

• S3
• ECR
• CloudWatch/monitoring services
• Secrets Manager
• KMS
• Other AWS services required by workloads

Reduce unnecessary public internet traffic from private workloads.

────────────────────────────────────────

LOAD BALANCING

Design load balancing for:

• Web application
• Public APIs
• Playback authorization APIs
• Artist/creator APIs
• Administrative APIs
• Webhook endpoints

Support:

• TLS
• Health checks
• Connection draining
• Timeouts
• Multi-AZ balancing

Do not send high-volume audio bytes through normal application load balancers when CloudFront/S3 should serve them.

────────────────────────────────────────

CLOUDFRONT

Design CDN infrastructure for:

• Audio manifests
• Audio segments
• Artwork
• Podcast media
• Static web assets
• Public metadata where appropriate

Support:

• Cache policies
• Origin access control
• Signed access where needed
• Origin protection
• Compression
• Cache invalidation
• Regional failover
• Cost optimization

Immutable audio segments should be optimized for long-lived caching.

Short-lived authorization data must not be treated as immutable media.

────────────────────────────────────────

S3

Create secure storage architecture for:

• Original audio
• Processed audio
• Audio renditions
• HLS manifests
• Audio segments
• Artist artwork
• Album artwork
• Podcast artwork
• Podcast audio
• Creator uploads
• Reports
• Backups
• Temporary processing assets

Support:

• Versioning
• Encryption
• Lifecycle policies
• Access controls
• Bucket policies
• Cross-region replication where appropriate
• Object ownership controls

Keep media buckets private behind approved delivery paths.

────────────────────────────────────────

ECR

Configure Amazon ECR.

Support repositories for:

• Backend APIs
• Background workers
• Media-processing workers
• Search workers
• Analytics workers
• Web application

Support:

• Image scanning
• Lifecycle policies
• Immutable tags where appropriate
• Repository permissions
• Retention

Tag images with:

• Git SHA
• Release version
• Environment

────────────────────────────────────────

IAM

Implement least-privilege IAM.

Create roles for:

• Terraform
• GitHub Actions
• EKS
• Application services
• Media workers
• Analytics workers
• Search workers
• Notification workers
• Backup systems
• Monitoring

Prefer:

• OIDC
• Short-lived credentials
• Workload identity
• IAM Roles for Service Accounts

Do not use long-lived AWS keys when short-lived federation is available.

────────────────────────────────────────

KMS

Create KMS architecture for:

• S3
• RDS/Aurora
• Redis
• EBS
• Secrets
• Logs
• Backups
• Terraform state

Define:

• Key ownership
• Rotation
• Access policies
• Environment separation

────────────────────────────────────────

EKS FOUNDATION

Create foundational Amazon EKS architecture.

Support:

• Multi-AZ nodes
• Managed node groups where appropriate
• Workload identity
• Kubernetes RBAC
• NetworkPolicies
• Pod Security controls
• Cluster logging
• Cluster monitoring

Prepare workload classes for:

• API services
• Web services
• Media workers
• Search workers
• Analytics workers
• Notification workers
• General background workers
• Observability

────────────────────────────────────────

KUBERNETES NAMESPACES

Define logical namespaces such as:

• ingress
• applications
• workers
• media-processing
• observability
• security

Do not create excessive namespaces without operational value.

────────────────────────────────────────

NODE GROUPS

Create workload-specific node-group strategy.

Support:

• General application nodes
• CPU-optimized nodes
• Memory-optimized nodes
• Media-processing nodes
• Analytics nodes
• Observability nodes

Define:

• Labels
• Taints
• Tolerations
• Affinity
• Anti-affinity
• Topology spread

────────────────────────────────────────

KUBERNETES RESOURCE GOVERNANCE

Define:

• Resource requests
• Resource limits
• ResourceQuota
• LimitRange
• PodDisruptionBudget
• ServiceAccounts
• RBAC
• NetworkPolicies

Prevent:

• Noisy neighbors
• Unbounded resource consumption
• Privilege escalation

────────────────────────────────────────

POSTGRESQL INFRASTRUCTURE

Configure production PostgreSQL.

Support:

• Multi-AZ
• Automated backups
• Point-in-time recovery
• Read replicas
• Encryption
• TLS
• Monitoring
• Failover
• Maintenance windows
• Storage scaling
• Connection limits

Prepare for high-scale domains:

• Users
• Subscriptions
• Catalog
• Playlists
• Library
• Payments
• Administration

Do not expose PostgreSQL publicly.

────────────────────────────────────────

DATABASE CONNECTION MANAGEMENT

Prepare for:

• Connection pooling
• PgBouncer or approved pooling strategy
• Service-specific connection limits
• Read/write separation where appropriate

Prevent connection exhaustion during traffic spikes.

────────────────────────────────────────

REDIS INFRASTRUCTURE

Configure ElastiCache or approved Redis infrastructure.

Support:

• Multi-AZ
• Replication
• Automatic failover
• Encryption at rest
• TLS
• Authentication
• Monitoring

Prepare workloads for:

• Session caching
• Rate limiting
• Playback coordination
• Recommendation caching
• Search caching
• Queue infrastructure
• Distributed locks
• Temporary state

Redis must never become the system of record.

────────────────────────────────────────

KAFKA / REDPANDA INFRASTRUCTURE

Design production event infrastructure.

Support:

• Multiple brokers
• Multi-AZ placement
• Replication
• Persistent volumes
• TLS
• Authentication
• Topic lifecycle
• Retention
• Monitoring

Prepare for high-volume events:

• Playback
• Search
• Recommendations
• Catalog
• Subscriptions
• Payments
• Notifications
• Advertising
• Analytics

────────────────────────────────────────

OPENSEARCH

Configure production OpenSearch/Elasticsearch infrastructure.

Support:

• Multi-node deployment
• Multi-AZ
• Shards
• Replicas
• Encryption
• Access control
• Snapshots
• Monitoring

Search must remain rebuildable from authoritative catalog data.

────────────────────────────────────────

SECRETS MANAGEMENT

Use:

• AWS Secrets Manager
• Kubernetes external secret integration where appropriate

Manage:

• PostgreSQL credentials
• Redis credentials
• Kafka credentials
• Stripe secrets
• Webhook secrets
• OAuth secrets
• Notification provider credentials
• Search credentials

Support:

• Rotation
• Access control
• Audit
• Environment separation

Never commit secrets to Git.

────────────────────────────────────────

DNS

Configure Route 53 for:

• Public application domains
• API domains
• Media domains
• Administrative domains
• Internal service discovery where appropriate

Prepare for:

• Latency-based routing
• Health checks
• Failover
• Weighted routing

────────────────────────────────────────

TLS

Use AWS Certificate Manager.

Support:

• Web TLS
• API TLS
• CDN TLS
• Internal TLS where appropriate

Automate certificate renewal.

────────────────────────────────────────

WAF

Create WAF foundation.

Protect:

• Web
• API
• Admin APIs
• Creator APIs
• Webhooks

Support:

• Rate-based rules
• Managed OWASP protections
• Request-size limits
• Bot controls where appropriate
• IP rules
• DDoS integration

────────────────────────────────────────

BACKUP FOUNDATION

Design backup architecture for:

• PostgreSQL
• S3
• Search snapshots
• Terraform state
• Critical configuration
• Kubernetes configuration where appropriate

Support:

• Encryption
• Retention
• Versioning
• Cross-region replication
• Restore testing

────────────────────────────────────────

LOCAL DEVELOPMENT

Create Docker Compose infrastructure for local development.

Support:

• PostgreSQL
• Redis
• Kafka/Redpanda
• OpenSearch
• S3-compatible local object storage where appropriate

Local development must not depend on production AWS credentials.

────────────────────────────────────────

DOCKER FOUNDATION

Create standards for production containers.

Support:

• Multi-stage builds
• Minimal runtime images
• Non-root users
• Read-only filesystem where possible
• Health checks
• Graceful shutdown
• Dependency pinning
• Reproducible builds

Do not place:

• Passwords
• Secrets
• Cloud credentials
• Provider tokens

inside images.

────────────────────────────────────────

INFRASTRUCTURE OBSERVABILITY FOUNDATION

Prepare infrastructure for:

• OpenTelemetry
• Prometheus
• Grafana
• Loki
• Tempo

Monitor:

• EKS
• Kubernetes nodes
• Pods
• API workloads
• Workers
• PostgreSQL
• Redis
• Kafka
• OpenSearch
• S3
• CloudFront
• Load balancers

────────────────────────────────────────

INFRASTRUCTURE LOGGING

Implement centralized logging architecture.

Support:

• Structured logs
• JSON
• Loki
• Trace ID
• Request ID
• Correlation ID
• Retention
• Access control

Filter:

• Passwords
• Tokens
• Payment credentials
• Secrets
• Private keys
• Sensitive user data

────────────────────────────────────────

HEALTH AND AVAILABILITY FOUNDATION

Prepare infrastructure health checks for:

• API
• Web
• Workers
• PostgreSQL
• Redis
• Kafka
• Search
• S3
• Load balancers
• CDN

Distinguish:

• Liveness
• Readiness
• Dependency health

────────────────────────────────────────

DISASTER RECOVERY FOUNDATION

Prepare infrastructure for:

• Availability-zone failure
• Database failure
• Redis failure
• Kafka failure
• Search failure
• EKS failure
• S3 failure
• Region failure

Define:

• Recovery dependencies
• Recovery order
• Backup requirements
• Infrastructure reconstruction

────────────────────────────────────────

COST MANAGEMENT

Establish baseline cost controls.

Evaluate:

• EKS node sizing
• Autoscaling
• Reserved capacity
• Savings Plans
• Spot instances for safe batch workloads
• S3 lifecycle policies
• CloudFront caching
• Search sizing
• Database sizing
• Log retention

Do not reduce critical availability to save cost.

────────────────────────────────────────

INFRASTRUCTURE TESTING

Define tests for:

• Terraform formatting
• Terraform validation
• Terraform plan
• Module validation
• Helm validation
• Kubernetes manifests
• Docker builds
• Image scanning
• IAM policies
• Security groups
• NetworkPolicies
• WAF
• Backup configuration

────────────────────────────────────────

DOCUMENTATION

Generate:

• AWS architecture
• Account strategy
• Region strategy
• Environment strategy
• VPC architecture
• Network segmentation
• IAM architecture
• KMS architecture
• EKS architecture
• Kubernetes foundation
• Terraform structure
• PostgreSQL infrastructure
• Redis infrastructure
• Kafka infrastructure
• OpenSearch infrastructure
• S3 architecture
• CloudFront architecture
• Route 53 architecture
• ACM architecture
• WAF architecture
• Secrets management
• Backup strategy
• Disaster recovery foundation
• Local Docker environment
• Infrastructure testing

────────────────────────────────────────

PROJECT INDEX

Maintain the infrastructure Project Index.

Track:

• AWS accounts
• Regions
• Environments
• VPCs
• Subnets
• Route tables
• Security groups
• IAM roles
• KMS keys
• EKS clusters
• Node groups
• Namespaces
• Terraform modules
• ECR repositories
• Docker configurations
• PostgreSQL
• Redis
• Kafka/Redpanda
• OpenSearch
• S3
• CloudFront
• Route 53
• ACM
• WAF
• Secrets
• Backup infrastructure
• Observability
• Generated files
• Remaining work
• Current milestone
• Dependencies

────────────────────────────────────────

IMPLEMENTATION MILESTONES

INFRASTRUCTURE MILESTONE 1

Terraform foundation, remote state, providers, environment structure, naming, tagging, variables, outputs, and reusable-module architecture.

INFRASTRUCTURE MILESTONE 2

AWS networking: VPCs, subnets, routing, NAT, security groups, Network ACLs, and VPC endpoints.

INFRASTRUCTURE MILESTONE 3

IAM, OIDC, GitHub Actions identity, EKS workload identity, KMS, ECR, and secrets foundations.

INFRASTRUCTURE MILESTONE 4

EKS cluster foundation, node groups, namespaces, RBAC, NetworkPolicies, resource governance, and autoscaling foundations.

INFRASTRUCTURE MILESTONE 5

PostgreSQL infrastructure, backups, replicas, failover, monitoring, and connection-management foundation.

INFRASTRUCTURE MILESTONE 6

Redis, Kafka/Redpanda, and OpenSearch production infrastructure.

INFRASTRUCTURE MILESTONE 7

S3, CloudFront, Route 53, ACM, WAF, media delivery, and CDN foundations.

INFRASTRUCTURE MILESTONE 8

Dockerfiles, Docker Compose, local development environment, ECR integration, and container-security foundations.

INFRASTRUCTURE MILESTONE 9

Infrastructure observability, logging, metrics, dashboards foundations, health checks, and alerting foundations.

INFRASTRUCTURE MILESTONE 10

Backup validation, disaster-recovery foundation, infrastructure testing, cost controls, documentation, and final Project Index.

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

This volume covers:

• AWS foundation
• Terraform
• Networking
• IAM
• KMS
• EKS foundation
• Kubernetes foundation
• Docker
• ECR
• PostgreSQL infrastructure
• Redis infrastructure
• Kafka/Redpanda infrastructure
• OpenSearch infrastructure
• S3
• CloudFront
• Route 53
• ACM
• WAF
• Secrets management
• Backups
• Disaster-recovery foundation
• Local development infrastructure
• Infrastructure observability foundation
• Infrastructure testing foundation

Do not implement:

• Backend domain logic
• Frontend features
• Mobile features
• Application business logic
• Production CI/CD pipelines
• Full multi-region failover automation

Those belong to later infrastructure and DevOps phases.

────────────────────────────────────────

QUALITY BAR

Treat this infrastructure as the foundation of a globally distributed music-streaming platform.

Assume:

• Hundreds of millions of users
• Tens of millions of concurrent listeners
• Millions of tracks
• Massive CDN traffic
• High playback-authorization traffic
• Large audio-processing workloads
• High search traffic
• Large recommendation workloads
• Large analytics volumes
• Multiple subscription plans
• Multiple devices
• Offline-capable mobile applications
• Global content rights
• High availability
• Disaster recovery
• Strict security requirements

Prioritize:

• Security
• Availability
• Scalability
• Reliability
• Observability
• Recoverability
• Cost efficiency
• Operational simplicity
• Automation
• Production readiness
