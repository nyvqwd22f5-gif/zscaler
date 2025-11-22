# About Privileged Consoles
Source: https://help.zscaler.com/unified/about-privileged-consoles
PDF: https://help.zscaler.com/pdf/com/en/1492531.pdf

After you have created a privileged portal, you can create and edit privileged consoles on the Privileged Consoles page. After a privileged console is created, you can enable it to appear on the end user’s Privileged Remote Access portal. You can enable the same privileged console to appear in one or more privileged portals.
Privileged consoles provide the following benefits and enable you to:
- Create privileged consoles that allow end users to access the systems they want to connect to.
- Manage which privileged portals the privileged consoles are assigned to.
- Update the description for privileged consoles that are displayed to end users.
About the Privileged Consoles Page
On the Privileged Consoles page (Policies > Clientless > Privileged Consoles), you can:
- Filter the list of privileged consoles linked to a specific privileged portal. By default, all privileged consoles are displayed.
- Expand all rows in the table to see more information about each privileged console.
- [Add a new privileged console](/unified/configuring-privileged-consoles).
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all the privileged consoles that are configured for your organization. For each console, you can see:
- **Name**: The name of the privileged console.
- **Description**: The description for the privileged console, if available.
- **Display on Console**: Enable to display the privileged console on the end user’s Privileged Remote Access portal.
- **Protocol**: There are three types of consoles that can be used for Privileged Remote Access: VNC, SSH, or RDP.
- **Domain**: A valid domain name.
- **Port**: The port number used for the console.
- [Edit an existing privileged console](/unified/editing-privileged-portals).
- Delete an existing privileged console.
If you delete a privileged console, you can no longer form a new connection and the privileged console is removed from the end user's Privileged Remote Access portal. If there are any existing connections prior to the deletion of the privileged console, these connections remain accessible until the browser is closed.
![Viewing and managing privileged consoles within the Privileged Consoles page](/downloads/unified/policies/private-applications/access-control/clientless/privileged-remote-access-management/privileged-consoles/about-privileged-consoles/unified-privileged-consoles-page.png)