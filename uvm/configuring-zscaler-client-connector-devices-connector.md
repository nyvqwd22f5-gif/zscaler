# Configuring the Zscaler Client Connector Devices Connector
Source: https://help.zscaler.com/uvm/configuring-zscaler-client-connector-devices-connector
PDF: https://help.zscaler.com/pdf/com/en/1530862.pdf

Zscaler Client Connector is an application deployed on the end-user device that automatically forwards all user traffic through the Zscaler Zero Trust Exchange (ZTE) to enforce policy and access controls while improving performance.
Zscaler Client Connector Devices retrieve data on assets in your organization, including which Zscaler products are installed on which assets.
Prerequisites
To configure the Zscaler Client Connector Devices connector, you need the source authentication configuration. The following parameters are required:
- [Client ID and Secret Key](#parameter1)
- [Cloud Name](#parameter2)
Configuring the Connector
To create the Zscaler Client Connector Devices data source in the Zscaler Security Operations (SecOps) platform:
- Go to **Configure** > **Sources**.
- Click **Create**.
-
Search for and select the connector tile from the available data sources.
[See image.](#vendor-tiles)
Configuring Retrieval Filters and Specifications
After you create the Zscaler Client Connector Devices data source, enter the following information in the source setup Retrieval section:
- [Authentication](#authentication)
- [Gateway](#gateway)
For complete configuration instructions, see [Creating Data Sources](/uvm/creating-data-sources).
[]
Before getting started, you must enable the API for your organization to obtain access to the Zscaler Client Connector API by contacting Zscaler Support. To create an API token, the admin must be assigned a role with full access to the public API resource in the Zscaler Client Connector Portal (Administration > Administration Management > Role Management).
[See image.](#public-api-full-access)
To retrieve the API key and secret key:
- Log in to the Zscaler Client Connector Portal.
- Go to **Administration** > **Public API**.
- Click **Add API Key**.
- In the **Add API Key** window:
- **Name**: Enter a name for the API key. The name must be alphanumeric, cannot contain spaces, and has a maximum of 50 characters.
- **Status**: Ensure that **Enabled** is selected. If Disabled, the key is unavailable to use. By default, this is enabled.
- **Role**: Select Read access for the key.
-
**Session Validity Interval (In Seconds)**: Enter the amount of time the key is available to use. The recommended session length is at least 43,200 seconds, which is equal to 12 hours.
[See image.](#add-api-key)
- Click **Save** to generate the client ID and client secret
-
Copy the client secret and close the **Add API Key** window.
[See image.](#copy-client-secret)
Store the client secret securely because it is only available when creating an API key. It is not available once you close the window.
-
On the **Public API** page, copy the **Client ID**.
[See image.](#copy-client-id)
[]
Your cloud name is located in the URL that the admin uses to log in to the Zscaler service. For example, if your organization logs into admin.zscalerbeta.net, then your organization's cloud name is zscalerbeta.net. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
![The Zscaler cloud name in the URL of your Zscaler portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zscaler-client-connector-devices-connector/zscaler-cloud-name.png)
[]
To configure authentication:
-
In the **Authentication** section, click **Create New**.
The **ZCC Authentication** window appears.
- In the **ZCC Authentication** window, enter the information from the Prerequisites section.
-
Click **Create**.
[See image.](#vendor-auth)
[]
Enter the gateway information in this section.
[]
![The ZCC Devices tile](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zscaler-client-connector-devices-connector/zccdevices.png)
[]
![The ZCC Authentication window displaying the Name, Api Key, Domain, and Secret Key fields in the SecOps platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zscaler-client-connector-devices-connector/zcc-auth-window.png)
[]
![The Add API Key window in the Zscaler Client Connector Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zscaler-client-connector-devices-connector/zdd-devices-add-api-key.png)
[]
![Selecting Full for Public API access in the Zscaler Client Connector Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zscaler-client-connector-devices-connector/zscaler-client-connector-view-admin-role.png)
[]
![Copying the client secret in the Add API Key window of the Zscaler Client Connector Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zscaler-client-connector-devices-connector/zcc-devices-copy-client-secret.png)
[]
![Copying the client ID on the Public API page of the Zscaler Client Connector Portal](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-zscaler-client-connector-devices-connector/zscaler-client-connector-public-api.png)