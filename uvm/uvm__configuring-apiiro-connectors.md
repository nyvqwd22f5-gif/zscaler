# Configuring the Apiiro Connectors
Source: https://help.zscaler.com/uvm/configuring-apiiro-connectors
PDF: https://help.zscaler.com/pdf/com/en/1528251.pdf

Apiiro helps security and development teams to gain complete visibility by discovering all application components like APIs, services, dependencies and sensitive data and mapping the application attack surface to remediate critical risks before releasing to the cloud.
To create the Apiiro data source, go to Configure > Sources. The connectors tiles appear among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#apiiro-tiles)
There are three available Apiiro streams. Select those that are in scope based on your Apiiro licenses and use cases:
- SCA: Retrieves vulnerabilities related to open-source and third-party components in the application code.
- Secrets: Retrieves vulnerabilities related to access to sensitive information within applications.
- Terraform Misconfiguration: Retrieves vulnerabilities specifically related to misconfigurations in Terraform infrastructure-as-code deployments.
[]![apiiro tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/apiiro-terraform-misconfigurations/apiiro%20tiles.png)
Authentication
The source authentication configuration requires an Apiiro API Token.
To retrieve the Apiiro API token:
- In the Apiiro platform, go to **Settings** > **General** > **Access Tokens**.
- Click **Create Token**.
- Enter a name for the token.
- Under **Define scopes and permissions**, select either **Read** or **Full Control**.
- Click **Save**.