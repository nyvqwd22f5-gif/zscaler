# Deploying Endpoint Deception with Zscaler Client Connector for Windows
Source: https://help.zscaler.com/deception/deploying-endpoint-deception-zscaler-client-connector-windows
PDF: https://help.zscaler.com/pdf/com/en/1531420.pdf

If your organization is provisioned for Zscaler Internet Access (ZIA), you can deploy endpoint deception capabilities on Microsoft Windows machines using Zscaler Client Connector.
This article provides information on prerequisites and how to deploy endpoint deception with Zscaler Client Connector for the Microsoft Windows operating system.
Prerequisites
Before deploying endpoint deception with Zscaler Client Connector, ensure that you have:
- Enabled endpoint deception capabilities on your Zscaler Client Connector by contacting your Zscaler Account team.
-
Endpoints with Windows 10 (64-bit only) or later with a 64-bit version of Zscaler Client Connector are installed. You must[ upgrade Zscaler Client Connector](/client-connector/downloading-zscaler-client-connector) to one of the supported versions:
- 4.5.0.344 or later
- 4.6.0.123 or later
- 4.7.0.31 or later
For Zscaler-recommended best practices for deploying Zscaler Client Connector, see [Best Practices for Zscaler Client Connector Deployment](/zscaler-client-connector/best-practices-zscaler-client-connector-deployment).
-
Enabled the Tunnel Internal Client Connector Traffic option in the Zscaler Client Connector Portal.
By default, the traffic sent to the Zscaler Deception Admin Portal is considered internal traffic. Enabling this option in the Zscaler Client Connector Portal ensures that all traffic sent to the Deception Admin Portal is tunneled through Zscaler. To learn more, see [Configuring Zscaler Client Connector App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#advanced).
-
Outbound HTTPS access from either or both of your proxy and firewall in your local environment to:
- Deception Admin Portal on port 443, i.e., <your_subdomain>.illusionblack.com on port 443
- dwv281inkfqg3.cloudfront.net on port 443
To learn more, see the [Zscaler Client Connector Config page](https://config.zscaler.com/zscaler.net/zscaler-app).
If you are running endpoint deception using a [landmine agent](/deception/about-landmine-agent-agentless) and want to migrate to Zscaler Client Connector, you can automatically migrate during the Zscaler Client Connector upgrade process. During the upgrade, important information such as lures applied and decoys deployed are automatically copied to the new installation location, and the standalone landmine agent is uninstalled.
Deploying Endpoint Deception with Zscaler Client Connector
Follow these steps to deploy endpoint deception with Zscaler Client Connector:
- [Step 1: Enable Deception in the Zscaler Client Connector Portal](#endpoint-deception-enable-deception-client-connector-portal)
- [Step 2: Customize the Zscaler Deception Landmine Installer](#endpoint-deception-customize-landmine-agent-service)
- [Step 3: Integrate Zscaler Client Connector with Deception](#endpoint-deception-integrate-with-zcc)
- [Step 4: Configure a Zscaler Client Connector Profile Policy Rule for Windows](#endpoint-deception-add-windows-policy)
- [Step 5: Verify the Zscaler Deception Service Status in Zscaler Client Connector](#endpoint-deception-verify-zd-service-status-client-connector)
- []Log in to the [Zscaler Client Connector Portal](/zscaler-client-connector/accessing-and-navigating-zscaler-client-connector-portal).
- Go to **Zscaler Service Entitlement** > **Zscaler Deception** **(Deception)**.
-
Enable **Zscaler Deception Enabled by Default** to enable endpoint deception for all Zscaler Client Connector users upgraded to 3.9 or later for Windows.
[See image.](#ed-enable-zd-by-default)
-
If you want to enable Deception for a specific group of users, disable **Zscaler Deception Enabled by Default**, and then select a group from the **User Groups** drop-down menu. To learn more, see [Enabling Deception for a Group of Users](/client-connector/selective-entitlement-enabling-deception-group-users).
[See image.](#ed-enable-zd-for-group)
- Click **Save**.
- []Log in to the Deception Admin Portal.
- Go to **Settings **> **Endpoint Settings **> **Agent Configuration**.
-
Customize the **Name**, **Display Name**, and **Description** of the landmine installer or service to prevent the agent from being fingerprinted. To learn more, see [Customizing Landmine Installer](/deception/customizing-landmine-installer).
[See image.](#ed-customize-landmine-agent-service)
- []Log in to the Zscaler Client Connector Portal.
- Click **Administration** on the top menu.
- In the left-side navigation, click **Zscaler Deception**.
-
Verify if the Zscaler Deception installer settings (**Name**, **Display Name**, and **Description**) you see on this page match the settings you entered in [the previous step](/deception/deploying-endpoint-deception-zscaler-client-connector-windows#endpoint-deception-customize-landmine-agent-service). If they don't match, click **Sync** to get the latest values. To learn more, see [Zscaler Client Connector Integration with Deception](/client-connector/about-zscaler-client-connector-integration-deception).
[See image.](#ed-sync-zscaler-deception)
- []In the Zscaler Client Connector Portal, click **App Profiles** on the top menu.
- On the **App Profiles** page, select **Windows**.
-
If you already have existing policies configured, click the **Edit **icon for the policy that you want to modify. If you do not have an existing policy, click **Add Windows Policy**.
[See image.](#ed-add-windows-policy-option)
-
In the **Edit Windows Policy** (or **Add Windows Policy**) window, enter the **Logout Password**, **Exit Password**, and **Password to access Deception Settings**.
[See image.](#ed-config-zd-password-rule)
If you are adding a new policy, make sure you have configured all necessary fields as required. To learn more, see [Adding a Zscaler Client Connector Profile Policy Rule for Windows](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#windows). If you are editing an existing policy, make sure **Enable **is selected.
- Click **Save**.
-
[]Log in to Zscaler Client Connector on your machine.
[See image.](#ed-zcc-sign-in-page)
-
In the left-side navigation, click **More**, and** **then click **Update Policy.**
[See image.](#ed-zcc-advanced-settings)
-
After the policy update is complete, click **Update App**.
[See image.](#deception-zcc-update-app)
-
After the app update is complete, click **Advanced Settings**.
[See image.](#deception-zcc-advanced-settings)
-
Enter the password you created in [the previous step](/deception/deploying-endpoint-deception-zscaler-client-connector-windows#endpoint-deception-add-windows-policy).
[See image.](#ed-zd-password)
-
Click **OK**.
[See image.](#ed-zd-service-running)
The configuration is successful and the **Service Status** is **Running**.
[]![Enabling Zscaler Deception by default for all users](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-enabled-by-default.png)
[]![Enabling Zscaler Deception for a specific group of users](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-enabled-group.png)
[]![Customize the landmine agent service](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-endpoint-settings.png)
[]![Syncing Zscaler Deception with Zscaler Client Connnector](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-download-client-connector-sync.png?1664785113)
[]![Add Windows Policy option on the App Profiles page](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-zcc-windows-policy-page.png)
[]![Configure logout, exit, and deception passwords in the rule](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-password.png?1664786406)
[]![Signing in to the Zscaler Client Connector](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-log-in.png)
[]![Zscaler Client Connector window with the Advanced Settings option highlighted ](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-update-policy-zcc.png)
[]![Zscaler Client Connector window with the option to update the app highlighted](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-update-app-zcc.png)
[]![Prompt for entering Advanced Settings password in Zscaler Client Connector window](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-enter-deception-password.png)
[]![Zscaler Client Connector window with the Advanced Settings option highlighted](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-advanced-settings-zcc.png)
[]![Zscaler Cleint Connector window showing Zscaler Deception service status](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-running.png)