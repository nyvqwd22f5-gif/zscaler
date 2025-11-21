# Configuring IAM Roles and Permissions for Microsoft Azure
Source: https://help.zscaler.com/cloud-branch-connector/configuring-iam-roles-and-permissions-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1507516.pdf

Configuring IAM roles and permissions for Microsoft Azure allows you to add Azure accounts in the Zscaler Cloud & Branch Connector Admin Portal. When configuring IAM roles and permissions, you can use Terraform or Azure. When adding permissions in Azure, you can use the built-in role of Reader or create a custom role. To learn more, see [Configuring the Workload Discovery Service for Microsoft Azure Accounts](/cloud-branch-connector/configuring-workload-discovery-service-microsoft-azure-accounts).
To configure IAM roles and permissions:
- Sign in to the [Azure portal](https://portal.azure.com).
-
In the Azure portal, under **Azure Resources**, select **App registrations**.
[See image.](#step2)
-
On the **App registrations** page, select **New registration**.
[See image.](#step3)
- On the **Register an application** page, configure the following:
- **Name**: Enter a name for your app.
- **Supported account types**: Select **Accounts in this organizational directory only**.
-
**Redirect URI (optional)**: Do not configure this field.
[See image.](#step4)
- Click **Register**. The app registration is created, and the page appears.
-
On the app registration page you created, copy and save the **Application (client) ID** and the **Directory (tenant) ID**. You use these credentials when [adding an Azure account in the Cloud & Branch Connector Admin Portal](/cloud-branch-connector/adding-microsoft-azure-account).
[See image.](#step6)
-
From the left-side navigation of the app registration page, select **Manage** > **Certificates & secrets**.
[See image.](#step7)
-
On the **Certificates & secrets** page, select **Client secrets**, and then click **New client secret**. The **Add a client secret** window appears.
[See image.](#step8)
- In the **Add a client secret** window:
- Configure the following:
- **Description**: Enter a description to identify the secret.
- **Expires**: From the drop-down menu, select a duration for which the secret is active.
-
Click **Add**.
[See image.](#step9)
- The client secret is created, and you can view the following:
- **Description**: The description of the client secret.
- **Expires**: The date the client secret expires.
-
**Value**: The value that Azure assigned to the client secret. You use this credential when [adding an Azure account in the Cloud & Branch Connector Admin Portal](/cloud-branch-connector/adding-microsoft-azure-account).
Immediately after creating the client secret, copy and save the **Value**. After you refresh the page, or when you access it later, you can no longer view or copy the **Value**.
-
**Secret ID**: The ID of the client secret.
[See image.](#step10)
-
Navigate to the Azure home page. Under **Azure Resources**, select **Subscriptions**.
[See image.](#step11)
- On the **Subscriptions** page, select your subscription.
-
On your subscription page, from the left-side navigation, select **Access control (IAM)**.
[See image.](#step13)
-
On the **Access control (IAM)** page, select **Add**, and from the drop-down menu select **Add custom role**.
[See image.](#step14)
- On the **Create a custom role** page:
- On the **Basics** tab, configure the following:
- **Custom role name**: Enter a name for the custom role.
- **Description**: Enter a description for the custom role.
-
**Baseline permissions**: Select **Start from scratch**.
[See image.](#step15a)
- On the **Permissions** tab, do not configure any settings.
- On the **Assignable scopes** tab, leave the settings unchanged.
- On the **JSON** tab, click **Edit**.
-
On line 10, `"actions": []`, replace the line with the following and then click **Save**:
`"actions": [
"Microsoft.Resources/subscriptions/resources/read",
"Microsoft.Network/virtualNetworks/read",
"Microsoft.Network/virtualNetworks/virtualMachines/read",
"Microsoft.Network/networkInterfaces/read",
"Microsoft.Compute/virtualMachines/read"
"Microsoft.Resources/subscriptions/resourceGroups/read"
],`
[See image.](#step15d)
Alternatively, instead of configuring settings on the **JSON** tab, you can assign the Reader role to your subscription.
- On the **Review + create** tab, select **Create**.
-
On the **Access control (IAM)** page, select **Add**, and from the drop-down menu select **Add role assignment**.
[See image.](#step16)
- On the **Add role assignment** page:
- On the **Role** tab, under **Job function roles**, select the custom role you created and click **Next**.
- On the **Members** tab, configure the following:
- **Selected role**: This field displays the custom role you selected.
-
**Assign access to**: Select **User, group, or service principal**.
[See image.](#step16b1)
- **Members**: Click **Select members**. The **Select members** window appears.
-
In the **Select members** window, search for and select the app registration you previously created. Click **Select**.
[See image.](#step16b2)
- **Description**: Enter a description for the role assignment.
- On the **Conditions** tab, do not configure any fields.
- On the **Review + create** tab, click **Create**.
In the Cloud & Branch Connector Admin Portal, you can use the **Application (client) ID**, **Directory (tenant) ID**, and client secret to create an Azure account. To learn more, see [Adding a Microsoft Azure Account](/cloud-branch-connector/adding-microsoft-azure-account).
[]
![Selecting App registrations under App Services in the Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep2.png)
[]![Selecting New registration on the App registrations page of the Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep3.png)
[]![The Register an application page details in the Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep4.png)
[]![Copying and saving the Application (client) ID and Directory (tenant) ID after creating an app registration in the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep6.png)
[]![Selecting Certificates & secrets under Manage on the app registration page in the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep7.png)
[]![Selecting New client secret under Client secrets on the Certificates & secrets page of the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep8.png)
[]![The Add a client secret window in the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep9.png)
[]![The Client secrets details on the Certificates & secrets page of the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep10.png)
[]![Selecting Subscriptions under App Services in the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep11.png)
[]![Selecting Access control (IAM) from the left side navigation of your subscription in the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep13.png)
[]![Selecting Add custom role on the Access control (IAM) page of the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep14.png)
[]![The Create a custom role Basics tab details in the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep15a.png)
[]![The Create a custom role JSON tab details in the Azure Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep15d.png)
[]![Selecting Add role assignment on the Access control (IAM) page of the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep16.png)
[]![The Members tab details on the Add role assignment page of the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep16b1.png)
[]![The Select members window on the Add role assignment page in the Azure portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-iam-roles-and-permissions-microsoft-azure/iamrolespermissionsstep16b2.png)