# Adding Tenant Details
Source: https://help.zscaler.com/dspm/adding-tenant-details
PDF: https://help.zscaler.com/pdf/com/en/1517356.pdf

The first step in the [onboarding process](/dspm/onboarding-microsoft-azure-tenant) is to provide the Azure tenant details. DSPM uses the tenant or management group details to generate a template to connect to the Microsoft Entra tenant.
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Click **Add New**.
- Under **Select Cloud Provider**, click the** Azure** tile.
-
[]Select **Tenant** or **Management Group**.
[See image.](#dspm-azure-tile)
- Click **Next**.
-
In the **Tenant Details** section:
The role name and service principal name must contain only alphabets, numbers, hyphens ("-"), and underscores ("_").
- **DSPM alias: **Enter a user-friendly name for the tenant or management group.
- **Tenant Name**: Enter the name of the tenant that you want to onboard.
- **Role Name**: Enter a unique role name. This role name is added as a prefix to all the [custom roles](/dspm/iam-roles-and-permissions-microsoft-azure) that are created during the onboarding process.
- []**Tenant ID**: Enter the Microsoft Entra tenant ID. You can find the tenant ID in the [Azure portal](https://portal.azure.com/) in multiple ways. For example:
- Sign in to the [Azure portal](https://portal.azure.com/).
- On the top right, select your account and then click **Switch directory**.
-
On the **Portal Settings |** **Directories + subscriptions** page, under **All Directories**, copy the **Directory ID** of the corresponding tenant that you want to onboard.
[See image.](#azure-directory-id)
- []**Service Principal**: Enter a unique name for the service principal (application). DSPM creates a service principal with this name in the Microsoft Entra tenant after deploying the [tree discovery template](/dspm/deploying-azure-tree-discovery-template). The service principal is used to define the access policy and permissions for DSPM to access specific resources within the tenant. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals?tabs=browser).
-
**Management Group ID**: Enter the management group ID. You can include multiple management group IDs to onboard the management groups.
This field is visible only if you select the [Management Group](#tenantormanagementgroup) for onboarding.
-
**Notification Emails** (Optional): Enter the email addresses of the recipients who must be notified of any configuration or permissions issues encountered with the onboarded tenant. You can add up to 30 email addresses to receive notifications about the issues. You can also add email addresses after completing the onboarding process.
[See image.](#mgtgrpdetails)
-
Click **Apply **to continue. Click **Reset** if you want to change the details.
[See image.](#provide-tenant-details)
If all the details are accurate, you are directed to the [Connect to the Tenant](/dspm/deploy-azure-tree-discovery-template) section to deploy the tree discovery template.
[]![Select Cloud Provider page with different cloud types in tiles and annotation around the Azure tile.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/adding-tenant-details/dspm-select-cloud-provider.png)
[]![Tenant Details section with blurred field information and the options to apply or reset.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/adding-tenant-details/dspm-azure-tenant-details.png)
[]![Directories + subscriptions page with a list of directories and annotation around a blurred directory ID.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-directory-ID.png)
[]![The tenant details section with all the required fields for onboarding.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/adding-tenant-details/dspm-azure-management-group-details.png)