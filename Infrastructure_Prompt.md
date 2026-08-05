Using the approved Architecture Blueprint and the Master Prompt above.

Begin infrastructure and DevOps implementation ONLY.

Do NOT generate backend business logic.

Do NOT generate frontend or mobile code.

Do NOT redesign the architecture.

Assume the Architecture Blueprint has been approved and the Backend and Frontend implementations will follow it exactly.

Your responsibility is to build the complete production infrastructure, cloud platform, media delivery network, CI/CD, observability, security, disaster recovery, and operational tooling for the enterprise music streaming platform.

Generate code incrementally according to the Master Prompt milestone strategy.

────────────────────────────────────────

MISSION

Build a complete enterprise-grade cloud infrastructure capable of supporting a Spotify-scale music streaming platform.

The infrastructure must support:

- 50M+ registered users
- 10M+ daily active listeners
- Hundreds of millions of tracks
- Millions of concurrent audio streams
- Global content delivery
- Multi-region deployment
- Zero-downtime deployments
- High availability
- Horizontal auto-scaling

The platform must be cloud-native, resilient, observable, secure, and cost-efficient.

────────────────────────────────────────

TARGET ENVIRONMENTS

Generate infrastructure for:

- Local Development
- Development
- Testing
- Staging
- Production
- Disaster Recovery

────────────────────────────────────────

CLOUD PLATFORM

Target AWS.

Generate infrastructure for:

Networking

- VPC
- Public Subnets
- Private Subnets
- Multi-AZ Architecture
- NAT Gateways
- Internet Gateway
- Route Tables
- Security Groups
- Network ACLs

Compute

- Amazon EKS
- Managed Node Groups
- Cluster Autoscaler
- Karpenter
- Horizontal Pod Autoscaler
- Vertical Pod Autoscaler

Load Balancing

- Application Load Balancer
- Internal Load Balancers

Storage

- Amazon S3
- Amazon EBS
- Amazon EFS

Database

- PostgreSQL
- Read Replicas
- Automated Backups
- Point-in-Time Recovery (PITR)

Cache

- Redis

Search

- OpenSearch / Elasticsearch

Messaging

- BullMQ
- Redis Queues

Registry

- Amazon ECR

DNS

- Route53

Certificates

- AWS Certificate Manager

Secrets

- AWS Secrets Manager

CDN

- Amazon CloudFront

────────────────────────────────────────

MEDIA DELIVERY INFRASTRUCTURE

Design infrastructure for:

Audio Upload Endpoints

CloudFront Distribution

Origin Access Control

HLS Adaptive Streaming

Regional Edge Caching

Signed URLs

Signed Cookies

Album Artwork CDN

Waveform Asset Delivery

Lyrics Delivery

Metadata Delivery

Cache Invalidation

Storage Lifecycle Policies

Cold Storage Strategy

────────────────────────────────────────

AUDIO PROCESSING INFRASTRUCTURE

Generate scalable FFmpeg processing infrastructure.

Support:

Worker Pools

Dedicated Processing Nodes

Queue Prioritization

Adaptive Bitrate Encoding

Audio Normalization

Waveform Generation

Artwork Processing

Metadata Extraction

Retry Policies

Dead Letter Queues

Processing Metrics

Processing Dashboards

────────────────────────────────────────

CONTAINERIZATION

Generate:

Development Dockerfiles

Production Dockerfiles

Multi-stage Builds

Docker Compose

Development Stack

Production Images

Image Optimization

Image Signing

Container Security

────────────────────────────────────────

KUBERNETES

Generate manifests for:

Namespaces

Deployments

StatefulSets

DaemonSets

Jobs

CronJobs

Services

Ingress

ConfigMaps

Secrets

Persistent Volumes

Persistent Volume Claims

Network Policies

Pod Security Standards

Service Accounts

RBAC

Resource Quotas

Limit Ranges

Pod Disruption Budgets

Horizontal Pod Autoscalers

Vertical Pod Autoscalers

────────────────────────────────────────

HELM

Generate:

Reusable Helm Charts

Environment Overrides

Secrets Integration

Values Files

Chart Documentation

────────────────────────────────────────

INFRASTRUCTURE AS CODE

Generate Terraform modules for:

Networking

IAM

EKS

PostgreSQL

Redis

OpenSearch

S3

CloudFront

ECR

Load Balancers

DNS

Certificates

Secrets

Monitoring

Logging

Backups

Disaster Recovery

────────────────────────────────────────

CI/CD

Generate GitHub Actions workflows for:

Formatting

Linting

Unit Tests

Integration Tests

Security Scans

Dependency Scans

Container Builds

Container Scanning

Artifact Publishing

Preview Environments

Development Deployment

Staging Deployment

Production Deployment

Canary Releases

Blue-Green Deployments

Automatic Rollback

Semantic Versioning

Release Tagging

────────────────────────────────────────

DATABASE OPERATIONS

Generate:

Migration Pipelines

Read Replica Configuration

Partitioning Support

Connection Pooling

Backup Automation

Restore Automation

Monitoring

Performance Dashboards

────────────────────────────────────────

REDIS

Configure:

High Availability

Replication

Persistence

Sentinel-ready Architecture

Distributed Locks

Recommendation Cache

Playback Cache

Monitoring

Automatic Failover

────────────────────────────────────────

SEARCH INFRASTRUCTURE

Configure:

OpenSearch / Elasticsearch Cluster

Index Templates

Snapshots

Backup

Recovery

Monitoring

Scaling

Hot/Warm Architecture

────────────────────────────────────────

OBJECT STORAGE

Configure:

Audio Storage

Artwork Storage

Waveform Storage

Lyrics Storage

Metadata Storage

Temporary Upload Storage

Versioning

Lifecycle Rules

Cross-Region Replication

Encryption

Storage Classes

────────────────────────────────────────

OBSERVABILITY

Generate:

Prometheus

Grafana

Loki

OpenTelemetry

Jaeger-compatible Tracing

Structured Logging

Playback Dashboards

Streaming Dashboards

Recommendation Dashboards

Infrastructure Dashboards

Business Metrics Dashboards

────────────────────────────────────────

ALERTING

Generate alerts for:

CPU

Memory

Disk

Node Health

Database Health

Redis Health

Search Health

Queue Health

Streaming Latency

Playback Errors

CDN Errors

Processing Failures

Application Health

SSL Expiration

Backup Failures

────────────────────────────────────────

LOGGING

Generate centralized logging using:

Loki

Structured JSON Logs

Correlation IDs

Trace IDs

Audit Logs

Retention Policies

────────────────────────────────────────

HEALTH CHECKS

Implement:

Liveness Probes

Readiness Probes

Startup Probes

Database Health

Redis Health

Search Health

Storage Health

Streaming Health

Media Processing Health

CDN Connectivity

────────────────────────────────────────

SECURITY

Implement:

TLS Everywhere

IAM Least Privilege

Kubernetes RBAC

Network Policies

Secrets Rotation

Container Scanning

Image Signing

Runtime Security

Encryption at Rest

Encryption in Transit

WAF-ready Architecture

DDoS-ready Architecture

OWASP Best Practices

SOC 2-ready Controls

PCI DSS Readiness (Subscriptions)

────────────────────────────────────────

BACKUPS

Generate:

Database Backups

Redis Backups

OpenSearch Snapshots

S3 Replication

Snapshot Policies

Retention Policies

Restore Procedures

Backup Verification

────────────────────────────────────────

DISASTER RECOVERY

Design:

Recovery Time Objective (RTO)

Recovery Point Objective (RPO)

Cross-Region Failover

Database Recovery

Redis Recovery

Search Recovery

Application Recovery

Traffic Failover

Operational Runbooks

────────────────────────────────────────

PERFORMANCE

Optimize:

Autoscaling

Connection Pooling

CloudFront Edge Caching

Streaming Throughput

Compression

Node Scaling

Worker Scaling

Resource Requests

Resource Limits

────────────────────────────────────────

COST OPTIMIZATION

Design:

Spot Instance Strategy

Reserved Capacity Strategy

Storage Tiering

CloudFront Optimization

Autoscaling Policies

Cloud Cost Monitoring

Lifecycle Policies

────────────────────────────────────────

COMPLIANCE

Prepare infrastructure for:

SOC 2

ISO 27001

GDPR

CCPA

PCI DSS (Subscriptions)

Audit Logging

────────────────────────────────────────

TESTING

Generate infrastructure testing for:

Terraform Validation

Helm Validation

Kubernetes Validation

Disaster Recovery Testing

Backup Restoration Testing

Streaming Load Testing

Audio Processing Stress Tests

Smoke Tests

Chaos Engineering Readiness

────────────────────────────────────────

DOCUMENTATION

Generate:

Infrastructure Overview

Deployment Guide

Environment Guide

Secrets Management Guide

Media Pipeline Guide

Monitoring Guide

Incident Response Guide

Runbooks

Disaster Recovery Guide

Maintenance Guide

Capacity Planning Guide

────────────────────────────────────────

PROJECT ORGANIZATION

Maintain throughout development:

Current Milestone

Generated Infrastructure Files

Terraform Modules

Helm Charts

Docker Images

GitHub Actions

Monitoring Components

Networking Components

Media Infrastructure

Remaining Work

────────────────────────────────────────

OUTPUT FORMAT

For every generated file provide:

1. Exact file path
2. Complete file contents

Never generate placeholders.

Never generate pseudo-code.

Never omit implementations.

Never regenerate unchanged files.

Only modify files when required.

────────────────────────────────────────

STOP CONDITIONS

Generate the infrastructure incrementally according to the Master Prompt.

Each milestone should contain approximately 20–40 files.

At the end of every milestone:

- Verify the infrastructure is deployable.
- Update the project index.
- List completed infrastructure components.
- Identify the next file to generate.

STOP and wait for approval before generating the next milestone.
