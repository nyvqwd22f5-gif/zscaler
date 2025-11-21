# Installing & Upgrading the Agent Manager
Source: https://help.zscaler.com/zpa/installing-upgrading-agent-manager
PDF: https://help.zscaler.com/pdf/com/en/1531951.pdf

The agent manager installs the Zscaler Microsegmentation agent service onto your device. It performs initial installation of the agent, monitors the agent service, and restarts the agent when it crashes.
Prerequisites
Before you install the agent manager, ensure the following prerequisites are met:
- Create a [signing certificate](/zpa/creating-certificate-signing-requests-enrollment-ca-certificates) to be used for Microsegmentation agents. To learn more, contact your Micosegmentation admin.
- Ensure that there is outbound connectivity to port any.zms-ag2ac.prod.zpath.net.
Installing the Agent Manager
To install the agent manager:
- Create a new [agent group](/zpa/microsegmentation/agent-management/agent-groups) to download the agent manager RPM to your device. You can also download it directly from the agent group page. To learn more, see [Configuring Agent Groups](/zpa/configuring-agent-groups).
- After the downloaded RPM from the new agent group is installed, the manager automatically downloads and installs the latest agent version. After the agent is downloaded and installed onto your device, the agent manager initiates a connection to the Zscaler Zero Trust Exchange (ZTE), and the setup is complete.
If the service fails to start or the agent fails to register with the Zscaler Zero Trust Exchange (ZTE), it is likely that a firewall or security appliance is interfering with the agent’s outbound mTLS connection. Ensure that this outbound connectivity to Port 443 is permitted, and that this connectivity is not subjected to DPI or similar security measures.
Upgrading the Agent
To configure automatic upgrades to the agent:
- Edit an existing agent group. To learn more, see [Editing Agent Groups](/zpa/editing-agent-groups).
- In the selected agent group, expand the **Version Profile & Configurations** menu.
- Expand the **Version Profile & Configurations** menu.
- Enable **Auto Update**.
- For **Version Profile**, select **Latest**.
- Complete the remaining steps for [editing the agent group](/zpa/editing-agent-groups).
- Click **Save.**
- The agent manager connects to the agent service, then downloads and installs the latest agent version to your device.