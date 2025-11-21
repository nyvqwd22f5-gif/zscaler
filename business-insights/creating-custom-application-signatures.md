# Creating Custom Application Signatures
Source: https://help.zscaler.com/business-insights/creating-custom-application-signatures
PDF: https://help.zscaler.com/pdf/com/en/1480666.pdf

You can create customer application signatures for specific URLs of a domain to pull various insights for your analysis. This helps display insights such as active and inactive users, download and upload bytes, the number of transactions, etc. for a custom-defined URL of an application. This article explains how to create a custom application signature. You can configure 32 custom application signatures.
SSL inspection of the requisite traffic must be enabled for viewing the metrics for the custom application signature. For example, if you are not inspecting the traffic for the Miro application, metrics won't be visible for anything beyond the host, www.miro.com. Go to the SSL Inspection Policy page (Policy > SSL Inspection) in the ZIA Admin Portal to check if SSL inspection for the application is configured or not. To learn more, see [About SSL Inspection Policy](/zia/about-ssl-inspection-policy).
To create a customer application signature:
- Go to **Application** > **Application Settings**.
-
Click **Create Customer Application Signature**.
The **Create Customer Application Signature **drawer appears**.**
- In the **Create Customer Application Signature** drawer:
- **Host**: Enter the host of the application. For example, xyz.com, abc.ai, etc. Prefixes such as https://, http://, ftp://, sftp://, etc. are automatically removed if added. Select **Contains** or **Exact Match **for the **Match Level**. You can only add one host for a custom application signature.
-
**URL**: Enter the URL from where you want to view the traffic data. It must be specific to what you are trying to determine (e.g., the URL immediately after logging into the app to view the login data). Select **Contains** or **Exact Match **for the **Match Level**.
Click **Add URL Criteria** to add more URLs to the signature. You can add up to 10 URLs.
- **Application Name**: Enter a name for the application. Zscaler recommends entering a unique name for this field to distinguish it from other custom application signatures for the same application.
- **Associated SaaS Application**: Enter the name of the application for which the signature is created. This helps to display metadata if the application is known to the Business Insights service. This also impacts the experience of the [Discovered Apps](/business-insights/about-application-inventory#discovered-apps), [Overlapping Apps](/business-insights/about-application-inventory#overlapping-apps), and [Cost Savings](/business-insights/about-application-inventory#cost-savings) metrics.
-
**Description**: Enter a description for the signature.
[See image.](#create)
-
Click **Create**.
The custom application signature is successfully created.
[]![Create Custom Application SIgnature](/downloads/business-insights/application-insights/creating-custom-application-signatures/Business-Inisghts-Create-Custom-Signature-Drawer.png)