# ServiceNow Generic
Source: https://help.zscaler.com/uvm/servicenow-generic
PDF: https://help.zscaler.com/pdf/com/en/1528346.pdf

![mceclip0.png](/downloads/uvm/configure/sources/servicenow-generic/mceclip0.png)
ServiceNow is used to set up systems that define, manage, automate, and structure companies' IT services.
There are 3 available **ServiceNow** connectors:
- **ServiceNow Assets** retrieves computer assets from ServiceNow. The assets are retrieved from the following tables - **cmdb_ci_computer, cmdb_ci_server, cmdb_ci_vm_instance**.
Optionally collects Application data.
- **ServiceNow Users** will retrieve user data from the **sys_user** tables and enrich every row with data from **cmn_department**.
- **ServiceNow Generic** allows you to retrieve any table from ServiceNow.
This article covers the **Generic** stream.
**Related Articles:** [ServiceNow Connectors](https://support.avalor.io/hc/en-us/articles/14492571699101)
Parameters
To connect to ServiceNow, first note your authentication type - Basic Auth or OAuth 2.0 - this will affect the fields required to set up the connection.
- **Instance Name -** the name of the hosted ServiceNow instance, found in the URL in the format `https://[instance-name].service-now.com`
For example, if your URL is `https://acme.service-now.com/`, then the Instance Name is **acme**
- [Username and Password](https://support.avalor.io/hc/en-us/articles/undefined#h_01HE0CQF30DGY6DR5PM93XNWAY) - used for **Basic Auth** and **OAuth 2.0**
- [Client ID and Client Secret](https://support.avalor.io/hc/en-us/articles/undefined#h_01HE0CQK4NZ743GWBJ1W90B94H) - used for** OAuth 2.0**
- **Table Name -** the name of the table you wish to retrieve from Service Now
- **Query -** determines whether the search will be limited to domains the user is configured to access. Enter either TRUE or FALSE according to your preference
- **false:** Exclude the record if it is in a domain that the Service Now user is not configured to access.
- **true:** Include the record even if it is in a domain that the Service Now user is not configured to access.
Username and Password
*Used for **Basic Auth** and for the **Password Grant Type** in **OAuth 2.0**.*
Username and password will be used to access ServiceNow -
- When using **Basic Auth** the user should have an Admin [role](https://docs.servicenow.com/bundle/utah-platform-administration/page/administer/roles/reference/r_BaseSystemRoles.html).
- When using **OAuth 2.0** the user should have a [Security Admin role](https://docs.servicenow.com/en-US/bundle/vancouver-platform-security/page/administer/security/concept/security-admin-role.html).
Creating Client ID and Client Secret
*Used for both **OAuth 2.0** grant types - Password and Refresh Token.*
To create a **Client ID** and **Secret**, you need a user with an **Admin role**
- In the relevant instance navigate to **System OAuth**
- Go to **Application Registry**
- Click **New**
- On the **interceptor** page, click **Create an OAuth API endpoint for external clients**
- Fill out the form.
The client ID and Secret will be automatically generated and available to you once you complete the form.
Scheduling
![19d01c0e-6cda-4609-853b-f8831a179fea.png](/downloads/uvm/configure/sources/servicenow-generic/19d01c0e-6cda-4609-853b-f8831a179fea.png)
- Full Refresh Frequency - the frequency in which all the data will be retrieved from the source
- Incremental Refresh Frequency - the frequency in which new and changed data will be retrieved from the source