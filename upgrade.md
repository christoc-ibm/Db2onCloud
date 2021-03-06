---

copyright:
  years: 2014, 2020
lastupdated: "2020-11-19"

keywords: upgrade, Db2 on Cloud, Standard plan, Enterprise plan, legacy

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
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

# Upgrading {{site.data.keyword.Db2_on_Cloud_short}} plans
{: #upgrade_plans}

{{site.data.keyword.Db2_on_Cloud_short}} legacy plans must be upgraded to current Standard or Enterprise plans because we are deprecating support for our legacy plans. Upgrades run from **August, 2020** until **November, 2020**.
{: shortdesc}

The following document describes the process to upgrade from the legacy {{site.data.keyword.Db2_on_Cloud_short}} plans to the current **Standard** and **Enterprise** plans. This topic covers upgrades that are initiated by users. For more information about auto-upgrades that are initiated on behalf of customers who don’t take action to upgrade their own instances, see [Automatic upgrading](/docs/Db2onCloud?topic=Db2onCloud-auto_upgrade_plans){: external}.

Effective **28-Oct-2020**, the originally communicated timeline was extended. The new timeline allows self-initiated upgrades to continue until **November 5, 2020** instead of the prior cutoff of October 15, 2020. Auto-upgrades for instances that have not taken any action have also been delayed from October 16, 2020 to **November 9, 2020**. Self-transition must complete by **November 15, 2020**. After November 9, 2020, instances with no action will be upgraded in batches **through to the end of November, 2020** and access will be restricted to legacy instances as the batches are auto-upgraded; then, you'll be notified that recovery is available.
{: important}

For more information about the affected legacy plans and the new replacement plans, see [Deprecation of the Db2 on Cloud Legacy Plans and Availability of New Replacement Plans](https://www.ibm.com/cloud/blog/announcements/deprecation-of-the-db2-on-cloud-legacy-plans-and-availability-of-new-replacement-plans){: external}.

Henceforth, the existing legacy plan instance is referred to as the "source" and the newly provisioned Standard or Enterprise plan instance for the upgrade is referred to as the "target".

<!--
## Prerequisites
{: #upgrade_prereqs}

Before starting the legacy plan upgrade process, you'll need to complete the following items:
- Retrieve the Cloud Resource Name (CRN) of your source {{site.data.keyword.Db2_on_Cloud_short}} plan. The CRN can be retrieved from the source plan on {{site.data.keyword.cloud_notm}}. For more information, see [Cloud Resource Names](/docs/account?topic=account-crn).
- If your source plan is still in Cloud Foundry, you must migrate your source plan to Resource Controller. See [Resource controller (RC)](/docs/Db2onCloud?topic=Db2onCloud-rc). After you migrate a plan instance to Resource Controller, you can no longer use Cloud Foundry CLI commands to manage it.
-->
<!--  Additional information:
  - [Managing resource groups](/docs/account?topic=account-rgs#adding-resources-to-a-resource-group)
  - [General {{site.data.keyword.cloud_notm}} CLI (ibmcloud) commands](/docs/cli?topic=cli-ibmcloud_cli)
-->  
<!--
## Ordering from the {{site.data.keyword.cloud_notm}} Catalog
{: #ug_catalog}

1. Log in to the {{site.data.keyword.cloud_notm}} account where the existing source {{site.data.keyword.Db2_on_Cloud_short}} plan was provisioned.
1. Navigate to the [{{site.data.keyword.Db2_on_Cloud_short}} catalog page](https://cloud.ibm.com/catalog/services/db2){: external}
1. Choose the **Enterprise** or **Standard** plan and input the CRN of the source {{site.data.keyword.Db2_on_Cloud_short}} plan. You cannot choose the {{site.data.keyword.Db2_on_Cloud_short}} Lite plan as your target for an upgrade. 
-->
<!--The source plan must belong to one of the following legacy plans: 
   - IBM Db2 on Cloud Flex
   - IBM Db2 on Cloud Precise Performance 2.8.500
   - IBM Db2 on Cloud Precise Performance 12.128.1400
   - IBM Db2 on Cloud Precise Performance 48.1000.10000 
-->
<!--Additional information:
  - [Video](https://video.ibm.com/recorded/128386612){: external} showing you how to upgrade from the legacy {{site.data.keyword.Db2_on_Cloud_short}} plans to the current Standard and Enterprise plans.-->

## Upgrade procedure
{: #ug_upgrade_steps}

The deadline for running the following steps was **November 5, 2020**. If you attempt to run these steps now, you will get an error.
{: important}

1. [Log in to the {{site.data.keyword.cloud_notm}} account](http://cloud.ibm.com){: external} where the legacy {{site.data.keyword.Db2_on_Cloud_short}} system was provisioned.

   ![List of instances](images/recovery_instance_list_blur.png "List of instances"){: caption="Figure 1. Highlight your service instance" caption-side="bottom"}

2. If your legacy plan instance is listed under **Cloud Foundry services**, it must be migrated to a resource group. 

   ![Cloud Foundry instance](images/recovery_cf_blur.png "Cloud Foundry instance"){: caption="Figure 2. Cloud Foundry instance" caption-side="bottom"}

   - To migrate to a resource group, select the instance and click **Migrate**. After completion of the migration, the Db2 instance is now listed under **Services**.

     ![Cloud Foundry Migration](images/recovery_cf_migration_blur.png "Cloud Foundry Migration"){: caption="Figure 3. Migrating Cloud Foundry Instance" caption-side="bottom"}

3. Copy the CRN of your legacy instance now listed under **Services**.

   ![Copy the legacy plan CRN](images/recovery_CRN_blur.png "Copy the legacy plan CRN"){: caption="Figure 4. Copy the legacy plan CRN" caption-side="bottom"}

4. Order a Standard or Enterprise instance, specifying the legacy plan CRN in the **Upgrade** field to start the upgrade process. When you are initiating an online upgrade for an instance that was not auto-upgraded, do **not** use the Recovery field.

5. The new {{site.data.keyword.Db2_on_Cloud_short}} service instance is visible under **Services**. You can read the data on the target system while the upgrade occurs, but do not update or delete any data on the target.

6. Navigate to the legacy source plan. Track the status of the upgrade by clicking **Upgrade**. For important guidance about changes that you must not make on the source plan during the upgrade, see the following sections.

Watch this video to see how to upgrade from the legacy {{site.data.keyword.Db2_on_Cloud_short}} plans to the current Standard and Enterprise plans.

![Upgrade your Db2 on Cloud plan](https://video.ibm.com/embed/channel/23952663/video/db2-upgrade){: video output="iframe" data-script="none" id="watsonmediaplayer" width="560" height="315" scrolling="no" allowfullscreen webkitallowfullscreen mozAllowFullScreen frameborder="0" style="border: 0 none transparent;"}

<!-- ![Intiate the upgrade](images/recovery_v2.png "Initiate the upgrade"){: caption="Figure 5. Initiate the upgrade" caption-side="bottom"} -->

<!--
## Tracking the self-initiated upgrade
{: #ug_track}

- Navigate to the source plan on the {{site.data.keyword.cloud_notm}} dashboard
- Track the status of the upgrade by clicking on the **Upgrade** button
-->

## Self-initiated upgrade phases
{: #ug_phases}

The upgrade from the legacy {{site.data.keyword.Db2_on_Cloud_short}} plans to the current **Standard** and **Enterprise** plans is a self-service and online process. It is initiated the moment a target plan is ordered along with a source CRN input. The upgrade goes through multiple phases and for most of them no user action is required.

### Phase 0 - Provisioning target
{: #ug_prov_tgt}

The target plan is provisioned and scaled automatically to the appropriate level. The values that are used for scale depend on the current configuration of the source. No user action is required for this phase.

### Phase 1 - Preparing upgrade
{: #ug_prep}

The prerequisite steps required to upgrade the source to the target plan are run during this phase. No user action is required for this phase.

### Phase 2 - Metadata migration
{: #ug_meta_mig}

The metadata such as DDL and the database user information that exists on the source are migrated to the target during this phase. No user action is required for this phase.

### Phase 3 - Data migration
{: #ug_data_mig}

The data from the source is migrated to the target. No user action is required for this phase.

### Phase 4 - Data migration complete
{: #ug_data_mig_cmplt}

User action is required for this phase.
{: important}

The data was migrated from the source to the target. Any transactions on the source continue to be replicated on the target, but it is possible to transition to the target. After the upgrade reaches this phase, a **Transition** button is now available on the source plan on {{site.data.keyword.cloud_notm}} where the upgrade is tracked. To proceed to the next phase, user action is required to initiate the transition.

### Phase 5 - Transition in progress
{: #ug_trans_inprog}

Certain post-migration tasks are run on the target during this phase. No user action is required for this phase.

### Phase 6 - Transition and upgrade complete
{: #ug_trans_inprog_cmplt}

The upgrade is complete. The **Transition** button is now disabled. The target plan is now available to use. Any further transactions on the source are **not** replicated on the target.

## Self-initiated upgrade features and recommendations
{: #ug_feat_recom}

The upgrade process can be self-initiated only one time per source. After the new {{site.data.keyword.Db2_on_Cloud_short}} instance is created, you must be prepared to complete all of the upgrade phases. If the target instance is deleted after the upgrade is started and before all of the upgrade phases are completed, the source cannot be upgraded a second time.
{: important}

- The upgrade process is a self-service, online process.
- Users can continue to use their source plan while the upgrade proceeds.
- Every upgrade is monitored by the {{site.data.keyword.Db2_on_Cloud_short}} Operations team who are available 24x7x365.
- The data replication is unidirectional - from the source to the target.
- Any users who are created or modified on the source DURING or AFTER the upgrade process might not be migrated to the target. Do not make any user administration actions on the source after the upgrade is initiated.
- Any DDL changes on the source DURING or AFTER the upgrade process might not be replicated on the target. Do not make any DDL changes on the source after the upgrade is initiated.
- Do not insert, update, or delete any data on the target during the upgrade. Any read operation is possible and can be used to verify the data migration.
- Users can continue using the source until transition is initiated. The average transition period is about 2 minutes. In case the transition was not completed even after 30 minutes, you are recommended to continue using the source. The {{site.data.keyword.Db2_on_Cloud_short}} Operations team is alerted if there is an issue with the transition and the button is re-enabled when it is possible to transition again.
- After the upgrade and transition to the new instance is completed, delete your legacy system. This is a final step to initiate, otherwise, the upgraded legacy instances will be blocked after **November 15, 2020**, and decommissioned in November if upgrades were successfully completed; unless a support case was opened to request an extension.

## Billing during the upgrade
{: #ug_billing}

- You are NOT billed for the target during the upgrade. You are billed for the source as usual.
- If you do not initiate transition after a period of 2 weeks since the option was available and you have 2 active systems, you might be billed for the target.
- After the upgrade is complete, you will be billed for the target and will NOT be billed for the source.
- If you do not delete the source plan before the end of the 2-week grace period that follows completion of the upgrade, you might then be billed for the source again.

## FAQs - Upgrading to Standard and Enterprise plans
{: #faq_db2oc_upgrade}

This section is a collection of frequently asked questions (FAQ) about upgrading the {{site.data.keyword.Db2_on_Cloud_long}} plans. We'll add more questions over time. [Create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} if you have any questions about the upgrade and migration.

<!--
Email notifications are being sent to customers associated with existing {{site.data.keyword.Db2_on_Cloud_short}} legacy plan instances. If you have not been receiving email notifications, ensure that account email addresses for {{site.data.keyword.Db2_on_Cloud_short}} plans are up to date. Many of you received an email alerting you to our new Standard and Enterprise plans, and the need for you to upgrade your legacy plans to our new plans via our online upgrade process, because we are deprecating support for our legacy plans. Upgrades will start in **August**. You have until **November 5, 2020** to initiate your upgrade and until **November 15, 2020** to complete testing and transition to your new system. After **November 9, 2020**, instances with no action will be upgraded in batches through to **November 17, 2020** and access will be restricted to legacy instances as the batches are auto-upgraded; then you'll be notified that recovery is available.
{: important}
-->

### Which instances are legacy instances that must be updated?
{: #q_which_legacy}
{: faq}
{: support}

The following plan instances must be upgraded to the Standard or Enterprise plan: 
   - IBM Db2 on Cloud Flex
   - IBM Db2 on Cloud Precise Performance 2.8.500 (small)
   - IBM Db2 on Cloud Precise Performance 12.128.1400 (large)
<!--   - IBM Db2 on Cloud Precise Performance 48.1000.10000 -->

If your instance name begins with the string `dashdb-txn-flex`, `dashdb-txn-small`, `dashdb-txn-large`, or one of those strings with `txnha` in place of `txn`, it is a legacy instance and must be upgraded.

Lite plan instances do not require an upgrade. Lite plan instance names contain the string `dashdb-txn-sbox`.

### In which data centers is the upgrade supported?
{: #q_which_dcs}
{: faq}
{: support}

The legacy plan upgrade is available in the following data centers:
- Amsterdam
- Dallas
- Frankfurt
- London
- Milan
- Montréal
- Sao Paulo
- Sydney
- Tokyo
- Toronto
- Washington, DC

<!--
The legacy plan upgrade will be available in the following data centers by **November 16, 2020**:
- Amsterdam
- Milan
- Montréal -->
<!-- - Paris -->
<!-- - Sao Paulo
- Toronto
-->
We will also support **EU-Cloud compliant** instances in Frankfurt at a later date. [Create a support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} if you have questions.

### How long will the upgrade take from Phase 0 to Phase 4 (Transition Ready)?
{: #q_upgrade_duration}
{: faq}
{: support}

The upgrade of each of your plans and databases is unique and depends on many factors. The time that is required can range between 6 hours and several days or weeks.

There are various factors that govern the pace of the upgrade. Some of the factors are the amount of data on the source, storage capacity on the target, the type and relationship between the data, the compute configurations of the source and target, the physical location and distance between the source and target, networking considerations such as the presence of allow lists or private endpoints, data-center-specific latency, and the volume of workload on the source during the upgrade. Due to these factors, it is not possible to provide an accurate time estimate for the upgrade. The time that is taken by the upgrade does not impact your use of the source on which there is zero downtime during the upgrade.

<!--
### What's new in our Standard and Enterprise plans?
{: #q_wn}
{: faq}
{: support}

Our new Standard and Enterprise plans run the Db2 11.5 engine. They include self-scheduling of software updates by customers, zero down-time scaling of storage and compute, self-service managed backup with point-in-time restore, and support for several {{site.data.keyword.cloud_notm}} integration features like **Activity Tracker** and **LogDNA**. If you choose a high-availability (HA) option, you get three high-availability nodes spanning multiple availability zones (where supported).
-->
<!--
### What are the plan specs?
{: #q_plan_specs}
{: faq}
{: support}

- **Enterprise**: You get one SQL database per service instance on dedicated compute slices with 4 vCPUs, 16 GB of RAM, and 20 GB of storage for data and logs. Each plan includes up to 1 TB of backup storage, stored for 14 days.

- **Standard**: You get one SQL database per service instance on a shared compute environment with 8 GB of RAM, and 20 GB of storage for data and logs. Each plan includes up to 100 GB of backup storage, stored for 14 days.

With either plan, you can scale up by purchasing additional storage or CPU. You can also purchase additional backup storage, Cloud Service Endpoint connectivity or HA options.
-->

### How much do the Standard and Enterprise plans cost?
{: #q_cost}
{: faq}
{: support}

Prices are detailed by plan in the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog/services/db2){: external}

### Will I be billed for two plans during the upgrade?
{: #q_bill_two}
{: faq}
{: support}

After you begin the upgrade, you have 14 days to move to the new plan. The upgrade timeline starts when you provision a {{site.data.keyword.Db2_on_Cloud_short}} Standard or Enterprise plan and provide your CRN from your legacy plan in the upgrade details on the **Service create** page in the {{site.data.keyword.cloud_notm}} catalog. If you don't complete the upgrade during that 14-day period, you might be charged for both source and target plans.

### What permissions will I need to initiate the upgrade to a Standard or Enterprise plan?
{: #q_perms}
{: faq}
{: support}

You must be a platform admin user on both source and target plan instances.

### What will I need to change after the upgrade to a new plan?
{: #q_change}
{: faq}
{: support}

See [Differences between legacy and current plans](/docs/Db2onCloud?topic=Db2onCloud-plan_diffs){: external}.

<!--
The current Standard and Enterprise plans VCAP Services json file is different from that of the legacy plans. Any of your applications that consume the legacy plan VCAP Services json file must be changed to handle the current Standard and Enterprise plan json file. For more information about the Standard and Enterprise VCAP Services json file, see [Connectivity options](https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-connect_options){: external}.
{: important}-->
<!--
Because {{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plans do not run with the `DB2_WORKLOAD=ANALYTICS` registry parameter, the behavior of the COUNT aggregate function has changed. COUNT now returns an **INTEGER**, not a DECIMAL value. For more information, see [COUNT aggregate function](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000759.html){: external}.
{: important}-->

### Can I use the new HADR feature in the new plans in place of our existing DR node solution in the legacy plans? 
{: #q_leverage_ha}
{: faq}
{: support}

The new plans offer a High Availability Disaster Recovery (HADR) feature with 3 nodes that are located in different independent availability zones and the failover is managed for you by IBM. This feature avoids any service disruption that is caused by a data center disaster, failure, or maintenance. For more information about {{site.data.keyword.cloud_notm}} Multi-Zone Regions (MZR), see [Why Deploy Applications on IBM Cloud Availability Zones?](https://www.ibm.com/cloud/blog/why-deploy-applications-on-ibm-cloud-availability-zones){: external}.

A few of you might require legacy-style disaster recovery (DR) instead of the new HADR feature. Legacy-style disaster recovery (DR) is planned to be supported by **November 30, 2020**. [Create a support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} and have a conversation with our Development Operations team if you require this Cross-Region DR-specific feature.

<!-- HA is also well suited as a disaster recovery (DR) option for those of you with requirements that are satisfied by it. If you have strict requirements for a cross-region DR node, you can leverage such a feature by **November 30, 2020**.-->

### I have a non-HA plan, but want to upgrade to Standard or Enterprise HADR (or vice versa). Can I do that?
{: #q_noha_ha}
{: faq}
{: support}

Yes, you can move from any legacy plan (Flex, Small, and Large) to any {{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plan. You can move from non-HA to HADR, or from HA to non-HADR. See the following question about HADR information in Standard and Enterprise plans.

### How is the high availability disaster recovery (HADR) feature done in Standard and Enterprise plans?
{: #q_dr}
{: faq}
{: support}

Standard and Enterprise plans provide automated redundancy across 3 different data centers with the HADR option. These data centers are physically isolated from each other and do not share any infrastructure. The reference design for different data centers within a multi-zone region (MZR) is that they are separated by at least 10 km or 6 mi. This is a significant improvement from our legacy plans in which you can have only 2 nodes that are in a single data center. In addition, Standard and Enterprise HADR plans also provide `Read on standby` capability. {{site.data.keyword.Db2_on_Cloud_short}} also provides backups, which can be restored to a new region if all data centers are unrecoverable. These backups, and archive logs, are geo-replicated across several regions (more than 400 km or 250 mi away from the MZR), protecting you from even the worst natural disasters. In many cases, this suffices instead of having a DR node in a different region. <!--If not, there is an upcoming Cross-Region DR feature. [Create a support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} and have a conversation with our Development Operations team if you require this Cross-Region DR-specific feature.-->

### Is HIPAA supported by Standard and Enterprise plans?
{: #q_hipaa}
{: faq}
{: support}

As of **October 20, 2020**, both the Standard and Enterprise plans support the **Health Information Portability and Accountability Act** of 1996 ("HIPAA"). 

For more information about restrictions, consult the [Service Description](http://www-03.ibm.com/software/sla/sladb.nsf/sla/bm-7519-14){: external}.

### How can we meet the published upgrade timeline if we require a key feature that isn't currently available?
{: #q_feat_not_avail}
{: faq}
{: support}

<!--
{{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plans will provide support for data centers in Amsterdam, Milan, Paris, and Toronto. However, these data centers are not currently available; we expect to support these by **November 6, 2020**. Cross-Region DR is targeted to be available by **November 30, 2020**. EU Cloud compliance certification will be available by **February, 2021**.
-->

If any not-yet-supported features remain a hard requirement for your new system, you must [create a support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} (include the affected hostnames) to obtain an extension beyond the published deadlines for initiating upgrades (**November 5, 2020**) and completing the transition (**November 15, 2020**). Our team will work with you to extend the deadlines. However, all upgrades must be completed by **November 30, 2020**. We'll provide more instructions in the support case to coordinate the upgrade for the specific hostnames that are impacted. 

It remains important that you schedule time to complete upgrades within the published extension timeline and not delay. Even if your support case granted an extension under this scenario, your systems will be blocked and automatic upgrading will begin on **December 1, 2020** if the upgrade was not completed by **November 30, 2020**. If there is a further delay for us to deliver any of these features beyond **November 30, 2020**, we'll seek an exception for you to continue using your legacy system until we delivery that feature. 

<!--
### My plan instance is still on Cloud Foundry. Do I need to migrate it to Resource Controller before I upgrade to a Standard or Enterprise plan?
{: #q_rc}
{: faq}
{: support}

Yes, you'll need to migrate to Resource Controller. See [Resource controller (RC)](/docs/Db2onCloud?topic=Db2onCloud-rc).

After you migrate a plan instance to Resource Controller, you can no longer use Cloud Foundry CLI commands to manage it.

Additional information:
- [Managing resource groups](/docs/account?topic=account-rgs#adding-resources-to-a-resource-group)
- [General {{site.data.keyword.cloud_notm}} CLI (ibmcloud) commands](/docs/cli?topic=cli-ibmcloud_cli)
-->

<!--
### What is the V2 upgrade timeline?
{: #q_timeline}
{: faq}
{: support}

We will send out notifications starting in **early August**. As we finish the prerequisites needed for your specific instance(s), we'll notify you that we are ready. You have until **October 15, 2020** to complete the upgrade, which means you should plan to start by early October at the latest.
-->
<!--
### What happens if I don't initiate the upgrade before the deadline?
{: #q_consequences}
{: faq}
{: support}

If you don't initiate the upgrade from your {{site.data.keyword.Db2_on_Cloud_short}} legacy plan by **November 5, 2020**, we will start the [upgrade](/docs/Db2onCloud?topic=Db2onCloud-auto_upgrade_plans){: external} on your behalf by creating a new {{site.data.keyword.Db2_on_Cloud_short}} plan instance, moving your data, DDL, and users into your new plan. Your legacy plan instance will remain in your dashboard list of resources and you will continue to be billed for this legacy plan instance until we restrict access. It is strongly recommended that you complete the plan upgrade to the new {{site.data.keyword.Db2_on_Cloud_short}} Standard or Enterprise plan. In most cases, the upgrade will lower your monthly costs.
-->
<!--More details about how you can connect to your auto-upgraded plan and how you will be billed will be provided in the near future.-->

<!-- If you don't initiate the upgrade, we will block access to your {{site.data.keyword.Db2_on_Cloud_short}} V1 system on **October 1, 2020**. You can reinstate access by creating a new V2 service instance or contacting our support team. If by **October 15**, you do nothing, we will start the migration on your behalf by creating a {{site.data.keyword.Db2_on_Cloud_short}} V2 system, move your data, DDL, and users into our new V2 plans, but without touching your V1 service instance. In other words, you'll still see your V1 plan in your list of service instances, and will continue to be billed for this V1 service instance, but under the covers your instance will be in a V2 plan. It is strongly recommended that you complete the upgrade so that your service instance is updated to the {{site.data.keyword.Db2_on_Cloud_short}} V2 plan. In most cases, this will lower your monthly costs. If you maintain both the V1 and V2 systems, you will be billed for both systems after the 14 day grace period. -->

<!--
### What do I need to do if my system was automatically upgraded?
{: #q_auto_upgrade}
{: faq}
{: support}

If you didn't initiate the upgrade and we created a V2 system on your behalf, you will lose connectivity to your V1 instance on **November 2, 2020** when we transition any remaining systems from V1 to V2. To gain access to your new system, log in to your cloud dashboard to obtain new access credentials and host information for your V2 system.  Update any {{site.data.keyword.Db2_on_Cloud_short}} applications with the new connection information. You completed the upgrade process. You upgraded your V1 plan to the new V2 plan with its related pricing. You can now delete the V1 plan.
-->
<!--
### You told me that I have an upgraded plan instance, but I can't find it in the {{site.data.keyword.cloud_notm}} dashboard -- what do I do?
{: #q_find}
{: faq}
{: support}
-->
<!--You might not have access to the service instance if you have only been connecting to it directly without going through {{site.data.keyword.cloud_notm}}. You probably provisioned it under a different account. Maybe you received an email because you own a functional ID that owns one or more instances.--> 
<!--If you are having difficulty, [create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external}.
-->

### I decided not to move my data to the new Standard or Enterprise plan. What should I do to opt out?
{: #q_opt_out}
{: faq}
{: support}

You must delete your legacy plan instance from the {{site.data.keyword.cloud_notm}} dashboard or contact Customer Support. We are moving all plans to the new Standard and Enterprise plans because of the upcoming **End of Support** of a key component in our legacy plans. <!-- For this reason we have no exception process for retaining your V1 legacy instance beyond November. If you have a business reason for needing an additional week or two after the **October 15, 2020** deadline, we will consider the request. The reason that we give a deadline of October 15 is because on this day we will start initiating the upgrade for all remaining instances (i.e. for any instance where the owner did not initiate it themselves). -->

### What if I previously created a new Standard or Enterprise plan instance and I want to migrate to it?
{: #q_previous_v2}
{: faq}
{: support}

You cannot migrate to an existing Standard or Enterprise plan instance after it's been previously created. You must delete your existing Standard or Enterprise plan instance and follow the steps that are outlined here to initiate the upgrade to a target to which you can migrate.

### What if I'm not receiving emails that are related to this legacy plan upgrade?
{: #q_no_emails}
{: faq}
{: support}

The owner of your {{site.data.keyword.cloud_notm}} account that is associated with the legacy {{site.data.keyword.Db2_on_Cloud_short}} plan instance must [create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} to add additional email addresses to the {{site.data.keyword.cloud_notm}} account.

### There is a new alert on my {{site.data.keyword.Db2_on_Cloud_short}} console that says the service will be restricted on November 2, 2020. What do I do?
{: #q_alert_shutdown}
{: faq}
{: support}

This is a generic alert on all legacy dashboards to provide another channel of communications for this required upgrade. This alert was published before the timeline was extended on October 28, 2020 - so the alert is incorrect now - you can rely on the information in this document as up-to-date and accurate. <!--If you are following the upgrade instructions and timeline in this document, there is no change with the existing information that describes key dates and upgrade steps. We hope that you were able to initiate upgrades through the cloud catalog and had a positive experience. **November 5, 2020** is an important milestone after which self-initiated upgrades are no longer available unless an extension was granted as a [feature availability gap](#q_feat_not_avail) or you experienced a technical issue or business impact; either situation would require a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} where we will coordinate with you on the next steps and, if needed, extend downstream timelines.-->
<!--
In general, we must restrict access to legacy systems with no upgrade activity so that our operations team can have enough time to auto-upgrade remaining systems prior to the End of Life occurring on **November 30, 2020**. Therefore, after **November 9, 2020**, instances with no action will be upgraded in batches through to **November 17, 2020** and access will be restricted to legacy instances as the batches are auto-upgraded; then you'll be notified that recovery is available. If you have an upgrade underway, which does not complete by **November 15, 2020** or if you have an open support case to resolve technical or business issues, your instance will not be auto-transitioned and we'll coordinate through the support case or grant an additional 5 business days after sync is ready. Instructions to recover your instance(s) to quickly get up and running under a new Standard or Enterprise plan will be available starting **November 9, 2020**. It's important to IBM that this upgrade not impact your business. If the alert and related timeline comes as a surprise, we urge you to review all of the information in this document and, if needed, open a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} to request an extension on the access restriction prior to **November 5, 2020**. Otherwise, the upgrade timeline will apply and you'll need to follow the recovery steps for [auto-upgraded instances](/docs/Db2onCloud?topic=Db2onCloud-auto_upgrade_plans){: external}. -->

### How can I learn more?
{: #q_learn_more}
{: faq}
{: support}

- For more information about the plan upgrades, see [Upgrading {{site.data.keyword.Db2_on_Cloud_short}} plans](#upgrade_plans).
- For information about our Standard and Enterprise plans, see [About: Plans and configurations](/docs/Db2onCloud?topic=Db2onCloud-about#ab_plans_cfgs)
- [Blog post that announces new Enterprise HA plan](https://www.ibm.com/cloud/blog/announcements/db2-on-cloud-announces-new-enterprise-high-availability-plan){: external}
- [Blog post announcing new Standard HA plan](https://www.ibm.com/cloud/blog/announcements/db2-on-cloud-standard-plan){: external}
- [What's New](https://www.ibm.com/support/pages/node/739537){: external} about the {{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plans now available in 6 data centers, including support for Oracle compatibility


<!--
You can also refer to the [What's New in IBM Db2 on Cloud](https://www.ibm.com/support/pages/node/739537){: external} where the new plans and features were announced. 

The legacy plan upgrade is currently available in the following data centers:
- Dallas
- Frankfurt
- London
- Sydney
- Tokyo
- Washington, DC

The legacy plan upgrade will be available in the following data centers by **November 16, 2020**:
- Amsterdam
- Milan
- Montréal
- Paris
- Sao Paulo
- Toronto

For those of you with a **HIPAA** requirement, the new systems were made available on **October 20, 2020**. 

Legacy-style disaster recovery (DR) is planned to be supported by **November 30, 2020**. However, [read more](#q_leverage_ha) about the high-availability nodes spanning multiple zones now available with the new plans to determine if this satisfies your DR requirements.
-->
