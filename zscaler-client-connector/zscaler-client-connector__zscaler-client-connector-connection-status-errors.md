# Zscaler Client Connector: Connection Status Errors
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-client-connector-connection-status-errors
PDF: https://help.zscaler.com/pdf/com/en/1285521.pdf

Zscaler Client Connector displays error messages in the **Service Status **field.
![The Zscaler Client Connector displaying an error message in the Status row](/downloads/tech-pubs-drafts/zscaler-client-connector-connection-status-errors-doc-55700/Client-Connector-Network_Error-600px.png)
The following table provides a list of possible error messages, an explanation of the error, and the action users can take to resolve it.
[][]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#zcc-fail-close-settings)
[]
[](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#zcc-fail-close-settings)
[][]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[][](/zia/configuring-disaster-recovery)[]
[](/zscaler-client-connector/configuring-user-access-restart-repair-options-zscaler-app)
[]
| **Error Message** | **Explanation** | **Required Action** |
| ----------------- | --------------- | ------------------- |
| Intermediate Authentication Error | A tunnel authentication error has occurred because an intermediate proxy service has intercepted the app authentication request. | No action required. |
| Authenticating... | A tunnel authentication error has occurred because the SME is waiting for user configuration. | No action required. |
| Authentication Error | A tunnel authentication error has occurred. | For Internet Security:Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.For Private Access:Click **Authenticate** to resolve the error. The **Authentication** option appears next to the **Authentication Status**.If the error persists, click **More** and click **Restart** **Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, log out of Zscaler Client Connector and log in again.If the error persists, contact Zscaler Support. |
| Captive Portal Detected | Zscaler Client Connector is in a fail-open state because Zscaler Client Connector detected a captive portal. | Click the **Open Browser **button to access the internet. The **Open Browser** button appears next to the **Status**. If you don't resolve the captive portal in time, click **Retry** to try again.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Captive Portal Error | The user has not resolved the captive portal within the time configured in the Zscaler Client Connector Portal. The error message disappears when the user reconnects. | Click **Retry** and then resolve the captive portal. The **Retry** option appears next to the **Status**. If you don't resolve the captive portal in time, click **Retry** to try again.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Chaining Authentication Error | A tunnel authentication error has occurred due to proxy chaining. | For Internet Security:Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.For Private Access:Click **Authenticate** to resolve the error. The **Authentication** option appears next to the **Authentication Status**.If the error persists, click **More** and click **Restart** **Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, log out of Zscaler Client Connector and log in again.If the error persists, contact Zscaler Support. |
| Connection Error | The Zscaler Internet Access (ZIA) Public Service Edge cannot be reached. | Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Driver Error | A Windows driver installation issue has been detected, and the tunnel interface cannot be started.Zscaler Client Connector is in a fail-open state unless you have a fail-close app profile option enabled. | In the **More** window, click **Repair App**. This option is available in the **Troubleshoot **section.If the error persists, contact Zscaler Support. |
| Endpoint FW/AV Error | The device has a firewall or antivirus program blocking Zscaler Client Connector traffic.Zscaler Client Connector is in a fail-open state unless you have a fail-close app profile option enabled. | Contact your administrator for any required configuration changes on the device.To learn more, contact Zscaler Support. |
| Fail Open | Zscaler Client Connector is in a fail-open state because Zscaler Client Connector detected Windows safe mode activation. | Restart Windows without safe mode. |
| Fail Close <reason> | Zscaler Client Connector is in a fail-close state because the tunnel interface cannot be started (e.g., a driver error or an endpoint FW/AV error). | Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Internal Error | Internal socket problem has been detected. | Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Installation Error | Zscaler Client Connector experienced a network error while trying to connect to the Zscaler Digital Experience (ZDX) server. | Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Network Error | No network interface is detected. | Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Safe Mode | The Zscaler service is down. You'll only have access to critical resources determined by your organization. | No action required. To learn more, see Configuring Disaster Recovery. |
| Server Error | Zscaler Client Connector is unable to connect to the ZDX cloud. | Check network connectivity.Click **Retry** to resolve the error. The **Retry** option appears next to the **Status**.If the error persists, click **More** and click **Restart Service**. To learn more, see Configuring User Access to the Restart & Repair Options for Zscaler Client Connector.If the error continues, contact Zscaler Support. |
| Untrusted Root Cert | Zscaler Client Connector is unable to validate the Zscaler Private Access (ZPA) Private Service Edge root certificate. | Contact Zscaler Support. |