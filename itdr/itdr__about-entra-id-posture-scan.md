# About Entra ID Posture Scan
Source: https://help.zscaler.com/itdr/about-entra-id-posture-scan
PDF: https://help.zscaler.com/pdf/com/en/1531773.pdf

You can connect your organization's Entra ID tenants with Zscaler ITDR to assess the posture of your Entra ID and monitor for malicious changes. The posture checks for Entra ID include identifying misconfigurations and potential risks across Entra ID users, service principals, and roles. In addition to posture checks, change detection is enabled by default to monitor and detect active changes in the Entra ID tenant. The changes are classified as good, bad, or info depending on the risk that posed the change.
ITDR collects Entra ID attributes, such as giveName, displayName, department, etc. After you [connect an Entra ID tenant](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) with ITDR for scanning, the attribute collection is enabled by default. When scanning the Entra ID tenants, ITDR collects these attributes. ITDR leverages these attributes to provide context for the misconfigurations detected in Entra ID tenants.
Entra ID Posture Scan provides the following benefits and enables you to:
- Get visibility into vulnerabilities, misconfigurations, and excessive permissions in Entra ID that open up attack paths and enable privilege escalation in the event of a compromise.
- Ensure 24/7 monitoring for changes being made to Entra ID that might potentially introduce new risks and open up privilege escalation paths.
ITDR uses a deployment script to set up all necessary resources such as resource group, app, storage account, and service principal, etc. in Entra ID. The diagnostic settings are also enabled by the deployment script to enable change detection using the logs. The audit logs are analyzed and updated in the Zscaler ITDR Admin Portal every 15 minutes.
About the Entra ID Page
On the Entra ID page (ITDR > Manage > Entra ID), you can do the following:
- View the list of Entra ID tenants connected to the ITDR Admin Portal. For each Entra ID tenant, you can view:
- **Tenant Name**: The name of the connected Entra ID tenant.
- **Tenant ID**: The tenant ID of the connected Entra ID tenant.
- **Client ID**: The client ID of the connected Entra ID tenant.
- **Storage Account**: The storage account created by the deployment script in Entra ID.
- **Scan Frequency**: The scan frequency (**Daily**, **Weekly**, **Monthly**, and **Quarterly**) configured for an Entra ID tenant while connecting it with the ITDR Admin Portal.
- **Info**: The last and next scans for an Entra ID tenant.
- **Last Scan Status**: The status of the last scan (**Scan Completed**, **Processing scan data**, **Unable to connect to the domain**, **Scan Timed Out**, **Scan Canceled**, and **Scan Failed**).
- **Subscriptions with Read Access**: The list of subscriptions that have read access to the deployed resources.
- **Current State**: The current scan status. The possible statuses are as follows:
- **Active**: The scan is enabled.
- **Disabled**: The scan is disabled.
- **Waiting**: The scan is yet to start.
- **Scanning**: The scan is in progress.
- **Error**: The scan is stopped or not started due to an error.
- [Connect an Entra ID tenant with the ITDR Admin Portal](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal).
- [Obtain the deployment script to run it on Azure Cloud Shell](/itdr/obtaining-deployment-script-azure)[.]
- Start or stop a scan:
- To start the posture scan for a tenant, click the **Start **icon and confirm your action.
- To stop the posture scan for a tenant, click the **Stop **icon and confirm your action.
- [Edit an Entra ID tenant connection](/itdr/editing-entra-id-tenant-connection).
- [Delete an Entra ID tenant connection](/itdr/deleting-entra-id-tenant-connection).
- [Trigger an on-demand scan](/itdr/triggering-demand-scan-entra-id).
![A screenshot of Entra ID page](/downloads/itdr/scan-configuration/entra-id-posture-scan/about-entra-id-posture-scan/itdr-manage-entra-id-page.png)