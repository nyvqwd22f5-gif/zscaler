# Adding Users
Source: https://help.zscaler.com/zia/adding-users
PDF: https://help.zscaler.com/pdf/com/en/1398816.pdf

[Watch a video about User Management, including how to add a user](https://fast.wistia.net/embed/iframe/65aszz5npz)
Zscaler provides a number of ways to provision users, [groups](/zia/about-groups), and [departments](/zia/about-departments) as described in [About Provisioning and Authentication Methods](/zia/choosing-provisioning-and-authentication-methods). You can also add users when you configure policies. This article describes how to add individual user accounts on the Users page in the ZIA Admin Portal. When adding users, you must specify their groups and departments. You can also add new groups and departments. A user can belong to up to 128 groups. The Zscaler service uses groups when it applies policies and uses departments for reporting purposes.
You can use a [CSV file to add multiple users](/zia/importing-user-information-csv-file) at once.
To add a user:
- Go to **Administration **>** User Management**.
- Click **Add User**.
- The **Add User** window appears.
- In the **Add User** window:
-
**User ID**:** **Enter a user ID.** **The user ID consists of a user name and domain name in email format. Enter the user name and if your organization has more than one domain, select the domain name. The username must be in the form of an email address. It does not have to be a valid email address, but it must be unique, and its domain must belong to the organization.
The User ID field allows values of alphanumeric characters and certain special characters up to a maximum of 127 characters. This field corresponds to the email field in the API. However, the data validation in the API supports a broader range of characters.
-
**User Name**: Enter a display name for the user. Typically, the full name of the user. This appears when choosing users for policies.
The User Name field allows values containing UTF-8 characters up to a maximum of 127 characters.
-
**Groups**: Select the groups that the user belongs to. Click the **Add** icon to add a new group.** **[Groups](/zia/about-groups) are used in policies. You can control access to apps based on user groups.
A company can have up to 140K groups. A user can be associated with maximum 127 groups via API and the ZIA Admin Portal. However, when a user is created or updated via Directory Sync or SCIM, they can be associated with more than 127 groups.
- **Department**: Choose the department that the user belongs to. Click the **Add** icon to add a new department.** **[Departments](/zia/about-departments) are used in policies and reports. Unlike groups, a user can belong to only one department.
-
**Status**: Enable or disable the user.
Disabling a user with the same user name as an [admin](/zia/about-administrators) also disables the admin.
- **Comments**: Optionally, enter additional notes or information. The content cannot exceed 10,240 characters.
- **Password**: Enter the user’s password.** **If you selected password as the authentication method, it must follow the guidelines that you defined.
- **Confirm Password**:** **Retype the user's password.
- **Temporary Authentication Email**: Enter a valid email address for the temporary authentication. This only appears if you selected [One-time Token or One-time Link](/zia/about-one-time-tokens-or-links) as the temporary authentication method in [Authentication Profile](/zia/about-authentication-profile#temporary-authentication).
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).