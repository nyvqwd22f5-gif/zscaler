# Configuring the Qualys WAS Connectors
Source: https://help.zscaler.com/uvm/configuring-qualys-was-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530818.pdf

Qualys Web Application Scanning (WAS) is an automated web application scanner that uses fault injection tests to identify vulnerabilities by injecting specially crafted inputs and analyzing application responses.
To create the Qualys WAS data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#qualys-was-tiles)
There are two available Qualys WAS streams. Select those that are in scope based on your Qualys WAS licenses and use cases:
- Assets: Retrieves the list of web applications within the user’s scope.
- Vulnerabilities: Retrieves a list of findings, which includes vulnerabilities, sensitive content, and information gathered, that is associated with web applications within the user's designated scope.
These connectors integrate with the Qualys WAS module.
If you’re looking for Qualys VMDR & PC, see [Configuring the Qualys VMDR & PC Connectors](/uvm/configuring-qualys-vmdr-pc-connectors).
[]![Tenable Security Center connector tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/qualys-was-connectors/qualys-was-tiles.png)
Authentication
The source authentication configuration requires the following parameters:
- [Username and Password](#param1)
- [Platform URL](#param2)
[]
The email and password for a Qualys user with access to the Qualys WAS module. Enable the **API Access** checkbox for the role assigned to the user.
To create an API reader user:
- In Qualys WAS, go to **Administration** > **User Management**.
- Select **Reader User**.
- In the **New Reader User** window, configure the following:
- In the **General Information** and **Locale** sections, enter your information as required.
- In the **User Role** section:
- **User Role**: From the drop-down menu, select **Reader**.
- **Allow access to**: Select the **API** checkbox.
- **Business Unit**: Enter your information as required.
- In the **Asset Groups** section, select the relevant asset groups you want to retrieve. Only assets from the selected asset groups are ingested into the platform.
- In the **Permissions** section, select the **Manage VM Module** and **Manage Web Applications** checkboxes.
After you create the user, edit the user and grant it full access to the WAS module.
If you created a new user for this connector, activate the user's account by completing the user registration process. This includes checking the email associated with the new user account for a message titled **Registration - Start Now**. Follow the instructions in this email, which guides you through the activation process and provides the login information, including the platform URL and login credentials.
The activation process includes logging in to the Qualys console.
[]
Your username includes your platform identifier. For example, in the username format `quays_ab1`, the underscore is the platform identifier for the US1 platform.
For a list of identifiers and their matching platform URL, refer to the [Qualys documentation](https://www.qualys.com/platform-identification/).
Roles and Permissions
When creating an API reader user, add the Manage VM Module and Manage Web Applications permissions to the user.
Troubleshooting and FAQs
| **Question** | **Answer** |
| ------------ | ---------- |
| I created a user and assigned the specified permissions. Why is my connector still failing? | Ensure that you have completed the user activation process, which includes logging into the Qualys console using the new user’s credentials. |