# About SCIM Groups
Source: https://help.zscaler.com/unified/about-scim-groups
PDF: https://help.zscaler.com/pdf/com/en/1491461.pdf

SCIM Groups are attributes configured in your identity provider (IdP) that get pulled into the Private Applications service when SCIM is enabled. This information is presented on the SCIM Groups pages.
SCIM Groups provide the following benefits and enable you to:
- Review the list of SCIM Groups synced to Private Applications over SCIM by the IdP.
- Enforce policies based on SCIM attributes and SCIM groups.
About the SCIM Groups Page
On the SCIM Groups page (Administration > Identity > Private Access > SCIM Groups), you can do the following:
- Filter the information that appears in the table. Select the appropriate option from the drop-down menu (e.g., **SCIM User Name**) or enter the proper value in a search filter (e.g., **SCIM Group Name**), and click **Apply**. By default, **None** is selected for the **Time Range** filter.
- View a list of groups provisioned for the IdP using SCIM. For each SCIM Group, you can see:
- **Last Updated**: The data and time of the group's last action. You can display the timestamp in local time (e.g., Pacific Daylight Time (PDT)) or Coordinated Universal Time (UTC) by clicking the hyperlink.
- **Internal Group ID**: Private Application's internal ID for the group.
- **SCIM Group Name**: The name of the group as identified by the IdP.
- **IdP SCIM Group ID**: The ID for the group as identified by the IdP.
- **Total Users in this Group**: The total number of users associated with the group.
- **Active Users in this Group**: The number of active users associated with the group.
- Copy the **SCIM Group Name** to your clipboard.
- Copy the **IdP SCIM Group ID** to your clipboard.
![Viewing the SCIM Groups page](/downloads/unified/administration/private-applications/identity/scim-configuration/about-scim-groups/unified-scim-groups-page.png)