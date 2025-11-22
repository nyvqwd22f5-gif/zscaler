# Containment Configuration Guide for Microsoft Defender
Source: https://help.zscaler.com/deception/containment-configuration-guide-microsoft-defender
PDF: https://help.zscaler.com/pdf/com/en/1531426.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Microsoft Defender to contain and isolate detected attackers.
Prerequisites
Before you configure the containment integration, ensure that you have:
- Network connectivity from the Zscaler Deception Admin Portal to the Microsoft Defender API servers.
- Installed the [Microsoft Windows Defender ATP agent](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/onboard-configure?view=o365-worldwide) on your endpoints.
Configuring Containment Integration with Microsoft Defender
Follow these steps to configure containment integration with Microsoft Defender:
- [Step 1: Create an Application Registration on Azure and Copy the Application and Tenant IDs](#deception-microsoft-defender-containment-create-app-reg)
- [Step 2: Configure API Permissions for the Application](#deception-microsoft-defender-config-api-permission)
- [Step 3: Create a Client Secret Key](#deception-microsoft-defender-containment-create-certificate-secret-id)
- [Step 4: Configure the Containment Integration Between Deception and Microsoft Defender](#deception-microsoft-defender-containment-integration-configuration)
- [Step 5: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#deception-ms-defender-contain-attacker-rule-investigate)
- []Log in to the [Azure portal](http://portal.azure.com/) using your credentials.
- Go to **Azure Active Directory** > **App registrations**.
-
On the **App registrations** page, click **New registration**.
[See image.](#deception-microsoft-defender-containment-new-reg)
-
On the **Register an application** page, enter a name for the application, and click **Register**.
[See image.](#deception-microsoft-defender-containment-config-app-reg)
The new application is created.
-
On the new application's **Overview** page, copy the **Application (client) ID** and **Directory (tenant) ID**.
[See image.](#deception-microsoft-defender-containment-copy-client-tenant-id)
-
[]In the left-side navigation, click **API permissions**.
[See image.](#deception-ms-defender-api-permissions-option)
-
On the **API permissions** page, click **Add a permission**.
[See image.](#deception-microsoft-defender-containment-add-api-permission-option)
-
On the **Request API permissions** page, click the **APIs my organization uses** tab, and then click **WindowsDefenderATP** application from the list.
[See image.](#deception-microsoft-defender-containment-select-api)
-
Click **Application permissions**.
[See image.](#deception-microsoft-defender-containment-application-permission)
-
Select the following permissions:
- **Machine.Isolate**
- **Machine.Read.All**
- **Machine.ReadWrite.All**
[See image.](#deception-microsoft-defender-containment-select-application-permissions)
-
Click **Add permissions**.
The application with configured API permissions appears.
[See image.](#deception-ms-defender-configured-api-permission-list)
-
Click **Grant admin consent** **for** your application.
[See image.](#deception-ms-defender-grant-admin-consent-for-app)
The permission status of the application changes to granted.
[See image.](#deception-ms-defender-api-permission-granted-list)
-
[]In the left-side navigation, click **Certificates & secrets**.
[See image.](#deception-microsoft-defender-containment-cert-secret)
-
On the **Certificates & secrets** page, click **New client secret**.
[See image.](#deception-microsoft-defender-containment-new-client-secret-option)
-
In the **Add a client secret** window:
- **Description**: Enter a description of your secret key.
-
**Expires**: Select an expiration period for the secret key from the drop-down menu.
Zscaler recommends selecting the maximum expiration period.
[See image.](#deception-microsoft-defender-containment-config-secret-key)
- Click **Add.**
-
After the key is created, copy the **Value**.
[See image.](#deception-microsoft-defender-containment-copy-client-secret-value)
- []Log in to the Deception Admin Portal.
- Go to **Orchestrate** > **Containment**.
-
In the table, locate **Microsoft Defender **and click the **Edit **icon.
[See image.](#deception-microsoft-defender-containment-edit-option)
-
In the **Microsoft Defender** configuration window:
- **Enabled**: Select to enable containment.
- **Tenant ID**: Enter the Directory (tenant) ID that you copied in [Step 1](#deception-microsoft-defender-containment-create-app-reg).
- **API ID**: Enter the Application (client) ID that you copied in [Step 1](#deception-microsoft-defender-containment-create-app-reg).
- **App Secret**: Enter the client secret value that you copied in [Step 3](#deception-microsoft-defender-containment-create-certificate-secret-id).
[See image.](#deception-microsoft-defender-containment-integration-config-details)
- Click **Save**.
- After the configuration is saved, click **Test** to verify network connectivity between the Deception Admin Portal and Microsoft Defender.
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create an orchestrated rule.](#deception-ms-defender-create-rule)
- [Take action from the Investigate page.](#deception-microsoft-defender-contain-attack-investigate)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#deception-ms-defender-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#deception-ms-defender-rule-details)
-
Under **Respond**, enable **Microsoft Defender**.
[See image.](#deception-response-rule-microsoft-defender)
-
Click **Save**.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#deception-ms-defender-investigate-action-option)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click **Contain with Microsoft Defender**.
[See image.](#deception-ms-defender-investigate-take-action)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![Create a new application registration option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-new-app-registration.png)
[]![Configure the new application registration on Azure](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-new-app-register.png)
[]![Copy registered application's client and tenant ID](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-new-app-copy-client-tenant-id.png)
[]![API permissions option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-application-api-permissions-option.png)
[]![Add API permission option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-new-app-add-api-permission.png?1666343600)
[]![Select an API to grant permissions](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-new-defender-atp.png?1666343979)
[]![Select Application permissions](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-application-permissions.png?1666848326)
[]![Configure application permissions](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-select-application-permissions.png?1665745578)
[]![Configured API permissions for the application](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-configured-api-permissions-for-application-2.png)
[]![Grant admin consent for the application in Microsoft Defender](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-application-grant-api-permissions-2.png)
[]![API permissions granted for the application](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-application-api-permissions-granted-2.png)
[]![Certificate & secret option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-microsoft-defender-certificate-secret-option-2.png)
[]![Create a client secret key on Azure](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-create-new-secret.png)
[]![Add a client secret key](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-configure-secret-key_0.png?1677236834)
[]![Copy the client secret value](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-copy-client-secret-value.png)
[]![Microsoft Defender containment integration Edit option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-microsoft-defender-edit.png)
[]![Microsoft Defender containment integration configuration details](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-containment-integration-details.png?1665999292)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure a rule to contain attacker with Microsoft Defender](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-create-response-rule-general.jpg)
[]![ A response rule with Microsoft Defender Enabled](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-response-rule.png)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-ms-defender-action-option.png)
[]![Contain attacker with Microsoft Defender](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-microsoft-defender-deployment-guide/zscaler-deception-microsoft-defender-take-action.png)