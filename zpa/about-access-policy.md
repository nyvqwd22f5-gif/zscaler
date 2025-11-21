# About Access Policy
Source: https://help.zscaler.com/zsdk/about-access-policy
PDF: https://help.zscaler.com/pdf/com/en/1509881.pdf

Access policy rules enable you to implement security-based access control for your applications. To configure an access policy rule, you must define which applications or segment groups the client groups can access.
Access policy rules provide the following benefits and enable you to:
-
Implement security-based access control for your application segments or segment groups.
-
Use additional criteria to restrict access based on client types.
If you want to configure application-based access control, you must create an access policy rule for specific application segments or segment groups. When you need to apply different policies to individual applications, create an access policy rule that includes one or more application segments. However, if you want all applications that need a similar level of access across those applications, create an access policy rule that includes one or more segment groups.
[]Access policy rules comprise two main building blocks:
- [Criteria](#criteriacondition)
- [Boolean Operators](#booleanoperands)
To view examples of how an organization can configure access policy rules for a variety of scenarios, see [Access Policy Configuration Examples](/zpa/access-policy-configuration-examples).
About the Access Policy Page
On the Access Policy page (Policy > Access Policy), you can do the following:
- [Add a new access policy rule](/zsdk/managing-access-policies).
- [Expand rows in the table.](#expand)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all access policy rules that were configured. For each rule, you can see:
-
**Rule Order**: The [policy evaluation order](/zpa/about-policies#PolicyEvalOrder) number for the rule. ZSDK applies policy rules based on the order they are listed here. Change the rule order by clicking the number and manually entering a new value.
[See image.](#img_ruleorder)
- **Name**: The name of the rule. The description is also displayed here, if available.
- **Rule Action**: The rule action is either **Allow Access**, **Block Access**, or **Require Approval**. When the row is expanded, it provides a visual representation of the **Criteria** and Boolean logic used within the rule.
- [Copy an existing access policy rule's criteria.](/zsdk/managing-access-policies)
- [Edit an existing access policy rule](/zsdk/managing-access-policies).
- [Delete an access policy rule.](/zsdk/managing-access-policies)
![Configure access policies on the Access Policy page](/downloads/zsdk/policies/about-access-policy/ZSDK-Access-Policy-Page-Closed-Overview_1.png)
[]You can expand the rows in the table to view access policy details in three different ways.
In the **Column Menu**, you can:
- **Expand Displayed Rules**: Expand all the displayed rows in the table to see more information about each policy rule.
- **Display All Rules**: Show all the rules on the table. The rows remain collapsed.
Depending on the number of rules, this can take a few minutes. By default, the UI only displays the first 100 rules. Alternatively, you can scroll to see more rules. If there are more than 1,000 rules, the **Display All Rules** button is not visible.
[See image.](#img_columnmenu)
Lastly, if you want to select a single row, you can click the respective row's **Expand** icon.
[See image.](#img_expand_1row)
[]
![Access Policy Column Menu](/downloads/zsdk/policies/about-access-policy/ZSDK-Access-Policy-Page-Expand-Menu-1.png)
[]
![Edit the Rule Order](/downloads/zsdk/policies/about-access-policy/ZSDK-Access-Policy-Page-RuleOrder-1.png)
[]![Application Segment Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample1.png)
[]![Segment Group Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample2.png)
[]![Shows Boolean OR Example of Application Segments with Segment Groups](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample3.png)
[]These are the conditions of a policy rule. A user's application request must match all the conditions within a policy rule.
You can apply any of the following criteria to a policy rule:
- Applications: A grouping of defined applications based upon access type or user privileges. To learn more, see [About Applications](/zsdk/about-applications).
- Client Types: The available client types are Prelogin Tunnel and Zero Trust Tunnel. To learn more, see [Managing Access Policies](/zsdk/managing-access-policies#client).
- Country Code: A grouping of country codes based upon where your users are accessing your mobile applications. To learn more, see [Managing Access Policies](/zsdk/managing-access-policies#country).
- Device Profiles: A grouping of defined device profiles to apply a set of criteria for evaluation. To learn more, see [About Device Profile](/zsdk/about-device-profile).
[]These are the operators used between criteria. Access policy rules use AND and OR operators only.
ZSDK uses an implicit OR Boolean operator between multiple application segments. For example, the following access policy rule includes three application segments. So, ZSDK evaluates this application segment criteria as "Sales Tools OR QA Application OR All Other Services."
[See image.](#appsegex)
Similar to application segments, ZSDK uses an implicit OR Boolean operator between multiple segment groups. For example, the following policy rule includes three segment groups. So, ZSDK evaluates the segment group criteria as "AD-Servers OR Web Services Group OR Azure Application Group."
[See image.](#sgmntgrpex)
ZSDK uses an explicit OR Boolean operator between application segment and segment group criteria. So, when a user requests access to an application, the policy rule is evaluated to check whether an application segment OR its segment group is present. For example, the following policy rule includes three application segments and three segment groups:
[See image.](#appsegsgmntgrpex)
[]
![Expand one row](/downloads/zsdk/about-access-policy/ZSDK-Access-Policy-Expand.png)