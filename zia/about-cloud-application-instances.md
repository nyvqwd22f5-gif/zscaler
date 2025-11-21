# About Cloud Application Instances
Source: https://help.zscaler.com/zia/about-cloud-application-instances
PDF: https://help.zscaler.com/pdf/com/en/1403151.pdf

The cloud application instances feature allows you to create instances for cloud applications where you can add specific instance identifiers (e.g., domains). The feature consists of two parts:
- Creating cloud application instances.
- Associating the instance with the Cloud App Control policy rules and DLP policy rules.
Cloud application instance provides the following benefits and enables you to:
-
Apply granular control (sharing, uploading, downloading, etc.) to cloud applications using Cloud App Control policy rules and use cloud app instances in DLP policy rules.
The following are not granular controls for their respective categories: viewing (File Sharing, Social Networking, and System & Development), viewing/listening (Streaming Media), and viewing mail (Webmail).
- Add specific instance identifiers (e.g., domains) for cloud applications.
You can create instances for the cloud applications in the following table:
| Cloud Applications |
| ------------------ |
| Appspace |
| Bitbucket |
| Box |
| GDrive |
| GitHub |
| Gmail |
| Launchpad |
| Microsoft Teams |
| Okta |
| OneDrive |
| Outlook |
| Quickbase |
| SharePoint Online |
| Slack |
| SourceForge |
| Workday |
| Zeplin |
| Zoom |
For cloud applications, if you allow access to an instance and block the rest using the Cloud App Control policy rule, the service blocks the main URLs (e.g., www.box.com, www.okta.com, etc.). In such a situation, you must use the corporate instance URL (e.g., www.zscaler.app.box.com/login, www.zscaler.okta.com/login, etc.) to log in instead of using the main URL (e.g., www.box.com, www.okta.com, etc.).
The feature enables you to granularly control the actions based on the domain types in the [Cloud App Control](/zia/adding-rules-cloud-app-control-policy) policy, [DLP policy with content inspection](/zia/configuring-dlp-policy-rules-content-inspection#Rules), and [DLP policy without content inspection](/zia/configuring-dlp-policy-rules-without-content-inspection#Add).
About the Cloud Application Instances Page
On the Cloud Application Instances page (Administration > Cloud Applications > Instances), you can do the following:
- [Add a cloud application instance.](/zia/adding-cloud-application-instance)
- Filter and search for cloud application instances based on the instance type (e.g., Any, Appspace, Bitbucket, etc.).
- Search for a cloud application instance.
- View a list of all configured cloud application instances. For each cloud application instance, you can see:
- **Cloud Application Instance Name**: The name of the cloud application instance that is displayed when configuring the Cloud App Control policy rule or DLP policy rule. You can sort this column.
- **Instance Type**: The parent cloud application to which the instance is tied.
- **No. of Instance Identifiers**: The total number of instance identifiers for the instance.
- [Edit or delete a cloud application instance.](/zia/editing-deleting-duplicating-items)
- Go to the [Applications](/zia/about-cloud-applications) page.
![ZIA Admin Portal Cloud Application Instances.](/downloads/zia/policies/cloud-apps/cloud-application-instances/about-cloud-application-instances/ZIA-Cloud-Applications_Instances.png)