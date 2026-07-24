---
copyright:
  years: 2025, 2026
lastupdated: "2026-07-24"

keywords: byol, bring your own license, licensing, cost optimization

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

# Bring Your Own License (BYOL)
{: #gh_byol}

This section explains how to configure BYOL in Db2 SaaS in the new Genius Hub–enabled console. Follow these instructions if you see the updated UI. If you are still using the **legacy console**, refer to the [BYOL](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-byol) section for the correct steps.
{: important}

The Bring Your Own License (BYOL) option for Db2 SaaS allows you to apply your existing eligible Db2 software licenses to your cloud instance, resulting in up to a **28% discount** on compute costs compared to the standard On Demand pricing model.
{: shortdesc}

## Prerequisites
{: #gh_byol-prerequisites}

Before switching to the BYOL license model, ensure that you meet the following requirements:

- An active Db2 SaaS instance on the **Performance** plan.
- Eligible Db2 software licenses (**Db2 Standard** or **Db2 Advanced**) with active Subscription and Support.
- Sufficient license VPCs (Virtual Processor Cores) to cover the compute allocation of your instance.
- Eligibility requirements as stated in **Section 5.4** of the [Db2 on Cloud Service Description](https://www.ibm.com/support/customer/csol/terms/?id=i126-7519&lc=en){: external} must be satisfied.

## Selecting BYOL during provisioning
{: #byol-provisioning}

You can select the BYOL license type when provisioning a new Db2 SaaS instance.

During the provisioning process, locate the **Reserved Instance/BYOL** dropdown. By default, the license is set to **Default license**. Select **Bring your own license (BYOL)** from the dropdown, then continue with the rest of the provisioning steps.

![Selecting BYOL during provisioning](caas_images/byol_provisioning.png){: caption="Select Bring your own license (BYOL) from the Reserved Instance/BYOL dropdown during provisioning" caption-side="bottom"}

## Configuring BYOL in the UI
{: #byol-configuration}

You can also change your license type on an existing Db2 SaaS instance through the console.

### Step 1: Navigate to the license settings
{: #gh_byol-step1}

From your Db2 SaaS instance dashboard:

The steps for configuring BYOL in the UI differ depending on whether you are using the legacy console or the new Genius Hub–enabled console.
{: note}

If you are still using the legacy console, refer to the [Configuring BYOL in the UI](https://cloud.ibm.com/docs/db2-saas?topic=db2-saas-byol#byol-configuration) section for the correct steps.
{: important}


1. Select **Administration** from the left navigation.  
2. In **Databases**, click your database.  
3. Select **Licensing** from the left menu.  
4. In the main content area, click **Manage license**.  
5. Click **Change** on the right side to modify your license type. 

![Navigating to Settings > License > Change](caas_images/new_mnglicence.png){: caption="Navigate to Settings > License and click Change" caption-side="bottom"}



### Step 2: Select the BYOL license type
{: #gh_byol-step2}

On the License selection page, select the **Bring Your Own License (BYOL)** radio button, then click **Save**.

The BYOL option provides the highest discount at 28% off compute costs. Ensure you meet the eligibility requirements stated in Section 5.4 of the Service Description before proceeding. Eligible licenses include Db2 Standard and Db2 Advanced, and you must maintain active Subscription and Support on your existing license entitlements.
{: important}

![Selecting the BYOL license option](caas_images/byol_ml.png){: caption="Select the Bring Your Own License (BYOL) option" caption-side="bottom"}


### Step 3: Confirm the license change
{: #gh_byol-step3}

A confirmation dialog appears showing the details of your license change:

1. Verify the **Change from** and **Change to** columns reflect the correct transition.
1. Check the certification box: *"I certify that I possess the required number of license VPCs."*
1. Click **Proceed** to apply the change.

The discount takes effect immediately.

![Confirming the license change](caas_images/step3_confirm_changes.png){: caption="Confirm the license change to BYOL" caption-side="bottom"}

### Step 4: Verify successful update
{: #gh_byol-step4}

After clicking Proceed, you are returned to the License settings page. A green success banner confirms that the license has been successfully updated. The new BYOL pricing is now active on your instance.

![License successfully updated](caas_images/step4_success.png){: caption="License successfully updated confirmation" caption-side="bottom"}

## Important notes
{: #gh_byol-notes}

- **Immediate effect**: The discount change takes place immediately upon confirmation. Your next billing cycle reflects the new BYOL pricing.
- **License compliance**: You are responsible for ensuring that you hold the required number of license VPCs for the compute resources allocated to your instance. IBM may audit compliance.
- **Reversibility**: You can switch back to On Demand type at any time. For switching to Reserved license types, you may need to first switch to the On Demand type and then switch to Reserved types by following the same steps and selecting a different option.
- **No service disruption**: Changing the license type does not affect your database instance availability. There is no downtime associated with this change.
- **Subscription and Support**: You must maintain active Subscription and Support on your existing Db2 license entitlements to remain eligible for the BYOL program.
