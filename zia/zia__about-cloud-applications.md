# About Cloud Applications
Source: https://help.zscaler.com/zia/about-cloud-applications
PDF: https://help.zscaler.com/pdf/com/en/1402256.pdf

The Cloud Applications page allows you to add custom cloud applications, which provides greater flexibility to add an application if it's not already present in Zscaler for discovery and usage metrics and to create rules to control access to custom applications. You can also edit the status of all the cloud applications of your organization from here, in addition to the [Application Information](/zia/shadow-it-report#appinfopage) page, to one of the following application statuses:
- Sanctioned: If you approve the application for your organization's use because it meets all your security requirements.
- Unsanctioned: If you don't approve the application for your organization’s use because of its attack vulnerability.
You can select the application status for cloud applications while adding a [cloud application risk profile](/zia/adding-cloud-application-risk-profile), and select the risk profile as a criterion in the [Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy) rule.
The Cloud Applications page provides the following benefits and enables you to:
- View a list of all supported cloud applications along with their category and risk index. This helps organizations define the cloud app control rules proactively for apps not yet discovered in your Shadow IT Report.
- Add custom cloud applications.
- Tag cloud applications with predefined and custom labels.
- Create cloud app instances to distinguish corporate and personal instances of cloud applications and manage access controls at a granular level for those instances.
SSL inspection must be enabled for the custom cloud application lookup.
About the Cloud Applications Page
On the Cloud Applications page (Administration > Cloud Applications), you can do the following:
- [Add a custom cloud application](/zia/adding-custom-cloud-applications).
- Filter and search for cloud applications based on the Application Category, Application Status (All, Sanctioned, or Unsanctioned), Application Type (All, Custom, or Predefined), Cloud Application Name, Risk Index, and Tag.
- Search for an application.
- View a list of all the cloud applications of your organization. For each cloud application, you can see the following attributes:
-
**Cloud Application Name**: The name of the application
You are redirected to the **Application Information **page when you click the predefined cloud application name link. The [security attributes](/zia/about-application-information#security-char) of the predefined cloud applications are displayed on this page.
- **Application Category**: The category to which the application belongs.
- **Application Status**: The state of the application (Sanctioned or Unsanctioned).
- **Application Type**: The type of application (All, Custom, or Predefined).
- **Tags**: The tags associated with the applications. To learn more, see [About Cloud Application Tags](/zia/about-cloud-application-tags).
- **Risk Index**: The risk index number (1–5, 1 being the lowest risk and 5 being the highest) of the application.
-
Edit the cloud application. Based on the application type you choose to edit, either **Edit Predefined Cloud Application **or **Edit Custom Cloud Application **window appears.
In the **Edit Predefined Cloud Application** window, you can edit the Application Status (Sanctioned or Unsanctioned), Risk Index, and Tags. However, in the **Edit Custom Cloud Application** window, you can edit the Cloud Application Name, Application Status (Sanctioned or Unsanctioned), Risk Index, Tags, URLs, and Description.
-
Delete the custom cloud applications.
The p​​​​redefined cloud applications cannot be deleted.
![Cloud Application Page](/downloads/zia/policies/cloud-apps/cloud-application-status/about-cloud-application-status/ZIA-Cloud-Applications-Applications.png)