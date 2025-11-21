# Adding Policy Templates
Source: https://help.zscaler.com/zia/adding-policy-templates
PDF: https://help.zscaler.com/pdf/com/en/1499591.pdf

You can add a policy template for tenants or tenant groups from the [Policy Template page](/zia/about-policy-template) in the Zscaler Management Portal for Partners. A tenant or tenant group can be associated to only one policy template.
To add a policy template:
- Go to **Policy Template **page.
-
Click **Policy Template.**
The **Add Policy Template** window appears.
-
In the **Add Policy Template** window:
- **Name**: Enter a name for the policy template.
- **Cloud**: Select the cloud on which the tenant is provisioned.
- **Tenants**: Select tenants from the drop-down menu. The list of tenants available is based on the cloud selected.
- **Add Cloud**: Click **Add Cloud **to add another cloud. You can add tenants under the selected cloud.
- **Tenant Groups**: Select tenant groups from the drop-down menu.
- **Allow Policy Rule Reorder**: This option is disabled by default and hence the policy is enforced at top priority. If enabled, the ZIA Admin Portal admins can change the order of the policy in the **Rule Order **option (Policy > URL & Cloud App Control > Edit URL Filtering Rule).
- **Description**: (Optional) Enter a description for the policy template. The description cannot exceed 256 characters.
[See image.](#add-policy-image)
- Click **Save and** **Edit Policies**.
[]![Add%20Policy%20Template.png](/downloads/zia/zscaler-management-portal-partners/administration/adding-policy-template/Add%20Policy%20Template.png)