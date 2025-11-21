# Configuring the Qualys VMDR & PC Connectors
Source: https://help.zscaler.com/uvm/configuring-qualys-vmdr-pc-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530768.pdf

Qualys Vulnerability Management, Detection, and Response (VMDR) and Policy Compliance (PC) modules is a cloud-based solution that detects vulnerabilities on all networked assets, including servers, network devices, peripherals, and workstations.
To create the Qualys VMDR & PC data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#qualys-vmdr-pc-tiles)
There are three available Qualys VMDR & PC streams. Select those that are in scope based on your Qualys VMDR & PC licenses and use cases:
- Assets: Retrieves hosts data, which includes IP addresses, DNS names, serial numbers, operating systems, and tags.
- Vulnerabilities: Retrieves vulnerabilities from the vulnerabilities and potential vulnerabilities categories.
- Policy Compliance: Retrieves compliance posture info records, which includes the compliance posture ID.
These connectors integrate with the Qualys VMDR & PC modules.
If you’re looking for Qualys WAS connectors, see [Configuring the Qualys WAS Connectors](/uvm/configuring-qualys-was-connectors).
[]![The Qualys - Assets, Qualys - Vulnerabilities, and Qualys - Policy Compliance tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-qualys-vmdr-pc-connectors/qualys.png)
Authentication
The source authentication configuration requires the following parameters:
- [Platform URL](#param1)
- [Username and password](#param2)
[]
Your username includes your platform identifier. For example, in the username format `quays_ab1`, the underscore is the platform identifier for the US1 platform.
For a list of identifiers and their matching platform URL, refer to the [Qualys documentation](https://www.qualys.com/platform-identification/).
- For Qualys Assets and Qualys Vulnerabilities, use the API server URL.
- For Qualys Policy Compliance, use the API gateway URL.
[]
Your Qualys user credentials grant access to your Qualys data. The user credentials you provide must carry a set of permissions for the connection to be successful.
Zscaler recommends that you create a new user with the scanner role for this purpose. Alternatively, you can use an existing user or create a custom role as long as they carry the proper permissions:
To create a user:
- Log in to the Qualys console.
- Navigate to **Administration module** > **User Management** > **Users**.
- Click **New**.
- Click **User**.
To learn more about creating a user, refer to the [Qualys documentation](https://docs.qualys.com/en/cloudview/latest/users/create_user.htm).
To assign a user role:
- Log in to the Qualys console.
- Assign the user the **Scanner** role. Alternatively, create a custom role (Administration > Users > Role Management) and assign it to the user. Ensure that the role you assign to the user (scanner or custom) carries the proper permissions:
- Vulnerability Management: all read permissions for this module
- AssetView (i.e., Asset Management): all read permissions for this module
- Policy Compliance (applicable in the PC connector): all read permissions for this module
- Reporting: all read permissions for this module
- In the **User Role** section, ensure that the **GUI** and **API** checkboxes are both checked.
- In the **Asset Groups** section, select the asset groups that the user must access, according to the assets for which you want to retrieve data.
If you created a new user for this connector, activate the user's account by completing the user registration process. This includes checking the email associated with the new user account for a message titled **Registration - Start Now**. Follow the instructions in this email, which guides you through the activation process and provides the login information, including the platform URL and login credentials.
The activation process includes logging in to the Qualys console.
Retrieval
In the source setup Retrieval section, set the following filters and specifications:
- [Vulnerability Status drop-down menu](#vulnerability-status)
- [Asset tag set to exclude field](#asset-tag-set-to-exclude)
- [Asset tag set to include field](#asset-tag-set-to-include)
- [arf_kernel_filter drop-down menu](#arf-kernel-filter)
[]
The Vulnerability Status drop-down menu allows you to select the vulnerability status types to include in the scope of your data retrieval (i.e., **New**, **Active**, **Re-Opened**, or **Fixed**).
The Vulnerability Status drop-down menu is applicable in the Qualys - Vulnerabilities stream.
[]
The Asset tag set to exclude field allows you to enter custom asset tag names to exclude specific groups of assets from the scope of your data retrieval. Separate multiple values with commas.
When using this filter, you must also specify the scope of assets to be retrieved in the include filter.
The Asset tag set to exclude field is applicable in the following streams:
- Qualys - Vulnerabilities
- Qualys - Assets
[]
The Asset tag set to include field allows you to enter custom asset tag names to include specific groups of assets from the scope of your data retrieval. Separate multiple values with commas.
When using this filter, you must also specify the scope of assets to be retrieved in the exclude filter.
The Asset tag set to include field is applicable in the following streams:
- Qualys - Vulnerabilities
- Qualys - Assets
[]
The arf_kernel_filter drop-down menu allows you to select the kernel filtering option to set how kernel-related vulnerabilities are filtered during ingestion.
- Vulnerabilities are not filtered based on kernel activity.
- Exclude kernel-related vulnerabilities that are not exploitable, or found on non-running kernels.
- Include only kernel-related vulnerabilities that are not exploitable, or found on non-running kernels.
- Include only kernel-related vulnerabilities that are exploitable, or found on running kernels.
The arf_kernel_filter drop-down menu is applicable in the Vulnerabilities stream.
Roles and Permissions
Ensure that you grant the following permissions to the role you assign to the user (i.e., scanner or custom):
- Vulnerability Management: all read permissions for this module
- AssetView (i.e., Asset Management): all read permissions for this module
- Policy Compliance (applicable in the PC connector): all read permissions for this module
- Reporting: all read permissions for this module
Ensure that you grant the following access permissions to the user:
- For Qualys Vulnerabilities and Qualys Assets, select the **Manage VM module** checkbox.
- For Qualys PC, select the **Manage PC module** checkbox.
Troubleshooting and FAQs
| **Question** | **Answer** |
| ------------ | ---------- |
| I created a user and assigned the specified permissions. Why is my connector still failing? | Ensure that you have completed the user activation process, which includes logging into the Qualys console using the new user’s credentials. |