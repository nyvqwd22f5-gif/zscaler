# Creating & Managing Users
Source: https://help.zscaler.com/uvm/creating-managing-users
PDF: https://help.zscaler.com/pdf/com/en/1527796.pdf

Admins can create and manage all users in your organization's Zscaler Security Operations (SecOps) account. Managing users includes defining their access and permissions by assigning role permissions (RBAC - Role-Based Access Control), optionally assigning content permissions (ABAC - Attribute-Based Access Control), and deactivating or deleting users.
Only users with admin privileges can create and manage users.
Creating Users
Admins can create new users by filling out basic information and assigning a user role.
To create a user:
- Click the **Profile** menu on the top right of the page.
- Go to **Account Settings** > **User Management**.
-
Click **Create**.
The **Create User** page appears.
- On the **Create User** page:
- **Email**: Enter the user's organization email.
- **First Name**: Enter the user's first name.
- **Last Name**: Enter the user's last name.
- **Main Account**: (Optional) If you have more than one account, set the user's default account.
-
**Role**: Select a role for the user. If you don’t, the user is assigned the default **No Access** role. To learn more, see [Understanding System Roles](/uvm/understanding-system-roles) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#assigning-role)
-
Click **Save**.
The new user appears in the User Management list.
[]**![mceclip2.png](/downloads/uvm/account-management/user-management/user-management/mceclip2.png)
**
Managing Users
As an admin, you can manage your account's users (e.g., adding and deleting users, assigning user roles, and applying content permissions).
To manage users, go to **Account Settings** > **User Management** to access the list of existing users. On the User Management page, you can use the column sort and filters to navigate the users list.
- To sort the users list in ascending or descending order by a specific column,** **hover over the header of the column you want to sort by and click the arrow icon.
-
To filter the users list, hover over the** **header of the column you want to filter by and click the Filter icon. You can select the users you want to filter by, or create a Condition filter.
[See image.](#users-list-filter)
When managing users, you can perform the following actions:
- [Assign User Roles and Content Permissions](#assign-user-permissions)
- [Deactivate Users](#deactivate-users)
- [Delete Users](#delete-users)
[]![mceclip6.png](/downloads/uvm/account-management/user-management/user-management/mceclip6.png)
[]You can assign users roles and content permission sets to control user access to features and data.
Every new user is assigned a system role or a custom role when created, and you can change this role at any time. To learn more, see [Understanding System Roles](/uvm/understanding-system-roles), [Creating Custom Roles](/uvm/creating-custom-roles), and [Assigning Roles to Users](/uvm/assigning-roles-users).
In addition to roles, you can assign content permission sets to control the data users can access. For example, you might want a Vulnerabilities Admin to see only the data related to their team, rather than all data in the account. To learn more, see [Creating & Managing Content Permissions](/uvm/creating-managing-content-permissions).
Content permissions can only be assigned after a user is created and saved, not during the user creation process. To learn more, see [Assigning Content Permissions](/uvm/assigning-content-permissions).
[]You can deactivate users in your organization's account to revoke their access to the system, without removing their user information. You can only deactivate one user at a time.
Deactivating users doesn't remove data associated with the user's account (e.g., reports or dashboards they created).
To deactivate a user:
- Click the **Profile **menu on the top right of the page.
- Go to **Account Setting** > **User Management**.
-
Hover over the user you want to deactivate, and click the **Edit** icon.
The **Edit User** page appears.
- In the **Personal Info** section, disable** Active** to the right of the user’s email.
- Click **Save**.
[]You can delete users from your organization's account to fully remove their information from the system and revoke their access to the system.
Deleting users doesn't remove data associated with the user's account (e.g., reports or dashboards they created).
To delete a single user:
- Click the **Profile **menu on the top right of the page.
- Go to **Account Setting** > **User Management**.
-
Hover over the user you want to delete, and click the **Delete **icon.
The **Confirm Deletion** window appears.
- Click **Delete**.
To delete multiple users:
- Click the **Profile **menu on the top right of the page.
- Go to **Account Setting** > **User Management**.
- From the users list, select the users that you want to delete.
-
Click **Delete** at the top of the page.
The **Confirm Deletion** window appears.
- Click **Delete**.