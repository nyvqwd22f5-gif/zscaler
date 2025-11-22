# Integrating with Amazon Security Lake
Source: https://help.zscaler.com/dspm/integrating-amazon-security-lake
PDF: https://help.zscaler.com/pdf/com/en/1487541.pdf

You can integrate DSPM with the Amazon Security Lake service to export and store the alert data in a dedicated Amazon Simple Storage Service (S3) bucket that is pre-configured as part of the Amazon Security Lake setup.
Amazon Security Lake is a data lake for security logs, built into the customer’s account. The data lake is backed by an Amazon S3 bucket and organizes data as a set of Lake Formation tables. Amazon Security Lake is designed to optimize the cost of storing and querying massive security logs. Amazon Security Lake uses the Open Cybersecurity Schema Framework (OCSF) as the selected format for the alert information and requires the Parquet file format for the stored alerts. To learn more, refer to the [AWS documentation](https://aws.amazon.com/security-lake/).
Prerequisites
Complete the following steps before exporting the alert data to Amazon Security Lake.
- [1. Configure the Amazon Security Lake service.](#awsslservice)
- [2. Configure the custom source.](#customsource)
- [3. Collect the S3 Bucket details.](#bucketdetails)
Integrating DSPM with Amazon Security Lake
To configure the Amazon Security Lake integration:
- Go to **Administration** > **Integrations**.
- Click **Add** for cloud storage integration.
-
On the **Add Cloud Storage Integration** page:
- For **Integration Name**, enter a unique name for the integration.
- For **Cloud Storage**, select **Amazon Security Lake**.
[See image.](#ds-selectlake)
- Click **Next**.
-
On the **Cloud Storage** page:
- []**DSPM AWS Account**: Copy the DSPM AWS Account ID and paste it in the **Account ID** field while [creating the custom source](#customsource) on the Amazon Security Lake console.
- **External ID**: Copy the External ID and paste it in the **External ID** field while [creating the custom source](#customsource) on the Amazon Security Lake console.
- **IAM Role**: Enter the AWS Identity and Access Management (IAM) ARN role that you copied after [creating the custom source](#customsource). This role allows the DSPM AWS account to write data to Security Lake.
- **Amazon S3 Bucket Name**: Provide the Amazon S3 bucket name.
- **Bucket Region**: Select the bucket region from the drop-down menu. You should have these details from the [Prerequisites](#bucketdetails) step.
- **Folder Location**: Provide the folder path for the S3 bucket set for Amazon Security Lake. You should have these details from the [Prerequisites](#bucketdetails) step.
[See image.](#ds-cs-details)
-
Click **Test Connection** to verify the connection between DSPM and the AWS service. The test connection validates that the S3 bucket exists.
A message is displayed that the connection is successful.
- Click **Next**.
-
Review the integration summary. Click the **Edit** icon if you want to make any changes.
[See image.](#ds-summary)
- Click **Finish**.
You can see the integration details on the Integrations page. The initial status shows as Pending because data is not yet sent to the Amazon Security Lake. After you configure and associate the alert rules with this integration, and when DSPM starts sending the alert data to Amazon Security Lake, the status changes to Success.
Partitioning
Partitioning is a technique for organizing datasets, so they can be queried efficiently. DSPM alerts are exported in OCSF format to Amazon Security Lake and are stored in Parquet files. The Parquet format is a column-based data format.
The files are limited by size. A new file is generated and posted whenever the file size reaches 256 MB or after 5 minutes. The files are stored under the root path created for the custom source. The folder structure is: `region=<awsregion>/accountid=<cloudaccountid>/eventDay=<YYYYMMDD>`.
New folders are generated to host new alert files.
OCSF Mapping
OCSF includes an open specification for the normalization of security telemetry across a wide range of security products and services, as well as open-source tools that provide support for using the OCSF schema. To learn more, refer to the [GitHub page on OCSF](https://github.com/ocsf/).
- [Cloud alert data logs written to OCSF](#cloudocsf)
Troubleshooting
Zscaler recommends the following resolutions for issues that you might encounter while integrating and using DSPM with Amazon Security Lake.
| **Issue** | **Resolution** |
| --------- | -------------- |
| The DSPM alert data is available in the Amazon Security Lake S3 bucket, but the Glue Crawler fails to parse the data into the Security Lake. | This issue typically occurs when the custom source that is created for the integration is using the wrong event class. Make sure you create the custom source with the `Security Finding` event class. |
| The Amazon Security Lake integration object on the DSPM Integrations page shows a Failed status. | This indicates that DSPM does not have the permission to access the Amazon Security Lake S3 bucket. While integrating DSPM with Amazon Security Lake, make sure you have applied the required policy to grant DSPM access to the S3 bucket. |
| New alerts are present in the DSPM Admin Portal but are not exported to the Amazon Security Lake. | Make sure you've configured the alert rule notification and check the scope of the alert rule. |
[]Make sure you have a configured Amazon Security Lake service that is connected to an S3 bucket in your AWS account. To learn more, refer to the [Amazon Security Lake documentation](https://aws.amazon.com/security-lake/).
[]Zscaler is regarded as a source integration for Amazon Security Lake. To enable the integration, you must generate a custom source in Amazon Security Lake. To learn more, refer to the [Amazon Security Lake documentation](https://aws.amazon.com/security-lake/).
- Sign in to your AWS account.
- Open the [Security Lake console](https://console.aws.amazon.com/securitylake/).
- From the Security Lake left-side navigation, select **customized sources**.
- Scroll down to the **Customized source details** section.
- **Data source name**: Provide a name for this custom source. This name determines the path in the S3 bucket to which the alert data is written. Amazon Security Lake generates a new folder for each custom source.
- **Event class**: Make sure you use the `Security_Finding` event class.
- **Region**: Select the region from the drop-down menu. The custom source is created in the region where the AWS console is connected. You need to specify this region while setting up the Security Lake integration in the DSPM Admin Portal.
- **Account ID**: Enter the [account ID that you copied](#zpc-accountid) from the **Cloud Storage** page in the DSPM Admin Portal.
-
**External ID**: Enter the [external ID that you copied](#zpc-accountid) from the **Cloud Storage** page in the DSPM Admin Portal. To learn more, see the [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html).
The **AWS Account ID** and **External ID** are identifiers of the custom source (DSPM) that writes logs and events to the data lake.
[See image.](#ds-customsourcedetails)
-
Click **Create**.
The Amazon Security Lake custom source is created.
- On the **Customized sources** page, search for the custom source you created.
-
Copy the ARN IAM role. You need to provide this value while setting up the Security Lake integration in the DSPM Admin Portal.
[See image.](#ds-arn)
[]Make sure you have the following information for setting up the DSPM integration:
- The Amazon Security Lake S3 region.
- The S3 bucket name (e.g., aws-security-data-lake-us-east-2-o-4g8wg3sx9z).
- The folder prefix for the custom source path on the S3 bucket (e.g., /ext/dspm-security-alerts).
[]![Select Amazon Security Lake as the cloud storage](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-security-lake/ds-securitylake-select.png)
[]![Configure Amazon Security Lake](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-security-lake/ds-securitylake-adddetails.png)
[]![Review the integration details](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-security-lake/ds-securitylake-review.png)
[]![Add the custom source details](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-security-lake/ds-securitylake-createsource.png)
[]![Create a custom source](/downloads/dspm/third-party-integrations/cloud-storage-services/integrating-amazon-security-lake/ds-securitylake-customsource.png)
[]
| **OCSF Field** | **DSPM Cloud Alert Field** | **Static Value** |
| -------------- | -------------------------- | ---------------- |
| category_name |  | Findings |
| category_uid |  | 2 |
| class_name |  | Security Finding |
| class_uid |  | 2001 |
| time | csp_event_timestamp |  |
| time_dt | csp_event_timestamp |  |
| activity | alert_status |  |
| activity_id | alert_status |  |
| type_name | alert_status |  |
| type_uid | alert_status |  |
| state_id | alert_status |  |
| status | alert_status |  |
| status_detail | alert_status_description |  |
| message | alert_description |  |
| severity | risk |  |
| severity_id | risk |  |
| finding.uid | alert_id |  |
| finding.title | policy_name |  |
| finding.created_time | alert_created_dt |  |
| finding.modified_time | alert_updated_dt |  |
| finding.desc |  | ocfs_finding_desc.txt |
| finding.types.0 | policy_type |  |
| finding.threat_category | policy_threat_category |  |
| finding.theme | policy_theme |  |
| finding.age | age |  |
| cloud.account_name | account_name |  |
| cloud.org_name | organisation_name |  |
| cloud.provider | csp |  |
| cloud.resource_uid | resource_id |  |
| cloud.account_uid | account_id |  |
| cloud.org_uid | organisation_id |  |
| resources.0.account_uid | account_id |  |
| resources.0.name | resource_name |  |
| resources.0.type | resource_type |  |
| resources.0.labels.0 | tags |  |
| resources.0.details |  | ocfs_resource_details.txt |
| resources.0.clusterName | cluster_name |  |
| resources.0.clusterType | cluster_type |  |
| resources.0.namespace | namespace |  |
| resources.0.associatedCloud | associated_cloud |  |
| resources.0.owner.name |  | “” |
| resources.0.owner.uid | identity_id |  |
| resources.0.owner.type | identity_type |  |
| resources.0.owner.type_id |  | 0 |
| resources.0.owner.domain | identity_source |  |
| resources.0.owner.email_addr | identity_name |  |
| resources.0.owner.groups.0.name | identity_power_category |  |
| resources.Owner.TypeId |  | 0 |
| metadata.product.name |  | dspm |
| metadata.product.vendor_name |  | zscaler |
| metadata.version |  | 2.2 |
| compliance.requirements.0 | compliance_benchmark |  |
| compliance.requirements.1 | compliance_control_number |  |
| attacks.0.tactics.0.uid | NA | NA |
| attacks.0.technique.uid | NA | NA |
| attacks.0.version |  | "ATT&CK v13" |