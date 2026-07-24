---
copyright:
  years: 2026
lastupdated: "2026-07-24"

keywords: CaaS, Genius Hub–enabled Consol, Impact Analysis

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

# Impact Analysis
{: #caas_impactanlys}

The Index Impact Analysis feature in the the new Genius Hub–enabled console(CaaS) helps database administrators evaluate the effect of index recommendations on system performance. It builds on existing query tuning capabilities and provides deeper insights into how suggested indexes influence query execution.  

You can use index impact analysis to estimate the effect of creating or dropping indexes. The feature helps you determine whether an index improves query performance, has no effect, or causes regressions. By reviewing the analysis results, you can ensure that recommendations are applied thoughtfully rather than implemented without review.  

In CaaS, event monitoring activities are turned off. As a result, Impact Analysis uses data from the **package cache** instead of event monitoring sources. This means the report is less comprehensive compared to environments where event monitoring is enabled and only queries available in the package cache are analyzed.  
{: important}


To set up the impact analysis, do the following steps:

 
1. Open the SQL workbench in the new Genius Hub–enabled console(CaaS) and run query tuning for the statement you want to evaluate.  

2. In the tuning results, go to the **Indexes** recommendation list and choose **Impact analysis** from the drop-down.  

3. In the **Impact Analysis** dialog, enter a job name (or keep the auto-generated name) and an optional description.  

4. Select the query types to which you want to analyze- **SELECT**, **INSERT**, **UPDATE**, or **DELETE**.

5. Choose a time range (preset or a custom single-day window up to 24 hours).  

6. Click **Run impact analysis** to submit the job. A job ID is created and the job appears in the Impact Analysis log.  

7. Monitor the job in the Impact Analysis log- view progress (progress bar updates while running), or view logs if the job errors.

8. When the job completes, review the summary metrics- CPU, I/O, and timeron. You can expand each row to view a detailed query analysis. Depending upon the number of queries to analyze, the job will take time.

   Timeron improvement serves as a key metric for evaluating overall cost efficiency, while CPU time reflects the processing effort and I/O time indicates the data access overhead involved in executing a query. Color coding: **Green= Improvement, Red= Regression, Zero= No impact**.
  {: note}  

9. Inspect the list of impacted queries. Use filters (**Improved**, **Unchanged**, or **Regressed**) and the search box to find specific statements. Expand rows to see current versus predicted metrics and execution counts.  

10. Decide what to do: apply indexes that show meaningful improvement, skip, or ignore redundant or no-impact indexes, and investigate any regressions before making changes.

11. Download the full report as a PDF for audit or sharing. If you see **'No statements found'** adjust the time range or query types and rerun the analysis.
