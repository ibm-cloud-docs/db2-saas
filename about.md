---
copyright:
  years: 2014, 2026
lastupdated: "2026-01-16"
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
{:warning: .warning}
{:attention: .attention}
# About
{: #about}
The [IBM Documentation for the service](https://www.ibm.com/docs/en/db2-as-a-service) covers the detailed commands and reference topics for the Db2 engine that powers Db2 SaaS. The IBM Cloud documentation covers the high-level functionality for the cloud offering, and refers back to this set of documentation where appropriate.
{: attention}

## Performance Plan
- Base configuration start at 4vCPU x 16GB RAM x 50GB Storage on dedicated compute slices
- 2-node High Availability
- Customizable IOPS Scaling
### Supported data centers (Performance)
The Performance plan is supported in the following data center geographies:
- **Dallas** - (us-south)
- **Washington** - (us-east)
- **Sydney** - (au-syd)
- **Sao Paulo** - (br-sao)
- **Toronto** - (ca-tor)
- **Frankfurt** - (eu-de)
- **Madrid** - (eu-es)
- **London** - (eu-gb)
- **Tokyo** - (jp-tok)
## Standard/Enterprise Plans
{: #ab_plans_cfgs}

The **Standard** and **Enterprise** plans are deprecated. All new deployments will use the **Performance** plan. Existing Standard/Enterprise customers are encouraged to migrate to the Performance plan. For migration instructions, see [Migration](/docs/db2-saas?topic=db2-saas-migration). For the latest status, see the [deprecation announcement](https://cloud.ibm.com/status/announcement?query=Deprecation+Announcement+-+IBM+Db2+SaaS+Standard+%26+Enterprise+Plans){: external}.
{: deprecated}


### Standard Plan (Deprecated)
- Base instances start at 8 GB RAM x 20 GB storage on shared compute slices
- 100 GB of free backup storage for up to 14 days of backups
### Enterprise Plan (Deprecated)
- Base instances start at 4 vCPU x 16 GB RAM x 20 GB storage on dedicated compute slices
- 1 TB of free backup storage for up to 14 days of backups
### Supported Data Centers
{: #ab_sup_dcs}
The Standard and Enterprise plans are supported in the following data center geographies:
### Multi-zone region (MZR)
- **Dallas** - (Dal10, Dal12, Dal13)
- **Frankfurt** - (Fra02, Fra04, Fra05)
- **London** - (Lon04, Lon05, Lon06)
- **Sydney** - (Syd01, Syd04, Syd05)
- **Tokyo** - (Tok02, Tok04, Tok05)
- **Washington, DC** - (Wdc04, Wdc06, Wdc07)
- **Sao Paulo** - (Sao01, Sao04, Sao05)
- **Toronto** - (Tor01, Tor04, Tor05)
MZRs support 3 node HA in 3 different data centers in that region.
{: note}
### Single-zone region (SZR)
- **Amsterdam** - (Ams03)
- **Montréal** - (Mon01)
SZRs support 3 node HA in a single data center in that region.
{: note}
### EU-Supported (MZR)
- **Frankfurt 02** - (Fra02, Fra04, Fra05)
EU-Supported MZR supports 3 node HA in 3 different data centers in that region.
{: note}
## API References by plan
- **Standard & Enterprise Plans:** [IBM Db2 as a Service REST API](https://cloud.ibm.com/apidocs/db2-on-cloud/db2-on-cloud-v4)
- **Performance Plan:** [IBM Db2 as a Service Performance REST API](https://cloud.ibm.com/apidocs/db2-on-cloud/db2-saas-perf-v4)
