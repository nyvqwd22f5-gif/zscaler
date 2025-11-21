# Configuring Authentications
Source: https://help.zscaler.com/uvm/configuring-authentications
PDF: https://help.zscaler.com/pdf/com/en/1527756.pdf

The Security Operations (SecOps) platform supports integration with a wide variety of third-party tools and services, and enables secure data exchange such as retrieving findings from external scanners or sending tickets to work management systems. To connect these tools, you must first configure API authentications. Authentication ensures the SecOps platform can access external resources using valid credentials with the necessary permissions, supporting uninterrupted automation and continuous data flow.
You can create a new authentication during the setup of a [data source](/uvm/creating-data-sources) or [outegration](/uvm/creating-outegrations), or directly from the Authentications page.
-
When setting up a source, the Authentication drop-down menu appears in the Retrieval section.
[See image.](#source-authentication-dropdown)
-
When configuring an outegration, the Authentication drop-down menu appears in the Details section of the Connect step.
[See image.](#outegration-authentication-dropdown)
[]![Authentication dropdown in source setup page with CrowdStrike options](/downloads/uvm/configure/authentication/configuring-authentications/mceclip0.png)
[]![outegration%20authentication%20dropdown.png](/downloads/uvm/configure/authentication/configuring-authentications/outegration%20authentication%20dropdown.png)
Creating Authentications
Before creating a new authentication, check whether a valid authentication method already exists for the third-party data source or outegration you plan to integrate.
For access to Authentications, your assigned role must include the Read, Create, Edit, and Delete permissions under the Platform - Authentications resource. To learn more, see [Creating Custom Roles](/uvm/creating-custom-roles) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#authentications-permissions)
[]![c977a02a-7693-43b4-bb16-5b254df0715d.png](/downloads/uvm/configure/authentication/configuring-authentications/c977a02a-7693-43b4-bb16-5b254df0715d.png)
To create an authentication:
- Go to **Configure **>** Authentications**.
A list of all existing authentications appears.
- Click **Create **to add a new authentication.
-
Select the vendor for which you want to configure authentication. You can also search for a vendor in the search field.
The <Vendor Name> **Authentication** window appears.
- In the <Vendor Name> **Authentication** window:
- **Name**: Enter an informative** **name for your authentication. This is the name displayed on the integration setup page, so it should clearly identify the specific authentication instance for the selected vendor. For example, enter `CrowdStrike Vulnerabilities` when creating an authentication for CrowdStrike to be used in the Vulnerabilities stream.
-
**Credentials**: Enter the required credentials** **for the API authentication. Each source or outegration has its own unique set of required parameters that must carry the appropriate scopes and permissions to ensure successful integration. Each vendor requires specific parameters with appropriate scopes and permissions. Refer to the vendor's Sources Configuration Guide or Outegration Configuration Guide for the exact requirements.
If you plan to use the same authentication for multiple integrations (e.g., both Assets and Vulnerabilities streams for CrowdStrike), ensure that the provided credentials have all necessary permissions. Missing or insufficient scopes can result in failed authentication or incomplete data ingestion.
- Click **Create** to save the authentication.
The newly created authentication appears in the Authentication drop-down menu on the corresponding vendor's data source or outegration setup page. You can reuse an authentication across multiple integrations, as long as it has the required access permissions.
After authentications are created, ongoing management of them are done through the Authentications page. To learn more, see [Managing Authentications](/uvm/managing-authentications).