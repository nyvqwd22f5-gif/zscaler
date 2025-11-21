# About Browser Protection Policy
Source: https://help.zscaler.com/zpa/about-browser-protection-policy
PDF: https://help.zscaler.com/pdf/com/en/1485636.pdf

Browser Protection policy rules allow you to set up Browser Protection for designated browsers and operating systems. For a complete list of ranges and limitations for Browser Protection policy rules, see [Ranges & Limitations](/zpa/ranges-limitations).
After you have created a [browser protection profile](/zpa/about-browser-protection-profiles), you can set the parameters for the related browsers and operating systems assigned to it. You can set a rule to monitor uses for selected applications and SAML and SCIM attributes.
Browser Protection policies enhance your ZPA experience by enabling you to:
- Create a policy to monitor and fingerprint user browser access sessions based on specific criteria (application segments and SAML and SCIM attributes).
- Apply a previously created Browser Protection profile to a policy with the unique attributes that are used to create a fingerprint.
Browser Protection policy rules are comprised of two main building blocks:
- Criteria: These are the conditions of a policy rule. A user's application request must match all the conditions within a policy rule.
- Boolean Operators: These are the operands used between criteria. Browser Protection policy rules use AND and OR operators.
Browser Protection is not supported with Isolation.
About the Browser Protection Policy Page
On the Browser Protection Policy page (Policy > Security Policy > Browser Protection), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Browser Protection Policy page to reflect the most current information.
- Select a Browser Protection profile under **General Profile Settings** to view the Browser Protection policies associated with that specific profile. After you have selected a Browser Protection profile, click **Confirm** and the table populates the Browser Protection policies related to that specific profile.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new Browser Protection policy rule.](/zpa/configuring-browser-protection-policies)
- Expand all of the displayed rows in the table to see more information about each policy rule.
- View a list of all Browser Protection policy rules that were configured. For each rule, you can see:
- **Rule Order**: The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed here. Change the rule order by clicking on the number and manually entering in a new value.
- **Name**: The name of the rule. The description is also displayed, if available.
- **Status**: The status of the rule, either **Enabled** or **Disabled**.
- **Rule Action**: Indicates if the rule is **Monitor** or **Do Not Monitor**. When the row is expanded, it provides a visual representation of the **Criteria** (e.g., [SAML attributes](/zpa/about-saml-attributes), application segments, posture profiles, etc.) and Boolean logic used within the rule.
- Copy an existing Browser Protection policy rule's criteria, and use it to create a new rule.
- [Edit an existing Browser Protection policy rule.](/zpa/editing-browser-session-policies)
- Delete a Browser Protection policy rule.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Depending on your AppProtection subscription, you see the following AppProtection policy option: [AppProtection Policy](/zpa/about-appprotection-policy).
- Depending on your ZPA Admin Portal subscriptions, you see the following ZPA policy options:
- [Access Policy](/zpa/about-access-policy)
- [Timeout Policy](/zpa/about-timeout-policy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [Privileged Policy](/zpa/about-privileged-policy)
- [Redirection Policy](/zpa/about-redirection-policy)
![Browser Protection Policy page in the ZPA Admin Portal](/downloads/zpa/policies/appprotection-private-application-traffic-policy-formerly-inspection/about-browser-protection-policy/Updated%20page%20w%20steps_0.png)