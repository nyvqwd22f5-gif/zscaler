# About Portals Policy
Source: https://help.zscaler.com/zpa/about-portals-policy
PDF: https://help.zscaler.com/pdf/com/en/1508946.pdf

You can configure rules for a Privileged Remote Access (PRA) Portal with a portals policy. Portals policy rules allow you to delete uploaded files, upload inspected files, upload inspected Zscaler Internet Access (ZIA) Sandbox files, access uninspected files in the [Privileged Remote Access (PRA) File Transfer System pages](/zpa/about-pra-file-system), and request and review privileged approvals on the [My Approvals and My Requests pages](/zpa/about-my-approvals). Portals policies allow users to access the PRA File Transfer System and My Approvals pages in the [PRA Portal](/zpa/accessing-privileged-remote-access-portal) they assign the rule to.
Portals policy rules include the following benefits and enable you to:
- Manage the permissions that provide the ability to upload inspected files, access uninspected files, and request and manage privileged approvals.
- Access the PRA File Transfer System and My Approvals feature in a PRA Portal.
- Control the file uploads and privileged approval requests for PRA.
If you want to configure portals policies, you must first create the [privileged portals](/zpa/about-privileged-portals) that you want to assign control to.
About the Portals Policy Page
On the Portals Policy page (Policy > Privileged Policy > Portals Policy), you can do the following:
- Expand all the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the table only displays the first 100 rules. Alternatively, you can scroll to see more rules. If there are more than 1,000 rules, **Display All Rules** is not visible.
- [Add a new portals policy rule.](/zpa/configuring-portals-policies)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all portals policy rules that were configured. For each rule, you can see:
- **Rule Order**: The policy evaluation order number for the rule. ZPA applies policy rules based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
- **Name**: The name of the rule. The description is also displayed here, if available.
- **Portal Configuration**: The portal configuration you have set for that specific policy rule, with the following options enabled or disabled:
- **Delete File**
- **Access Uninspected File**
- **Upload Inspected Sandbox**
- **Upload Inspected Scan**
- **Request Approvals**
- **Review Approvals**
- Copy an existing portals policy rule's criteria, and use it to create a new rule.
- Edit an existing portals policy rule.
- Delete a portals policy rule.
- Depending on your PRA subscriptions, you will see the following [privileged policy](/zpa/about-privileged-policy) options:
- [Consoles Policy](/zpa/about-privileged-capabilities-policy)
- [Privileged Credentials Policy](/zpa/about-privileged-credentials-policy)
- Depending on your ZPA Admin Portal subscriptions, you will see the following ZPA policy options:
- [Access Policy](/zpa/about-access-policy)
- [Timeout Policy](/zpa/about-timeout-policy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Security Policy](/zpa/about-security-policy)
- [Redirection Policy](/zpa/about-redirection-policy)
![Portals Policy page within the ZPA Admin Portal](/downloads/zpa/policies/privileged-remote-access-policy/about-portals-policy/Updated%20existing%20portals%20policy%20page_0.png)