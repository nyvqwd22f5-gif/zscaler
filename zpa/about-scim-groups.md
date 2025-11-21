# About SCIM Groups
Source: https://help.zscaler.com/zpa/about-scim-groups
PDF: https://help.zscaler.com/pdf/com/en/1485781.pdf

SCIM groups are attributes configured in your identity provider (IdP) that get pulled into ZPA when SCIM is enabled. This information is presented on the SCIM Groups page.
SCIM groups provide the following benefits and enable you to:
- Review the list of SCIM groups synced to ZPA over SCIM by the IdP.
- Enforce policies based on SCIM attributes and SCIM groups.
About the SCIM Groups Page
On the SCIM Groups page (Authentication > User Authentication > SCIM Management > SCIM Groups), you can do the following:
- Filter the information that appears in the table over a period between **7 Days** and **6 Months**, or you can select **Custom Range**. If you use a **Custom Range**, the start and end date must be within the last 6 months. By default, this is set to **None**.
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking** Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the SCIM Groups page to reflect the most current information.
- Filter the information that appears in the table. Select the appropriate option from the drop-down menu (e.g., **SCIM User Name**) or enter the proper value in a search filter (e.g., **SCIM Group Name**), and click **Apply**. By default, no filters are selected.
- Select a SCIM-enabled IdP to generate a list of attributes in the table.
- View a list of groups provisioned for the IdP using SCIM. For each SCIM group, you can see:
- **Last Updated**: The data and time of the group's last action. You can display the timestamp in local time (e.g., Pacific Daylight Time (PDT)) or Coordinated Universal Time (UTC) by clicking the hyperlink.
- **Internal Group ID**: ZPA's internal ID for the group.
- **SCIM Group Name**: The name of the group as identified by the IdP.
- **IdP SCIM Group ID**: The ID for the group as identified by the IdP.
- **Total Users in this Group**: The total number of users associated with the group.
- **Active Users in this Group**: The number of active users associated with the group.
- Copy the SCIM group name to your clipboard.
- Copy the IdP SCIM group ID to your clipboard.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [SCIM Attributes](/zpa/about-scim#SCIMattributes) page to view the SCIM attributes for the selected IdP.
- Go to the [SCIM Users](/zpa/about-scim-users) page to view the users provisioned for the IdP using SCIM.
- Go to the [SCIM Sync Logs](/zpa/about-scim-sync-logs) page to view the logs associated with the IdP using SCIM.
![Viewing the SCIM Groups page ](/downloads/zpa/authentication/identity-management/about-scim-groups/zpa-scim-groups-page-react.png)