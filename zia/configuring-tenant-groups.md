# Configuring Tenant Groups
Source: https://help.zscaler.com/zia/configuring-tenant-groups
PDF: https://help.zscaler.com/pdf/com/en/1506531.pdf

You can configure tenant groups to boost easy tenant management and to apply security policies to multiple tenants at once. You can create, view, or manage tenant groups based on your organization’s needs.
Only an admin with permission to manage tenants can create, view, or modify tenant groups.
Creating and Viewing a Tenant Group
- [Creating a Tenant Group](#creating-a-tenant-group)
- [Viewing a Tenant Group's details](#viewing-tenant-group-details)
[]
To create a new tenant group:
- Go to **Tenants > Tenant Groups.**
- Click on the **Add Tenant Group** button. The **Add Tenant Group** window appears.
-
In the **Add Tenant Group** window:
- **Name**: Enter a name for the group.
- **Cloud**: Select a cloud.
- **Tenants**: Select tenants from the cloud.
- **Description**: Add a description, if you want.
[See image.](#adding-tenant-group-image)
- Click **Save**.
To learn how to apply policy to a tenant group, see [About Policy Templates](/zia/about-policy-template).
[]
![Add Tenant Group window](/downloads/zia/zscaler-management-portal-partners/tenant-management/configuring-tenant-groups/adding-tenant-group.png)
[]To see the details of a particular tenant group,
- Go to **Tenants > Tenant Groups**.
-
Click on the group's name. On the Tenant group details page, you can see:
- **Tenant Name**: The name of the tenants in the group.
- **Organization ID**: The organization ID of the particular tenant.
- **Customer name**: The name of the customer the tenant comes under.
- **Customer ID**: The customer ID.
- **Domains**: The domains registered by the tenant.
- **Subscription**: The subscription plan of the tenant.
- **Policy Templates**: The policies provisioned to the tenant.
- **Clouds**: The clouds provisioned to the tenant.
- **Status**: The tenant's status (Active or Disabled).
[See image.](#tenant-group-details)
[]
![Viewing a Tenant Group's details](/downloads/zia/zscaler-management-portal-partners/tenant-management/configuring-tenant-groups/tenant-grp-details-2.png)
[]Editing Tenant Groups
To edit an existing tenant group:
- Go to** Tenants > Tenant Groups.**
- Click on the **Edit** icon next to the group.
-
Modify the fields you want to change:
- **Name**: The name of the tenant group.
- **Clouds**: The clouds provisioned to the tenant group.
- **Tenants**: The tenants in the group.
- **Description**: The group's description.
[See image.](#editing-tenant-groups)
- Click **Save**.
[]
![Edit Tenant Group window](/downloads/zia/zscaler-management-portal-partners/tenant-management/configuring-tenant-groups/editing-tenant-groups.png)
[]Adding Policy Templates to Tenant Groups
To assign security policy templates to a tenant group:
- Go to **Policy Templates**.
- Click on the **Edit** icon next to the policy you want to assign. The **Edit Policy** **Template** window appears.
-
In the** Edit Policy Template** window, add the tenant group under **Tenant Groups**.
[See image.](#adding-policy-templates-to-groups)
- Click **Save and Sync**.
[]
![Edit Policy Template window](/downloads/zia/zscaler-management-portal-partners/tenant-management/configuring-tenant-groups/adding-policy-temp-to-tenant-groups.png)