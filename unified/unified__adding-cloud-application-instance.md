# Adding a Cloud Application Instance
Source: https://help.zscaler.com/unified/adding-cloud-application-instance
PDF: https://help.zscaler.com/pdf/com/en/1494806.pdf

The cloud application instances feature allows you to create instances for cloud applications where you can add specific instance identifiers (e.g., domains). The feature consists of two parts:
- Creating cloud application instances.
- Associating the instance with the Cloud App Control policy rules and DLP policy rules.
To add a cloud application instance:
- Go to **Policies** > **Access Control** > **Internet & SaaS** > **SaaS Applications** > **Instances**.
-
Click **Add Cloud Application Instance**.
The **Add Cloud Application Instance **window appears.
-
In the **Add Cloud Application Instance **window:
- **Cloud Application Instance Name**: Enter the name of the cloud application instance. This is displayed when configuring the Cloud App Control policy rules and DLP policy rules.
-
**Instance Type**: Select a parent cloud application for which you want to add instances.
- For cloud applications, if you allow access to an instance and block the rest using the Cloud App Control policy rule, the service blocks the main URLs (e.g., www.box.com, www.okta.com, etc.). In such a situation, you must use the corporate instance URL (e.g., www.zscaler.app.box.com/login, www.zscaler.okta.com/login, etc.) to log in instead of using the main URL (e.g., www.box.com, www.okta.com, etc.).
-
For the **GitHub** instance type, you can add keywords as instance identifiers in addition to URLs. The organizations following a similar naming convention through a single keyword can use the keyword instance identifier to identify a large number of GitHub repositories.
[See image.](#github-instance-type)
- **Name**: Enter the name of the instance identifier.
-
**Instance Identifier**: Enter the URL of the instance identifier.
The URL formats for the **Bitbucket** and **GitHub **instance types are as follows, respectively:
`.bitbucket.com/<organization name>/<repository name>/
.github.com/<organization name>/<repository name>/`
- **Name**: (Optional) Enter the name of the keyword. This field is applicable only for the **GitHub** instance type.
- **Keyword**: (Optional) Enter the keyword. This field is applicable only for the **GitHub** instance type.
To add multiple instance identifiers or keywords, click **+ Add More** after each entry. You can remove the identifiers using the **Trash** icon.
You can add a maximum of 1,024 instance identifiers per cloud application instance. For guidance on entering URLs, see the [URL Format Guidelines](/unified/url-format-guidelines).
[See image.](#cloud-app-instances)
- Click **Save **and activate the change.
[]![Screenshot of ZIA Add Cloud Application Instance Window](/downloads/zia/policies/cloud-apps/cloud-application-instances/adding-cloud-application-instance/ZIA-Add-Cloud-Application-Instance.png)
[]![Screenshot of ZIA Add Cloud Application Instance for the GitHub Instance Type](/downloads/zia/policies/cloud-apps/cloud-application-instances/adding-cloud-application-instance/ZIA-Add-Cloud-Application-Instance-GitHub.png)