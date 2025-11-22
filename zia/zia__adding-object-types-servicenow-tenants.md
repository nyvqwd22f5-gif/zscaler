# Adding Object Types for ServiceNow Tenants
Source: https://help.zscaler.com/zia/adding-object-types-servicenow-tenants
PDF: https://help.zscaler.com/pdf/com/en/1401981.pdf

ServiceNow has many object types available, so the Zscaler service provides a default list of the most commonly used object types. You can add additional object types if they're not on the list.
To add object types for ServiceNow tenants:
- Go to **Administration **> **SaaS Application Tenants**.
- Click the **Edit** icon for the ServiceNow tenant that you want to add object types for.
The **Edit Tenant **window appears.
- In the **Edit Tenant** window:
- **Default Object Types**: View the default list of ServiceNow object types that you can scan with the [Data at Rest Scanning DLP policy](/zia/configuring-saas-security-api-dlp-policy).
- **Additional Object Types**: Enter the object types and click **Add items** to include them for scanning.
For the additional object types that are included, the policy scans only the fields specific to **description**, **short_description**, and **close_notes.**
[See image.](#seeimage)
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The Edit Tenant window.](/downloads/zia/policies/saas-security-api/saas-application-tenants/adding-object-types-servicenow-tenants/ZIA-Edit-Tenant-Window.png)