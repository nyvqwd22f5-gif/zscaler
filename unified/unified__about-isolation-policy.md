# About Isolation Policy
Source: https://help.zscaler.com/unified/about-isolation-policy
PDF: https://help.zscaler.com/pdf/com/en/1492636.pdf

Using the isolation policy, you can create rules that define when application requests are redirected to [What Is Isolation?](/unified/what-isolation) This requires having Isolation enabled for your organization and creating an [Isolation profile](/unified/creating-isolation-profiles-private-applications) prior to setting up the isolation policy rule.
Isolation policy rules allow you to:
- Define policies to provide secure clientless access to critical applications via a containerized isolated browser on the Zscaler cloud, ensuring the posture of a user's machine doesn't affect the related applications.
- Reduce the surface area of attacks by providing true application-level zero trust access to critical applications (e.g., hiding all application-level transactions between the browser and the related applications).
- Enforce data exfiltration controls by ensuring users are unable to copy, paste, upload, or download files between their computers and the applications they are accessing.
When the user is authenticated, the session timeout value is the minimum timeout across all [timeout policies](/unified/about-timeout-policy) configured. After the timeout happens, the user needs to reauthenticate with Private Applications to access applications via Isolation.
Along with [defining an isolation policy](/unified/configuring-isolation-policies), you also need to [define an access policy](/unified/configuring-access-policies) for the application to be accessible from within the browser isolation environment. Application requests not directed to Isolation are reviewed based on [access policies](/unified/about-access-policy).
If you are undergoing a maintenance period, Isolation might not be available.
Isolation policy rules are comprised of two main building blocks:
- Criteria: These are the conditions of a policy rule. A user's application request must match all of the conditions within a policy rule.
- Boolean Operators: These are the operands used between criteria. Isolation policy rules use AND and OR operators only.
About the Isolation Policy Page
On the Isolation Policy page (Policies > Access Control > Clientless > Isolation Policy), you can do the following:
- [Add new isolation policy rules.](/unified/configuring-isolation-policies)
- Click the **Menu **icon. Within the menu, you can do the following:
- Expand all of the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI only displays the first 100 rules. Alternatively, you can scroll to see more rules.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all isolation policy rules that were configured.
- Copy an existing isolation policy rule's criteria, and use it to create a new rule.
- [Edit an existing edit policy rule.](/unified/editing-isolation-policies)
- Delete an isolation policy rule.
- Review the **Default Rule**. This rule is not editable.
![Viewing and managing isolation policies within the Isolation Policy page](/downloads/unified/policies/private-applications/access-control/clientless/isolation-policy/about-isolation-policy/unified-isolation-policy-page.png)