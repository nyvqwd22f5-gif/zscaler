# About Access Policy
Source: https://help.zscaler.com/unified/about-access-policy
PDF: https://help.zscaler.com/pdf/com/en/1492046.pdf

Access policy rules enable you to implement role-based access control. To configure an access policy rule, you must first define the users and then define which applications or segment groups they can access. For example, you would specify the users first (i.e., SalesStaff), then specify which application segments or segment groups they can access (i.e., Sales App and Intranet Group). For a complete list of ranges and limitations for access policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
Access policy rules provide the following benefits and enable you to:
-
Implement role-based access control to your application segments or segment groups.
-
Use additional criteria to restrict access based on device posture profile conditions, trusted networks, client types, Cloud Connector Groups, Machine Groups, and SAML or SCIM attributes.
If you want to configure application-based access control, you must create an access policy rule for specific application segments or segment groups. When you need to apply different policies to individual applications, create an access policy rule that includes one or more application segments. However, if you want all applications within a group of users who need a similar level of access across those applications, create an access policy rule that includes one or more segment groups.
Access policy rules are evaluated using the most specific application segment and a top-down, first-match principle. To learn more, see [Policy Evaluation Order](/unified/about-policies).
[]Access Policy rules are comprised of two main building blocks:
- [Criteria](#criteriacondition)
- [Boolean Operators](#booleanoperands)
To view examples of how an organization can configure access policy rules for a variety of scenarios, see [Access Policy Configuration Examples](/unified/access-policy-configuration-examples).
About the Access Policy Page
On the Access Policy page (Policies > Access Control > Private Applications > Access Policy), you can do the following:
- Expand all the displayed rows in the table to see more information about each policy rule.
- Show all the rules in the table. The rows remain collapsed. Depending on the number of rules, this can take a few minutes.
By default, the UI only displays the first 100 rules. Alternatively, you can scroll to see more rules. If there are more than 1,000 rules, the **Display All Rules** button is not visible.
- [Add a new access policy rule](/unified/about-access-policy).
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all access policy rules that were configured. For each rule, you can see:
- **Rule Order**: The [policy evaluation order](/unified/about-policies) number for the rule. Policy rules are applied based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
Updating the rule order of an access policy configured using Zscaler Deception is not supported. When changing the rule order of a regular access policy and there is an access policy configured using Deception, the rule order of the regular access policy must be greater than the rule order for an access policy configured using Deception.
- **Name**: The name of the rule. The description is also displayed here, if available.
- **Rule Action**: Indicates if the rule will **Allow Access**, **Block Access**, or **Require Approval**. When the row is expanded, it provides a visual representation of the **Criteria** (e.g., [SAML attributes](/unified/about-saml-attributes), application segments, [posture profiles](/unified/configuring-device-posture-profiles), etc.) and Boolean logic used within the rule.
- Copy an existing access policy rule's criteria, and use it to create a new rule.
- [Edit an existing access policy rule](/unified/about-access-policy).
- Delete an access policy rule.
If an access policy is configured using Deception, the copy, edit, and delete options are unavailable.
[See image.](#DeceptionAccessPolicy)
![Viewing and managing access policies within the ZPA Admin Portal](/downloads/unified/policies/private-applications/access-control/access-policy/about-access-policy/about-access-policies.png)
[]![Application Segment Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample1.png)
[]![Segment Group Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample2.png)
[]![Application Segments and Segment Groups Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample3.png)
[]![Additional Criteria Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample4.png)
[]![Deception access policy](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-deception-integration-accessPolicies.png)
[]These are the conditions of a policy rule. A user's application request must match all of the conditions within a policy rule.
You can apply any of the following criteria to a policy rule:
- Application Segments: A grouping of defined applications based upon access type or user privileges. To learn more, see [About Defined Application Segments](/unified/about-defined-application-segments).
- Branch Connector Groups: The group of Branch Connectors to which the policy applies. To learn more, see [About Branch Connector Groups](/unified/about-branch-connector-groups).
- Chrome Enterprise Browser: Verify if the users are accessing private applications by using the Chrome Enterprise browser. To learn more, see [Configuring Chrome Enterprise Browser Connector Settings](/unified/configuring-chrome-enterprise-browser-connector-settings).
- Client Connector Posture Profiles: Zscaler Client Connector device posture profiles is the set of criteria that a user's device must meet to access applications. To learn more, see [About Device Posture](/unified/about-device-posture-profiles).
- Client Connector Trusted Networks: The type of networks the user is connected to that Zscaler Client Connector can trust. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
- Client Types: The available client types are Zscaler Client Connector, Client Connector Partner, Branch Connector, Cloud Connector, Machine Tunnel, Web Browser, or Service Edge. To learn more, see, [About Branch Connectors](/unified/about-branch-connectors), [About Cloud Connectors](/zpa/about-cloud-connectors), [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels), [About Browser Access](/unified/about-browser-access), and [About Source IP Anchoring](/unified/understanding-source-ip-anchoring).
- Cloud Connector Groups: The group of Cloud Connectors to which the policy applies. To learn more, see [About Cloud Connector Groups](/zpa/about-cloud-connector-groups).
-
Country Codes: The country that a user's IP address is located in.
In the case of Cloud Connectors, Source IP Anchoring traffic, or Private App multi-hop, Private App country criteria policy is applied using the last NATed layer 3 public IP address. For example, SIPA traffic identifies the country based on the Public Service Edge’s public IP address.
- Locations: The Branch Connector, Cloud Connector, or other locations and sub-locations.
- Machine Groups: The group of configured machines. To learn more, see [About Machine Groups](/unified/about-machine-groups).
- Platforms: The user devices to which the policy applies. The available platform types are Windows, macOS, Linux, and Android..
- Risk Scores: User risk scores from a risk source. To learn more, see [About User Risk Scores](/unified/about-user-risk-scores).
- SAML Attributes: User attributes obtained from the SAML assertion from an IdP. To learn more, see [About SAML Attributes](/unified/about-saml-attributes).
- SCIM Attributes: User attributes learned via SCIM from an IdP. To learn more, see [About SCIM](/unified/about-scim).
- SCIM Groups: SCIM groups learned via SCIM from an IdP. To learn more, [About SCIM Groups](/unified/about-scim-groups).
- Segment Groups: The group of configured application segments. To learn more, see [About Segment Groups](/unified/about-segment-groups).
- Workload Groups: The Workload Groups from your cloud workloads. To learn more, see [About Workload Groups](/unified/about-workload-groups).
To learn more, see [Configuring Access Policies](/unified/configuring-access-policies).
[]These are the operands used between [criteria](/unified/about-access-policy). Access Policy rules use AND and OR operators only.
Private Apps use an implicit OR Boolean operator between multiple application segments. For example, the following access policy rule includes three application segments. So, this application segment criteria is evaluated as "Sales Tools OR QA Application OR All Other Services."
[See image.](#appsegex)
Similar to application segments, Private Apps uses an implicit OR Boolean operator between multiple segment groups. For example, the following policy rule includes three segment groups. So, the segment group criteria is evaluated as "AD-Servers OR Web Services Group OR Azure Application Group."
[See image.](#sgmntgrpex)
Private Apps uses an explicit OR Boolean operator between application segment and segment group criteria. So, when a user requests access to an application, the policy rule is evaluated to check if an application segment OR its segment group are present. For example, the following policy rule includes three application segments and three segment groups:
[See image.](#appsegsgmntgrpex)
If additional criteria are included, Private Apps use an explicit AND Boolean operator between them. So, when a user requests access to an application, Private Apps verifies the following criteria and logic:
[See image.](#morecriteriaex)
To learn more about implicit and explicit Boolean operators between and within criteria, see [Configuring Access Policies](/unified/configuring-access-policies).