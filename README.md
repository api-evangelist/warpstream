# WarpStream (warpstream)

WarpStream is a diskless, Apache Kafka-compatible data streaming platform built directly on top of cloud object storage such as S3, GCP, and Azure. It eliminates local disks, broker rebalancing, and ZooKeeper by delivering Kafka compatibility through a single, stateless Go binary deployed as auto-scaling agents in customer VPCs. WarpStream offers a REST management API for programmatically controlling workspaces, virtual clusters, topics, ACLs, pipelines, agent pools, and BYOC deployments. The platform supports Exactly Once Semantics, transactions, a built-in Schema Registry, and Tableflow for streaming data into Iceberg tables, with pricing based on compute minutes and uncompressed data written and stored.

- APIs.json: https://raw.githubusercontent.com/api-evangelist/warpstream/refs/heads/main/apis.yml
- Naftiko: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=warpstream-api-evangelist&utm_content=repo

## Tags

- Kafka
- Streaming
- Serverless
- Object Storage
- BYOC
- Data Streaming
- Apache Kafka
- Message Queue
- Event Streaming

## APIs

| Name | Description | Docs |
|------|-------------|------|
| WarpStream Management API | REST API for managing clusters, virtual clusters, agent pools, topics, ACLs, pipelines, and BYOC deployments via POST requests authenticated with the warpstream-api-key header | [Docs](https://docs.warpstream.com/warpstream/reference/api-reference) |

## Plans / Rate Limits / FinOps

| Resource | File |
|----------|------|
| Plans & Pricing | [plans/warpstream-plans-pricing.yml](plans/warpstream-plans-pricing.yml) |
| Rate Limits | [rate-limits/warpstream-rate-limits.yml](rate-limits/warpstream-rate-limits.yml) |
| FinOps | [finops/warpstream-finops.yml](finops/warpstream-finops.yml) |

**Cluster Tiers:** Dev ($100/mo, 4,096 partitions), Fundamentals ($500/mo, 99.9% SLA, 16,384 partitions), Pro ($1,500/mo, 99.99% SLA, 50,000 partitions), Enterprise (custom, 99.999% SLA, 200,000+ partitions). Usage billed in 15-minute intervals with scale-to-zero — idle clusters are free. New accounts receive $400 in non-expiring free credits.

## Timestamps

- Created: 2026-06-13
- Modified: 2026-06-13

## Common

| Type | URL |
|------|-----|
| Website | https://www.warpstream.com/ |
| Documentation | https://docs.warpstream.com/warpstream |
| GitHub Org | https://github.com/warpstreamlabs |
| LinkedIn | https://www.linkedin.com/company/warpstream/ |
| Blog | https://www.warpstream.com/blog |
| Pricing | https://www.warpstream.com/pricing |
| Status Page | https://status.warpstream.com/ |
| X / Twitter | https://twitter.com/warpstream_labs |

## Maintainers

| Name | Email |
|------|-------|
| Kin Lane | kin@apievangelist.com |
