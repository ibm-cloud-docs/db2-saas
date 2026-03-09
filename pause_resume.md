---
copyright:
  years: 2025, 2026
lastupdated: "2026-02-18"

keywords: pause, resume, pause compute, resume compute, cost savings

subcollection: Db2onCloud
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

# Pause and Resume
{: #pause-resume}

You can pause and resume the compute resources of your Db2 on Cloud instance at any time. While paused, you are not charged for compute, but storage charges continue to apply.
{: shortdesc}

## Pausing your instance
{: #pause}

### Step 1: Navigate to Pause & Resume
{: #pause-step1}

From your Db2 on Cloud instance dashboard:

1. Click the **Settings** icon in the left sidebar (wrench icon).
1. Select **Pause & Resume** from the top navigation bar.
1. Click the **Pause now** button.

![Navigate to Pause & Resume and click Pause now](images/pause_navigate.png){: caption="Navigate to Pause & Resume and click Pause now" caption-side="bottom"}

### Step 2: Confirm the pause
{: #pause-step2}

A confirmation dialog appears with details about what happens when you pause compute. Review the following before proceeding:

- All current queries will be cancelled and no future or scheduled activities will run until compute is resumed.
- Your team members will be logged out as soon as the pause starts.
- Your data will remain unchanged and secure.
- All future activities and scheduled tasks will be suspended.
- While on pause, you won't be charged for the compute.
- Storage charges will continue to be applied.

If you want to check your current in-flight executions before pausing, go to **Monitoring > Statement > In-flight executions**.
{: tip}

Click **Confirm** to pause the instance.

![Pause compute resource confirmation dialog](images/pause_confirm.png){: caption="Confirm the pause compute action" caption-side="bottom"}

### Step 3: Instance is paused
{: #pause-step3}

After confirming, the instance enters a paused state. The dashboard displays a **Database Paused** screen with a **Resume now** button.

The instance can remain paused for up to 7 days. After 7 days, the instance automatically resumes. Once resumed, you may choose to pause the instance again through the console.
{: important}

![Database Paused screen](images/pause_paused.png){: caption="Database Paused screen" caption-side="bottom"}

## Resuming your instance
{: #resume}

### Step 1: Click Resume now
{: #resume-step1}

From the **Database Paused** screen, click the **Resume now** button. The instance begins preparing to resume. This may take up to a few hours depending on the database size.

![Database Paused - Preparing to resume](images/pause_resuming.png){: caption="Preparing to resume" caption-side="bottom"}

### Step 2: Verify successful resume
{: #resume-step2}

Once the resume completes, you are returned to the instance dashboard. A **Resume success!** notification confirms that the instance is back online.

![Resume success notification](images/pause_resume_success.png){: caption="Resume success notification" caption-side="bottom"}

## Important notes
{: #pause-resume-notes}

- **Compute charges stop**: While paused, you are not charged for compute resources. However, instances on a Reserved Instance (1-Year or 3-Year) term will continue to be billed at the regular rate, even while paused.
- **Storage charges continue**: Storage charges continue to be applied while the instance is paused.
- **Connections terminated**: All active connections and queries are cancelled when the pause starts. Team members are logged out immediately.
- **Scheduled tasks suspended**: All future activities and scheduled tasks are suspended during the pause and resume when the instance is brought back online.
- **Resume time**: Resuming may take up to a few hours depending on the database size.
- **Disaster recovery**: Pause and Resume is not supported on instances with a disaster recovery (DR) configuration.
- **Maintenance updates**: If a maintenance update is required while your instance is paused, the system will temporarily resume the instance to perform the update. Compute charges will apply during the update. The instance will be paused again once the update is complete.
