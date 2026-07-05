---
title: "Week 6 Worklog"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

* Master the core concepts and management operations of **Amazon DynamoDB**.
* Learn about and deploy **Amazon ElastiCache for Redis**.

### Tasks to be carried out this week:

| Topic | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Amazon DynamoDB | **DynamoDB Core Concepts** <br> - DynamoDB is a fully managed NoSQL database service with fast, predictable performance, seamless scalability, and encryption at rest <br> - Core components: tables, primary keys (partition key and composite key), secondary indexes (Global and Local), data types, read consistency models <br> - Read/Write Capacity modes: on-demand and provisioned <br> - Backup & recovery: on-demand backup, point-in-time recovery up to 35 days, TTL <br> - Managed via Console (create tables, CRUD, GSI), via CloudShell (CLI), and via AWS SDK/Python Boto3 | 05/25/2026 | 05/31/2026 | AWS Study Group |
| Amazon ElastiCache | **ElastiCache for Redis** <br> - A fully managed in-memory caching service with automatic failure detection, recovery, backups, and patching <br> - Core components: clusters, nodes, shards (up to 500 shards with cluster mode enabled) <br> - Cluster modes: Cluster Mode Disabled and Cluster Mode Enabled <br> - Node storage types: Standard and memory-optimized, deployable within a VPC <br> - Created clusters via Console and CLI: subnet groups, cluster mode, permissions, and connectivity <br> - Used the AWS SDK: create cluster, connect, Set/Get, hash, publish/subscribe, stream read/write | 05/25/2026 | 05/31/2026 | AWS Study Group |

# Week 6 Achievements

## NoSQL Database (DynamoDB)
- Gained a clear understanding of core components: tables, primary keys, secondary indexes (GSI/LSI), data types, and read consistency.
- Understood the difference between On-Demand and Provisioned Capacity modes.
- Practiced CRUD operations, creating and querying GSIs via Console, CloudShell, and the AWS SDK (Python/Boto3).
- Studied backup/recovery mechanisms: on-demand backup, PITR (35 days), TTL.

## In-Memory Caching (ElastiCache for Redis)
- Understood core components: clusters, nodes, and shards (up to 500 shards with cluster mode enabled).
- Distinguished between Cluster Mode Enabled/Disabled and node storage types.
- Practiced creating clusters via Console and CLI (subnet groups, permissions, connectivity).
- Used the AWS SDK to perform Set/Get, hash, publish/subscribe, and stream read/write operations.
