# About Data at Rest Scanning DLP
Source: https://help.zscaler.com/unified/about-data-rest-scanning-dlp
PDF: https://help.zscaler.com/pdf/com/en/1493556.pdf

The SaaS Security Data at Rest Scanning Data Loss Prevention (DLP) policy allows you to create rules to discover and protect sensitive data at rest in sanctioned SaaS applications.
Adding a DLP policy for a SaaS application provides the following benefits and enables you to:
- Maintain individualized DLP policies for each SaaS application tenant in your organization.
- Detect threats to your data and protect against data loss in your SaaS applications.
This policy uses Zscaler [DLP engines](/unified/about-dlp-engines) to scan content within your organization’s [SaaS application tenants](/unified/about-saas-application-tenants). You can configure criteria, such as file type or collaboration scope, to specify the type of content for the policy to scan. You can also configure actions for the policy to take if it detects content that matches the criteria.
After creating a policy rule, you must schedule a scan for it to inspect content based on the rule's specifications (e.g., tenant, DLP engines, action, etc.). To learn more, see [About SaaS Security Scan Configuration](/unified/about-saas-security-scan-configuration).
When a scan inspects content, it uses all applicable DLP engines for that application tenant in addition to the DLP rule’s selected engines. However, the Zscaler service only enforces the DLP policy based on the highest priority DLP rule. The service uses the other DLP engines for sensitive information discovery. You can view this information in the [SaaS Security Report](/unified/about-saas-assets-summary-report).
Evidence Collection
You can forward the data related to the rule violation, including the file, to an on-premises DLP incident receiver or to your public cloud, such as Microsoft Azure, Amazon S3, or Google Cloud Platform. To learn more, see [Configuring the Data at Rest Scanning DLP Policy with Content Inspection](/unified/configuring-data-rest-scanning-dlp-policy-content-inspection) and [Configuring the Zscaler Incident Receiver for On-Premises VMs](/unified/configuring-zscaler-incident-receiver-premises-vms).
There are three different methods of evidence collection:
- Email Notification: This method sends an email notification for a rule violation.
- Incident Receiver: This method forwards the content that caused the rule violation to an on-premises incident receiver or to your public cloud.
- For file sharing applications, a link to the file causing the rule violation is provided.
Supported DLP Actions
The following table lists the Zscaler-supported DLP actions categorized by applications:
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| DLP Action | Apps Supported |
| ---------- | -------------- |
| Admin Quarantine | Google DriveMicrosoft OneDriveMicrosoft SharePoint |
| Apply Box Classification Label | Box |
| Apply Google Drive Label | Google Drive |
| Apply MIP Label | Microsoft OneDriveMicrosoft SharePoint |
| Change to Read Only for All Collaborators | Atlassian ConfluenceBoxCitrix ShareFileDropboxGoogle Cloud PlatformGoogle DriveMicrosoft OneDriveMicrosoft SharePointSalesforce |
| Change to Read Only for External Collaborators | BoxCitrix ShareFileDropboxGoogle Cloud PlatformGoogle DriveMicrosoft OneDriveMicrosoft SharePointSalesforce |
| Change to Read Only for Internal Collaborators | BoxCitrix ShareFileDropboxGoogle Cloud PlatformGoogle DriveMicrosoft OneDriveMicrosoft SharePointSalesforce |
| Move to Restricted Folder | Atlassian Confluence |
| Notify Users Only | Microsoft TeamsSlackWebex Teams |
| Quarantine | Atlassian JiraDynamics 365SalesforceServiceNowSlackWebex Teams |
| Quarantine to User Root Folder | BoxCitrix ShareFileDropboxGoogle Cloud PlatformGoogle DriveMicrosoft OneDriveMicrosoft SharePointSalesforce |
| Remove | Atlassian ConfluenceAtlassian JiraDynamics 365SalesforceServiceNowSmartsheetZoom |
| Remove All Collaborators | DropboxGoogle Cloud Platform |
| Remove External Collaborators | Smartsheet |
| Remove External Collaborators and Shareable Link | BoxCitrix ShareFileDropboxGoogle Cloud PlatformGoogle DriveMicrosoft OneDriveMicrosoft SharePointSalesforce |
| Remove Internal Collaborators and Shareable Link | BoxCitrix ShareFileDropboxGoogle Cloud PlatformGoogle DriveMicrosoft OneDriveMicrosoft SharePointSalesforce |
| Remove Public Shareable Link | Amazon Web ServicesBoxDropboxGoogle Cloud PlatformGoogle DriveSalesforce |
| Remove Sharing | Atlassian BitbucketBoxCitrix ShareFileDropboxGoogle DriveMicrosoft OneDriveMicrosoft SharePointSalesforceSmartsheet |
| Report Incident Only | Amazon Web ServicesAtlassian BitbucketAtlassian ConfluenceAtlassian JiraAzureBoxChatGPTCitrix ShareFileDropboxDynamics 365GitHubGmailGoogle Cloud PlatformGoogle DriveMicrosoft ExchangeMicrosoft OneDriveMicrosoft SharePointMicrosoft TeamsSalesforceServiceNowSlackSmartsheetWebex TeamsZoom |
| Update to Not Discoverable for All | Google Drive |
About the Data at Rest Scanning DLP Page
On the DLP page (Policies > Data Protection > Policy > Out-of-Band CASB), you can do the following:
-
From the drop-down menu, choose an application type to configure the DLP policy for related SaaS applications.
To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
- [Configure a Data at Rest Scanning DLP policy rule.](/unified/configuring-data-rest-scanning-dlp-policy)
- Search for a DLP policy rule.
- View a list of all configured DLP policy rules. For policy rules, you can see and sort:
- **Rule Order**: The policy rule's order number. SaaS Security Data at Rest Scanning DLP policy rules are evaluated in ascending numerical order.
- **Admin Rank**: The assigned [admin rank](/unified/about-admin-rank) for the rule. This is visible only if admin ranking is enabled in the [Advanced Settings](/unified/configuring-advanced-settings#admin-ranking).
- **Rule Name**: The name of the policy rule.
- **Severity**: The severity level of the incidents that match the policy rule.
- **Criteria**: The policy rule's criteria (i.e., SaaS Application Tenant, DLP Engine, Collaboration Scope, etc.)
- **Action**: The configured action for the policy rule.
- **Label and Description**: The label and description of the policy rule, if available.
- **Status**: Whether the policy rule is enabled or disabled.
- Edit, duplicate, or delete a DLP policy rule.
- [Modify the table and its columns.](/unified/using-tables)
- Go to the [Exceptions](/unified/configuring-data-rest-scanning-dlp-policy-exceptions) page, where you can configure DLP policy exceptions.
- Go to the [Malware Detection](/unified/about-data-rest-scanning-malware-detection) page, where you can create rules to discover and prevent threats to data at rest in sanctioned SaaS applications. You can also configure exceptions to the policy.
- Go to the [Scanning Exceptions](/unified/configuring-data-rest-scanning-exceptions) page, where you can configure scanning exceptions for file sharing applications.
![The SaaS Security Data At Rest Scanning Data Loss Prevention page details.](/downloads/zia/policies/saas-security-api/saas-security-api-policies/saas-security-api-control/about-saas-security-api-dlp/SaaS%20Security%20Data%20At%20rest%20Scanning%20DLP.png)