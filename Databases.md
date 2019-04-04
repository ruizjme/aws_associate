# Databases
* relational: database > table > row > fields
  - sql server
  - oracle
  - mysql
  - PostgreSQL
  - Aurora
  - MariaDB
* non-relational: database > collection > document > key-value pairs
  - DynamoDB (json, nosql)

* data warehousing
  - Cognos
  - Jaspersoft


## RDS (OLTP)
Pull data by row

RDS endpoint is a DNS name, not an IP (ip managed by aws).
Ensure RDS instance's security group allows inbound mysql traffic to 3306 into RDS instance from EC2 instance's SG.

## DynamoDB (NoSQL)

## RedShift (OLAP)
(for warehousing)
Pulls large numbers of records

## Elasticache (in-memory)
in-memory cache in the cloud (instead of disk-based). E.g. if prod db is under a lot of load, you can store most used queries in cache.
Supports two open source in-memory caching engines
* Memcached
* Redis


# Backups

* automated backups: restore db to any point in time within retention period (1-35 days). Takes full daily snapshot and transaction logs. Point in time down to seconds. Enabled by default. IO suspended while backup happens (backup window)
* database snapshots: always user initiated. standalone file. if RDS instance is deleted, they are not.

Restored DB has different endpoint.

Encryption at rest with KMS.

## Multi-AZ

For DR only. Any changes to DB A are automatically replicated to DB B. Since DNS endpoint is managed by AWS, if DB fails AWS updates record to point to DB B. Aurora has this enabled by default.

## Read-replica

Scale prod DB 'out' so servers can read off replicas. (Read only copies of main DB). (Not available for sql server or oracle)
Used for scaling (performance enhancement
  ) not DR.
Needs auto-backup to be enabled.
Up to 5 read replica copies of any db.
Can have read replicas of read replicas
Each replica has dns endpoint
Replicas can have multi-az.
Multi-az can have replicas.
Replicas can be promoted to become a main DB, but this breaks replication.
Replica can be in different region


# DynamoDB

NoSQL, single digit millisecond latency. Supports both document and key-value.
SSD storage in 3 geographically distinct data centres.
Great economy for reads, expensive for writes.
Can reserve capacity (1 or 3 year)
Scaling is really easy and has no downtime.

* Eventual consistent reads: within one second
* Strongly consistent reads:

## Costs

Provisioned throughput capacity
* Write $0.0065/hour/10 units
* Read $0.0065/hour/50 units

Storage cost
* $0.25/Gb/month


# RedShift
Pb scale warehouse. $0.25/hour for small
$1000/terabyte/year (1/10th of cost of other warehousing)

Single node (160Gb of data) or multi-node with leader node (manages client connection) and compute nodes (up to 128 nodes).

Column based. Storing data sequentially on disk.
10 times faster. Advanced compression (compression based, all items in column are the same data type)

MPP massively parallel processing. Automatically distributes load across nodes.

Pricing:
* Compute node hours
* Backup
* Data transfer

Encrypted in transit with ssl, at rest aes 256. Keys are managed by AWS or an be managed through KMS or HMS.

Single AZ available. Can restore snapshots to new AZ.

# Elasticache

in-memory cache in cloud. Improves performance of web apps. Takes load off DBS. Less latency.

E.g. recommendation engine, networking, media sharing, gaming.

* Memcached: Memory object caching system.
* Redis: Open source in-memory key value. Multi AZ. Supports master/slave replication.

Elasticache is good for read heavy and not prone to frequent changing. If DBs are heavily loaded.

# Aurora
AWS database engine. MySQL compatible. Speed, simplicity, cost effective. (1/10th of price of others). HA. performance.

10Gb. Scales in 10Gb increments. Up to 64 Tb

Compute can scale to 32vCPU and 244Gb RAM. (with a couple of min downtime)

2 copies of data in each AZ, min 3 AZ. (6 copies of data).

Transparently handle loss of up to 2 copies of data without affecting write availability. Up to 3 copies without affecting read availability. Self-healing (detect errors).

* Aurora replicas (15)
* Mysql read replicas (5)

Encryption, monitoring, Mulit AZ available (optional).

If replicas are made, they are readers (main one is writer). Use cluster endpoint. Traffic will be redirected in case of failover.
