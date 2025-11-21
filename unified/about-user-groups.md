# About User Groups
Source: https://help.zscaler.com/zidentity/about-user-groups
PDF: https://help.zscaler.com/pdf/com/en/1499111.pdf

Group is a logical entity that includes several users. Creating user groups helps in assigning multiple users to the Zscaler services quickly. You can create user groups to categorize users for various services and assign these user groups to administrative entitlements, service entitlements, admin roles, etc. You can create custom groups and use the predefined groups for a set of users.
The predefined groups are:
- Dynamic Group Administrators: User group with administrative entitlements.
- Zscaler Global Administrators: Initial user group with global administrative entitlements.
- Zscaler Emergency Access: User group that has Zscaler Private Access (ZPA) emergency access entitlement.
- Dynamic Group Guest Domains: Group of users from guest domains.
- Dynamic Group Registered Domains: Group of users from registered domains.
User Groups provide the following benefits and enable you to:
- Provide a quick and simple way to assign multiple users to a Zscaler service in one attempt.
- Categorize users into groups based on their admin roles, administrative access, service access, etc.
A user can be part of up to 1,000 groups. You must have similar limits on the respective services to support this 1,000 group assignment per user. If you don't have enough limits on the service side, the respective service considers group assignments up to the service limit for a user. For example, if you assign a user to 500 groups, but you have a ZIA service subscription for only 128 groups per user, then only the first 128 group assignment for the user is considered on the ZIA service.
About the User Groups Page
On the User Groups page (Directory > User Groups), you can do the following:
- View a list of configured user groups. For each user group, you can see:
- **Name**: The name of the user group.
- **Description**: A short description about the user group.
- [Add a user group](/zidentity/adding-user-groups).
- [Import new user group, or modify existing user group, using a CSV file](/zidentity/importing-group-details-csv-file).
- Bulk delete user groups. This option is visible only when you select more than one user group.
- Reset your search results.
- Search for a user group by **User Name** or **Group Name**.
-
View the predefined group details.
[See image.](#view-group-details)
You cannot edit or delete predefined groups.
- [Edit or delete user a group](/zidentity/editing-or-deleting-items).
- Select groups to perform bulk deletions. Select more than one user group to view the **Actions** option.
![A screenshot capturing the various options in the User Groups page](/downloads/zidentity/administration/user-groups/about-user-groups/zidentity-about-users-groups-page_0.png)
[]![Viewing Predefined Group Details](/downloads/zidentity/administration/user-groups/about-user-groups/zidentity-group-details.png)