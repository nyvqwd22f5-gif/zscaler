# Integrating with Amazon Security Lake
Source: https://help.zscaler.com/zpc/integrating-amazon-security-lake
PDF: https://help.zscaler.com/pdf/com/en/1420996.pdf

You can integrate Zscaler Posture Control (ZPC) with the Amazon Security Lake service to export and store the alert data in a dedicated Amazon Simple Storage Service (S3) bucket that is pre-configured as part of the Amazon Security Lake setup.
Amazon Security Lake is a data lake for security logs, built into the customer’s account. The data lake is backed by an Amazon S3 bucket and organizes data as a set of Lake Formation tables. Amazon Security Lake is designed to optimize the cost of storing and querying massive security logs. Amazon Security Lake uses the Open Cybersecurity Schema Framework (OCSF) as the selected format for the alert information and requires the Parquet file format for the stored alerts. To learn more, see the [AWS documentation](https://aws.amazon.com/security-lake/).
[Prerequisites]
Complete the following steps before exporting the alert data to Amazon Security Lake.
- [1. Configure the Amazon Security Lake Service](#awsslservice)
- [2. Configure the Custom Source](#customsource)
- [3. Collect the S3 Bucket Details](#bucketdetails)
Integrating ZPC with Amazon Security Lake
To configure the Amazon Security Lake integration:
- Go to **Administration** > **Integrations**.
- Click **Add** for cloud storage integration.
-
On the **Add Cloud Storage Integration** page:
- For **Integration Name**, enter a unique name for the integration.
- For **Cloud Storage**, select **Amazon Security Lake**.
[See image.](#zpc-selectsecurity)
- Click **Next**.
-
On the **Cloud Storage** page:
- []**ZPC AWS Account**: Copy the ZPC AWS Account ID and paste it in the **Account ID** field while [creating the custom source](#customsource) on the Amazon Security Lake console.
- **External ID**: Copy the External ID and paste it in the **External ID** field while [creating the custom source](#customsource) on the Amazon Security Lake console.
- **IAM Role**: Enter the AWS Identity and Access Management (IAM) ARN role that you copied after [creating the custom source](#customsource). This role allows the ZPC AWS account to write data to Security Lake.
- **Amazon S3 Bucket Name**: Provide the Amazon S3 bucket name.
- **Bucket Region**: Select the bucket region from the drop-down menu. You should have these details from the [Prerequisites](#bucketdetails) step.
- **Folder Location**: Provide the folder path for the S3 bucket set for Amazon Security Lake. You should have these details from the [Prerequisites](#bucketdetails) step.
[See image.](#zpc-config)
-
Click **Test Connection** to verify the connection between ZPC and the AWS service. The test connection validates that the S3 bucket exists.
A message is displayed that the connection is successful.
- Click **Next**.
-
Review the integration summary. Click the **Edit** icon if you want to make any changes.
[See image.](#zpc-lakesummary)
- Click **Finish**.
You can see the integration details on the Integrations page. The initial status shows as *Pending* because data is not yet sent to the Amazon Security Lake. Once you configure and associate the alert rules with this integration, and when ZPC starts sending the alert data to Amazon Security Lake, the status changes to *Success*. [See image.](#zpc-lakestatus)
Adding Alert Rules for Amazon Security Lake
Once the integration is set up, you must configure the alert rules on the ZPC Admin Portal. Alert rules define which alerts should be sent to the integrated Amazon Security Lake service.
To add an alert rule:
- Go to **Alerts** > **Notifications**.
-
Click **Create Rule**.
[See image.](#zpc-alertrule)
-
Under **General Information**:
- For **Alert Rule Name**, enter a unique name for the rule.
- For **Alert Type**, select **Cloud**.
- To enable the alert rule immediately after it’s created, set the **Alert Rule Status** to **Enabled**.
[See image.](#zpc-ruletype)
- Click **Next**.
-
Under **Scope**:
- Select the scope for which you want to receive alert notifications. You can filter the scope by Business Units, Clouds, Accounts, Regions, or Tags. To learn more about scope, see [About Administrators](/zpc/about-administrators).
- Select the policies that must be associated with this alert rule, so alert notifications are sent whenever those policies are impacted. You can filter the policies by **Compliance**, **Severity**, **Threat Category**, and **Policy Type**. To learn more, see [About Security Policies](/zpc/about-security-policies).
[See image.](#zpc-scope)
- Click **Next**.
-
Under **Notifications**:
- For **Cloud Storage**, select **Amazon Security Lake**.
- From the drop-down menu that appears, select the relevant Amazon Security Lake integration you previously configured.
[See image.](#zpc-alertnotification)
- Click **Next**.
-
Review the alert rule summary. Click the **Edit** icon if you want to make any changes.
[See image.](#zpc-alertreview)
- Click **Finish**.
Partitioning
Partitioning is a technique for organizing datasets so they can be queried efficiently. ZPC alerts are exported in Open Cybersecurity Schema Framework (OCSF) format to Amazon Security Lake and are stored in Parquet files. The Parquet format is a column-based data format.
The files are limited by size. A new file is generated and posted whenever the file size reaches 256 MB or after 5 minutes. The files are stored under the root path created for the custom source. The folder structure is: `region=<awsregion>/accountid=<cloudaccountid>/eventDay=<YYYYMMDD>`.
New folders are generated to host new alert files.
OCSF Mapping
The Open Cybersecurity Schema Framework (OCSF) includes an open specification for the normalization of security telemetry across a wide range of security products and services, as well as open-source tools that provide support for using the OCSF schema. To learn more, see the [GitHub page on OCSF](https://github.com/ocsf/).
The following tables provide the list of cloud alert and IaC alert data logs that are written to OCSF.
- [Cloud Alert Payload](#cloudocsf)
- [IaC Alert Payload](#iacocsf)
Troubleshooting
Zscaler recommends the following resolutions for issues that you might encounter while integrating and using ZPC with Amazon Security Lake.
| **Issue** | **Resolution** |
| --------- | -------------- |
| The ZPC alert data is available in the Amazon Security Lake S3 bucket, but the Glue Crawler fails to parse the data into the Security Lake. | This issue typically occurs when the custom source that is created for the integration is using the wrong event class. Make sure you create the custom source with the `Security Finding` event class. |
| The Amazon Security Lake integration object on the ZPC Integrations page shows a *Failed* status. | This indicates that ZPC does not have the permission to access the Amazon Security Lake S3 bucket. While integrating ZPC with Amazon Security Lake, make sure you have applied the required policy to grant ZPC access to the S3 bucket. |
| New alerts are present on the ZPC Admin Portal but are not exported to the Amazon Security Lake. | Make sure you've configured the alert rule notification and check the scope of the alert rule. |
[]Make sure you have a configured Amazon Security Lake service that is connected to an S3 bucket in your AWS account. To learn more, see the [Amazon Security Lake documentation](https://aws.amazon.com/security-lake/).
[]Zscaler is regarded as a source integration for Amazon Security Lake. To enable the integration, you must generate a custom source in Amazon Security Lake. To learn more, see the [Amazon Security Lake documentation](https://aws.amazon.com/security-lake/).
- Sign in to your AWS account.
- Open the [Security Lake console](https://console.aws.amazon.com/securitylake/).
- From the Security Lake left-navigation menu, select customized** sources**.
- Scroll down to the Customized** source details** section.
- **Data source name**: Provide a name for this custom source. This name determines the path in the S3 bucket to which the alert files will be written. Amazon Security Lake generates a new folder for each custom source.
- **Event class**: Make sure you use the `Security_Finding` event class.
- **Region**: Select the region from the drop-down menu. The custom source is created in the region where the AWS console is connected. You need to specify this region while setting up the Security Lake integration on the ZPC Admin Portal.
-
**Account ID**: Enter the [account ID that you copied](#zpc-accountid) from the **Cloud Storage** page in the ZPC Admin Portal.
[See image.](#zpc-actid)
- **External ID**: Enter the [external ID that you copied](#zpc-accountid) from the **Cloud Storage** page in the ZPC Admin Portal. To learn more, see the [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html).
-
The **AWS Account ID** and **External ID** are identifiers of the custom source (ZPC) that writes logs and events to the data lake.
-
Click **Create**.
The Amazon Security Lake custom source is created.
- On the **Customized sources** page, search for the custom source you created.
-
Copy the ARN IAM role. You need to provide this value while setting up the Security Lake integration on the ZPC Admin Portal.
[See image.](#zpc-arn)
[]Make sure you have the following information for setting up the ZPC integration:
- The Amazon Security Lake S3 region
- The S3 bucket name (e.g., aws-security-data-lake-us-east-2-o-4g8wg3sx9z)
- The folder prefix for the custom source path on the S3 bucket (e.g., /ext/zpc-security-alerts)
[]![Select Amazon Security Lake as the cloud storage](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-add-securitylakeintegration.png)
[]![Set up the security lake configuration](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-securitylake-configexternalid1.png)
[]![Review the integration details](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-securitylake-review.png?1685525443)
[]![View the Amazon Security Lake integration status](/downloads/zpc/integrations/about-third-party-integrations/zpc-integrationstatus.png)
[]![Create an alert rule](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-createalertrule.png)
[]![Specify the alert rule name and type](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-alertrule-details.png)
[]![Select the scope and policies](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-alertrule-scope.png)
[]![Set up the alert notification](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-alertrule-notification.png)
[]![Review the alert rule details](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-alertrule-review.png)
[]![Enter the account ID copied from the ZPC Admin Portal](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-securitylake-ZPCacctID.png)
[]![Copy the ARN IAM role](/downloads/zpc/third-party-integrations/cloud-storage-integrations/integrating-amazon-security-lake/zpc-securitylake-copyarn.png)
[]
| **OCSF Field** | **ZPC Cloud Alert Field** | **Static Value** |
| -------------- | ------------------------- | ---------------- |
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
| metadata.product.name |  | zpc |
| metadata.product.vendor_name |  | zscaler |
| metadata.version |  | 2.2 |
| compliance.requirements.0 | compliance_benchmark |  |
| compliance.requirements.1 | compliance_control_number |  |
| attacks.0.tactics.0.uid | NA | NA |
| attacks.0.technique.uid | NA | NA |
| attacks.0.version |  | "ATT&CK v13" |
[]
| **OCSF Field** | **ZPC IaC Alert Field** | **Static Value** |
| -------------- | ----------------------- | ---------------- |
| category_name |  | Findings |
| category_uid |  | 2 |
| class_name |  | Security Finding |
| class_uid |  | 2001 |
| time | alert_created_dt |  |
| time_dt | alert_created_dt |  |
| activity | alert_status |  |
| activity_id | alert_status |  |
| type_name | alert_status |  |
| type_uid | alert_status |  |
| state_id | alert_status |  |
| status | alert_status |  |
| status_detail | alert_status_description |  |
| message | alert_description |  |
| severity | severity |  |
| severity_id | severity |  |
| finding.uid | alert_id |  |
| finding.age | age |  |
| finding.title | policy_name |  |
| finding.created_time | alert_created_dt |  |
| finding.modified_time | alert_updated_dt |  |
| finding.desc |  | ocfs_finding_desc.txt |
| cloud.provider | scan_plugin |  |
| resources.0.name | resource_name |  |
| resources.0.uid | resource_id |  |
| resources.0.labels | tags |  |
| metadata.product.name |  | zpc |
| metadata.product.vendor_name |  | zscaler |
| metadata.version |  | 2.2 |
| compliance.requirements.0.name | compliance_benchmark |  |
| compliance.requirements.0.uid | compliance_control_number |  |
| policy.theme | policy_theme |  |
| policy.uid | policy_id |  |
| policy.type | policy_type |  |