# Configuring SaaS Security Scan Schedules
Source: https://help.zscaler.com/zia/configuring-saas-security-scan-schedules
PDF: https://help.zscaler.com/pdf/com/en/1401466.pdf

[Watch a video about Scan Configuration](https://fast.wistia.net/embed/iframe/3of852jyfl)
Before scheduling a scan, you must configure the SaaS Security Data at Rest Scanning [Data Loss Prevention (DLP)](/zia/about-saas-security-api-dlp) and [Malware Detection](/zia/about-saas-security-api-malware-detection) policies because the scan uses these policies during inspection.
SaaS Security Scan Configuration allows you to schedule scans that use your SaaS Security DLP and Malware Detection policies to inspect content in sanctioned SaaS applications.
To learn more, see [Understanding SaaS Security Scan Schedules](/zia/understanding-saas-security-api-scan-schedules).
Adding a SaaS Security Scan Schedule
You can configure only one scan per SaaS application tenant, but you can configure scans for multiple application tenants. To learn more about SaaS Security scan limits, see [Ranges & Limitations](/zia/ranges-limitations#Rules).
To add a SaaS Security scan schedule:
- Go to **Policy** > **SaaS Security **> **Scan Configuration**.
-
Click **Add Scan Schedule**.
The **Add Scan Schedule** window appears.
- In the **Add Scan Schedule** window:
- **SaaS Application Tenant**: Select the [SaaS application tenant](/zia/about-saas-application-tenants) to which you want to apply the scan.
- **Policy**: Select the SaaS Security API policies you want the scan to use when inspecting content. You must choose at least one policy to schedule a scan.
- **Data to Scan**: Specify the amount of historical data for the scan to inspect. When the scan processes historical content, it continuously inspects active data at the same time. To learn more, see [Configuring a Scan to Inspect Historical Data](/zia/understanding-saas-security-api-scan-schedules#configure-scan-inspect-historic).
- **All Data**: The scan inspects all historical data. The time it takes to complete the scan depends on the amount of data you have.
- **Data Created or Modified After**: The scan inspects historical data within a specific time frame. Use the **Calendar** menu to choose the starting date for the time frame.
- **New Data Only**: The scan ignores all historical data.
A few things to keep in mind regarding Webex Teams tenants:
- The Zscaler service can scan a historic data file only if a user downloads the file before the scan is started from the [SaaS Security API Scan Configuration page](/zia/about-saas-security-api-scan-configuration). This is due to an API limitation from Webex, [where only downloaded events are returned if the resource is a file](https://developer.webex.com/docs/api/v1/events/list-events).
- Due to a limitation from Webex, the Zscaler service can only scan historical data from 15 days prior to the scan’s start date. If you choose a date older than 15 days with the **Data Created or Modified After** option or choose **All Data**, the scan only inspects 15 days of historical data.
For example, you create a scan on November 14, 2023, and choose May 1, 2023, as the starting date of the time frame with the **Data Created or Modified After** option. You then start the scan on November 22, 2023. The scan inspects only historical data created or modified from November 7, 2023, to November 22, 2023.
- **Amazon S3 Buckets**: This section appears for only Amazon S3 tenants. In the table, view a list of all buckets associated with the tenant. You can set all buckets to be automatically scanned for DLP or Malware rules, or you can manually choose which buckets are scanned. You can also search for buckets by **Name**, **Exposure**, and **Tags**; and you can [modify the table and its columns](/zia/using-tables).
- [List of Columns for the Amazon S3 Buckets Table](#amazon-s3-buckets)
- **Bitbucket Repositories to be Scanned**: This section appears for only Atlassian Bitbucket tenants. In the table, view a list of all repositories associated with the tenant. You can set all repositories to be automatically scanned for DLP or Malware rules, or you can manually choose which repositories are scanned. You can also search for repositories by **Name** and **Exposure**, and you can [modify the table and its columns](/zia/using-tables).
- [List of Columns for the Bitbucket Repositories Table](#bitbucket-repositories)
If a user account’s public repository isn’t shared with the admin, the admin doesn't know the exact path of those repositories even though they are accessible. The admin can't identify the path because of the non-availability of Bitbucket cloud APIs to list all users, which limits the discovery of all accessible repositories against all user accounts. If a user shares their private repository with the admin, they become known, allowing the admin to discover public repositories in that user's account.
- **GitLab Repositories to be Scanned**: This section appears for only GitLab tenants. In the table, view a list of all repositories associated with the tenant. You can set all repositories to be automatically scanned for DLP or Malware rules, or you can manually choose which repositories are scanned. You can also search for repositories by **Name **and **Exposure **and [modify the table and its columns](/zia/using-tables).
- [List of Columns for the GitLab Repositories Table](#gitlab-buckets-table)
- **Google Cloud Platform Buckets**: This section appears for only Google Cloud Platform tenants. In the table, view a list of all buckets associated with the tenant. You can set all buckets to be automatically scanned for DLP or Malware rules, or you can manually choose which buckets are scanned. You can also search for buckets by **Name**, **Exposure**, and **Tags**; and you can [modify the table and its columns](/zia/using-tables).
- [List of Columns for the Google Cloud Platform Buckets Table](#google-cloud-platform-buckets)
- **Microsoft Azure Blob Containers**: This section appears for only Microsoft Azure tenants. In the table, view a list of all blob containers associated with the tenant. You can set all blob containers to be automatically scanned for DLP or Malware rules, or you can manually choose which blob containers are scanned. You can also search for blob containers by **Name**, **Exposure**, and **Tags**; and you can [modify the table and its columns](/zia/using-tables).
- [List of Columns for the Microsoft Azure Blob Containers Table](#microsoft-azure-blob-containers)
- **SharePoint Sites to be Scanned**: This section appears for only SharePoint tenants. In the table, view a list of all sites associated with the tenant. You can set all sites to be automatically scanned for DLP or Malware rules, or you can manually choose which sites are scanned. You can also search for sites by **Name **and [modify the table and its columns](/zia/using-tables).
- [List of Columns for the SharePoint Sites Table](#sharepoint-sites-table)
To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
- (Optional) Enter a **Description** including additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]For Amazon S3 tenants, you can view the list of all the scannable and unscannable buckets. For each bucket, you can view the following details:
- **Name**: The name of the bucket. You can sort this column.
When you select the bucket names, you create a list of available buckets for the DLP and Malware Detection policies, where you can specify buckets for inspection. You can’t select the CloudTrail and quarantine buckets for inspection. To learn more, see [Configuring the Data at Rest Scanning Policy](/zia/configuring-saas-security-api-control-policy).
- **Exposure**: Displays if the bucket is external, internal, private, or public.
- **Tags**: The Amazon S3 tags associated with the bucket.
- **Files**: The number of files the bucket contains.
![The Amazon S3 Buckets table for the Add Scan Schedule window](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/Amazon%20S3%20Buckets.png)
[]For the Bitbucket tenants, you can view the list of all the scannable and unscannable repositories. For each repository, you can view the following details:
- **Name**: The name of the repository. You can sort this column.
When you select the repository names, you create a list of available repositories for the DLP and Malware Detection policies, where you can specify repositories for inspection. You can’t select the quarantine repositories for inspection. To learn more, see [Configuring the Data at Rest Scanning Policy](/zia/configuring-saas-security-api-control-policy).
- **Exposure**: Displays if the repository is external, internal, private, or public.
![The Atlassian Bitbucket Buckets table for the Add Scan Schedule window.](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/Bitbucket%20Repositories.png)
[]For Google Cloud Platform tenants, you can view the list of all the scannable and unscannable buckets. For each bucket, you can view the following details:
- **Name**: The name of the bucket. You can sort this column.
When you select the bucket names, you create a list of available buckets for the DLP and Malware Detection policies, where you can specify buckets for inspection. You can’t select the quarantine buckets for inspection. To learn more, see [Configuring the Data at Rest Scanning Policy](/zia/configuring-saas-security-api-control-policy).
- **Exposure**: Displays if the bucket is external, internal, private, or public.
- **Tags**: The Google Cloud Platform tags associated with the bucket.
- **Files**: The number of files the bucket contains.
![The Google Cloud Platform Buckets table for the Add Scan Schedule window](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/Google%20Cloud%20Platform%20Buckets.png)
[]For Microsoft Azure tenants, you can view the list of all the scannable and unscannable blob containers. For each blob container, you can view the following details:
- **Name**: The name of the blob container. You can sort this column.
When you select the blob container names, you create a list of available blob containers for the DLP and Malware Detection policies, where you can specify blob containers for inspection. You can’t select the quarantine blob containers for inspection. To learn more, see [Configuring the Data at Rest Scanning Policy](/zia/configuring-saas-security-api-control-policy).
- **Exposure**: Displays if the blob container is external, internal, private, or public.
- **Tags**: The Microsoft Azure tags associated with the blob container.
- **Files**: The number of files the blob container contains.
![The Microsoft Azure Blob Containers table for the Add Scan Schedule window](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/Microsoft%20Blob%20Containers.png)
[]For SharePoint tenants, you can view the list of all the discovered and custom sites.
For discovered sites, you can view the following details:
- **Name**: The name of the site. You can sort this column.
When you select the site names, you automatically create a list of available sites for the DLP and Malware Detection policies, where you can specify sites for inspection. You can’t select the quarantine sites for inspection. To learn more, see [Configuring the Data at Rest Scanning Policy](/zia/configuring-saas-security-api-control-policy).
[See image.](#sharepoint-dscovered)
For custom sites, click **Add Items** to manually enter the site names to be scanned.
[See image.](#sharepoint-custom)
[]![The SharePoint Sites table for the Add Scan Schedule window.](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/SharePoint%20Sites-Discovered.png)
[]![The SharePoint Sites custom list for the Add Scan Schedule window.](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/configuring-saas-security-api-scan-schedules/SharePoint%20Sites-Custom.png)
[]For GitLab tenants, you can view the list of all the scannable and unscannable repositories. For each repository, you can view the following details:
- **Name**: The name of the repository. You can sort this column.
When you select the repository names, you automatically create a list of available repositories for the DLP and Malware Detection policies, where you can specify repositories for inspection. You can’t select the quarantine repositories for inspection. To learn more, see [Configuring the Data at Rest Scanning Policy](/zia/configuring-saas-security-api-control-policy).
- **Exposure**: Displays if the repository is external, internal, private, or public.
![The GitLab Buckets table for the Add Scan Schedule window.](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-saas-security-api-scan-schedules-draft/GitLab-Repositories-Table.png)