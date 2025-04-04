---
title: Updating your Content Fragments for Optimized GraphQL Filtering
description: Learn how to update your Content Fragments for Optimized GraphQL Filtering in Adobe Experience Manager as a Cloud Service for headless content delivery.
exl-id: 211f079e-d129-4905-a56a-4fddc11551cc
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
---
# Updating your Content Fragments for optimized GraphQL Filtering {#updating-content-fragments-for-optimized-graphql-filtering}

To optimize the performance of your GraphQL filters, run a procedure to update your Content Fragments.

>[!NOTE]
>
>After updating your Content Fragments, you can follow the recommendations for [Optimizing GraphQL Queries](/help/headless/graphql-api/graphql-optimization.md).


## Prerequisites {#prerequisites}

There are prerequisites for this task:

1. Ensure that you have a minimum of the 2023.1.0 release  of AEM as a Cloud Service.

1. Ensure that the user performing the task has the required permissions:

   * at a minimum, the `Deployment Manager` role in Cloud Manager is required.

## Updating your Content Fragments {#updating-content-fragments}

1. Enable the update by setting the following variables for your instance using the Cloud Manager UI:

   ![Cloud Manager Environment Configuration](assets/cfm-graphql-update-01.png "Cloud Manager Environment Configuration")

   The available variables are:

   | |Name |Value |Default Value |Service |Applied |Type |Notes |
   |---|---|---|---|---|---|---|---|
   |1 |`CF_MIGRATION_ENABLED` |`1` |`0` |All | |Variable |Enables(!=0) or disables(0) triggering of Content Fragment migration job. |
   |2 |`CF_MIGRATION_ENFORCE` |`1` |`0` |All | |Variable |Enforce (!=0) remigration of Content Fragments. Setting this flag to 0 does an incremental migration of CFs. This means, if the job is terminated for any reason, then the next run of the job starts migration from the point where it got terminated. The first migration is recommended for enforcement (value=1). |
   |3 |`CF_MIGRATION_BATCH` |`50` |`50` |All | |Variable |Size of the batch for saving the number of Content Fragments after migration. This is relevant to how many CFs are saved to the repository in one batch, and can be used to optimize the number of writes to the repository. |
   |4 |`CF_MIGRATION_LIMIT` |`1000` |`1000` |All | |Variable |Max number of Content Fragments to process at a time. See also notes for `CF_MIGRATION_INTERVAL`. |
   |5 |`CF_MIGRATION_INTERVAL` |`60` |`600` |All | |Variable |Interval (seconds) to process the remaining Content Fragments up until the next Limit. This interval is also considered as both a wait-time before starting the job, and a delay between processing of each subsequent CF_MIGRATION_LIMIT number of CFs. (*) |

   >[!NOTE]  
   >
   >(*)
   >
   >The value of `CF_MIGRATION_INTERVAL` can also help to approximate the total execution time of the migration job. 
   >
   >For example:
   >
   >* Total number of Content Fragments = 20,000
   >* CF_MIGRATION_LIMIT = 1000
   >* CF_MIGRATION_INTERNAL = 60 (Sec)
   >* Approximate time required to complete the migration = 60 + (20,000/1000 * 60) = 1260 Sec = 21 Minutes
   >  The additional "60" seconds added at the start is due to the initial delay when starting the job.
   >
   >This is only the *minimum* time required to complete the job, and does not include the I/O time. The actual time taken could be more than this estimation.  

1. Monitor the progress and completion of the update.

   To do this, monitor the logs on author and golden-publish from:
   
   * `com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob`

     * Author logs; for example:

       ```shell
       23.01.2023 13:13:45.926 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<dd9ffdc1-0c28-4d04-9a96-5d4d223e457e> is the leader, will schedule the upgrade schedule job.
       ...
       23.01.2023 13:13:45.941 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
       
       23.01.2023 13:20:40.960 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 6m, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
       ```

     * Golden-publish logs; for example:

       ```shell
       23.01.2023 12:35:05.150 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<ad1b399e-77be-408e-bc3f-57097498fddb> is the leader, will schedule the upgrade schedule job.
      
       23.01.2023 12:35:05.161 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
       ...
       23.01.2023 12:40:45.180 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 5m, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
       ```

   Customers, who enabled access to the environment logs using Splunk, can use the example query below to monitor the upgrade process. For details about enabling Splunk logging, see [Debugging Production and Stage](/help/implementing/developing/introduction/logging.md#debugging-production-and-stage).

   ```splunk
   index=<indexName> sourcetype=aemerror aem_envId=<environmentId> msg="*com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished*" 
   (aem_tier=golden-publish OR aem_tier=author) | table _time aem_tier pod_name msg | sort -_time desc
   ```

   Where:

   * `environmentId` - a customer environment identifier; for example, `e1234`
   * `indexName` - a customer index name, gathering `aemerror` events

   Example output:

   <table style="table-layout:auto">
     <thead>
       <tr>
       <th>_time</th>
       <th>aem_tier</th>
       <th>pod_name</th>
       <th>msg</th>
       </tr>
     </thead> 
     <tbody>
       <tr>
         <td>2023-04-21 06:00:35.723</td>
         <td>author</td>
         <td>cm-p1234-e1234-aem-author-76d6dc4b79-8lsb5</td>
         <td>[sling-threadpool-bb5da4dd-6b05-4230-93ea-1d5cd242e24f-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 391m, slingJobId: 2023/4/20/23/16/db7963df-e267-489b-b69a-5930b0dadb37_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=36756, failedCount=0, skippedCount=0}</td>
       </tr>
       <tr>
         <td>2023-04-21 06:05:48.207</td>
         <td>golden-publish</td>
         <td>cm-p1234-e1234-aem-golden-publish-644487c9c5-lvkv2</td>
         <td>[sling-threadpool-284b9a9a-8454-461e-9bdb-44866c6ddfb1-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 211m, slingJobId: 2023/4/20/23/15/66c1690a-cdb7-4e66-bc52-90f33394ddfc_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=19557, failedCount=0, skippedCount=0}</td>
       </tr>
     </tbody>
   <table>

1. Disable the update procedure.

   >[!IMPORTANT]
   >
   >This step is required to complete the upgrade.

   After the update procedure has run, reset the cloud environment variable `CF_MIGRATION_ENABLED` to '0', to trigger the recycling of all pods.

   | |Name |Value |Default Value |Service |Applied |Type |Notes |
   |---|---|---|---|---|---|---|---|
   | |`CF_MIGRATION_ENABLED` |`0` |`0` |All | |Variable |Disables(0) (or Enables(!=0)) triggering of Content Fragment migration job.  |

   >[!NOTE]
   >
   >This is important for the publish tier, as the content update is only done on golden-publish, and when recycling of pods, all normal publish pods are based on the golden-publish.

1. Verify completion of the update procedure.

   You can verify the successful completion of the update using the repository browser in the Cloud Manager developer console to check the content fragment data.

   * Before the first complete migration, the `cfGlobalVersion` property does not exist. 
     Therefore, the presence of this property, on the JCR node `/content/dam` with a value of `1`, confirms the completion of the migration.

   * You can also check the following properties on the individual Content Fragments:

     * `_strucVersion` should have the value of `1`
     * `indexedData` structure must exist

     >[!NOTE]
     >
     >The procedure updates Content Fragments on Author and Publish instances. 
     >
     >Therefore, Adobe recommends that you perform the verification by way of the repository browser for *at least* one Author *and* one Publish instance.

## Limitations {#limitations}

Be aware of the following limitations:

* Optimization of the performance of GraphQL filters is only possible after a complete update of all your Content Fragments (indicated by the presence of the `cfGlobalVersion` property for the JCR node `/content/dam`)

* If Content Fragments are imported from a content package (using `crx/de`) after the update procedure is run, then those Content Fragments are not considered in the GraphQL query results until the update procedure is run again.
