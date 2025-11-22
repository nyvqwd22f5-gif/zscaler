# About Privileged Approvals
Source: https://help.zscaler.com/unified/about-privileged-approvals
PDF: https://help.zscaler.com/pdf/com/en/1492516.pdf

Privileged approvals allow third-party users and contractors to be able to log in to a [Privileged Remote Access (PRA) portal](/unified/accessing-privileged-remote-access-portal). Privileged approvals maintain a secure access point only for the email addresses you include in a privileged approval. These users are given entry to the specific applications you need them to access.
Privileged approvals provide the following benefits and enable you to:
- Create privileged approvals with a set amount of time that one or more designated application segments can be accessed.
- Delete existing privileged approvals to revoke access to those application segments.
- Delete all expired privileged approvals.
The Privileged Approvals page is where you can create and edit privileged approvals. After you have created a [privileged portal](/unified/about-privileged-portals) and [privileged console](/unified/about-privileged-consoles), you can start creating privileged approvals to allow users into the Privileged Remote Access portal.
You need to create an [access policy](/unified/configuring-privileged-approvals) that uses the Conditional Access** **rule action with the **Allow for Privileged Approval** checkbox selected for a privileged approval to take effect.
About the Privileged Approvals Page
On the Privileged Approvals page (Policies > Clientless > Privileged Approvals), you can do the following:
- Refresh the Privileged Approvals page.
- Expand all rows in the table to see more information about each application segment.
- Purge expired privileged approvals listed in the table. After you select **Delete** in the confirmation window, all of the privileged approvals with an expired status listed in the table are removed.
-
[Add a new privileged approval](/unified/configuring-privileged-approvals).
If Privileged Approvals are disabled, only users with the matching authentication domains are applicable in the [Microtenant](/unified/about-microtenants).
- Filter the information that appears in the table. By default, no filters are applied.
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
[Edit an existing privileged approval](/unified/editing-privileged-approvals).
If you are a third-party user or contractor using a Microtenant with Privileged Approvals disabled, you cannot edit an existing privileged approval.
- Delete an existing privileged approval.
![Viewing and managing privileged approvals on the Privileged Approvals page](/downloads/unified/policies/private-applications/access-control/clientless/privileged-remote-access-management/privileged-approvals/about-privileged-approvals/unified-privileged-approvals-page.png)