# Configuring the ZIA Devices and Users Connector
Source: https://help.zscaler.com/uvm/configuring-zia-devices-and-users-connector
PDF: https://help.zscaler.com/pdf/com/en/1530878.pdf

Zscaler Internet Access (ZIA) is a cloud-based security platform that provides secure internet access for users, protecting organizations from various online threats by enforcing security policies, filtering content, and ensuring secure connections to public applications and services on the internet.
The ZIA Devices and Users connector retrieves information about devices and their owners from ZIA.
In the ZIA Admin Portal, you can view the lists of devices and users, along with their associated group and department details:
- To view devices, go to **Administration** > **Device Management** > **Devices**. To learn more, see [About Devices](/zia/about-devices).
- To view users, go to **Administration** > **User Management** > **Users**. To learn more, see [About Users](/zia/about-users).
Prerequisites
To configure the ZIA Devices and Users connector, you need the source authentication configuration. The following parameters are required:
- [Username](#parameter1)
- [Password](#parameter2)
- [API Key](#parameter3)
- [Company ID](#parameter4)
- [Cloud Name](#parameter5)
Configuring the Connector
To create the ZIA Devices and Users data source in the Zscaler Security Operations (SecOps) platform:
- Go to **Configure** > **Sources**.
- Click **Create**.
-
Search for and select the connector tile from the available data sources.
[See image.](#vendor-tiles)
Configuring Retrieval Filters and Specifications
After you create the ZIA Devices and Users data source, enter the following information in the source setup Retrieval section:
- [Authentication](#authentication)
- [Gateway](#gateway)
Roles and Permissions
To successfully use the ZIA Devices and Users connector and ensure that all the relevant data is retrieved successfully, ensure that you use an admin user with at least the following permissions and scope. To learn more, see [Adding Admin Roles](/zia/adding-admin-roles).
Configure the following permissions for the admin who creates the API key:
- All permissions: When possible, set to **View Only**.
- **User Names**: Set to **Visible**.
- **Device Information**: Set to **Visible**.
- **Workflow Access**: Set to **None**.
The user providing the credentials (i.e., username and password) for the configuration must be an admin with access to all functional scopes.
Troubleshooting and FAQs
If you entered all the required parameters with the appropriate permissions, but are still encountering an error when attempting to save the connector, you might need to enable **Password Based Login** for the user whose credentials you are entering into the system. To enable password-based login:
- Log in to the ZIA Admin Portal as a super admin.
- Go to **Administration** > **Administration Management**.
- On the **Administrators** tab, click the edit icon of the user to configure the credentials used to authenticate the connector.
- In the **Edit Administrator** window, select the **Password Based Login** checkbox.
[]
The username associated with a ZIA admin account.
[]
The password associated with a ZIA admin account.
[]
Before getting started, ensure that your organization has an API subscription and an API key enabled. If you do not have a valid subscription, contact Zscaler Support.
To locate your API key:
- Log in to the ZIA Admin Portal.
-
Go to **Administration** > **Cloud Service API Security**.
[See image.](#zia-cloud-service-api-security)
-
On the **Cloud Service API Key** tab, view the **Key**.
[See image.](#zia-api-key)
An organization can only have one API key. If you already have an API key, creating a new API key is not possible. To create a new API key, delete the existing API key.
[]
To retrieve the company ID:
- Log in to the ZIA Admin Portal.
-
Go to **Administration** > **Company Profile**.
[See image.](#zia-company-profile)
-
On the **Organization** tab, in the **General Information** section, view the **Company ID**.
[See image.](#zia-company-id)
[]
Your cloud name is located in the URL that the admin uses to log in to the Zscaler service. For example, if your organization logs into admin.zscalerbeta.net, then your organization's cloud name is zscalerbeta.net. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
![The Zscaler cloud name located in the URL of the portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zia-devices-and-users-connector/zscaler-cloud-name.png)
[]
To configure authentication:
-
In the **Authentication** section, click **Create New**.
The **ZIA Authentication** window appears.
- In the **ZIA Authentication** window, enter the information from the Prerequisites section.
-
Click **Create**.
[See image.](#vendor-auth)
[]
Enter the gateway information in this section.
For complete configuration instructions, see [Creating Data Sources](/uvm/creating-data-sources).
[]
![The ZIA Devices and Users tile](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zia-devices-and-users-connector/zia-tiles.png)
[]
![The ZIA Authentication window displaying the Name, User Name, Password, Api Key, Company Id, and Cloud Name fields in the SecOps platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zia-devices-and-users-connector/zia-auth-window.png)
[]
![Navigating to the Company Profile page in the ZIA Admin Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zia-devices-and-users-connector/zia-company-profile.png)
[]
![Viewing the Company ID on the Organization tab of the Company Profile page of the ZIA Admin Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zia-devices-and-users-connector/zia-company-id.png)
[]
![Navigating to the Cloud Service API Security page in the ZIA Admin Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zia-devices-and-users-connector/zia-cloud-service-api-security.png)
[]
![Viewing the API Key under Key in the table on the Cloud Service API Key tab of the Cloud Service API Security page of the ZIA Admin Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zia-devices-and-users-connector/zia-api-key.png)