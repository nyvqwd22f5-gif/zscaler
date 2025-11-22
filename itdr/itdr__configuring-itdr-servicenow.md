# Configuring ITDR with ServiceNow
Source: https://help.zscaler.com/itdr/configuring-itdr-servicenow
PDF: https://help.zscaler.com/pdf/com/en/1531871.pdf

Zscaler ITDR supports integration with third-party IT Service Management (ITSM) tools, such as ServiceNow, to track and assess issues across the Zscaler ITDR Admin Portal (AD domain, Entra ID, credential issues) and bad changes detected in the AD domain and Entra ID. You can configure ITDR with ServiceNow to:
- Create ServiceNow tickets and assign the ticket to the appropriate user.
- Track and assess the issues in both ServiceNow and the ITDR Admin Portal.
You can create only one ticket for an issue.
To configure ITDR with ServiceNow:
- Go to **ITDR** > **Integrations** > **Configurations**.
-
Locate **ServiceNow **and click the **Edit** icon under the **Actions** column.
The **ServiceNow **drawer opens.
[See image.](#edit-servicenow)
-
In the **ServiceNow** drawer:
- **Enabled**: Select to configure ServiceNow.
- **Base URL**: Enter the base URL of the ServiceNow instance.
- **Username**: Enter the username for ServiceNow.
- **Password**: Enter the password for ServiceNow.
[See image.](#servicenowdrawer)
-
(Optional) Click **Test** to validate the ServiceNow connection.
If the credentials are valid and ServiceNow can communicate with ITDR, a confirmation message appears indicating that the test is successful. If not, check the previous steps and try again. To learn more, refer to the [ServiceNow documentation](https://support.servicenow.com/kb?id=kb_article_view&sysparm_article=KB0516495).
- Click **Save**.
After configuring ITDR with ServiceNow, you must configure a ServiceNow webhook. To learn more, see [Configuring a ServiceNow Webhook](/itdr/configuring-servicenow-webhook).
[]![The ServiceNow drawer displaying the list of fields required to integrate with ITDR.](/downloads/itdr/third-party-integrations/configuring-itdr-servicenow/itdr-servicenow-drawer.png)
[]![The Configurations tab listing the ServiceNow settings and annotation around edit icon.](/downloads/itdr/third-party-integrations/configuring-itdr-servicenow/itdr-edit-configurations.png)