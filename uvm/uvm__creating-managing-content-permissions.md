# Creating & Managing Content Permissions
Source: https://help.zscaler.com/uvm/creating-managing-content-permissions
PDF: https://help.zscaler.com/pdf/com/en/1527791.pdf

Admins can configure content permission sets using specific data attributes that can be assigned to users to specify the data they can access. While role permissions dictate the actions the user can perform (e.g., create a dashboard, merge tickets), content permissions limit the scope of data the user can view and is authorized to perform those actions on. For example, a user might be assigned a role allowing them to create reports, but limited by content permissions, they’ll only see data relating to their team (e.g., the team responsible for all Linux assets). To learn more, see [Understanding System Roles](/uvm/understanding-system-roles) and [Creating Custom Roles](/uvm/creating-custom-roles).
After content permissions are created, you can assign permission sets to users. When assigned, access changes take effect on the user's next browser refresh. To learn more, see [Assigning Content Permissions](/uvm/assigning-content-permissions).
Creating Content Permission Sets
To create a content permission set:
- Click the **Profile** menu on the top right of the page.
- Go to **Account Settings **> **Permissions **> **Content**.
-
Click **Create**.
The **Create new permission set** drawer appears.
- In the **Create new permission set** drawer:
- **Name**: Enter a unique name for the permission set.
- **Rule**: Define filter conditions for the permission set. Conditions define the data included in the permission set (i.e., what data should be included in the user's access).
- Select a field that the condition should be based on.
- Select an operator (e.g., **Equals**, **Contains**). Available operators vary depending on the selected field type, indicated to the left of the field name.
-
Enter the value that the rule should apply to.
[See image.](#example-ruleset-conditions)
To apply content permissions to users, without having to manually enter unique identifiers, you can add a user's email as a [dynamic value](#dynamic-value).
- (Optional) Use **AND**/**OR** logic to define compound rules.
- **AND** applies the content permissions to users only if all conditions in the rule are met.
- **OR** applies the content permissions to users if any of the conditions in the rule are met.
- Click **Save** to create the permission set.
After saving the permission set, you can assign it to users on the User Management page. The newly assigned permission set is applied on the user's next browser refresh. To learn more, see [Assigning Content Permissions](/uvm/assigning-content-permissions).
Scope of Content Permissions
Content permissions only apply to an account's mapped data, so they won't restrict access to unmapped data across the platform. For example, if a user's role grants them access to Logs or Data Mapping, their content permissions won't apply to those resources.
Additionally, content restrictions for scheduled reports and custom dashboard exports conform to the permission set of the user that created the report or the dashboard. The permission set of the receiver is not taken into account, so the delivered report can include data that the receiver can't access by their own permissions if they are also a user in the system.
[]![mceclip3.png](/downloads/uvm/account-management/user-management/content-permissions/mceclip3.png)
[]Setting a Dynamic Value
You can grant dynamic access based on the email address of the current user to avoid the need to create a separate condition for each individual user email address. For example, to grant access to all Linux Team users to the tickets assigned to each individual team member, you can add a condition to the Linux Team permission set, selecting the Assignee Email field and entering the dynamic `{user_email}` value.
To create dynamic rule conditions:
- Click the **Profile** menu on the top right of the page.
- Go to **Account Settings **> **Permissions **> **Roles** > **Content**.
-
Click **Create**.
The **Create new permission set** drawer appears.
- In the **Create new permission set** drawer:
- **Name**: Enter a unique name for the permission set.
-
**Rule**: Define filter conditions for the permission set.
Conditions define the data included in the permission set (i.e., what data should be included in the user's access).
- Select the relevant field from the list that contains your users' email address information (e.g., **Assignee Email**).
-
Select the **Equals **operator.
Only the Equals operator is supported, as the field's value should be a unique identifier.
- Enter the `{user_email}` value.
[See image.](#example-dynamic-value)
- (Optional) Use **AND**/**OR** logic to define compound rules.
- **AND** applies the content permissions to users only if all conditions in the rule are met.
- **OR** applies the content permissions to users if any of the conditions in the rule are met.
- Click **Save** to create the permission set.
After saving the permission set, you can assign it to users on the User Management page. The newly assigned permission set is applied on the user's next browser refresh. To learn more, see [Assigning Content Permissions](/uvm/assigning-content-permissions).
[]![mceclip4.png](/downloads/uvm/account-management/user-management/content-permissions/mceclip4.png)
Managing Content Permission Sets
After creating content permission sets, you can can manage and monitor them from the Content page. This page provides a centralized view of all configured content permission sets in your account.
Go to **Account Settings** > **Permissions **> **Content **to perform the following actions:
- [Edit a Permission Set](#editing-content-permission-set)
- [Delete a Permission Set](#deleting-content-permission-set)
[]You can edit any of your existing permission sets on the Content Permissions page.
To edit a permission set:
- Hover over the permission set you want to edit and click the **Edit **icon, or select the permission set and click **Edit **at the top of the page.
- Adjust the permission set as needed.
- Click **Save** to apply the changes to the set.
Adjustments to permission sets apply on the user's next login or on browser refresh.
[]You can delete a permission set that is no longer necessary in your account. This removes the data access restrictions from users that were assigned the deleted set.
This action is irreversible and will delete the permission set immediately.
To delete a permission set:
- Select the permission sets you want to delete.
-
Click **Delete**.
[See image.](#delete-content-permissions-button)
Adjustments to permission sets apply on the user's next login or on browser refresh.
[]![mceclip5.png](/downloads/uvm/account-management/user-management/content-permissions/mceclip5.png)