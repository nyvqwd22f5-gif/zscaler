# About AppProtection Policy
Source: https://help.zscaler.com/zpa/about-appprotection-policy
PDF: https://help.zscaler.com/pdf/com/en/1484926.pdf

AppProtection policy rules allow you to set up AppProtection controls for ZPA web applications. For a complete list of ranges and limitations for AppProtection Policy rules, see [Ranges & Limitations](/zpa/ranges-limitations).
AppProtection policies work similarly to access policies. You can reuse an existing access policy's criteria to [create an AppProtection policy](/zpa/configuring-inspection-policies). This allows you to match up your AppProtection policies to your access policies. To learn more, see [About Access Policy](/zpa/about-access-policy).
AppProtection policy rules enhance your experience by enabling you to:
- Create a policy to inspect traffic to internal web applications based on specific criteria (e.g., application segments, Client Connector posture profiles, and SAML and SCIM attributes).
- Apply a previously created AppProtection profile to a policy with the default actions (Allow, Block, or Redirect) set for each related AppProtection control.
AppProtection policy rules are comprised of two main building blocks:
- Criteria: These are the conditions of a policy rule. A user's application request must match all the conditions within a policy rule.
- Boolean Operators: These are the operands used between criteria. AppProtection policy rules use AND and OR operators.
About the AppProtection Policy Page
On the AppProtection Policy page (Policy > AppProtection Policy), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the AppProtection Policy page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new AppProtection policy rule.](/zpa/configuring-appprotection-policies)
- [Add a dynamic rule](/zpa/configuring-appprotection-dynamic-rules) to an AppProtection profile.
- Expand all of the displayed rows in the table to see more information about each policy rule.
- View a list of all AppProtection policy rules that were configured. For each rule, you can see:
- **Rule Order:** The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed here. Change the rule order by clicking on the number and manually entering in a new value.
- **Name:** The name of the rule. The description is also displayed, if available.
- **Status**: The status of the rule, either Enabled or Disabled.
- **Rule Action:** Indicates if the rule is to **Inspect** or **Bypass Inspection**. When the row is expanded, it provides a visual representation of the **Criteria** (e.g., [SAML attributes](/zpa/about-saml-attributes), application segments, posture profiles, etc.) and Boolean logic used within the rule.
- Copy an existing AppProtection policy rule's criteria, and use it to create a new rule.
- [Edit an existing AppProtection policy rule](/zpa/editing-appprotection-policies).
- Delete an AppProtection policy rule.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Depending on your AppProtection subscription, you see the following Security policy option: [Browser Protection](/zpa/about-browser-protection-policy).
- Depending on your ZPA Admin Portal subscriptions, see the following ZPA policy options:
- [Access Policy](/zpa/about-access-policy)
- [Timeout Policy](/zpa/about-timeout-policy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Privileged Policy](/zpa/about-privileged-policy)
- [Redirection Policy](/zpa/about-redirection-policy)
![AppProtection Policy page in the ZPA Admin Portal](/downloads/zpa/policies/appprotection-private-application-traffic-policy-formerly-inspection/about-appprotection-policy/Full%20page%20w%20steps_0.png)