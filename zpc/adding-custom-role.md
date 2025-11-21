# Adding a Custom Role
Source: https://help.zscaler.com/zpc/adding-custom-role
PDF: https://help.zscaler.com/pdf/com/en/1417416.pdf

You can add custom roles and configure permissions for users to access or manage tasks in specific modules in the Zscaler Posture Control (ZPC) Admin Portal. A single role is assigned to a group, so all users in that group have the same role and permissions. To learn more, see [About Groups](/zpc/about-groups).
If you are a user with an administrator role, you can add and manage additional custom admin roles. Zscaler recommends that you add groups before adding administrators, because you must select a group for each administrator that you create.
Modules
The ZPC features in the Admin Portal are classified as:
- **Global Modules**: Data is not segregated by cloud accounts and [business units](/zpc/about-business-units) are not applicable for these modules.
- **Modules**: Data can be filtered by cloud accounts that are associated with business units. The business unit filters are applicable for these modules.
To learn more, see [ZPC Modules and Global Modules](/zpc/zpc-modules-and-global-modules).
Adding a Custom Role
To add a custom role:
- Go to **Administration** > **Role Management**.
- On the **Role Management **page, click **Add Role**.
[See image.](#role-button)
- In the **Add Role** window:
- **Role Name**: Enter a unique name for the custom role.
- **Permissions: **Assign any of the following permissions:
- **Access**: Select the checkbox for tasks that users can perform in each [module or global module](/zpc/zpc-modules-and-global-modules). [See image.](#modules)
- **View Only**: Select to provide view-only access to specific modules or global modules.
- **None**: Select to restrict users from accessing or viewing specific modules or global modules.
- Click **Save**.
[See image.](#addrole-window)
The custom role is created and displayed on the **Role Management** page.
[![Add a role](/downloads/zpc/authentication-authorization/role-management/adding-custom-role/zpc-rolebutton.jpg)
]
[![Add the role and permissions](/downloads/zpc/authentication-authorization/role-management/adding-custom-role/zpc-add-role.jpg)
]
[![Select tasks in modules and global modules](/downloads/zpc/authentication-authorization/role-management/adding-custom-role/zpc-modulesaccess.png)
]