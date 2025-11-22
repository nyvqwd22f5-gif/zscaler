# About Client Forwarding Policy
Source: https://help.zscaler.com/unified/about-client-forwarding-policy
PDF: https://help.zscaler.com/pdf/com/en/1494876.pdf

Using the client forwarding policy, you can create rules that define when application requests are forwarded to Private Applications from Zscaler Client Connector. For a complete list of ranges and limitations for client forwarding policy rules, see [Ranges & Limitations](/unified/ranges-limitations#private-applications).
Client forwarding policy rules provide the following benefits and enable you to:
- Route specific private application traffic through Private Applications.
- Bypass traffic for specific applications if an exception is required (e.g., VoIP).
- Bypass traffic on trusted networks if an exception is required (e.g., campus users).
A client forwarding policy evaluates rules using the most specific application segment and a top-down, first-match principle. This process occurs before the access policy rules are evaluated. When a match is found in the client forwarding policy, other policy rules are disregarded, including conflicts.
About the Client Forwarding Policy Page
On the Client Forwarding Policy page (Infrastructure > Private Access > Client Forwarding Policies > Client Forwarding Policies), you can do the following:
- [Add a new client forwarding policy rule.](/unified/configuring-client-forwarding-policies)
- Click the **Menu **icon. In the menu, you can do the following:
- Expand all of the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI displays the first 100 rules. Alternatively, you can scroll to see more rules.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all client forwarding policy rules that were configured. For each rule, you can see the following:
- **Rule Order**: The policy evaluation order number for the rule. Policy rules are applied based on the order they are listed here. Change the rule order by clicking on the number and manually entering in a new value.
- **Name**: The name of the rule. When the row is expanded, the description is also displayed here, if available.
- **Rule Action**: Indicates if the rule will **Bypass ZPA**, **Only Forward Allowed Applications**, or **Forward to ZPA**. When the row is expanded, it provides a visual representation of the **Criteria** (e.g., [SAML attributes](/unified/about-saml-attributes), application segments, trusted networks, etc.) and Boolean logic used within the rule.
- Copy an existing client forwarding policy rule's criteria, and use it to create a new rule.
- [Edit an existing client forwarding policy rule.](/unified/editing-client-forwarding-policies)
- Delete a client forwarding policy rule.
![Viewing and managing client forwarding policies on the Client Forwarding Policy page](/downloads/unified/networking/private-applications/client-connector-policies/client-forwarding-policy/about-client-forwarding-policy/unified-client-forwarding-policy-page.png)