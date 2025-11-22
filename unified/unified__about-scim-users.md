# About SCIM Users
Source: https://help.zscaler.com/unified/about-scim-users
PDF: https://help.zscaler.com/pdf/com/en/1491456.pdf

SCIM Users are attributes configured in your identity provider (IdP) that get pulled into the Private Applications service when SCIM is enabled. This information is presented on the SCIM Users page.
SCIM Users provide the following benefits and enable you to:
- Review the list of users synced to Private Applications over SCIM by the IdP.
- Filter by SCIM Group Name or SCIM User Name.
- Quickly remove users from Private Applications when a user is disabled or deleted in your user directory.
About the SCIM Users Page
On the SCIM Users page (Administration > Identity > Private Access > SCIM Users), you can do the following:
- Filter the information that appears in the table. Select the appropriate option from the drop-down menu (e.g., **SCIM User Name**), enter the proper value in a search filter (e.g., **SCIM Group Name**), or click **Add Filters** to filter by SCIM attribute, and then click **Apply**. By default, **None** is selected for the **Time Range** filter.
- View a list of users provisioned for the IdP using SCIM. For each SCIM User, you can see:
- **Last Updated**: The data and time of the user's last action. You can display the timestamp in local time (e.g., Pacific Daylight Time (PDT)) or Coordinated Universal Time (UTC) by clicking the hyperlink.
- **Internal User ID**: Private Application's internal ID for the user.
- **SCIM User Name**: The name of the user as identified by the IdP.
- **IdP SCIM User ID**: The ID for the user as identified by the IdP.
- Click the **View **icon to open the **Attribute Values** window and view the attribute values of the Internal User ID.
- Copy the **SCIM User Name** to your clipboard.
- Copy the **IdP SCIM User ID** to your clipboard.
![Viewing the SCIM Users page](/downloads/unified/administration/private-applications/identity/scim-configuration/about-scim-users/unified-scim-users-page.png)