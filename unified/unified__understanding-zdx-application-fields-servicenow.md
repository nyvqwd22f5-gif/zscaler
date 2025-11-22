# Understanding the Digital Experience Monitoring Application Fields on ServiceNow
Source: https://help.zscaler.com/unified/understanding-zdx-application-fields-servicenow
PDF: https://help.zscaler.com/pdf/com/en/1492036.pdf

After assigning the Incident Management role `x_zsca2_zdx_manage.zdx_management` to your ServiceNow service user, you can configure the following in the Digital Experience Monitoring Application on ServiceNow:
- The **Settings** module to meet your Digital Experience Monitoring integration needs.
- The **Mappings** module to map categories and subcategories for incoming alerts or created incidents.
Settings Module
In the **Settings** module under the Zscaler Digital Experience application menu, you can configure the following setting properties:
- **Enter a username to use for Caller Name field (Make sure to use web service user's ID)**: The name or ID of the user who is designated to create the incidents. It is mandatory to use the user ID of the service user created for the application. Otherwise, the Caller name remains empty in incidents.
-
**Specify the logging level for the transform script**: Specifies the minimum level of log messages to be created. The default is **Information**.
For example, if the logging level is set to Information, only Information and Error messages are logged, and the debug messages are skipped.
-
**Only create incidents for severity level or higher**: Specifies the minimum level of severity for incoming alerts. The default level is **High**.
For example, if the severity is set to Medium, only alerts with the severity of Medium or High are created, and Low severity alerts are skipped.
-
**Automatically resolve incidents if the alert ended**: Enables the application to automatically resolve incidents whose source alert ended in ZDX.
For example, if the value is set to **Yes**, then the state of the incident is set to **Resolved**. Otherwise, the state does not change, but the Active field is set to **false**.
- **Enter a default name or ID of the resolver for automatically resolved incidents (Make sure to use web service user's ID)**: The name or ID of the user who is designated to resolve the incidents. It is mandatory to use the user ID of the service user created for the application. Otherwise, the Caller name remains empty in incidents.
- **Select resolution code for automatically resolved incidents**: The code used when resolving an incident. You can select one of the options defined for the property. The options match SeviceNow's resolution code values. The default is **Closed/Resolved by the caller**.
- **Enter a ZDX PORTAL URL**: The URL of a target Admin Portal that is used to run Deep Tracing sessions and ZDX Score Analysis.
- The supported format is `[subdomain].[second-level-domain].[top-level-domain]`.
-
**Enter a ZDX API URL**: The URL where the public API has access.
The supported format is `[subdomain].[second-level-domain].[top-level-domain]`.
- **Enter the Key ID used to access the ZDX Admin Portal. Should be created via ZDX API Key Management**: The Key ID from your API Key.
- **Enter the Key Secret used to access the ZDX Admin Portal. Should be created via ZDX API Key Management**: The Key Secret from your API Key.
[See image.](#ServiceNow-ZDX-Settings)
Mappings Module
Prior to configuring the Mappings module, you must map the Digital Experience Monitoring Alert Types to the ServiceNow categories and subcategories. To learn more, see [Digital Experience Monitoring Integration with ServiceNow](/unified/zdx-integration-servicenow).
In the **Mappings** module under the Zscaler Digital Experience application menu, you can configure the following to map Digital Experience Monitoring Alert types to ServiceNow Incident's category and subcategory:
-
**Mapping for Zscaler Alerts**: To map all the Digital Experience Monitoring Alerts to one category and use subcategories for specific Digital Experience Monitoring types.
For example: The **Zscaler Alert Category** is used for all Digital Experience Monitoring Alerts and the following alert types: Device, Network, ZDX Score, and Application. The property value remains empty if:
- Each Digital Monitoring Experience alert type is mapped to a specific ServiceNow category.
- No mapping is provided.
- **Mapping for Zscaler Alert type - Device**: Provides mapping for all the alerts that have been configured as Device alerts in the Admin Portal.
- If the root mapping is not empty, then the value is mapped to the **subcategory** field of the incident table.
- If the root mapping is empty, then the value is mapped to the **category** field of the incident table.
- **Mapping for Zscaler Alert type - Network**: Provides mapping for all alerts that have been configured as Network alerts in the Admin Portal.
- If the root mapping is not empty, then the value is mapped to the **subcategory** field of the incident table.
- If the root mapping is empty, then the value of this field is mapped to the **category** field of the incident table.
- **Mapping for the Zscaler alert type - ZDX Score**: Provides mapping for all alerts that have been configured in the Admin Portal as ZDX Score.
- If the root mapping is not empty, then the value is mapped to the **subcategory** field of the incident table.
- If the root mapping is empty, then the value is mapped to the **category** field of the incident table.
- **Mapping for Zscaler alert type - Application**: Provides mapping for all alerts that have been configured as Application alerts in the Admin Portal.
- If the root mapping is not empty, then the value is mapped to the **subcategory** field of the incident table.
- If the root mapping is empty, then the value is mapped to the **category** field of the incident table.
- If no mapping was provided at all, then the value for **category** field is mapped to **Inquiry / Help**.
[See image.](#ServiceNow-ZDX-Mappings)
[]![Select Settings under the ZDX application.](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/mapping-zdx-application-fields-servicenow/ServiceNow-ZDXApplicationMenu-Settings_0.jpg)
![Zscaler Digital Experience System Properties](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/servicenow-configuration-guides/understanding-zdx-application-fields-servicenow/ZDX-SNOW-ZDXProperties-Settings.png)
[]![Select Mappings under the ZDX Application Menu.](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/mapping-zdx-application-fields-servicenow/ServiceNow-ZDXApplicationMenu-Mappings.jpg)
![Mappings Module](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/mapping-zdx-application-fields-servicenow/ServiceNow-ZDX-Mappings.jpg)