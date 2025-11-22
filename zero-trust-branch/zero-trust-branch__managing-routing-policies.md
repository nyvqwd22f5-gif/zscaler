# Managing Routing Policies
Source: https://help.zscaler.com/zero-trust-branch/managing-routing-policies
PDF: https://help.zscaler.com/pdf/com/en/1532642.pdf

You can view, edit, delete, or organize routing policies and configure routing settings when required.
Editing a Policy
To edit a policy:
- Go to **Deployment **> **Sites**.
-
On the **Sites **page, locate the entry for the site whose routing policy you want to edit, and click the name of the site in the **Site Name **column.
[See image.](#select-site-for-editing)
- On the site details page, click the **Routing Policy **tab.
-
Locate the policy that you want to edit, click the corresponding **Gear **icon, and select **Edit**.
[See image.](#edit-option)
-
In the **Edit Routing Rule **drawer, make the necessary changes.
[See image.](#editing-drawer)
-
Click **Save**.
The policy changes are saved.
-
Click **Commit **to apply the changes.
[See image.](#commit-rule-routing)
Reordering Policies
You can reorder policies to change the order of evaluation.
To reorder policies:
- Go to **Deployment **> **Sites**.
-
On the **Sites **page, locate the entry for the site whose routing policies must be reordered, and click the name of the site in the **Site Name **column.
[See image.](#select-site-for-reorder)
- On the site details page, click the **Routing Policy **tab.
-
Click **Reorder**.
[See image.](#reorder-button)
A **Drag **icon appears for each custom policy.
-
Click and drag each policy to the desired position using the **Drag **icon.
-
Click **Save policy reorder**.
[See image.](#drag-icon-reorder)
Deleting a Policy
To delete a policy:
- Go to **Deployment **> **Sites**.
-
On the **Sites **page, locate the entry for the site whose routing policy you want to delete, and click the name of the site in the **Site Name **column.
[See image.](#select-site-for-delete)
- On the site details page, click the **Routing Policy **tab.
-
Locate the policy that you want to delete, click the corresponding **Gear **icon, and select **Delete**.
[See image.](#delete-option)
-
In the delete confirmation window, enter `DELETE` and click **Confirm**.
[See image.](#delete-confirmation)
The policy is removed from the Zero Trust Branch Admin Portal.
Configuring Routing Settings
You can configure Zero Trust Branch to use local learned routes over Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) policies.
To configure route preference:
- Go to **Deployment **> **Sites**.
-
On the **Sites **page, locate the entry for the site whose routing policy settings must be updated, and click the name of the site in the **Site Name **column.
[See image.](#select-site-for-settings)
- On the site details page, click the **Routing Policy **tab.
-
Click **Settings**.
[See image.](#settings-button)
-
In the **Policy Routing Settings** drawer, enable or disable **Prefer local learned routes over the ZIA and ZPA policies**.
[See image.](#settings-drawer)
-
Click **Save**.
The routing preference is applied.
[]![Selecting a site to manage routing policies](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-select-site-for-routing-policies.jpg)
[]![Site details page showing the option to edit a policy](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-edit-option.jpg)
[]![Editing a routing rule](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-edit-routing-policy-drawer.jpg)
[]![Site details page showing the option to commit changes](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-commit-routing-rulw.jpg)
[]![Selecting a site to manage routing policies](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-select-site-for-routing-policies.jpg)
[]![Site details page showing the option to reorder policies](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-reordering-routing-policy.jpg)
[]![Animation showing how to reorder routing policies](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-redorder-routing-policy.gif)
[]![Selecting a site to manage routing policies](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-select-site-for-routing-policies.jpg)
[]![Site details page showing the option to delete policy](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-delete-routing-policy.jpg)
[]![Deleting a routing policy](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-delete-confirmation-routing-policy.jpg)
[]![Selecting a site to manage routing policies](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-select-site-for-routing-policies.jpg)
[]![Site details page showing the option to configure routing policy settings](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-settings-routing-policies.jpg)
[]![Configuring policy routing settings](/downloads/zero-trust-branch/administration/deployment-configuration/managing-routing-policies/ztb-settings-drawer.jpg)