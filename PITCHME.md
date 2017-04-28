# ch 7 - Databases and AWS


## Databases!

  - Relational databases
    - PostgreSQL, MSSQL, ORACLE,
    - Tables, Referential integrity, Consistency
    - Structured Query Language
    - OLAP (Analytical, DataWarehouses) or OLTP (Transactional)
  - Amazon RDS
 

## Databases!

  - OLAP
    - Used for reporting, Analysis
    - High Query Complexity
    - Low Query Frequency
    - Batch Processing
  - OLTP
    - Main production database
    - Many IO operations per second
    - Not-so-complex queries
  - RDS is iften used for OLTP workloads, but it can be used for OLAP
  - Redshift is a data warehouse designed specially for OLAP
 

## Databases!


  - NoSQL databases
    - Simpler to use
    - More flexoble
    - Better performance than a RDBMS
    - Horizontal scalability at a fraction of the cost
    - Non-relational! (no tables, no sql)
    - Key/value-based or document-based (generally) that can evolve easily
    - Large volumes of data with high transaction rates
    - MongoDB, HBase, Cassandra, CouchDB, Amazon DynamoDB
  - You can deploy your own on an EC2 or use AWS DynamoDB
 

## Amazon Relational Database Service

  - Managed DB service
  - Focus on the app and schema and let AWS handle backup, patching, scaling and replication
  - Provides an enpoint that you can use to work with the database using SQL
  - Amazon doesn't provide shell access to the instance
  - Access to high-privileged procedures and system tables is restricted
  - Usually all it takes to work with RDS is changing the connection string
  - It is handled in DB instances
  - Provides an API
  - Computational power is handled by instance types (can change over time)


## Database Engines

  - MySQL - MultiAZ deployments, Horizontal Scaling with Read Replicas
  - PostgreSQL -  MultiAZ deployments, Horizontal Scaling with Read Replicas
  - Oracle - MultiAZ on every version/edition
  - MSSQL server -  MultiAZ only onthe standard and enterprise editions
  - Aurora - its a defacto cluster that spans over several AZ

## Licenses for MSSQL and Oracle can be purchased or BYOL

## Storage Options

  - Magnetic
  - General purpose
  - Provisioned IOPS

## Backup and Recovery

  - Automated Backups or Manual Snapshots
  - RPO - Maximum period of data loss
  - RTO - Maximum amount of downtime that is permitted to recover from Backup
  - Automated backups
    - Backups are done for entire instances
    - Retention period is 1 day by default, but can increase up to 35
    - When you delete the instances, these are completely lost
  - Manual DB snapshots
    - Initiated by the user
    - Aren't lost when the instance is deleted
    - Restore the DB Instance to a specific state
    - it impacts the performance while the db is being backed up
    - It is suggested to use multiAZ to reduce the impact of performing it

## Backup and Recovery

  - RDS allows for quick recovery of the DB
  - New DB instance is created for the recovery
  - AWS combines the daily backups with transaction logs to restore the DB instance to any point during the retention period

## HA with multiAZ

  - Allows to create a DB cluster across AZ
  - You can meet the most demanding RTO and RPO by using sync replication
  - A single endpoint is provided
  - A master DB is placed in one AZ and a slave in another
  - Automatically replicates the primary data to the slave DB in sync
  - Auto-failover for the most common failure scenarios

## Scaling Up and Out

  - Vertical Scalability - Adding more resources to a DB (Immediate/Scheduled)
    - Storage can scale from 5gb to 6tb
  - Horizontal Scalability with partitioning
    - more users and requests but requires additional logic in the app layer
  - Horizontal Scalability with read replicas
    - Offloading read transactions from the primary DB
    - For read intensive db workloads
    - Offloading reporting and data warehousing
    - Special DB Instance called replica


## Secutiry

## Use IAM policies!

## Deploy the DB instance into a private subnet!

## Restrict using security groups and ACLs

## Use in transit and at-rest encryption for data and logs (SSL, KMS, TDE)



