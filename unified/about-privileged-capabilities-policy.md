# About Privileged Capabilities Policy
Source: https://help.zscaler.com/unified/about-privileged-capabilities-policy
PDF: https://help.zscaler.com/pdf/com/en/1493871.pdf

Privileged capabilities policy rules allow you to designate privileged consoles with the ability to upload or download Internet & SaaS Sandbox files. After you have completed the [Sandbox integration settings](/unified/configuring-sandbox-integrations) for Internet & SaaS, you can then inspect files that are being uploaded. Privileged capabilities policies also allow you to use the [Clipboard functions (Copy and Paste)](/unified/copying-and-pasting-clipboard), [record privileged sessions (Join, Record, and Share), and configure live privileged sessions (join, share, control, and monitor)](/unified/accessing-privileged-sessions).
Privileged capabilities policy rules include the following benefits and enable you to:
- Manage the permissions that provide the ability to upload and download files.
- Set permissions to allow the inspection of sandbox files from Internet & SaaS during the upload process.
- Share, record, and provide functional abilities for privileged sessions.
If you want to configure privileged capabilities-based control, you must first create the [privileged portals](/unified/about-privileged-portals) and [privileged consoles](/unified/about-privileged-consoles) that you want to assign control to.
About the Privileged Capabilities Policy Page
On the Privileged Capabilities Policy page (Policies > Access Control > Clientless > Privileged Policy), you can do the following:
- Go to the [Privileged Credentials Policy](/unified/about-privileged-credentials-policy) page to add a new privileged credentials policy or manage existing policies.
- Expand all the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI only displays the first 100 rules. Alternatively, you can scroll to see more rules. If there are more than 1,000 rules, the Display All Rules button is not visible.
- [Add a new privileged capabilities policy rule.](/unified/configuring-privileged-capabilities-policies)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all privileged capabilities policy rules that were configured. For each rule, you can see:
- **Rule Order**: The policy evaluation order number for the rule. Policy rules are applied based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
- **Name**: The name of the rule. The description is also displayed here, if available.
- **Privileged Capabilities**: The privileged capabilities you have set for that specific policy rule, either **Enable** or **Disable** with the options:
- **Clipboard Copy**
- **Clipboard Paste**
- **Download**
- **Inspect Upload**
- **Join Sessions**
- **Record Sessions**
- **Share Sessions**
- **Upload**
- Copy an existing privileged capabilities policy rule's criteria, and use it to create a new rule.
- Edit an existing privileged capabilities policy rule.
- Delete a privileged capabilities policy rule.
![Viewing and managing Privileged Capabilities policies within the Admin Portal](/downloads/unified/policies/private-applications/access-control/clientless/privileged-remote-access-policy/about-privileged-capabilities-policy/unified-privileged-capabilities-policy-page.png)