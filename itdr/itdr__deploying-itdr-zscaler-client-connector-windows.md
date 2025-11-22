# Deploying Zscaler ITDR with Zscaler Client Connector for Windows
Source: https://help.zscaler.com/itdr/deploying-itdr-zscaler-client-connector-windows
PDF: https://help.zscaler.com/pdf/com/en/1531716.pdf

ITDR uses Deception configuration because there is no separate service entitlement for ITDR in Zscaler Client Connector.
If your organization has a Zscaler Client Connector rollout, you can deploy ITDR on Microsoft Windows machines.
This article provides information on prerequisites and how to deploy ITDR with Zscaler Client Connector for the Microsoft Windows operating system.
Prerequisites
Before deploying ITDR with Zscaler Client Connector, ensure that you have:
- [Configured SSO in ZIA.](/zia/configuring-saml)
-
[Downloaded Zscaler Client Connector or updated to the latest supported version](/client-connector/downloading-zscaler-client-connector):
- 4.3.0.264 or later
- 4.4.0.383 or later
- 4.5.0.344 or later
For Zscaler-recommended best practices to deploy Zscaler Client Connector, see [Best Practices for Zscaler Client Connector Deployment](/z-app/zscaler-app-deployment-best-practices-guide).
- Enabled ITDR capabilities on your Zscaler Client Connector by contacting your Zscaler Account team.
-
Outbound HTTPS access from either or both of your proxy and firewall in your local environment to:
- Zscaler ITDR Admin Portal on port 443, i.e., <your_subdomain>.illusionblack.com on port 443
- dwv281inkfqg3.cloudfront.net on port 443
To learn more, see the [Zscaler Client Connector Config page](https://config.zscaler.com/zscaler.net/zscaler-app).
Deploying ITDR with Zscaler Client Connector
Follow these steps to deploy ITDR with Zscaler Client Connector:
- [Step 1: Enable ITDR in the Zscaler Client Connector Portal](#endpoint-deception-enable-deception-client-connector-portal)
- [Step 2: Customize the Zscaler ITDR Endpoint Installer](#endpoint-deception-customize-landmine-agent-service)
- [Step 3: Integrate Zscaler Client Connector with ITDR](#endpoint-deception-integrate-with-zcc)
- [Step 4: Configure a Zscaler Client Connector Profile Policy Rule for Windows](#endpoint-deception-add-windows-policy)
- [Step 5: Verify the Zscaler Deception Service Status in Zscaler Client Connector](#endpoint-deception-verify-zd-service-status-client-connector)
[]
ITDR uses Deception configuration and there is no separate UI for ITDR in the Zscaler Client Connector Portal.
- Log in to the [Zscaler Client Connector Portal](/z-app/about-zscaler-app-portal/#zia-admin-portal).
- Go to **Zscaler Service Entitlement** > **Zscaler Deception** **(Deception)**.
-
Enable **Zscaler Deception Enabled by Default** to enable ITDR for all Zscaler Client Connector users upgraded to 3.9 or later for Windows.
[See image.](#ed-enable-zd-by-default)
-
If you want to enable ITDR for a specific group of users, disable **Zscaler Deception Enabled by Default**, and then select a group from the **User Groups** drop-down menu. To learn more, see [Enabling Deception for a Group of Users](/client-connector/selective-entitlement-enabling-deception-group-users).
[See image.](#ed-enable-zd-for-group)
- Click **Save**.
- []Log in to the Zscaler ITDR Admin Portal.
- Go to **Settings** > **Endpoint Settings** > **Agent Configuration**.
-
Customize the **Name**, **Display Name**, and **Description** of the endpoint installer or service to prevent the agent from being fingerprinted. To learn more, see [Customizing Endpoint Installer](/itdr/customizing-endpoint-installer).
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
To add a new policy to configure access to **Deception Settings** from Zscaler Client Connector, click **Add Windows Policy**. To edit an existing policy, click the **Edit **icon for the policy that you want to modify.
[See image.](#ed-add-windows-policy-option)
-
In the **Add Windows Policy** or the **Edit Windows Policy** window, enter the **Logout Password**, **Exit Password**, and **Password to access Deception Settings**.
[See image.](#ed-config-zd-password-rule)
If you are adding a new policy, make sure you have configured all necessary fields as required. To learn more, see [Adding a Zscaler Client Connector Profile Policy Rule for Windows](/client-connector/configuring-zscaler-client-connector-profiles#windows). If you are editing an existing policy, make sure **Enable **is selected.
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
[]![Enable Zscaler Deception by default for all users](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-enabled-by-default.png)
[]![Enable Zscaler Deception for a specific group of users](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-enabled-group.png)
[]![Customize the landmine agent service](/downloads/itdr/endpoint-settings/agents/deploying-itdr-zscaler-client-connector-windows/itdr-zcc-deployment-customizing-installer_0.png)
[]![Sync Zscaler Deception ](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-download-client-connector-sync.png?1664785113)
[]![Add Windows Policy option on the App Profiles page](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-zcc-windows-policy-page.png)
[]![Configure logout, exit, and deception passwords in the rule](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-password.png?1664786406)
[]![Zscaler Client Connector Sign In page](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-log-in.png)
[]![Zscaler Client Connector Advance Settings ](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-update-policy-zcc.png)
[]![A screenshot capturing the option to update app on Zscaler Client Connector](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-update-app-zcc.png)
[]![Enter Zscaler Deception password](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-enter-deception-password.png)
[]![A screenshot capturing the Advanced Settings option in Zscaler Client Connector](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector-windows/zscaler-deception-advanced-settings-zcc.png)
[]![Zscaler Deception service running ](/downloads/deception/deceive/landmine-decoys/endpoint-deception-zscaler-client-connector/deploying-endpoint-deception-zscaler-client-connector/zscaler-deception-client-connector-deception-running.png)