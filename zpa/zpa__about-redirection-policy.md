# About Redirection Policy
Source: https://help.zscaler.com/zpa/about-redirection-policy
PDF: https://help.zscaler.com/pdf/com/en/1485826.pdf

Redirection policy rules allow you to set criteria for preferring ZPA Private Service Edges over ZPA Public Service Edges. You can configure redirection policy rules to prefer ZPA Private Service Edges based on country code, client type, and SAML and SCIM attributes. You can specify the method used (Default, Preferred, or Always) for selecting ZPA Private Service Edge groups to redirect to. For a complete list of ranges and limitations for redirection policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
Redirection policy rules provide the following benefits and enable you to:
-
Prefer ZPA Private Service Edges over public brokers.
-
Control usage of ZPA Private Service Edges based on criteria set in the redirection policy rules.
About the Redirection Policy Page
On the Redirection Policy page (Policy > Redirection Policy), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Redirection Policy page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new redirection policy rule](/zpa/configuring-redirection-policies).
- Expand all the displayed rows in the table to see more information about each policy rule.
By default, the UI only displays the first 100 rules. Alternatively, you can scroll to see more rules.
- View a list of all redirection policy rules that were configured. For each rule, you can see:
- **Rule Order **The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
- **Name**: The name of the rule. When the row is expanded, the description is also displayed, if available.
- **Private Service Edge Selection Method**: Indicates the selection method the rule uses when selecting ZPA Private Service Edges:
- **Default**: Uses the current ZPA Service Edge selection algorithm.
- **Preferred**: Redirects users to the selected ZPA Private Service Edge groups if available, with ZPA Public Service Edges as a fallback.
- **Always**: Always redirects users to the selected ZPA Private Service Edge groups, if available, and prevents the use of ZPA Public Service Edges. If there are no active ZPA Private Service Edges available in the selected ZPA Private Service Edge groups, then users are redirected to a ZPA Public Service Edge.
- Copy an existing redirection policy rule's criteria, and use it to create a new rule.
- [Edit an existing redirection policy rule](/zpa/editing-redirection-policies).
-
Delete a redirection policy rule.
Redirection policy rules that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Depending on your ZPA Admin Portal subscriptions, you will see the following ZPA policy options:
- [Access Policy](/zpa/about-access-policy)
- [Timeout Policy](/zpa/about-timeout-policy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Privileged Policy](/zpa/about-privileged-policy)
- [Security Policy](/zpa/about-security-policy)
![Viewing and Managing Redirection Policies on the Redirection Policy Page](/downloads/zpa/policies/redirection-policy/about-redirection-policy/zpa-redirection-policy-page_1.png)