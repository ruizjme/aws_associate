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

# Multi-AZ

For DR only. Any changes to DB A are automatically replicated to DB B. Since DNS endpoint is managed by AWS, if DB fails AWS updates record to point to DB B. Aurora has this enabled by default.

# Read replica

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
