# Creating an Active Directory Custom Change Detection Policy
Source: https://help.zscaler.com/itdr/creating-active-directory-custom-change-detection-policy
PDF: https://help.zscaler.com/pdf/com/en/1531803.pdf

[Watch a video on Active Directory Change Detection.](https://fast.wistia.net/embed/iframe/37o4d4nbip)
You can configure an Active Directory (AD) Custom Change Detection policy to detect changes in an AD domain based on users, groups, or computers. You can also notify specific users via email if the configured changes are detected.
To create an AD Custom Change Detection policy:
- Go to **ITDR** > **Manage **> **Active Directory** **Change Detection**.
-
Click **Add Policy**.
[See image.](#add-policy-button)
The **Policy Details **window appears.
-
In the **Policy Details **window:
- **Enabled**: Select to enable the policy.
- **Policy Name**: Enter a name for the policy.
- **Domain**: Select an AD domain from the drop-down menu to which the policy must be applied.
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
- [Groups](#groups-property)
- [Computers](#computers-property)
- [Notify](#notification)
The policy is added, and the changes in the AD domain are detected based on the policy configuration.
[]To detect changes based on user properties, select **Users** and follow these steps:
- Select **Enabled **and click **Save**.
-
Click **Add User**.
[See image.](#add-user)
The **User Details **window appears.
-
In the **User Details **window:
- **Distinguished Name**: Enter the value that identifies the user entry in your AD domain.
- **Properties**: Select the properties based on which the changes must be detected (e.g., **ACLs**, **Password Changes**, and **Group Memberships**).
[See image.](#user-details-window)
- Click **Save**.
[]To detect changes based on group properties, select **Groups** and follow these steps:
- Select **Enabled **and click **Save**.
-
Click **Add Group**.
[See image.](#add-group-button)
The **Group Details **window appears.
-
In the **Group Details **window:
- **Distinguished Name**: Enter the value that identifies the group entry in your AD domain.
- **Properties**: Select the properties based on which the changes must be detected (e.g., **ACLs**, **Password Changes**, and **Group Memberships**).
[See image.](#group-window)
- Click **Save**.
[]To detect changes based on computer properties, select **Computers** and follow these steps:
- Select **Enabled **and click **Save**.
-
Click **Add Computer**.
[See image.](#add-computer)
The **Computer Details **window appears.
-
In the **Computer Details **window:
- **Distinguished Name**: Enter the value that identifies the computer entry in your AD domain.
- **Properties**: Select the properties based on which the changes must be detected (e.g., **ACLs**, **Password Changes**, and **Group Memberships**).
[See image.](#computer-window)
- Click **Save**.
[]To notify specific users via email when changes are detected by the policy conditions, select **Notify** and follow these steps:
- **Enabled**: Select to enable email notifications.
-
**Users**: Select the users that you want to notify for changes to the AD domain matching the policy conditions from the drop-down menu.
[See image.](#notify)
- Click **Save**.
[]![AD Change Detection Policy Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-ad-change-detection-add-policy.png)
[]![Policy Details Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-policy-details-window.png)
[]![AD Change Detection Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-ad-change-detection-edit-icon.png)
[]![Policy Configuration Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-policy-configuration-window-ad.png)
[]![Policy Configuration Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-add-user-button.png)
[]![User Details Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-user-details-window.png)
[]![Groups Option in Policy Configuration Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-groups-window-add.png)
[]![Group Details Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-group-details-window.png)
[]![Computer Option in Policy Configuration Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-computer-add-button.png)
[]![Computer Details Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-computer-details-window.png)
[]![Notify Window](/downloads/itdr/change-detection-policies/active-directory-custom-change-detection-policies/creating-active-directory-custom-change-detection-policy/itdr-notify-window-ad-policy_0.png)