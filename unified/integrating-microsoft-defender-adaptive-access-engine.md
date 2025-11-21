# Integrating Microsoft Defender with Adaptive Access Engine
Source: https://help.zscaler.com/unified/integrating-microsoft-defender-adaptive-access-engine
PDF: https://help.zscaler.com/pdf/com/en/1529562.pdf

The Adaptive Access Engine receives device signals from Microsoft Defender, which might be used to control user access to applications via Zscaler. You can configure the Microsoft Defender settings in the Experience Center and establish the connection between Microsoft Defender and Adaptive Access Engine. This enables Microsoft Defender to share the user and device context signals with the Adaptive Access Engine.
The following signals are evaluated by Microsoft Defender for Endpoint and sent to Adaptive Access Engine:
- **Risk Score**: Values are None, Informational, Low, Medium, and High.
Exposure Level: Values are None, Low, Medium, and High.
- **Health Status**: The machine health status and values are Active, Inactive, ImpairedCommunication, NoSensorData, NoSensorDataImpairedCommunication, and Unknown.
- **Device Tag (Machine Tag)**: Set of machine tags.
- **RBAC Group**: The machine group name.
- **RBAC Group ID**: The machine group ID.
Prerequisites
Before integrating Microsoft Defender with Adaptive Access Engine, ensure that you have the following:
- A Microsoft Entra user account with admin privileges.
- A Microsoft Defender for Endpoint account.
- A Microsoft Azure account with subscription for Event Hub and Logic App.
- Register a Microsoft Entra application with the [required permissions](#ec-aae-apppermissions) in the Azure tenant account and create a service principal. This is required for the Zscaler integration. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal).
Zscaler Client Connector Windows 4.8 version or higher is required on devices using Microsoft Defender and Zscaler Client Connector and which require Adaptive Access profiles for Zscaler Internet Access (ZIA) or Zscaler Private Access (ZPA) policy enforcement.
Configure Azure Event Hub and Logic App
The Azure resources are required to fetch the Microsoft Defender signals and transmit them to Adaptive Access Engine.
To configure the Azure resources:
- Log in to [Microsoft Azure portal](https://portal.azure.com/#home).
- Create a resource group to store all resources related to the Zscaler Adaptive Access Engine application. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups).
- Run the Bicep script (hosted in Zscaler GitHub) to create the resources and pass the appropriate parameter values. Bicep is a declarative domain specific language (DSL) that is used to provision Azure resources. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep).
Configure Microsoft Defender Integration in Adaptive Access
To configure the Microsoft Defender settings in Experience Center:
- Go to **Policies** > **Common Configuration** > **Adaptive Access** > **Integrations**.
-
On the **Integrations** page, click the **Edit** icon for Microsoft Defender.
[See image.](#aae-integ-md)
The **Edit Microsoft Defender** window appears.
-
In the **Edit Microsoft Defender** window:
- **Event Hub Instance**: Enter the event hub instance.
- **Event Hub Host**: Enter the host name of the event hub.
- **Consumer Group**: Enter the name of the consumer group that is used to read and process the Microsoft Defender events. The name should be `$Default`. You can also create a different consumer group on the event hub instance and use it.
-
**Connection String**: Enter the connection string corresponding to the shared access service (SAS) policy created in the event hub. This allows the Adaptive Access Engine to connect to the event hub and receive signals.
To get the connection string:
- In the Azure portal, go to **All services** > **Analytics** > **Event Hubs**.
- Select your event hub and go to the **Event Hubs Namespace** page
- In the left-side navigation, under **Settings**, select **Shared access policies**.
- Select the policy and click the **Edit** icon.
-
Select the **Copy** icon next to the **Connection string-primary key** field to copy the connection string.
To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-get-connection-string?source=recommendations).
- **Status**: Enable to make the integration active.
- **Signal **and** Value Type**: The context signal type that Microsoft Defender shares with Adaptive Access Engine.
[See image.](#aae-md-edit)
- Click **Save**.
-
Click **Test Integration** to verify the connection between Adaptive Access Engine and Microsoft Defender.
A message appears indicating that the connection is successful. You can proceed to create device profiles.
Service Permissions
You need to manage permissions in the following services, to allow Adaptive Access Engine to communicate with Microsoft Defender:
[]
| Service | Permission | Type | Description | Admin Consent Required? |
| ------- | ---------- | ---- | ----------- | ----------------------- |
| Microsoft Graph | DeviceManagementManagedDevices.Read.All | Application | Read Microsoft Intune devices | Yes |
| SecurityEvents.Read.All | Application | Read your organization’s security events | Yes |
| User.Read | Delegated | Sign in and read user profile | No |
| Microsoft Threat Protection | AdvancedHunting.Read.All | Application | Run advanced hunting queries | Yes |
| CustomDetections.ReadWrite.All | Application | Read and write all custom detection rules | Yes |
| Incident.Read.All | Application | Read all incidents | Yes |
| Incident.ReadWrite.All | Application | Read and write all incidents | Yes |
| WindowsDefenderATP | Ip.Read.All | Application | Read IP address profiles | Yes |
| Machine.Read.All | Application | Read all machine profiles | Yes |
| Machine.ReadWrite.All | Application | Read and write all machine information | Yes |
| Machine.Scan | Application | Scan machine | Yes |
| Alert.Read.All | Application | Read all alerts | Yes |
| Score.Read.All | Application | Read threat and vulnerability management score | Yes |
[]
![Enter the details to integrate Microsoft Defender with Adaptive Access Engine](/downloads/unified/policies/adaptive-access-engine/integrating-microsoft-defender-adaptive-access-engine/aae-editdefender1.png)
[]
![Click the Edit icon to configure Microsoft Defender](/downloads/unified/policies/adaptive-access-engine/integrating-microsoft-defender-adaptive-access-engine/aae-integpage-defender.png)