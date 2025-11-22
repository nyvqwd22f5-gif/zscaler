# About Redirection Policy
Source: https://help.zscaler.com/unified/about-redirection-policy
PDF: https://help.zscaler.com/pdf/com/en/1494891.pdf

Redirection policy rules allow you to set criteria for preferring Private Service Edges for Private Applications over Public Service Edges for Private Applications. You can configure redirection policy rules to prefer Private Service Edges for Private Applications based on country code, client type, and SAML and SCIM attributes. You can specify the method used (Default, Preferred, or Always) for selecting Private Service Edge for Private Applications groups to redirect to. For a complete list of ranges and limitations for redirection policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
Redirection policy rules provide the following benefits and enable you to:
-
Prefer Private Service Edges for Private Applications over public brokers.
-
Control usage of Private Service Edges for Private Applications based on criteria set in the redirection policy rules.
About the Redirection Policy Page
On the Redirection Policy page (Infrastructure > Private Access > Client Forwarding Policies > Redirection Policy), you can do the following:
- [Add a new redirection policy rule](/unified/configuring-redirection-policies).
- Click the **Menu **icon. In the menu, you can do the following:
- Expand all the displayed rows in the table to see more information about each policy rule.
- Show all rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI only displays the first 100 rules. Alternatively, you can scroll to see more rules.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all redirection policy rules that were configured. For each rule, you can see:
- **Rule Order **The policy evaluation order number for the rule. Policy rules are applied based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
- **Name**: The name of the rule. When the row is expanded, the description is also displayed here, if available.
- **Private Service Edge Selection Method**: Indicates the selection method the rule uses when selecting Private Service Edges for Private Applications:
- **Default**: Use the current Service Edge for Private Applications selection algorithm.
- **Preferred**: Redirect users to the selected Private Service Edge groups for Private Applications if available, with Public Service Edges for Private Applications as a fallback.
- **Always**: Always redirect users to the selected Private Service Edge groups for Private Applications if available and prevent the use of Public Service Edges for Private Applications. If there are no active Private Service Edges for Private Applications available in the selected Private Service Edge groups for Private Applications, then users are redirected to a Public Service Edge for Private Applications.
- **Actions**: Click icon to copy, edit, or delete a redirection rule.
- Copy an existing redirection policy rule's criteria, and use it to create a new rule.
- [Edit an existing redirection policy rule](/unified/editing-redirection-policies).
-
Delete a redirection policy rule.
Redirection policy rules that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
![Viewing and managing redirection policy rules within the Redirection Policy page](/downloads/unified/networking/private-applications/client-connector-policies/redirection-policy/about-redirection-policy/unified-redirection-policy-page.png)