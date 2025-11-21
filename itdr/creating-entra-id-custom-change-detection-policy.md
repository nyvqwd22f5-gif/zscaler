# Creating an Entra ID Custom Change Detection Policy
Source: https://help.zscaler.com/itdr/creating-entra-id-custom-change-detection-policy
PDF: https://help.zscaler.com/pdf/com/en/1531807.pdf

[Watch a video on Entra ID Change Detection.](https://fast.wistia.net/embed/iframe/y1qs9e29jz)
You can configure an Entra ID Custom Change Detection policy to detect changes in an Entra ID tenant based on users, service principals, or roles. You can also notify specific users via email if the configured changes are detected.
To create an Entra ID Custom Change Detection policy:
- Go to **ITDR** > **Manage **> **Entra Change Detection**.
-
Click **Add Policy**.
[See image.](#add-policy-button)
The **Policy Details **window appears.
-
In the **Policy Details **window:
- **Enabled**: Select to enable the policy.
- **Policy Name**: Enter a name for the policy.
- **Tenant**: Select an Entra ID tenant from the drop-down menu to which the policy must be applied.
[See image.](#policy-window-first)
-
Click **Save**.
The policy is added to the table.
-
Locate the policy that you added, and click the **Edit **icon under the **Actions **column.
[See image.](#edit-policy)
The policy configuration window appears.
[See image.](#policy-configuration-window)
- In the policy configuration window, configure the required properties using which changes must be detected:
- [Users](#users-property)
- [Service Principals](#groups-property)
- [Roles](#computers-property)
- [Notify](#notification)
The policy is added, and the changes in the Entra ID tenant are detected based on the policy configuration.
[]To detect changes based on user properties, select **Users **and follow these steps:
- Select **Enabled **and click **Save**.
-
Click **Add User**.
[See image.](#add-user)
The **Add User **window appears.
-
In the **Add User **window:
- **Identity Name**: Select an Entra ID user that must be monitored for changes from the drop-down menu.
- **Change Type**: Select the changes that you want to detect for the selected identity (e.g., **Role Assignments**, **Password Changes**, **Changes in MFA,** **Being marked 'Risky'**, **Delegated consent grants to applications**, **Administrative Units**, and **Group Memberships**).
[See image.](#user-details-window)
- Click **Save**.
[]To detect changes based on service principal properties, select **Service Principal** and follow these steps:
- Select **Enabled **and click **Save**.
-
Click **Add Service Principal**.
[See image.](#add-group-button)
The **Add Service Principal **window appears.
-
In the **Add Service Principal **window:
- **Identity Name**: Select a service principal that must be monitored for changes from the drop-down menu.
- **Change Type**: Select the changes that you want to detect for the selected identity (e.g., **Changes to secret/cert**, **Added/revoked Admin Consent**, and **Changed ownership**).
[See image.](#group-window)
- Click **Save**.
[]To detect changes based on role properties, select **Role** and follow these steps:
- Select **Enabled **and click **Save**.
-
Click **Add Role**.
[See image.](#add-computer)
The **Add Role **window appears.
-
In the **Add Role **window:
- **Identity Name**: Select a role that must be monitored for changes from the drop-down menu.
- **Change Type**: Select the changes that you want to detect for the selected identity (e.g., **Additions and removals**).
[See image.](#computer-window)
- Click **Save**.
[]To notify specific users via email when changes are detected by the policy conditions, select **Notify** and follow these steps:
- **Enabled**: Select to enable email notifications.
-
**Users**: Select the users that you want to notify for changes to the Entra ID tenant matching the policy conditions from the drop-down menu.
[See image.](#notify)
- Click **Save**.
[]![The Entra Change Detection page](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-entra-change-detection-add-policy.png)
[]![The Change Detection Policy Details Window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-policy-window-entra-id.png)
[]![The Entra Change Detection page](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-entra-change-detection-edit-icon.png)
[]![The Policy Configuration window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-entra-policy-configuration-window.png)
[]![The User configuration window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-add-user-entra.png)
[]![The Add User window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-add-user-window-entra.png)
[]![The Service Principal details window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-service-principal-add-button.png)
[]![The Add Service Principal details window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-service-principal-window.png)
[]![The Role details window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-add-role-entra-button.png)
[]![The Add Role window](/downloads/itdr/change-detection-policies/entra-id-custom-change-detection-policies/creating-entra-id-custom-change-detection-policy/itdr-role-window-entra-id.png)
[]![The Notify Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-notify-window-ad-policy_0.png)