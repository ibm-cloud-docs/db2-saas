---

copyright:
  years: 2026
lastupdated: "2026-09-02"

keywords: monitoring for code engine, performance metrics, monitor, metrics, requests, pods, application, attributes, jobrun, panic mode

subcollection: db2-saas

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Monitoring for {{site.data.keyword.Db2_on_Cloud_short}}
{: #monitor}

Get insight into your {{site.data.keyword.Db2_on_Cloud_short}} instance. These metrics can help you find bottlenecks or predict possible production problems.



For additional details on platform metrics, please see [Platform Metrics Introduction](https://www.ibm.com/cloud/blog/announcements/introducing-ibm-cloud-platform-metrics-for-db2-on-cloud). {: important}

Monitoring metrics are currently available for only Enterprise and Standard plans. Lite plans are currently not supported.
{: important}

Sharing metrics with customers is not yet supported on Performance plans. Sharing logs with customers is supported.
{: important}

## Set up your {{site.data.keyword.Db2_on_Cloud_short}} service instance
{: #setup-monitor}

To set up Monitoring for {{site.data.keyword.Db2_on_Cloud_short}}, you must create a service instance and then enable Platform Metrics in the same region as the {{site.data.keyword.Db2_on_Cloud_short}} instance  that you want to monitor. If you have deployments in more than one region, you must provision Monitoring and enable platform metrics for each region.

To set up {{site.data.keyword.mon_short}},

1. From the {{site.data.keyword.cloud_notm}} navigation menu, select **Observability**.
2. Select **Monitoring**.
3. Either use an existing {{site.data.keyword.mon_short}} service instance or create a new one.
4. After the instance is ready, enable platform metrics by clicking **Configure platform metrics**.
5. Select a region and then a {{site.data.keyword.mon_short}} instance from that region. If you have deployments in more than one region, you must provision {{site.data.keyword.mon_short}} and enable platform metrics for each region.

## Accessing your {{site.data.keyword.mon_full_notm}} metrics
{: #access-monitor}

To see your {{site.data.keyword.Db2_on_Cloud_short}} customer metrics dashboards in {{site.data.keyword.mon_short}}:

1. From the {{site.data.keyword.cloud_notm}} navigation menu, select **Observability**.
2. Select **Monitoring**.
3. Select **View {{site.data.keyword.mon_full_notm}}** to open the dashboard.

For more information, see [{{site.data.keyword.mon_short}} Getting started tutorial](/docs/monitoring?topic=monitoring-getting-started).

## Metrics available by Service Plan
{: metrics-by-plan}
​
| Metric Name |
|-----------|
| [Database Availability Check](#ibm_db2_db_availability_check) |
| [Database commits time](#ibm_db2_db_commits_time) |
| [Database rollbacks](#ibm_db2_db_rollbacks) |
| [Disaster recovery Log Gap](#ibm_db2_dr_log_gap) |
| [High Availability Disaster Recovery Log Gap](#ibm_db2_hadr_log_gap) |
| [Is disaster recovery connected?](#ibm_db2_is_dr_connected) |
| [Is disaster recovery configured?](#ibm_db2_is_dr_configured) |
| [Last backup duration in minutes](#ibm_db2_last_backup_duration_minutes) |
| [Log Disk wait](#ibm_db2_log_disk_wait) |
| [Number of Unique ID statements](#ibm_db2_uid_stmts) |
| [Number of rows deleted](#ibm_db2_rows_deleted) |
| [Number of rows updated](#ibm_db2_rows_updated) |
| [Numbers of rows inserted](#ibm_db2_rows_inserted) |
| [Time since last backup in hours](#ibm_db2_since_last_backup_hours) |
| [Total Activities Aborted](#ibm_db2_db_act_aborted) |
| [Total Activities Completed](#ibm_db2_db_act_completed) |
| [Total Activities Rejected](#ibm_db2_db_act_rejected) |
| [Total Connections](#ibm_db2_total_conn) |
| [Total number of commits](#ibm_db2_db_num_commits) |


​
### Database Availability Check
{: #ibm_db2_db_availability_check}
​
​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_availability_check`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The current status of the database.` |
{: caption="Database availability check metric" caption-side="top"}


​
### Database commits time
{: #ibm_db2_db_commits_time}
​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_commits_time`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Indicates the number of applications that are currently connected to the database.` |
{: caption="Database commits time metric" caption-side="top"}

​
### Database rollbacks
{: #ibm_db2_db_rollbacks}
​​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_rollbacks`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total number of rollback statements issued by the client application and total number of rollbacks initiated internally by the database manager.` |
{: caption="Database rollback metric" caption-side="top"}

​
### Disaster recovery Log Gap
{: #ibm_db2_dr_log_gap}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_dr_log_gap`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Disaster Recovery Log Gap​.` |
{: caption="Disaster recovery Log Gap metric" caption-side="top"}

​
### High Availability Disaster Recovery Log Gap
{: #ibm_db2_hadr_log_gap}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_hadr_log_gap`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `HADR Log Gap monitor element This element shows the recent average of the gap between the PRIMARY_LOG_POS value and STANDBY_LOG_POS value. The gap is measured in number ofbytes.` |
{: caption="High Availability disaster recovery log gap metric" caption-side="top"}

​
### Is disaster recovery connected?
{: #ibm_db2_is_dr_connected}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_is_dr_connected`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Availability disaster recovery connection status of the database.` |
{: caption="Disaster recovery status metric" caption-side="top"}


### Is disaster recovery configured?
{: #ibm_db2_is_dr_configured}


| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_is_dr_configured`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Is this formation configured with DR.` |
{: caption="Table 7: Metric metadata" caption-side="top"}

​
### Last backup duration in minutes
{: #ibm_db2_last_backup_duration_minutes}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_last_backup_duration_minutes`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The duration of the last successful backup.` |
{: caption="Last backup time mteric" caption-side="top"}

​
### Log Disk wait
{: #ibm_db2_log_disk_wait}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_log_disk_wait`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The number of times agents have to wait for log data to write to disk.` |
{: caption="Log Disk wait metric" caption-side="top"}

​
### Number of Unique ID statements
{: #ibm_db2_uid_stmts}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_uid_stmts`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The number of UPDATE, INSERT, MERGE and DELETE statements that were executed.` |
{: caption="Number of unique ID statements metric" caption-side="top"}

​
### Number of rows deleted
{: #ibm_db2_rows_deleted}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_rows_deleted`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total of number of row deletions attempted and total number of rows deleted from the database as a result of internal activity.` |
{: caption="Number of rows deleted metric" caption-side="top"}

​
### Number of rows updated
{: #ibm_db2_rows_updated}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_rows_updated`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total number of row updates attempted and total number of rows updated from the database as a result of internal activity.` |
{: caption="Number of rows updated metric" caption-side="top"}

​
### Numbers of rows inserted
{: #ibm_db2_rows_inserted}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_rows_inserted`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total number of row insertions attempted and total number of rows inserted  from the database as a result of internal activity.` |
{: caption="Number of rows inserted metric" caption-side="top"}

​
### Time since last backup in hours
{: #ibm_db2_since_last_backup_hours}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_since_last_backup_hours`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The number of hours since there was a last successful backup.` |
{: caption="Time since last backup in hours metric" caption-side="top"}

​
### Total Activities Aborted
{: #ibm_db2_db_act_aborted}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_act_aborted`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The total number of coordinator activities at any nesting level that completed with errors.` |
{: caption="Total activities aborted metric" caption-side="top"}

​
### Total Activities Completed
{: #ibm_db2_db_act_completed}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_act_completed`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The total number of coordinator activities at any nesting level that completed successfully.` |
{: caption="Total activities completed metric" caption-side="top"}

​
### Total Activities Rejected
{: #ibm_db2_db_act_rejected}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_act_rejected`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The total number of coordinator activities at any nesting level that were rejected instead of being allowed to execute.` |
{: caption="Total activities rejected metric" caption-side="top"}

​
### Total Connections
{: #ibm_db2_total_conn}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_total_conn`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Indicates the number of applications that are currently connected to the database.` |
{: caption="Total connections metric" caption-side="top"}

​
### Total number of commits
{: #ibm_db2_db_num_commits}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_num_commits`|
| `Metric Type` | `counter` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` , `Resource` |
| `Metric Description` | `Total number of commit statements issued by the client application and the total number of commits initiated internally by the database manager.` |
{: caption="Total number of commits metric" caption-side="top"}

​
## Attributes for Segmentation
{: attributes}
​
### Global Attributes
{: global-attributes}
​
The following attributes are available for segmenting all of the metrics listed above
​
| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of public, dedicated or local |
| `Location` | `ibm_location` | The location of the monitored resource - this may be a region, data center or global |
| `Resource` | `ibm_resource` | The database member resource being measured by the service |
| `Scope` | `ibm_scope` | The scope is the account, organization or space GUID associated with this metric |
| `Service name` | `ibm_service_name` | Name of the service generating this metric |
​
### Additional Attributes
{: additional-attributes}
​
The following attributes are available for segmenting one or more attributes as described in the reference above.  Please see the individual metrics for segmentation options.
​
| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance the metric is associated with |

# Monitoring
The Monitoring module in IBM CaaS provides a centralized view of database health, performance, and resource utilization. It enables database administrators and users to monitor real-time activity, analyze performance trends, and identify potential issues across database workloads and system resources.

The Monitoring page combines high-level performance summaries with detailed operational metrics, helping users quickly assess the current state of a database and investigate performance, availability, or resource-related concerns.

## Database Selection
The database selection dropdown allows users to choose a database and view monitoring data specific to the selected database.
![Database Selection](image.png)


## Tags
Tags help organize and categorize databases. Users can add or remove tags from the selected database for easier identification and filtering.
![tags](image.png)

## Overview
The Monitoring page provides visibility into key aspects of database operation, including:
- Database responsiveness and workload activity
- Throughput and transaction trends
- CPU, memory, storage, and log utilization
- SQL statement execution and package cache activity
- Locking and contention events
- Application and connection behaviour
- Workload management statistics
- Storage and tablespace performance
Users can select a database and view monitoring data across multiple categories using configurable charts and metric tabs.

## Summary Dashboard
At the top of the Monitoring page, summary charts provide an overview of database performance and activity.

### Responsiveness
Displays the distribution of statement execution times, helping identify slow-running workloads and performance bottlenecks.

## Throughput
Shows database activity trends such as statements processed, transactions executed, and rows accessed over time.

## Resource Utilization
Provides visibility into resource consumption, including CPU, memory, storage, and log space usage. These charts help users quickly identify unusual activity and determine where further investigation may be required.

## Contention
Displays locking and concurrency activity, helping identify lock waits and contention that may impact database performance.

## Time Spent
Shows how database request processing time is distributed across SQL execution, I/O operations, lock waits, and other activities.

## Response Time
Provides visibility into database response time trends, helping identify latency issues and changes in database responsiveness over time.
![Response Time](image-1.png)

## Compare Database
The Compare Database feature enables users to compare performance and resource metrics across multiple databases.
Users can:
- Select one or more databases for comparison
- Choose specific monitoring charts and metrics
- Adjust the timeline or monitoring period
- Compare trends side-by-side across databases
- Identify differences in workload behaviour, resource consumption, and performance patterns

This feature is useful for capacity planning, performance benchmarking, troubleshooting, and evaluating the impact of configuration or workload changes across environments.
![Compare Database 1](image-2.png)
![Compare Database 2](image-3.png)

## Monitoring Categories
Detailed monitoring information is organized into categories that focus on specific areas of database activity.

## Database Monitoring
Provides visibility into overall database activity, usage patterns, partition behaviour, and workload distribution.

## Statement Monitoring
Displays SQL execution information, including running statements, package cache activity, and stored procedure execution details.

## Locking Monitoring
Helps identify lock contention and waiting conditions by providing information about blockers, waiters, locked objects, and locking events.

## Application Monitoring
Provides insights into application activity, connections, utilities, units of work, and event monitor data.

## Throughput Monitoring
Shows connection activity and operating-system-level processing metrics that affect database throughput.

## Memory Monitoring
Displays memory utilization at both the instance and database levels, helping identify memory pressure and allocation trends.

## I/O Monitoring
Provides information about buffer pool activity, prefetch operations, and logging performance.

## Storage Monitoring
Helps monitor storage utilization, table performance, tablespace performance, and capacity trends.

## Workload Management Monitoring
Provides visibility into workload management activity, service classes, and workload-level resource consumption.
![Workload management 1](image-4.png)
![Workload management 2](image-5.png)

## Customization and Analysis
The Monitoring page includes tools that help users focus on the information most relevant to their environment.
Users can:
- Filter monitoring data
- Select different time ranges
- Refresh or pause monitoring views
- Synchronize charts for easier analysis
- Add additional charts
- Customize visible monitoring tabs

These capabilities allow users to tailor the monitoring experience to specific operational and troubleshooting requirements.

## Typical Use Cases
![typical use cases](image-6.png)
Use the Monitoring module to:
- Monitor overall database health and performance
- Investigate slow-running workloads
- Analyze resource consumption trends
- Identify locking and contention issues
- Monitor application and connection activity
- Review storage and memory utilization
- Compare performance across multiple databases
- Support troubleshooting and capacity planning activities

## Notes
- Available monitoring data depends on database activity and configuration.
- Some monitoring views may display limited information if no related activity is occurring.
- Monitoring metrics are updated periodically based on the selected timeframe.
- Compare Database provides comparative analysis across databases using selected charts and timelines.
- The Monitoring module is intended to provide both high-level visibility and detailed operational insights from a single interface.

# CaaS Monitoring Profile
The Monitoring Profiles feature defines how monitoring is applied to databases managed through the service. A monitoring profile acts as a monitoring policy that controls how performance and operational data is collected and retained for associated databases.
For cloud databases, IBM CaaS automatically assigns instances to a system-managed Cloud monitoring profile, ensuring that monitoring starts without any manual configuration.

## Overview
When a cloud database instance is added to IBM CaaS:
- The instance is automatically associated with the Cloud monitoring profile
- Monitoring begins using predefined collection settings
- The database becomes available in monitoring views and dashboards
- The profile remains active and continues to manage monitoring for all associated databases

The Cloud monitoring profile is managed by the platform and cannot be modified by users.

## Accessing Monitoring Profiles
To view monitoring profiles:
1. Go to Administration.
2. Open Console.
3. Select Monitoring Profiles.

The Monitoring Profiles page displays all available monitoring profiles in the environment.

## Monitoring Profiles List
The Monitoring Profiles page provides a summary of each profile, including:
- Profile Name - Name of the monitoring profile
- Default - Indicates whether the profile is the default profile
- Active - Shows whether the profile is currently active
- Database List - Databases associated with the profile
- Last Updated - Date and time of the latest update
- Description - Brief description of the profile
![monitoring profiles](image-7.png)
In cloud environments, the Cloud profile is displayed as the default and active monitoring profile.

## Cloud Monitoring Profile
The Cloud monitoring profile is automatically applied to cloud databases onboarded into IBM CaaS. When a cloud instance is added:
- The instance is automatically added to the Cloud profile.
- Monitoring starts using predefined settings.
- The database appears in the profile's associated database list.
- No manual profile assignment is required.

This automatic onboarding ensures consistent monitoring coverage across all cloud databases.

## System-Managed Profile
The Cloud monitoring profile is a read-only, system-managed profile.


**Users can:**
- View profile information
- View associated databases
- Review monitoring settings

**Users cannot:**
- Modify profile settings
- Change collection parameters
- Update retention policies
- Delete the profile

This ensures a consistent monitoring configuration across the environment.

## Profile Details
Selecting a monitoring profile opens the profile details page, which includes:
- Status – Current profile status
- Profile Name – Name of the profile
- Databases – Number of associated databases
- Description – Profile description and management information
![profile details](image-8.png)
The database count helps identify how many databases are currently monitored by the profile.

## Monitoring Settings
The Monitoring Settings section displays the monitoring configuration applied to databases associated with the profile.
![monitoring settings](image-9.png)

## Collection Settings
Collection settings determine how monitoring data is gathered. 
Typical settings include:
- Data collection interval
- Number of SQL statements captured from package cache
- SQL statement normalization
- Lock wait monitoring threshold
- Table data read threshold
- Storage metrics collection
- Storage collection schedule
- Table performance data collection
- Object scope included in monitoring

These settings control the type and frequency of monitoring data collected from databases.

## Persistence Settings
Persistence settings define how monitoring data is stored and retained. 
Typical settings include:
- Monitoring data persistence
- Monitor data retention period
- Package cache persistence
- Package cache retention period

These settings ensure monitoring data remains available for historical analysis and troubleshooting.

## Database Association
The profile displays all databases currently associated with it. As new cloud databases are onboarded into IBM CaaS, they are automatically added to the Cloud monitoring profile.
This ensures:
- Consistent monitoring coverage
- Automatic onboarding of new databases
- Easy verification of monitored databases

## Key Features
- Automatic Onboarding – Cloud databases are automatically added to the monitoring profile.
- Immediate Monitoring – Monitoring starts as soon as a database is onboarded.
- System-Managed Configuration – Monitoring settings are maintained by the platform.
- Consistent Monitoring Policy – All cloud databases use the same monitoring configuration.

## When to Use This Page
Use the Monitoring Profiles page to:
- Verify that a database is being monitored
- Confirm that the Cloud profile is active
- View databases associated with the profile
- Review monitoring collection and retention settings
- Understand how monitoring is configured for cloud databases

## Notes
- The Cloud monitoring profile is intended for cloud databases managed through IBM CaaS.
- Database association is performed automatically during onboarding.
- The profile is read-only and cannot be modified.
- Monitoring begins automatically after a database is associated with the profile.
- The profile remains active and available for viewing at all times.

# CaaS - Event Monitoring Profile
The Event Monitoring feature in IBM CaaS enables you to capture and analyze database events. 
Event Monitoring provides a centralized interface for configuring event monitors, viewing data collection settings, and reviewing monitoring-related storage usage.

## Overview
Event monitors collect detailed information about specific database events and store it for later analysis. This information can be used to investigate database behaviour, identify performance bottlenecks, and support troubleshooting activities.

Using the Event Monitoring module, you can:
- Configure event monitors for supported event types
- Enable or disable event collection
- View collection and retention settings
- Review monitoring tablespace usage
- Scale monitoring storage when required
- View event monitor objects associated with a database

## Accessing Event Monitoring
To access Event Monitoring:
1. Go to Administration.
2. Select Console.
3. Click Event Monitoring.
![Event monitoring](image-10.png)
The landing page displays monitored databases along with summary information and access to event monitor configuration.

## Event Monitor Configuration
Each monitored database can have one or more event monitors configured. Event monitor settings control how event data is collected, stored, and retained. Common configuration options include:
- Status – Enable or disable event collection
- Collection Interval – Frequency at which event data is gathered
- Data Retention – Duration for retaining collected data
- Threshold Settings – Event-specific collection thresholds
- Administrative Task Scheduler – Optional scheduled collection support
![event monitor configuration](image-12.png)

## Supported Event Monitor Types

### Activity
Captures database activity information that can be used to analyse workload behaviour and query execution patterns.

### Locking
Captures lock-related events, including lock waits and contention. This monitor helps identify blocking applications and concurrency issues.

### Utility
Captures information related to database utility operations, such as maintenance and administrative activities.

### Statistics
Collects database statistics that can be used to analyse performance trends and operational behaviour over time.

### Configuration (Config)
Captures configuration-related events, helping track changes that may affect database behaviour or performance.

### DDL
Captures Data Definition Language (DDL) events, including schema and database object changes.

### Registry Variables (Regvar)
Captures events related to database registry variables and associated changes.

## Monitoring Storage Management
Event monitoring data is stored in a dedicated monitoring tablespace. The Event Monitoring page provides visibility into:
- Current tablespace size
- Storage utilisation
- Usage thresholds
- Overall tablespace health
![monitor storage management](image-13.png)
When additional capacity is required, the tablespace can be scaled directly from the Event Monitoring interface.

## Event Monitor Objects
The module also displays the event monitor objects created for a database. This allows administrators to verify the monitors currently configured and ensure that the required monitoring components are available.

## Typical Use Cases

Use Event Monitoring to:
- Investigate locking and wait-related issues
- Analyse database activity and workload patterns
- Monitor utility execution and maintenance operations
- Track configuration and schema changes
- Collect diagnostic information for troubleshooting
- Maintain historical event data for operational analysis

These informations can be viewed under tabs for respective event monitoring , in the monitoring page.

## Key Features
- Centralized event monitor management
- Support for multiple event monitor types
- Configurable collection and retention settings
- Monitoring tablespace visibility and scaling
- Event monitor object management
- Database-level monitoring configuration

## Notes
- Event Monitoring is intended for targeted diagnostics and performance analysis
- Storage usage increases as event data is collected and retained
- Monitoring requirements vary by event type and workload
- Tablespace utilisation should be reviewed periodically when event monitoring is enabled
- Only enable the event monitors required for your analysis or troubleshooting activities
