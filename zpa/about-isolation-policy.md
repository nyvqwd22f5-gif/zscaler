# About Isolation Policy
Source: https://help.zscaler.com/zpa/about-isolation-policy
PDF: https://help.zscaler.com/pdf/com/en/1484881.pdf

Using the isolation policy, you can create rules that define when application requests are redirected to [Cloud Browser Isolation](/zia/about-cloud-browser-isolation). This requires having Cloud Browser Isolation enabled for your organization and creating a [Cloud Browser Isolation profile](/zia/creating-zpa-isolation-profile-cloud-browser-isolation) prior to setting up the isolation policy rule.
Isolation policy rules allow you to:
- Define policies to provide secure clientless access to critical applications via a containerized isolated browser on the Zscaler cloud, ensuring the posture of a user's machine doesn't affect the related applications.
- Reduce the surface area of attacks by providing true application-level zero trust access to critical applications (e.g., hiding all application-level transactions between the browser and the related applications).
- Enforce data exfiltration controls by ensuring users are unable to copy, paste, upload, or download files between their computers and the applications they are accessing.
When the user is authenticated, the session timeout value is the minimum timeout across all [timeout policies](/zpa/about-timeout-policy) configured. After the timeout happens, the user needs to reauthenticate with ZPA to access applications via Cloud Browser Isolation.
Along with [defining an isolation policy](/zpa/configuring-isolation-policies), you also need to [define an access policy](/zpa/configuring-access-policies) for the application to be accessible from within the browser isolation environment. Application requests not directed to Cloud Browser Isolation are reviewed based on [access policies](/zpa/about-access-policy).
If ZPA is undergoing a maintenance period, Cloud Browser Isolation might not be available.
Isolation policy rules are comprised of two main building blocks:
- Criteria: These are the conditions of a policy rule. A user's application request must match all of the conditions within a policy rule.
- Boolean Operators: These are the operands used between criteria. Isolation policy rules use AND and OR operators only.
About the Isolation Policy Page
On the Isolation Policy page (Policy > Isolation Policy), you can do the following:
- Expand all of the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI only displays the first 100 rules. Alternatively, you can scroll to see more rules.
- [Add new isolation policy rules.](/zpa/configuring-isolation-policies)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all isolation policy rules that were configured.
- Copy an existing isolation policy rule's criteria, and use it to create a new rule.
- [Edit an existing edit policy rule.](/zpa/editing-isolation-policies)
- Delete an isolation policy rule.
- Review the **Default Rule**. This rule is not editable.
- Go to the [Access Policy](/zpa/about-access-policy) page to add a new access policy or manage existing policies.
- Go to the [Timeout Policy](/zpa/about-timeout-policy) page to add a new timeout policy or manage existing policies.
- Go to the [Client Forwarding Policy](/zpa/about-client-forwarding-policy) page to add a new client forwarding policy or manage existing policies.
- Go to the [Privileged Policy](/zpa/about-privileged-policy) page to add new [privileged capabilities policies](/zpa/about-privileged-capabilities-policy) and [privileged credentials policies](/zpa/about-privileged-credentials-policy) or manage existing policies.
- Go to the Security Policy page to add new [AppProtection Policies](/zpa/about-appprotection-policy) and [Browser Protection Policies](/zpa/about-browser-protection-policy) or to manage existing policies.
![Viewing and managing isolation policies within the ZPA Admin Portal](/downloads/zpa/access-timeout-policies/isolation-policy/about-isolation-policy/Isolation%20policy%20w%20steps_0.png)