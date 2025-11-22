# Tanium Connectors
Source: https://help.zscaler.com/uvm/tanium-connectors
PDF: https://help.zscaler.com/pdf/com/en/1528376.pdf

![The Tanium CVE, Tanium Compliance, and Tanium Assets tiles](/downloads/uvm/configure/sources/tanium-connectors/3d7d384e-6531-4f9e-ba15-1ee9dfacea17.png)
Tanium helps you secure your endpoint devices with the only Converged Endpoint Management (XEM) platform.
There are three available Tanium Connectors:
- CVE: Retrieves vulnerability data, including CVE ID, score, summary, last scan date, severity.
- Compliance: Retrieves a detailed list of all compliance findings on the endpoint, including ID, state, category, rule, first found date, last scan date.
- Assets: Retrieves essential asset data, such as serial number, computer ID, operating system, IP address.
Required Parameters
The source Authentication configuration requires the following parameters:
- [API Key](#api-key)
- [Domain](#domain)
In the source setup Retrieval section, optionally set the sensors.
A sensor is a script that runs on endpoints to gather specific data in response to a Tanium question. To learn more, refer to the [Tanium documentation](https://help.tanium.com/bundle/ug_console_onprem/page/platform_user/authoring_sensors.html). To retrieve sensor data, enter the relevant sensor names in the Sensor field. To add multiple sensors, press Enter after each entry.
Roles and Permissions
To issue API URL and token from the Tanium platform and enable the integration, you must use a user with an **Admin Reserved** role.
The following list is the necessary permissions and content sets to which the generated API token must be bound:
| **Streams** | **Permissions** | **Content Sets** |
| ----------- | --------------- | ---------------- |
| Tanium** **AssetsTanium CVETanium Compliance | Administration > Token - UseAdministration > Token - ViewGateway > Gateway API(Execute)Administration > Computer Group(Read)Unrestricted Management Rights (This is recommended to ensure that all endpoint data is accessible.)Platform Content Permissions > Sensor(Read) | BaseReservedDefaultCore ContentPerformance |
| Tanium Assets | Assets > Asset API User(Read) | Asset |
| Tanium CVETanium Compliance | None | Comply Reporting |
[]
To create an API token:
- From the main menu, go to **Administration** > **Permissions** > **API Tokens**.
- Click **New API Token** and configure the token settings:
- **Notes:** Optionally, enter a description for the token.
- **Expiration:** Enter the expiration interval in days. The default is 7 days and the maximum is 365 days.
- **Persona:** Select the user account (Default persona) or an alternative persona you created for this purpose, with the permissions and content sets listed in the Roles and Permissions section. To learn more, refer to the [Tanium documentation](https://help.tanium.com/bundle/ug_console_cloud/page/platform_user/console_personas.html). The default option is the currently selected persona for your Tanium Console session.
- **Trusted IP addresses:** Enter `0.0.0.0/0` or the list of IP addresses. Use commas or new lines to separate multiple entries.
- Click **Save** and review the token details.
- Copy the token and save it securely. Then, click **Close**. You do not have access to the token after the visibility timeout (i.e., 5 minutes) or after leaving this page.
To learn more, refer to the [Tanium documentation](https://help.tanium.com/bundle/ug_console_cloud/page/platform_user/console_api_tokens.html).
[]
The domain is your tenant name as it appears in the API URL: `<TENANT_NAME>.cloud.tanium.com`.
For example, if your API URL is: `acme.cloud.tanium.com`, enter `acme` in the Domain field.
![Entering the domain in the Tanium console](/downloads/uvm/configure/sources/tanium-connectors/mceclip0.png)