# Configuring the Prisma Cloud CSPM Connector
Source: https://help.zscaler.com/uvm/configuring-prisma-cloud-cspm-connector
PDF: https://help.zscaler.com/pdf/com/en/1531040.pdf

Prisma Cloud is a Cloud Native Application Protection Platform (CNAPP) supplying security and compliance coverage for infrastructure, workloads, and applications across the entire cloud-native technology stack throughout the development lifecycle.
Prisma Cloud CSPM retrieves vulnerabilities and asset data on cloud resources.
For Prisma Cloud, see [Configuring the Prisma Cloud Connectors](/uvm/configuring-prisma-cloud-connectors).
Prerequisites
To configure the Prisma Cloud CSPM connector, you need the source authentication configuration. The following parameters are required:
- [Access Key and Secret Key](#parameter1)
- [Server URL](#parameter2)
Configuring the Connector
To create the Prisma Cloud CSPM data source in the Zscaler Security Operations (SecOps) platform:
- Go to **Configure** > **Sources**.
- Click **Create**.
-
Search for and select the connector tile from the available data sources.
[See image.](#vendor-tiles)
Configuring Retrieval Filters and Specifications
After you create the Prisma Cloud CSPM data source, enter the following information in the source setup Retrieval section:
- [Authentication](#authentication)
- [Gateway](#gateway)
Roles and Permissions
Zscaler recommends creating a user in the **Account Group Read Only** permission group. You need to enable the user to create API keys.
To create a user:
- Login to the Prisma Cloud CSM platform as a system admin.
- Go to **Settings** > **Access Control**.
- Create a new reader role with the following configurations:
- **Permission Group**: Select **Account Group Read Only**.
- **Account Group**: Select the account groups for scanning.
- In the **Access Control** section, go to **Users** and add a new user to configure the following:
- Enter a name for your user.
- In the **Assign and Default roles** section, select the role you created.
- To enable the user to create access and secret keys later, ensure that you select the **Allow user to create API Access Keys** checkbox.
[]
To create an access key and a secret key, ensure that your user is permitted to create access and secret keys. By default, only system admins have the ability to create access and secret keys. However, system admins can enable API access by adding administrative users in the Prisma Cloud platform. To learn more, refer to the [Prisma Cloud documentation](https://docs.prismacloud.io/en/enterprise-edition/content-collections/administration/add-prisma-cloud-users#id2730a69c-eea8-4e00-a7f1-df3b046615bc).
- Log in to the Prisma Cloud platform.
- Select menu:Settings[Access Control > Access Keys].
- Select menu:Add[Access Key] and configure the following:
- Enter a name for your key.
- Set the key expiration date by selecting the **Enable Expiration** checkbox and then specify the expiration date and time. If you do not select the checkbox, the key never expires. If the checkbox is checked, but no expiration date is specified, the key expires within a month.
- Create the key and either copy or download it as a CSV file. After you close the window, you do not have access to the key again.
[]
Your Prisma Cloud CSPM admin console URL varies according to the cluster in which your tenant is deployed. The correct URL is in your fulfillment email from Prisma Cloud CSPM. After you retrieve your admin console URL, convert it to the matching API URL. To learn more, refer to the [Prisma Cloud documentation](https://pan.dev/prisma-cloud/api/cspm/api-urls/).
[]
To configure authentication:
-
In the **Authentication** section, click **Create New**.
The **Prisma Authentication** window appears.
- In the **Prisma Authentication** window, enter the information from the Prerequisites section.
-
Click **Create**.
[See image.](#vendor-auth)
[]
Enter the gateway information in this section.
For complete configuration instructions, see [Creating Data Sources](/uvm/creating-data-sources).
[]
![The Prisma Cloud CSPM tile](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/prisma-cloud-cspm-tiles.png)
[]
![The Prisma Authentication window displaying the Name, Access Key, Secret Key, and Server Url fields in the SecOps platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-prisma-cloud-cspm-connector/prisma-auth-window.png)