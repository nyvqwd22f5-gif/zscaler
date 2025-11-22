# About the Assets Report
Source: https://help.zscaler.com/unified/about-assets-report
PDF: https://help.zscaler.com/pdf/com/en/1497531.pdf

The Assets Report shows you the current state of your files, email messages, and objects. It also allows you to see the activity for any particular file, email message, or object all in one place.
The Assets Report provides the following benefits and enables you to:
- Gain visibility into your SaaS assets for various risk factors based on the application category.
- Analyze the report for application-specific vulnerabilities to configure stronger policies to mitigate threats.
About the Assets Report Page
On the Assets Report page (Analytics > Internet & SaaS > Analytics > SaaS Security Report > Assets), you can do the following:
- Select an **Application Category **to** **view the report for that category.
- Select to view the scans for a particular time frame. You can choose to view scans for the current day, the current week, the last 24 hours, the last 7 days, or customize up to the last 90 days.
- Click **Apply** to update the page with your selections. You can click **Reset** at any time.
![This image shows the filter options in the SaaS Assets Report - Gen AI Category](/downloads/zia/dashboard-analytics/reports/saas-security/saas-assets-report/Filter_options_in_assets_report1.png)
After you apply the preceding actions, a generated report appears for the application category you selected:
- [Collaboration Applications](#collabapps)
- [CRM Applications](#crmapps)
- [Email Applications](#emailapps)
- [File Sharing Applications](#fileapps)
- [Gen AI Applications](#genaiapps)
- [ITSM Applications](#itsmapps)
- [Public Cloud Storage Applications](#publiccloudstorage)
- [Source Code Repository Applications](#sourcecodeapps)
3rd-Party Integrations
The 3rd-Party Integrations tab shows [Zscaler 3rd-Party App Governance](/unified/what-3rd-party-app-governance) data about the integrations associated with an application across your corporate SaaS platforms. For example, integrations with the OneDrive application indicate potential third-party access to your organization's Google Workspace account. The following applications support the tab:
- Collaboration Applications (Slack, Microsoft Teams)
- File Sharing Applications (OneDrive, SharePoint, Google Drive)
- Email Applications (Exchange, Gmail)
- CRM Applications (Salesforce and Dynamic 365)
On the 3rd-Party Integrations tab, you can view:
- **Total Integrations**: The total number of integrations associated with the application (e.g., Google Drive) across your configured tenants.
- **Potentially Harmful / Vulnerable**: The number of integrations that are potentially harmful or vulnerable.
- **Dormant**: The number of integrations that are dormant (i.e., abandoned, inactive, or not maintained).
- **Overprivileged**: The number of integrations with excessive or underused permissions.
As shown in the following image, you can click the link to see more in the 3rd-Party App Governance Admin Portal. To see more information, you must be an Internet & SaaS super admin and your organization must be subscribed to [3rd-Party App Governance](/unified/what-3rd-party-app-governance). To obtain a subscription, contact Zscaler Support.
[See image.](#3rd-party-integrations-tab)
[]The following sections appear in your generated report for file sharing applications (Box, Confluence, OneDrive, ShareFile, SharePoint, Dropbox, Smartsheet, and Google Drive):
- The number of **Files with Incidents Matching A Rule**, **Files with DLP Violation**, **Files with Malware**, and **Externally Shared Files with DLP Violation**.
- The applications, along with their number of **Files with Incidents Matching A Rule**, **Files with DLP Violation**, **Files with Malware**, and **Externally Shared Files with DLP Violation**.
- The **Files per Tenant **section breaks down the individual tenants with those files. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/understanding-assets-report-assets-with-incidents) page.
[See image.](#fileapps-img)
[]![This image shows the SaaS Assets page for file sharing apps.](/downloads/zia/dashboard-analytics/reports/saas-assets-report/Assets_report_filesharing_apps.png)
[]The following sections appear in your generated report for email applications (Exchange and Gmail):
- The number of **Email Messages with Incidents Matching A Rule**, **Email Messages with DLP Violation**, **Email Messages with Malware**, and **Externally Sent Email Messages with DLP Violation**.
- The applications along with their number of **Email Messages with Incidents Matching A Rule**, **Email Messages with DLP Violation**, **Email Messages with Malware**, and **Externally Sent Email Messages with DLP Violation**.
- The **Files per Tenant** section breaks down the individual tenants with those email messages. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/understanding-assets-report-assets-with-incidents) page.
[See image.](#emailapps-img)
[]![This image shows the SaaS Assets page for Email apps.](/downloads/zia/dashboard-analytics/reports/saas-assets-report/Assets_report_email_app.png)
[]The following sections appear in your generated report for Gen AI applications (ChatGPT):
- The number of **Messages with Incidents Matching A Rule**, **Messages with DLP Violation**, and **Messages with Malware**.
- The option to **Expand All **or **Collapse All **sections.
- The applications along with their number of **Messages with Incidents Matching A Rule**, **Messages with DLP Violation**, and **Messages with Malware**.
- The **Messages per Tenant** section breaks down the individual tenants with those messages. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/understanding-assets-report-assets-with-incidents) page.
[See image.](#genaiapps-img)
[]![This image shows the SaaS Assets Report - Gen AI Category](/downloads/zia/dashboard-analytics/reports/saas-security/saas-assets-report/Assets_report_genai_apps.png)
[]The following sections appear in your generated report for source code repository applications (GitLab, Bitbucket, and GitHub):
- The **Total Number of Scanned Repositories**, **Exposure **(**Private **or** Public**), **Repositories without Tags**, and **Number of Objects with Incidents **(**DLP Violation** and **Malware**).
- **Scanned Repositories**: The information about all the scanned repositories. The following columns appear under this tab:
- **Repository Name**: The name of the repository. When you click on a repository name, the **Repository** **Details** window appears with the following information about that specific repository:
- **Overview**: The overview of the repository (e.g., date created, modified, admin, its size, tags, etc.).
- **Access Policy**: The type of exposure.
[See image.](#repo-detials-wind)
- **Exposure**: The type of exposure for the repository (public or private).
- **Tags**: The tag sets assigned to the repository.
- **Files**: The number of files in the repository.
- **Unscanned Repositories**: The information about all the unscanned repositories. The following columns appear under this tab:
- **Repository Name**: The name of the repository. When you click on a repository name, the **Repository** **Details** window appears with the following information about that specific repository:
- **Overview**: The overview of the repository (e.g., date created, modified, admin, its size, tags, etc.).
- **Access Policy**: The type of exposure.
[See image.](#repo-detail-wind-unscan)
- **Exposure**: The type of exposure for the repository (public or private).
- **Tags**: The tag sets assigned to the repository.
- **Files**: The number of files in the repository.
- The** Files **tab shows the number of **Objects with Incidents Matching a Rule**, **Objects with DLP Violation**, **Objects with Malware**, and **Externally Sent Objects with DLP Violation**.
- The **Objects per Tenant **section breaks down the individual tenants with those email messages. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/saas-assets-report-assets-incidents) page.
[See image.](#source_code_repo_img)
![SaaS Assets Report Source Code Repository Apps](/downloads/zia/dashboard-analytics/reports/saas-assets-report/Assets_report_source_code_repo_app.png)
[]
[]![Repository Details window in SaaS Assets Report for Repository Apps](/downloads/ZIA-6.2r-SaaS-Assets-Report-Repository-Apps-repository-details-window.png)
[]![Repository Details window in SaaS Assets Report for Repository Apps](/downloads/ZIA-6.2r-SaaS-Assets-Report-Repository-Apps-repository-details-window%20(1).png)
[]The following sections appear in your generated report for collaboration applications (Slack, Webex Teams, Zoom, and Microsoft Teams):
- The number of **Messages with Incidents Matching A Rule**, **Messages with DLP Violation**, **Messages with Malware**, and **Externally Sent Messages with DLP Violation**.
- The applications along with their number of **Messages with Incidents Matching A Rule**, **Messages with DLP Violation**, **Messages with Malware**, and **Externally Sent Messages with DLP Violation**.
- The **Messages per Tenant** section breaks down the individual tenants with those objects. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/saas-assets-report-assets-incidents) page.
- The** Content Locations with Violations** section shows which locations have violations. Use the** All Tenants** dropdown to select which tenant you'd like to view. Each location listed has the following columns:
- **Content Location**: The location of the content.
- **Tenant**: The name of the tenant.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., Edit).
- **Violations**: The number of violations. You can sort this column. You can click on the number to further analyze the violations; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page. The number of violations listed in the column is for current scan results, whereas the SaaS Security Insights Logs page shows you all scans. You can sort this column.
- **Malware Detection**: The amount of malware detected. You can sort this column. You can click on the number to further analyze the malware detected; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page. The number of malware detected listed in the column is for current scan results, whereas the SaaS Security Insights Logs page shows you all scans. You can sort this column.
[See image.](#collabapps-img)
[]![SaaS Assets Report Collaboration Apps](/downloads/zia/dashboard-analytics/reports/saas-assets-report/Assets_report_collabs_app.png)
[]The following sections appear in your generated report for CRM applications (Salesforce and Dynamic 365):
- The number of **Objects with Incidents Matching A Rule**, **Objects with DLP Violation**, **Objects with Malware**, and **Externally Sent Objects with DLP Violation**.
- The applications, along with their number of **Objects with Incidents Matching A Rule**, **Objects with DLP Violation**, **Objects with Malware**, and **Externally Sent Objects with DLP Violation**.
- The **Objects per Tenant **section breaks down the individual tenants with those email messages. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/saas-assets-report-assets-incidents) page.
- The **Entities with Violation **section shows which repositories have violations. Each repository listed has the following columns:
- **Object Type**: The type of object (e.g., report, campaign, dashboard).
- **Violations**: The number of violations. You can sort this column. You can click on the number to further analyze the violations; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page. The number of violations listed in the column is for current scan results, whereas the SaaS Security Insights Logs page shows you all scans.
- **Malware Detection**: The amount of malware detected. You can sort this column. You can click on the number to further analyze the malware detected; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page. The number of malware detected listed in the column is for current scan results, whereas the SaaS Security Insights Logs page shows you all scans.
[See image.](#crmapps-img)
[]![SaaS Assets Report CRM Apps](/downloads/zia/dashboard-analytics/reports/saas-assets-report/Assets_report_crm_app.png)
[]The following sections appear in your generated report for ITSM applications (Jira Software and ServiceNow):
- The number of **Objects with Incidents Matching A Rule**, **Objects with DLP Violation**, **Objects with Malware**, and **Externally Sent Objects with DLP Violation**.
- The option to **Expand All** or **Collapse All **sections.
- The applications, along with their number of **Objects with Incidents Matching A Rule**, **Objects with DLP Violation**, **Objects with Malware**, and **Externally Sent Objects with DLP Violation**.
- The **Objects per Tenant **section breaks down the individual tenants with those email messages. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/saas-assets-report-assets-incidents) page.
- The **Now Entities with Violation **section shows which repositories have violations. Each repository listed has the following columns:
- **Object Type**: The type of object (e.g., report, campaign, dashboard).
- **Violations**: The number of violations. You can sort this column. You can click on the number to further analyze the violations; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page. The number of violations listed in the column is for current scan results, whereas the SaaS Security Insights Logs page shows you all scans.
- **Malware Detection**: The amount of malware detected. You can sort this column. You can click on the number to further analyze the malware detected; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page. The number of malware detected listed in the column is for current scan results, whereas the SaaS Security Insights Logs page shows you all scans.
[See image.](#itsmapps-img)
[]![SaaS Assets Report ITSM Apps](/downloads/zia/dashboard-analytics/reports/saas-assets-report/Assets_report_itsm_apps1.png)
To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
The following section appears in your generated report for public cloud storage applications:
- Total Number of Object Storages
- Exposure
- Object Storages Without Tags
- Number of Objects with Incidents
[See image.](#tiles-public)
[]The following information appears in your generated report depending on the public cloud storage application:
- [For Amazon S3](#amazons3)
- [For Microsoft Azure](#Azure)
- [For Google Cloud Platform](#GCP)
- []**Storage Buckets**: The following columns appear under this tab:
- **Bucket Name**: The name of the bucket. When you click on a bucket name, the **Bucket Details** window appears with the following information about that specific bucket:
- **General Info**: The general information of the bucket (e.g., region, bucket type, bucket owner, etc.).
- **Exposure**: The type of exposure, the bucket policy, and the bucket access control list (ACL) which shows the AWS accounts or groups with access to the bucket and their permission type.
[See image.](#bucket-window-img)
- **Exposure**: The type of exposure for the bucket (i.e., public, private, external, or internal).
- **Tags**: The tag sets assigned to the bucket.
- **Files**: The number of files in the bucket.
[See image.](#storage-buckets-amazons3)
- **Files**: The following sections appear under this tab:
- The number of **Objects with Incidents Matching A Rule**, **Objects with DLP Violation**, and **Objects with Malware **for the application.
- The **Objects per Tenant **section breaks down the individual tenants with those email messages. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/saas-assets-report-assets-incidents) page.
[See image.](#files-amazons3)
- []**Blob Containers**: The following columns appear under this tab:
- **Container Name**: The name of the container. When you click on a container name, the **Blob** **Container Details** window appears with the following information about that specific container:
- **Storage Account Properties**: The properties of the container** **(e.g., resource group, location, subscription, etc.).
- **Overview**: The overview of the container (e.g., name, lease state, URL, etc.).
- **Exposure**: The type of exposure and permissions, which shows the accounts or groups with access to the container, their start date, end date, and permission type.
[See image.](#bucket-window-azure)
- **Exposure**: The type of exposure for the container (i.e., public, private, external, or internal).
- **Tags**: The tag sets assigned to the container.
- **Files**: The number of files in the container.
[See image.](#blob-containers-azure)
- **Blobs**: The following sections appear under this tab:
- The applications, along with their number of **Objects with Incidents Matching A Rule**, **Objects with DLP Violation**, and **Objects with Malware **for the application
- The **Objects per Tenant **section breaks down the individual tenants. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/saas-assets-report-assets-incidents) page.
[See image.](#blob-azure)
- []**Storage Buckets**: The following columns appear under this tab:
- **Bucket Name**: The name of the bucket. When you click on a bucket name, the **Bucket Details** window appears with the following information about that specific bucket:
- **Overview**: The overview of the bucket (e.g., cloud console URL, permissions, location, etc.).
- **Exposure**: The type of exposure, the bucket policy, and permissions, which shows the name and role.
[See image.](#bucket-gcp)
- **Exposure**: The type of exposure for the bucket (i.e., public, private, external, or internal).
- **Tags**: The tag sets assigned to the bucket.
- **Files**: The number of files in the bucket.
[See image.](#storage-bucket-gcp)
- **Files**: The following sections appear under this tab:
- The number of **Objects with Incidents Matching A Rule**, **Objects with DLP Violation**, and **Objects with Malware **for the application.
- The **Objects per Tenant **section breaks down the individual tenants with those email messages. You can click on a tenant to further analyze it; you are redirected to the [Assets with Incidents](/unified/saas-assets-report-assets-incidents) page.
[See image.](#files-gcp)
[]![Tiles in the SaaS Assets Reports for Public Storage Cloud](/downloads/zscaler-tech-pubs-style-guide/draft-articles/saas-assets-report-draft/ZIA-6.1r-asset-tiles.png)
[]![The Bucket Details Window that shows general information, exposure, and the bucket access control List](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report/ZIA-6.1-Bucket-Details-Window.png)
[]![Screenshot of Storage tab for the Amazon S3 in the SaaS Assets Report ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/saas-assets-report-draft/ZIA-6.1r-Amazons3-storage_0_0.png)
[]![Screenshot of the Files tab for Amazon S3](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report/ZIA-6.1r-Amazons3-files%20(1)%20(1)%20(1).png)
[]![The Bucket Details Window for Azure](/downloads/zscaler-tech-pubs-style-guide/draft-articles/saas-assets-report-draft/ZIA-6.1r-Azure-container-window.png)
[]![Screenshot of Blob Containers tab for the Azure in the SaaS Assets Report ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/saas-assets-report-draft/ZIA-6.1r-Blob-containers_0_0.png)
[]![Screenshot of Blob tab for the Azure in the SaaS Assets Report ](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report/ZIA-6.1r-Blob-azure%20(1)_11.png)
[]![Screenshot of the Bucket window for GCP in the SaaS Assets Report ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/saas-assets-report-draft/ZIA-6.1r-gcp-bucket.png)
[]![Screenshot of Storage Buckets tab for GCP in the SaaS Assets Report ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/saas-assets-report-draft/ZIA-6.1r-GCP-storage_0_0.png)
[]![Screenshot of the Files tab for GCP in the SaaS Assets Report ](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report/ZIA-6.1r-GCP-files%20(1)%20(1).png)
[]![3rd-Party Integrations tab in the SaaS Assets Report](/downloads/zia/dashboard-analytics/reports/saas-assets-report/3party_integrations_tab_saas_security_report.png)