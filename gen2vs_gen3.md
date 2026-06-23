---
copyright:
  years: 2026
lastupdated: "2026-06-23"

keywords:

subcollection: db2-saas
---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Before you migrate: Standard/Enterprise vs Performance Plan
{: #gen2vs_gen3}

Before migrating your {{site.data.keyword.Db2_on_Cloud_long}} deployment from Standard/Enterprise Plan to Performance Plan, review the key differences between the environments. The Db2 Performance Plan is built on modern cloud infrastructure and provides improved scalability, automation, and configuration flexibility.

Understanding these differences helps you prepare your applications, connectivity, and operations for a smooth migration.

## What changes in Perfomance Plan
{: #gen3_change}

The Db2 Performance Plan is designed for data-intensive, mission-critical workloads. It combines Db2 capabilities with next-generation cloud infrastructure to deliver consistent performance, scalability, and high availability.

Key improvements include:

- Simplified operations with reduced management overhead
- Better performance through modern infrastructure
- Built-in scalability for growing workloads
- More flexible configuration and automation capabilities
- Support for Db2 v12.1 on the Performance Plan

The following sections describe the key functional differences between Standard/Enterprise Plan and Perfomance Plan.

## Standard/Enterprise Plan to Performance Plan: Key considerations
{: #key-consider}

### Storage and I/O scaling
{: #storage}

The Db2 Performance Plan introduces a more flexible approach to storage and performance management.

- **Independent scaling of storage and IOPS**

  You can scale storage capacity and input/output performance (IOPS) separately. This allows you to optimize cost and performance without over-provisioning resources.

- **Automatic storage scaling**

  Storage capacity automatically adjusts as your data grows. This reduces manual intervention and prevents capacity bottlenecks.

### Backup and recovery strategy
{: #backup_recovery}

The Db2 Performance Plan uses a snapshot-based backup model designed to improve efficiency and recovery speed.

- Snapshot-based backups for faster and more efficient recovery  
- Lower storage consumption  
- Improved backup and restore performance

Additional capabilities include:

- Self-service backup scheduling to align with business needs
- Point-in-time recovery (PITR) for precise restoration
- Continuous transaction log archiving to IBM Cloud Object Storage
- Automated disaster recovery backups stored securely

### High availability (HA)
{: #ha_gen2vsgen3}

The Db2 Performance Plan simplifies the HA architecture while maintaining reliability.

- **Two-node HA configuration** (compared to three-node in Standard/Enterprise Plan plans)
- Lower infrastructure cost with the same level of resiliency

How it works:

- Primary node handles read and write operations
- Standby node maintains synchronous replication
- Transactions are committed on both nodes before completion
- Automatic failover using **Automatic Client Reroute (ACR)**

High Availability (HA) operates within a single region (MZR) and ensures near-zero downtime during failover, scaling, and maintenance activities. 

**Disaster Recovery (DR)**: With [Geo‑Replicated Disaster Recovery](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-dr_gen) nodes, you can extend availability to another region by adding an on‑demand DR node, ensuring continued data access even if the primary region experiences an outage.



### Networking and connectivity
{: #net_conn}

The Db2 Performance Plan leverages Virtual Private Endpoints (VPE) to enable secure, private network connectivity between Db2 and your VPC environment. This provides a modern, streamlined approach to private access. You can learn more about VPE [here](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-vpeg).

In contrast, the earlier Standard and Enterprise plans relied on Cloud Service Endpoints (CSE) for private connectivity. As customers transition to the Performance plan, those requiring private network access will need to configure VPE for their environments.

For more details, refer to:
- [Connecting to IBM Cloud services privately using virtual private endpoints](https://cloud.ibm.com/docs/overview?topic=overview-endpoints-support)
- [Db2 Saas Connectivity Options](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-connect_options)

### Configurable Db2 parameters
{: #db2_config}

The Db2 Performance Plan provides enhanced configurability through API-based management.

- Configure Db2 system parameters directly
- Tune performance based on workload requirements
- Use DBM and registry variables for fine-grained control

You can retrieve available parameters using this [API](
https://cloud.ibm.com/apidocs/db2-on-cloud/db2-saas-perf-v4#gettuneableparameters). This level of configurability is not available in Standard/Enterprise Plan plans.

### Support for Db2 v12.1
{: #121_support}

The Db2 Performance Plan on IBM Cloud supports Db2 version 12.1, giving customers access to the latest and most advanced Db2 capabilities.

With the transition from Db2 11.5 to 12.1, users benefit from a range of new enhancements and features designed to improve performance, scalability, and overall database efficiency, including:

- Includes AI Query Optimizer capabilities that automatically tune performance and reduce operational overhead
- Vector support for AI Semantic search
- Intra-table-space Parallelism (ITP) for backup operations
- Namespace isolation by using the Db2 tenant object
- New registry variable for reserving memory for caching log records produced for the db2ReadLog() API
- The DB2_USE_FAST_LOG_PREALLOCATION performance variable allows the fast preallocation file system feature to reserve space for log files, so large log files can be created or altered faster. This variable is now ON by default.
- The ADMIN_MOVE_TABLE stored procedure is enhanced to provide better performance for row to columnar conversion through parallel and vectorized insert operations.
- Recovery time is now reduced in the unlikely event of a system crash
- Compact varchar enhancements now provide better performance of UPDATE and JOIN operations.
- Support for the latest International Components for Unicode (ICU) collations by introducing Unicode Collation Algorithm (UCA)–based collations through the CLDRCOLL collation keyword.
- Online movement of columnar tables using the ADMIN_MOVE_TABLE command.
- ADMIN_MOVE_TABLE provides faster move from row to columnar table format.
- ADMIN_MOVE_TABLE now works with range-clustered tables.
- Improvement to MASK at read
- Improved access plan management by the automatic generation of statement profiles
- GENERATE_UUID scalar function now returns the formatted string representation of a Universally Unique Identifier (UUID)
- GENERATE_UUID_BINARY scalar function returns the binary string representation of a UUID
- MongoDB 8.x client support
- Alter the precision of decimal-type columns in Db2 column-organized tables
- New transaction application lock types and shared locking for DBMS_LOCK

For more information, see [Whats's New](https://www.ibm.com/docs/en/db2/12.1.x?topic=database-whats-new)

### Terraform support
{: #terr_support}

The Db2 Performance Plan provides native support for Terraform, enabling modern infrastructure management.

- Automate provisioning and deployment
- Manage environments using infrastructure as code
- Improve consistency and reduce manual errors

This allows teams to integrate Db2 deployments into DevOps workflows and scale environments more efficiently.

## Planning your migration: What is different in Db2 Perfomance Plan
{: #migr_planning}

To prepare for migration, review the following actions:

1. **Plan connectivity**

   Configure Virtual Private Endpoints (VPE) if private access is required

2. **Validate application compatibility**

    - Review dependencies on Standard/Enterprise Plan behavior
    - For customers upgrading Db2 to v12.1: Test applications with the latest version.
    
    Customers can choose to remain on Db2 v11.5. Upgrading to v12.1 is optional and based on customer preference. Please note that upgrading to v12.1 may result in a longer outage window during migration.
    {: note}

3. **Update configurations**

    Identify Db2 parameters to tune using APIs

4. **Consider automation**

     Use Terraform for provisioning and environment management
