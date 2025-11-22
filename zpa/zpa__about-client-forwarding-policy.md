# About Client Forwarding Policy
Source: https://help.zscaler.com/zpa/about-client-forwarding-policy
PDF: https://help.zscaler.com/pdf/com/en/1484376.pdf

Using the client forwarding policy, you can create rules that define when application requests are forwarded to ZPA from Zscaler Client Connector. For a complete list of ranges and limitations for client forwarding policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
Client forwarding policy rules provide the following benefits and enable you to:
- Route specific private application traffic through ZPA.
- Bypass traffic from ZPA for specific applications if an exception is required (e.g., VoIP).
- Bypass traffic from ZPA on trusted networks if an exception is required (e.g., campus users).
ZPA evaluates client forwarding policy rules using the most specific application segment and a top-down, first-match principle. This process occurs before ZPA evaluates access policy rules. When a match is found in the client forwarding policy, ZPA disregards other policy rules, including conflicts. To learn more, see [Policy Evaluation Order](/zpa/about-policies#PolicyEvalOrder).
[]Using the Default Client Forwarding Policy Rule
ZPA provides a default client forwarding policy rule. The default rule specifies that all application requests to application segments from clients are forwarded to ZPA. You can edit the default rule, and it will always apply to the criteria you specify if you do not configure your own client forwarding policy rules. If you've configured additional client forwarding policies that apply to a specific application, the default rule still applies to all other applications for which there are application segments created.
To edit the default rule:
- Go to **Policies > Client Forwarding Policy**.
- Click **Default Rule**. The **Default Rule** drawer appears.
- Click the **Edit** icon. The **Edit Client Forwarding Policy** window appears.
- Edit the default rule, and then click **Save**.
[See image.](#default-rule-image)
About the Client Forwarding Policy Page
On the Client Forwarding Policy page (Policy > Client Forwarding Policy), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Client Forwarding Policy page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new client forwarding policy rule.](/zpa/configuring-client-forwarding-policies)
- Edit the default rule. To learn more, see [Using the Default Client Forwarding Policy Rule](#default-rule).
- Expand all the displayed rows in the table to see more information about each policy rule.
- View a list of all client forwarding policy rules that were configured. For each rule, you can see the following:
- **Rule Order**: The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed. Change the rule order by clicking on the number and manually entering in a new value.
- **Name**: The name of the rule. When the row is expanded, the description is also displayed here, if available.
- **Status**: Indicates if the rule is enabled or disabled.
- **Rule Action**: Indicates if the rule will **Bypass ZPA**, **Only Forward Allowed Applications**, or **Forward to ZPA**. When the row is expanded, it provides a visual representation of the criteria (e.g., [SAML attributes](/zpa/about-saml-attributes), application segments, trusted networks, etc.) and Boolean logic used within the rule.
- [Modify the columns displayed in the table](/zpa/using-tables).
- Copy an existing client forwarding policy rule's criteria, and use it to create a new rule.
- [Edit an existing client forwarding policy rule.](/zpa/editing-client-forwarding-policies)
- Delete a client forwarding policy rule.
- Display more rows or a different page of the table.
- Depending on your ZPA Admin Portal subscriptions, you will see the following ZPA policy options:
- [Access Policy](/zpa/about-access-policy)
- [Timeout Policy](/zpa/about-timeout-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Privileged Policy](/zpa/about-privileged-policy)
- [Security Policy](/zpa/about-security-policy)
- [Redirection Policy](/zpa/about-redirection-policy)
![Viewing and managing bypass policies within the ZPA Admin Portal](/downloads/zpa/access-timeout-policies/client-forwarding-policy/about-client-forwarding-policy/client-forwarding-policy-page-w-steps.png)
[]![Image of Default Client Forwarding Policy Rule](/downloads/zpa/access-timeout-policies/client-forwarding-policy/about-client-forwarding-policy/client-forwarding-policy-default-rule.png)