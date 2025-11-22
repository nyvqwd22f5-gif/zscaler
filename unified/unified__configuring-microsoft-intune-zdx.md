# Configuring Microsoft Intune for Digital Experience Monitoring
Source: https://help.zscaler.com/unified/configuring-microsoft-intune-zdx
PDF: https://help.zscaler.com/pdf/com/en/1492806.pdf

The integration of Microsoft Intune with Digital Experience Monitoring provides access to Endpoint Analytics for user and device insights. To learn more, see [Understanding Microsoft Endpoint Analytics for Digital Experience Monitoring](/unified/understanding-microsoft-endpoint-analytics-digital-experience-monitoring).
Adding the Intune Integration
In the Admin Portal:
- Go to **Policies **> **Digital Experience Monitoring**>** Data Collection Integrations**.
- Click **Add New Integration**.
-
Select **Microsoft Intune **from the drop-down menu. The **Add New Microsoft Intune Integration** window appears.
[See image.](#tenant-modal)
- In the **Add New Microsoft Intune Integration** window:
- **Name**: Enter a name for Microsoft Intune integration.
- **Status**: Click **Enable** to allow for data collection from Microsoft Intune.
- **Monitoring Criteria**: Use the filters to help identify the users from whom data can be collected for Endpoint Analytics. Selections among the filters are cumulative, whereas selections within a single filter are not cumulative. For example, if you select DevTest and Service Admin in the User Groups filter, and then select Engineering and IT in the Departments filter, you can identify users who belong to the DevTest or Service Admin user group *and *the Engineering or IT department.
-
**Authentication**: Click **Microsoft Office 365 Authentication**.
You must authenticate with Microsoft before you can save the Intune integration. You must also reauthenticate whenever you update the **Monitoring Criteria** settings.
-
Sign in and enter your credentials. Verify your identity if multi-factor authentication is required.
[See image.](#ms-signin)
-
**Accept **the resource permissions from Microsoft.
[See image.](#permissions)
Zscaler uses sign-in and read permissions for the Microsoft Intune integration. To learn more about Intune permission scopes, refer to the [Microsoft Intune documentation](https://learn.microsoft.com/en-us/intune/intune-service/developer/intune-graph-apis).
- After the **Add New Microsoft Intune** **Integration** window appears, click **Save**. The Intune integration appears in the table for Data Collection.
-
(Optional) Select the **Edit **icon in the table to re-open the **Add New Microsoft Intune** **Integration** window. Click **Validate **to verify your setup with Microsoft was successful.
[See image.](#validate)
- Click **Save**.
Disabling the Intune Integration
To disable the Microsoft Intune integration:
- Go to **Policies **> **Digital Experience Monitoring**>** Data Collection Integrations**.
- Click the **Edit **icon for the Microsoft Intune integration.
- In the **Add New Microsoft Intune Integration** window, configure the Status to **Disable**.
- Click **Save**.
- Activate your change.
Deleting the Intune Integration
To delete the Microsoft Intune integration:
- Go to **Policies **> **Digital Experience Monitoring**>** Data Collection Integrations**.
- Click the **Delete **icon for the Microsoft Intune integration.
- In the dialog window, confirm you want to delete the integration.
- Activate your change.
[]![Modal to add Microsoft Intune integration](/downloads/zdx/configuration/applications/configuring-microsoft-intune-zdx/zdx-add-intune-integration-modal2.png)
[]![Microsoft sign-in modal](/downloads/zdx/analytics/configuring-microsoft-intune-zdx/zdx-intune-integration-ms-signin.png)
[]![Modal to accept Microsoft permissions](/downloads/zdx/analytics/configuring-microsoft-intune-zdx/zdx-intune-permissions.png)
[]![Button on Add New Microsoft Intune modal to validate setup](/downloads/zdx/configuration/applications/configuring-microsoft-intune-zdx/zdx-intune-integration-validate2.png)