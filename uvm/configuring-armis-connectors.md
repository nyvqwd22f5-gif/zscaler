# Configuring the Armis Connectors
Source: https://help.zscaler.com/uvm/configuring-armis-connectors
PDF: https://help.zscaler.com/pdf/com/en/1528391.pdf

Armis provides context about an organization’s assets (i.e., owner, location, dependencies, and vulnerabilities) and continuously analyzes their behavior to identify both operational and cyber risks to protect them against cyber attacks.
To create the Armis data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#armis-tiles)
There are two available Armis streams. Select those that are in scope based on your Armis licenses and use cases:
- Devices: Retrieves information about the discovered devices, including their attributes and states.
- CVE: Retrieves vulnerability data related to devices, including matched device details.
[]![The Armis - Devices and Armis - CVE tiles](/downloads/uvm/configure/sources/armis-connectors/a2592035-c277-4685-907a-4882795a183f.png)
Authentication
The source authentication configuration requires the following parameters:
- [API Token](#param1)
- [Tenant](#param2)
[]The API token must be associated with a user carrying the appropriate roles and permissions.
To retrieve the API Token:
- Log in to the Armis app.
-
Go to **Settings** > **API Management**.
[See image.](#settings-api-management)
-
If an API secret key was not already created, click **Create**.
[See image.](#click-create)
-
When the secret key is available, click **Show **to view it.
[See image.](#click-show)
-
In the API Secret Key dialog, click **Copy**.
[See image.](#click-copy)
[]**![c505c70c-5aa2-4f07-aa02-070b24afba64.png](/downloads/uvm/configure/sources/armis-connectors/c505c70c-5aa2-4f07-aa02-070b24afba64.png)
**
[]![f82ecee7-987f-4c19-8976-0751800fa0e9.png](/downloads/uvm/configure/sources/armis-connectors/f82ecee7-987f-4c19-8976-0751800fa0e9.png)
[]![5045aaca-36fa-4554-8291-7671ce70e10e.png](/downloads/uvm/configure/sources/armis-connectors/5045aaca-36fa-4554-8291-7671ce70e10e.png)
[]![64b51b88-57ff-42e1-93d2-35b4d5c877b7.png](/downloads/uvm/configure/sources/armis-connectors/64b51b88-57ff-42e1-93d2-35b4d5c877b7.png)
[]In the **Tenant** field, enter your specific Armis instance, which can be found in your management console URL, in the format `https://<Tenant>.armis.com`
For example, if your URL is `https://acme.armis.com`, then your tenant is `acme`.
[See image.](#armis-tenant)
[]![7adf3bde-ce7b-4ced-96c2-529d8074e58b.png](/downloads/uvm/configure/sources/armis-connectors/7adf3bde-ce7b-4ced-96c2-529d8074e58b.png)
Retrieval
In the source setup Retrieval section of the Devices stream, set the Days to fetch field. Enter the number of days you want to retrieve in each run.
Roles and Permissions
The API token must be associated with a user that carries the appropriate permissions as detailed in the table below:
| **Stream** | **Permissions** |
| ---------- | --------------- |
| Armis Devices | `Device > Read` |
| Armis CVE | `Vulnerability > Read` |