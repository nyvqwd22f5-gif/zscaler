# About Privileged Approvals
Source: https://help.zscaler.com/zpa/about-privileged-approvals
PDF: https://help.zscaler.com/pdf/com/en/1485221.pdf

Privileged approvals allow third-party users and contractors to be able to log in to a [Privileged Remote Access (PRA) portal](/zpa/accessing-privileged-remote-access-portal). Privileged approvals maintain a secure access point only for the email addresses you include in a privileged approval. These users are given entry to the specific applications you need them to access.
Privileged approvals provide the following benefits and enable you to:
- Create privileged approvals with a set amount of time that one or more designated application segments can be accessed.
- Delete existing privileged approvals to revoke access to those application segments.
- Delete all expired privileged approvals.
The Privileged Approvals page is where you can create and edit privileged approvals. After you have created a [privileged portal](/zpa/about-privileged-portals) and [privileged console](/zpa/about-privileged-consoles), you can start creating privileged approvals to allow users into the Privileged Remote Access portal.
You need to create an [access policy](/zpa/configuring-privileged-approvals-draft) that uses the Conditional Access rule action with the **Allow for Privileged Approval checkbox** selected for a privileged approval to take effect.
About the Privileged Approvals Page
On the Privileged Approvals page (Resource Management > Privileged Remote Access > Privileged Approvals), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Privileged Approvals page.
- Purge expired privileged approvals. After you click **Delete** in the confirmation window, the privileged approvals with an expired status listed in the table are removed.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
-
[Add a new privileged approval](/zpa/configuring-privileged-approvals-draft).
If Privileged Approvals are disabled, only users with the matching authentication domains are applicable in the [Microtenant](/zpa/about-microtenants).
- View a list of all the privileged approvals that are configured for your organization. For each privileged approval, you can see:
- **User Email**: The email address for the user assigned to the privileged approval.
- **Application Segments**: The application segments selected for the privileged approval. If just one application segment is selected, it will be listed in the table. If there are two or more selected application segments, select the drop-down menu for that specific approval to view them.
- **Start Time**: The set start time that the user has access to the Privileged Remote Access portal.
- **End Time**: The set end time that the user no longer has access to the Privileged Remote Access portal.
- **Approval Status**: Displays one of the following privileged approval status types:
- **Active**: The privileged approval is currently available for the user.
- **Expired**: The privileged approval is no longer available for the user.
- **Future**: The privileged approval is available for the user at a set time in the future.
-
[Edit an existing privileged approval](/zpa/editing-privileged-approvals).
If you are a third-party user or contractor using a Microtenant with Privileged Approvals disabled, you cannot edit an existing privileged approval.
- Delete an existing privileged approval.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Privileged Consoles](/zpa/about-privileged-consoles) page to add new consoles or manage existing consoles.
- Go to the [Privileged Credentials](/zpa/about-privileged-credentials) page to add new credentials or manage existing credentials.
- Go to the [Privileged Portals](/zpa/about-privileged-portals) page to add new portals or manage existing portals.
![Privileged Approvals page within ZPA Admin Portal](/downloads/zpa/privileged-remote-access-management/privileged-approvals/about-privileged-approvals/Privileged%20Approvals%20page%20w%20steps_0.png)