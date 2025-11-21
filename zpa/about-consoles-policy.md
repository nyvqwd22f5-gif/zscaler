# About Consoles Policy
Source: https://help.zscaler.com/zpa/about-consoles-policy
PDF: https://help.zscaler.com/pdf/com/en/1524711.pdf

Consoles policy rules allow you to designate privileged consoles with the ability to upload or download Zscaler Internet Access (ZIA) Sandbox files. After you have completed the [integration settings](/zpa/about-integrations) for ZIA, you can then inspect files that are being uploaded. Consoles policies also allow you to use the [Clipboard functions (copy and paste)](/zpa/copying-and-pasting-clipboard), [record privileged sessions, and configure live privileged sessions (join, share, control, and monitor)](/zpa/accessing-privileged-sessions).
Consoles policy rules include the following benefits and enable you to:
- Manage the permissions that provide the ability to upload and download files.
- Set permissions to allow the inspection of sandbox files from ZIA during the upload process.
- Share, record, and provide functional abilities for privileged sessions.
If you want to configure consoles-based control, you must first create the [privileged portals](/zpa/about-privileged-portals) and [privileged consoles](/zpa/about-privileged-consoles) that you want to assign control to.
About the Consoles Policy Page
On the Consoles Policy page (Policy > Privileged Policy > Consoles Policy), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Consoles Policy page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new consoles policy rule.](/zpa//configuring-privileged-capabilities-policies)
- Expand all the displayed rows in the table to see more information about each policy rule.
- View a list of all consoles policy rules that were configured. For each rule, you can see:
- **Rule Order**: The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
- **Name**: The name of the rule. The description is also displayed if available.
- **Status**: The status of the rule as being enabled or disabled to a privileged console.
- **Console Configuration**: The console configuration options you have set for that specific policy rule: **Clipboard Copy**, **Clipboard Paste**, **Download**, **Inspect Upload,** **Join Sessions**, **Record Sessions**, **Share Sessions Control**, **Share Sessions Monitor**, and **Upload**.
- Copy an existing consoles policy rule's criteria, and use it to create a new rule.
- Edit an existing consoles policy rule.
- Delete a consoles policy rule.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Depending on your Privileged Remote Access (PRA) subscriptions, you see the following privileged policy options:
- [Portals Policy](/zpa/about-portals-policy)
- [Privileged Credentials Policy](/zpa/about-privileged-credentials-policy)
- Depending on your ZPA Admin Portal subscriptions, you see the following ZPA policy options:
- [Access Policy](/zpa//about-access-policy)
- [Timeout Policy](/zpa/about-timeout-policy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Security Policy](/zpa/about-security-policy)
- [Redirection Policy](/zpa/about-redirection-policy)
![Privileged Capabilities Policy page within the ZPA Admin Portal](/downloads/zpa/policies/privileged-remote-access-policy/about-privileged-capabilities-policy/Update%20page%20w%20steps.png)