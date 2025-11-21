# About SCIM Users
Source: https://help.zscaler.com/zpa/about-scim-users
PDF: https://help.zscaler.com/pdf/com/en/1484436.pdf

SCIM users are attributes configured in your identity provider (IdP) that get pulled into ZPA when SCIM is enabled. This information is presented on the SCIM Users page.
SCIM users provide the following benefits and enable you to:
- Review the list of users synced to ZPA over SCIM by the IdP.
- Filter by SCIM Group Name or SCIM User Name.
- Quickly remove users from ZPA when a user is disabled or deleted in your user directory.
About the SCIM Users Page
On the SCIM Users page (Authentication > User Authentication > SCIM Management > SCIM Users), you can do the following:
- Filter the information that appears in the table over a period between **7 Days** and **6 Months**, or you can select **Custom Range**. If you use a **Custom Range**, the start and end date must be within the last 6 months. By default, this is set to **None**.
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the SCIM Users page to reflect the most current information.
- Filter the information that appears in the table. By default, **None** is selected for the **Time Range** filter.
- Select a SCIM-enabled IdP to generate a list of SCIM users in the table.
- View a list of users provisioned for the IdP using SCIM. For each SCIM user, you can see:
- **Last Updated**: The data and time of the user's last action. You can display the timestamp in local time (e.g., Pacific Daylight Time (PDT)) or Coordinated Universal Time (UTC) by clicking the hyperlink.
- **Internal User ID**: ZPA's internal ID for the user.
- **SCIM User Name**: The name of the user as identified by the IdP.
- **IdP SCIM User ID**: The ID for the user as identified by the IdP.
- Click the **View **icon (![View icon](/downloads/zpa/authentication/about-scim-users-and-groups/zpa-view-icon.png)
) to open the **Attribute Values** drawer and view the attribute values of the Internal User ID.
- Copy the SCIM user name to your clipboard.
- Copy the IdP SCIM user ID to your clipboard.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [SCIM Attributes](/zpa/about-scim#SCIMattributes) page to view the SCIM attributes for the selected IdP.
- Go to the [SCIM Groups](/zpa/about-scim-groups) page to view the groups provisioned for the IdP using SCIM.
- Go to the [SCIM Sync Logs](/zpa/about-scim-sync-logs) page to view the logs associated with the IdP using SCIM.
![Viewing the SCIM Users page](/downloads/zpa/authentication/about-scim-users-and-groups/zpa-scim-users-page-react.png)