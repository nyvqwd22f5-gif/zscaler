# About AppProtection Policy
Source: https://help.zscaler.com/unified/about-appprotection-policy
PDF: https://help.zscaler.com/pdf/com/en/1493711.pdf

AppProtection policy rules allow you to set up AppProtection controls for web applications. For a complete list of ranges and limitations for AppProtection Policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
AppProtection policies work similarly to access policies. You can reuse an existing access policy's criteria to [create an AppProtection policy](/unified/configuring-appprotection-policies). This allows you to match up your AppProtection policies to your access policies. To learn more, see [About Access Policy](/unified/about-access-policy).
AppProtection policy rules enhance your experience by enabling you to:
- Create a policy to inspect traffic to internal web applications based on specific criteria (e.g., application segments, Client Connector posture profiles, and SAML and SCIM attributes).
- Apply a previously created AppProtection profile to a policy with the default actions (Allow, Block, or Redirect) set for each related AppProtection control.
AppProtection policy rules are comprised of two main building blocks:
- Criteria: These are the conditions of a policy rule. A user's application request must match all the conditions within a policy rule.
- Boolean Operators: These are the operands used between criteria. AppProtection policy rules use AND and OR operators.
About the AppProtection Policy Page
On the AppProtection Policy page (Policies > Cybersecurity > Inline Security > Protection Policies), you can do the following:
- Go to the [Browser Protection Policy](/unified/about-browser-protection-policy) page to add a new Browser Protection policy or manage existing policies.
- [Add a dynamic rule](/unified/configuring-appprotection-dynamic-rules) to an AppProtection profile.
- Expand all of the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI displays the first 100 rules. Alternatively, you can scroll to see more rules.
- [Add a new AppProtection policy rule](/unified/configuring-appprotection-policies).
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all AppProtection policy rules that were configured. For each rule, you can see:
- **Rule Order:** The policy evaluation order number for the rule. Policy rules are applied based on the order they are listed here. Change the rule order by clicking on the number and manually entering in a new value.
- **Name:** The name of the rule. The description is also displayed here, if available.
- **Rule Action:** Indicates if the rule is Allow Access or Block Access. When the row is expanded, it provides a visual representation of the Criteria (e.g., SAML attributes, application segments, posture profiles, etc.) and Boolean logic used within the rule.
- Copy an existing AppProtection policy rule's criteria, and use it to create a new rule.
- [Edit an existing AppProtection policy rule](/unified/editing-appprotection-policies).
- Delete an AppProtection policy rule.
![Viewing and managing AppProtection policies on the AppProtection page](/downloads/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-policy/about-appprotection-policy/unified-appprotection-policy-page.png)