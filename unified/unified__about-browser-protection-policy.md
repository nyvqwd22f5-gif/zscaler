# About Browser Protection Policy
Source: https://help.zscaler.com/unified/about-browser-protection-policy
PDF: https://help.zscaler.com/pdf/com/en/1493691.pdf

Browser Protection policy rules allow you to set up Browser Protection for designated browsers and operating systems. For a complete list of ranges and limitations for Browser Protection Policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
After you have created a [browser protection profile](/unified/about-browser-protection-profiles), you can set the parameters for the related browsers and operating systems assigned to it. You can set a rule to monitor uses for selected applications and SAML and SCIM attributes.
Browser Protection policies enhance your experience by enabling you to:
- Create a policy to monitor and fingerprint user browser access sessions based on specific criteria (Application segments and SAML and SCIM attributes).
- Apply a previously created Browser Protection profile to a policy with the unique attributes that are used to create a fingerprint.
Browser Protection Policy rules are comprised of two main building blocks:
- Criteria: These are the conditions of a policy rule. A user's application request must match all the conditions within a policy rule.
- Boolean Operators: These are the operands used between criteria. Browser Protection policy rules use AND and OR operators.
Cloud Browser Isolation is not supported with Browser Protection.
About the Browser Protection Policy Page
On the Browser Protection Policy page (Policies > Cybersecurity > Inline Security > Protection Policies), you can do the following:
- Go to the [AppProtection Policy](/unified/about-appprotection-policy) page to add a new AppProtection policy or manage existing policies.
- Expand all of the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI displays the first 100 rules. Alternatively, you can scroll to see more rules.
- [Add a new Browser Protection policy rule.](/unified/configuring-browser-protection-policies)
- Select a **Browser Protection Profile** under **General Profile Settings** to view the Browser Protection policies associated with that specific Browser Protection profile. After you have selected a Browser Protection profile, click **Confirm** and the table below populates the Browser Protection policies related to that specific Browser Profile.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all Browser Protection policy rules that were configured. For each rule, you can see:
- **Rule Order**: The policy evaluation order number for the rule. Policy rules are applied based on the order they are listed here. Change the rule order by clicking on the number and manually entering in a new value.
- **Name**: The name of the rule. The description is also displayed here, if available.
- **Rule Action**: Indicates if the rule is Allow Access or Block Access. When the row is expanded, it provides a visual representation of the Criteria (e.g., SAML attributes, application segments, posture profiles, etc.) and Boolean logic used within the rule.
- Copy an existing Browser Protection policy rule's criteria, and use it to create a new rule.
- [Edit an existing Browser Protection policy rule.](/unified/editing-browser-protection-policies)
- Delete a Browser Protection policy rule.
![unified-browser-protection-policy-page.png](/downloads/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-policy/about-browser-protection-policy/unified-browser-protection-policy-page.png)