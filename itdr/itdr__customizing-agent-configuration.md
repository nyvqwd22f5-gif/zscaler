# Customizing Agent Configuration
Source: https://help.zscaler.com/itdr/customizing-agent-configuration
PDF: https://help.zscaler.com/pdf/com/en/1531654.pdf

The Agent Configuration tab allows you to perform following:
- [Customize Agent Configuration](#customize-endpoint-agent)
- [Enable Auto-cleanup](#auto-cleanup)
[]
Customize the agent configuration such as name, display name, and description of the endpoint service to prevent the agent from being fingerprinted.
To customize the endpoint agent installer properties:
- Go to **Settings **> **Endpoint Settings **> **Agent Configuration**.
-
On the **Agent Configuration** page, under** Installer Customizations**:
- **Name**: Edit the endpoint agent service name. The default name is **ZSAITDR**.
- **Display name**: Edit the endpoint agent service display name. The default display name is **Zscaler ITDR**.
- **Description**: Enter a description of the endpoint agent service.
[See image.](#installer-customization)
The endpoint agent service name should be unique. To avoid conflicts with existing services, make sure to check the names of the services running in the systems where you want to install the endpoint agents before configuring the service name.
- Click **Save**.
[]
Enable the auto-cleanup to automatically delete endpoint agents with duplicate hostnames from the Zscaler ITDR Admin Portal. The most recently connected hostnames and the ones that are connected for less than 7 days are retained.
Endpoint agents deleted via auto-cleanup are not uninstalled from the system. You have to manually [uninstall](/itdr/managing-endpoint-agents) them.
To enable the auto-cleanup of duplicate endpoint agents:
- Go to **Settings **> **Endpoint Settings **> **Agent Configuration**.
-
Enable the **Auto-Cleanup Duplicate Agents **option.
[See image.](#auto-cleanup-img)
- Click **Save**.
[]
![Customize landmine installer properties](/downloads/itdr/endpoint-settings/agent-configuration/customizing-endpoint-installer/itdr-agent-configuration-installer-customization.png)
[]![Enable auto clean up of duplicate landmine agents](/downloads/itdr/endpoint-settings/agent-configuration/enabling-auto-clean-duplicate-endpoint-agents/itdr-enable-auto-cleanup-agent-configuration.png)