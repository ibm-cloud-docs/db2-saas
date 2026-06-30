---

copyright:
  years: 2026
lastupdated: "2026-06-30"

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
{:support: data-reuse='support'}
{:faq: data-hd-content-type='faq'}
{:video: .video}

# Migration - FAQs
{: #faq_mig_db2oc}

This page provides answers to frequently asked questions (FAQs) about migrating {{site.data.keyword.Db2_on_Cloud_long}} Standard/Enterprise instances to the Performance plan.
{: shortdesc}

## Do my endpoints change after migration?
{: #q_endpts}
{: faq}
{: support}

Yes. Endpoints, URLs, and hostnames change when you transition to the Performance plan.

## Is upgrading to Db2 v12 mandatory during migration?
{: #q_upgrd}
{: faq}
{: support}

No. Upgrading to Db2 v12 is optional. If you plan to move to v12, test your systems on v12 before final migration.

## How can I test Db2 v12 in the Performance plan?
{: #q_testv12}
{: faq}
{: support}

In Step 8 of the [Migration Procedure](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-migration), select **“Yes, create a clone for testing.”** This creates a clone of your existing database for testing. 

The original database is not impacted and continues running, while the clone provides a clean, separate environment where you can safely test Db2 v12. Once you are satisfied with your testing, you can delete the clone without affecting your production system.

## What happens if I select “No, upgrade without creating a clone?"
{: #q_no_upgrade}
{: faq}
{: support}
  
Select this option when you are ready to perform the final migration and move on from your Standard or Enterprise database. Up to this step, the last full backup from the old system has already been restored in the new Performance instance, and transaction logs have been continuously rolled forward. 

When you choose **“No, upgrade without creating a clone,”** the transaction logs are rolled forward one final time to the destination database. The compute resources of the old database are then scaled down to 0, making it obsolete. At this point, you will receive new endpoints in the Performance plan, which must be updated across your consuming systems.

## Is my old database deleted after migration?
{: #q_db}
{: faq}
{: support}

No. The old instance is not deleted. Compute is scaled to 0, but storage and objects remain. Storage is free for 14 days, after which billing begins.

## Can I bring back my old (Standards/Enterprise) instance?
{: #q_oldinstance}
{: faq}
{: support}

Yes. Open a cloud support ticket with **SEV 1** priority. Be sure to include the CRN and the region of the instance. The support team will work with you to bring it back online.

## Will endpoints change if my old (Standards/Enterprise) instance is restored?
{: #q_endpointschange}
{: faq}
{: support}

No. Endpoints remain the same.

## Is data synchronized between old and new instances?
{: #q_datasync}
{: faq}
{: support}

Yes. The source and destination instances remain synchronized until Step 8 of the [Migration procedure](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-migration).  

- Up to Step 8: The last full backup of the old database is copied to the new Performance instance, and transaction logs are continuously rolled forward.  
- At Step 8: You must select one of the available options. Once an option is chosen, synchronization stops and a cutoff point is established.  

This ensures that the new Performance instance is fully up to date until the moment you finalize the migration.

## When does downtime occur during migration?
{: #q_downtime}
{: faq}
{: support}

Downtime begins at Step 8 when you select **“No, upgrade without creating a clone.”** It ends when new endpoints appear in the console.

## How can I estimate downtime? 
{: #q_estimatedwntime}
{: faq}
{: support}
  
To estimate downtime for your Standard or Enterprise instance, select **“Yes, create a clone for testing”** in Step 8 of the [Migration procedure](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-migration). After creating the clone, monitor the time it takes for the new system’s endpoints to appear in the migration tool UI. The duration between these two actions represents your expected downtime.

## How can downtime be minimized?
{: #q_minimisedwtm}
{: faq}
{: support}

Downtime cannot be completely avoided. However, if you migrate and remain on **Db2 v11.5** in the Performance plan, the process is significantly faster compared to upgrading to v12. For customers who want the least downtime, we recommend staying on v11.5 during migration.

## What happens to audit configurations during migration?
{: #q_auditconfg}
{: faq}
{: support}

During migration from Standard/Enterprise plan to Perfomance plan, all existing audit policies and audit data are retained.  

However, configurations that rely on **Db2 audit tables** are no longer supported in the Performance plan. While your existing audit data remains intact, you must transition to a supported auditing mechanism specifically, audit output to COS storage.  

If you currently use Db2 audit table based auditing, open a support ticket and the SRE team will assist you with configuring the supported auditing method.

## Can I migrate more than 7 instances at once?
{: #q_instance_mig}
{: faq}
{: support}

Yes. You can migrate multiple Standard or Enterprise instances either sequentially or in parallel. The choice has no impact on the overall process, so you may proceed in whichever way is most convenient for you.

## Can I change storage size during migration?
{: #q_sign}
{: faq}
{: support}

Yes. The migration tool allows you to specify a **custom storage value** based on your requirements. Be mindful that if the value you select is less than what your workload needs, the migration will fail. Ensure the storage size you choose is sufficient to support your database before proceeding.

## Can I change IOPs during migration?
{: #q_change_storage}
{: faq}
{: support}

The migration tool automatically sets **10 IOPs per GB of provisioned storage**. If you are unsure of the value you need, we recommend using this default. After transitioning to the Performance plan, you can adjust the IOPs up or down as required to match your workload.

## Is storage autoscale enabled by default?
{: #q_auto_storage}
{: faq}
{: support}

Yes.

## Can Db2 parameters be changed in the Performance plan?
{: #q_dbparameters}
{: faq}
{: support}

Yes. See the full list of configurable parameters in the [Db2 SaaS API reference](https://cloud.ibm.com/apidocs/db2-on-cloud/db2-saas-perf-v4#gettuneableparameters).

## Do I need to delete DR node before migration?
{: #q_deletedr}
{: faq}
{: support}

Yes. Delete DR node before migration. After migration, set it up again.

## Do I need to take special considerations for HA during migration?
{: #q_duringmig}
{: faq}
{: support}

No. High Availability (HA) is automatically handled as part of the migration process. Your new Performance plan instance will have HA enabled by default, so no additional action is required on your part.

## The endpoints are visible and so is the console. But the Migration tool UI Shows "Convert to HA". Is the new system available to be used or should I wait for the action to finish?
{: #q_endpnts_console}
{: faq}
{: support}

The system is ready to be used. You may update your applications with the new endpoints and start consuming it.


## Is the new system usable if the UI shows “Backup in progress”?
{: #bkprogress}
{: faq}
{: support}

Yes. You can begin updating applications with new endpoints.

## Are users and privileges retained?
{: #q_userpriv}
{: faq}
{: support}

Yes. Existing users, roles, and group memberships are preserved.

## What if the migration UI seems stuck?
{: #q_ui_stuck}
{: faq}
{: support}

Use Google Chrome in an Incognito window. If the issue still persists please open a support ticket.

## Can I move my instance to a different location during migration?
{: #q_loc_change}
{: faq}
{: support}

Yes. Location changes are supported.

## What changes in network connectivity occur from Standard/Enterprise plan to Perfomance plan?
{: #q_netwrk_conn}
{: faq}
{: support}

The network connectivity model changes when transitioning from Standard/Enterprise plan to Perfomance plan:

- **Standard/Enterprise plans:** Connectivity is established using [Cloud Service Endpoints (CSE)](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-connect_options) for private access.  
- **Performance plan:** Connectivity uses [Virtual Private Endpoints (VPE)](https://cloud.ibm.com/docs/overview?topic=overview-endpoints-support) to enable private network access to your VPC environment.  

As part of the migration, customers moving from Standard/Enterprise plan to Performancen plan must set up VPE to maintain private connectivity. For more details, see [Configuring VPE for Db2 SaaS](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-vpeg).

## Do Explain Tables need to be recreated after upgrading to Db2 v12?
{: #q_explain_tables}
{: faq}
{: support}

After upgrading to Db2 v12, it is necessary to recreate the Explain Tables once migration is completed.

## Is Private Endpoint–to–Private Endpoint federation supported?
{: #q_explain_tables}
{: faq}
{: support}

No, Private Endpoint to Private Endpoint federation is not supported at this time on the Performance Plan. Federation is supported only through public endpoints on the performance plan
