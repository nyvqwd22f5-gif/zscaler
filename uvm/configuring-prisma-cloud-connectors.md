# Configuring the Prisma Cloud Connectors
Source: https://help.zscaler.com/uvm/configuring-prisma-cloud-connectors
PDF: https://help.zscaler.com/pdf/com/en/1531035.pdf

Prisma Cloud is a Cloud Native Application Protection Platform (CNAPP) supplying security and compliance coverage for infrastructure, workloads, and applications across the entire cloud-native technology stack throughout the development lifecycle.
There are two available Prisma Cloud streams. Select those that are based on your Prisma Cloud feature plan and use cases:
- Container Issues: Retrieves container scan compliance reports.
- All Findings: Retrieves deployed scan vulnerability reports.
For Prisma Cloud's CSPM, see [Configuring the Prisma Cloud CSPM Connector](/uvm/configuring-prisma-cloud-cspm-connector).
Prerequisites
To configure the Prisma Cloud connector, you need the source authentication configuration. The following parameters are required:
- [Access Key and Secret Key](#parameter1)
- [Server URL](#parameter2)
Configuring the Connector
To create the Prisma Cloud data source in the Zscaler Security Operations (SecOps) platform:
- Go to **Configure** > **Sources**.
- Click **Create**.
-
Search for and select the connector tile from the available data sources.
[See image.](#vendor-tiles)
Configuring Retrieval Filters and Specifications
After you create the Prisma Cloud data source, enter the following information in the source setup Retrieval section:
- [Authentication](#authentication)
- [Scan Types](#scan-types)
- [Gateway](#gateway)
Roles and Permissions
Zscaler recommends creating a user under the **Account Group Read Only** permission group. You need to enable the user to create API keys.
To create a user:
- Log in to the Prisma CSM platform as a system admin.
- Go to **Settings** > **Access Control** > **Roles** > **Add** > **Role**.
- Create a new reader role with the following configurations:
- **Permission Group**: Select **Account Group Read Only**.
- **Account Group**: Select the account groups for scanning.
- Click** View Permissions** and select **On-prem/Other cloud providers**.
- In **Access Control** section, go to **Users** > **Add a new user**.
- Enter a name for your user.
- In the **Assign Roles and Default role** section, select the role you created.
- To enable the user to create access and secret keys later, ensure that you select the **Allow user to create API Access Keys** checkbox.
[]
Before you retrieve your access key and secret key, log in to the Prisma Cloud platform with the reader role user you created in the Roles and Permissions section. Ensure this user has permissions to create access and secret keys. By default, only system admins can create access and secret keys. However, system admins can enable API access by adding administrative users on Prisma Cloud.
To create the API keys:
- Log in to the Prisma Cloud platform.
- Go to **Settings** > **Manage** > **Access Control** > **Access Keys**.
- From the top right menu, go to **Add** > **Access Key**. If the option to add a new key is unavailable, create a user with the proper permissions.
- Enter a name for your key.
- Set the key expiration date:
- Switch on the **Enable Expiration** toggle.
- Specify the expiration date and time. If you do not select the checkbox, the key never expires. If the checkbox is selected, but no expiration date is specified, the key expires within a month.
- Click **Save** to create the key.
- You can either copy the key or download it as a CSV file.
After you close the window, you do not have access to the key again.
[]
To retrieve the server URL:
- Log in to the Prisma Cloud platform.
- Go to **Runtime Security** > **Manage** > **System**.
- Select the **Utilities** tab.
- The **Server URL** appears in the **Path to Console** section. The server URL format is `https://``<region>``.cloud.twistlock.com/``<customer>`, and should not include the path (e.g., `https://us-west1.cloud.twistlock.com/us-92398838`).
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
Set the Scan Types filters and specifications (i.e., **Images**, **CI Images**, **Registry**, **Host**, and **Serverless Function**).
The Scan Types drop-down menu is available in the Prisma Cloud All Findings stream.
[]
Enter the gateway information in this section.
For complete configuration instructions, see [Creating Data Sources](/uvm/creating-data-sources).
[]
![The Prisma Cloud - Container Issues and Prisma Cloud - All Findings tiles](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/prisma-cloud-tiles.png)
[]
![The Prism Authentication window displaying the Name, Access Key, Secret Key, and Server Url fields in the SecOps platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-prisma-cloud-connectors/prisma-auth-window.png)