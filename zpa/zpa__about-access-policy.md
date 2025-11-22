# About Access Policy
Source: https://help.zscaler.com/zpa/about-access-policy
PDF: https://help.zscaler.com/pdf/com/en/1483656.pdf

Access policy rules enable you to implement role-based access control. To configure an access policy rule, you must first define the users and then define which applications or segment groups they can access. For example, you would specify the users first (i.e., Sales Staff), then specify which application segments or segment groups they can access (i.e., Sales App and Intranet Group). For a complete list of ranges and limitations for access policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
Access policy rules provide the following benefits and enable you to:
-
Implement role-based access control to your application segments or segment groups.
-
Use additional criteria to restrict access based on device posture profile conditions, trusted networks, client types, Cloud Connector groups, machine groups, and SAML or SCIM attributes.
If you want to configure application-based access control, you must create an access policy rule for specific application segments or segment groups. When you need to apply different policies to individual applications, create an access policy rule that includes one or more application segments. However if you want all applications within a group of users who need a similar level of access across those applications, create an access policy rule that includes one or more segment groups.
ZPA evaluates access policy rules using the most specific application segment and a top-down, first-match principle. To learn more, see [Policy Evaluation Order](/zpa/about-policies#PolicyEvalOrder).
[]Access Policy rules are comprised of two main building blocks:
- [Criteria](#criteriacondition)
- [Boolean Operators](#booleanoperands)
To view examples of how an organization can configure access policy rules for a variety of scenarios, see [Access Policy Configuration Examples](/zpa/access-policy-configuration-examples).
About the Access Policy Page
On the Access Policy page (Policy > Access Policy), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- Refresh the Access Policy page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new access policy rule](/zpa/configuring-access-policies).
- Expand all the displayed rows in the table to see more information about each policy rule.
- View a list of all access policy rules that were configured. For each rule, you can see:
-
**Rule Order**: The [policy evaluation order](/zpa/about-access-and-application-group-policies#PolicyEvalOrder) number for the rule. ZPA applies policy rules based on the order they are listed here. Change the rule order by clicking on the number and manually entering a new value.
Updating the rule order of an access policy configured using Zscaler Deception is not supported. When changing the rule order of a regular access policy and there is an access policy configured using Deception, the rule order of the regular access policy must be greater than the rule order for an access policy configured using Deception.
When the row is expanded, the description is displayed if available and a **Criteria** section provides a visual representation of the criteria (e.g., [SAML attributes](/zpa/about-samlattributes), application segments, [posture profiles](/zpa/configuring-device-posture-profiles-zpa), etc.) and Boolean logic used within the rule.
- **Name**: The name of the rule.
- **Status**: Indicates if the rule is enabled or disabled.
- **Rule Action**: Indicates if the rule will **Allow Access**, **Block Access**, or **Require Approval**.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Copy an existing access policy rule's criteria, and use it to create a new rule.
- [Edit an existing access policy rule](/zpa/editing-access-policies).
- Delete an access policy rule or [view the policy usage details](/zpa/viewing-policy-usage-details).
If an access policy is configured using Deception, the copy, edit, and delete options are unavailable.
[See image.](#DeceptionAccessPolicy)
- Display more rows or a different page of the table.
- Depending on your ZPA Admin Portal subscriptions, you see the following pages:
- [Timeout Policy](/zpa/about-timeout-policy): Manage timeout policies to control authentication and idle connection timeouts.
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy): Manage client forwarding policies when application requests are forwarded to ZPA from Zscaler Client Connector.
- [Isolation Policy](/zpa/about-isolation-policy): Manage isolation policies that define when application requests are redirected to Isolation.
- [Privileged Policy](/zpa/about-privileged-policy): Manage privileged policies to designate privilege consoles to inspect, upload, or download files.
- [Security Policy](/zpa/about-security-policy): Manage security policies to designate AppProtection and Browser Protection policy-specific features.
- [Redirection Policy](/zpa/about-redirection-policy): Manage redirection policies to configure rule criteria for preferred ZPA Private Service Edges over ZPA Public Service Edges.
![Viewing and adding the access policy and its rules in the ZPA Admin Portal](/downloads/zpa/policies/access-policy/about-access-policy/zpa-access-policy-overview-numbers.png)
[]![Application Segment Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample1.png)
[]![Segment Group Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample2.png)
[]![Application Segments and Segment Groups Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample3.png)
[]![Additional Criteria Example](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-aboutaccesspolicy-booleanexample4.png)
[]![Deception access policy](/downloads/zpa/documentation-knowledgebase/policies/access-policy/about-access-policy/zpa-deception-integration-accessPolicies.png)
[]These are the conditions of a policy rule. A user's application request must match all of the conditions within a policy rule.
You can apply any of the following criteria to a policy rule:
- Application Segments: A grouping of defined applications based upon access type or user privileges. To learn more, see [About Applications](/zpa/about-applications).
- Branch Connector Groups: The group of Branch Connectors to which the policy applies. To learn more, see [About Branch Connector Groups](/zpa/about-branch-connector-groups).
- Chrome Enterprise Browser: Verify if the users are accessing private applications by using the Chrome Enterprise browser. To learn more, see [Configuring Chrome Enterprise Browser Connector Settings](/zpa/configuring-chrome-enterprise-browser-connector-settings).
- Client Connector Posture Profiles: Zscaler Client Connector device posture profiles is the set of criteria that a user's device must meet to access applications with ZPA. To learn more, see [About Device Posture](/zscaler-client-connector/about-device-posture).
- Client Connector Trusted Networks: The type of networks the user is connected to that Zscaler Client Connector can trust. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-app).
- Client Types: The available client types are Zscaler Client Connector, Client Connector for VDI, Client Connector Partner, Branch Connector, Cloud Connector, Machine Tunnel, Web Browser, or ZIA Service Edge. To learn more, see [What Is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector), [About Branch Connectors](/zpa/about-branch-connectors), [About Cloud Connectors](/zpa/about-cloud-connectors), [What Is Zscaler Client Connector for VDI?](/cloud-branch-connector/what-zscaler-client-connector-vdi), [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels), [About Browser Access](/zpa/about-browser-access), and [About Source IP Anchoring](/zia/about-source-ip-anchoring).
- Cloud Connector Groups: The group of Cloud Connectors to which the policy applies. To learn more, see [About Cloud Connector Groups](/zpa/about-cloud-connector-groups).
-
Country Codes: The country that a user's IP address is located in.
In the case of Cloud Connectors, Source IP Anchoring traffic, or ZPA multi-hop, ZPA country criteria policy is applied using the last NATed layer 3 public IP address. For example, SIPA traffic identifies the country based on the ZIA Public Service Edge’s public IP address.
- Locations: The Branch Connector, Cloud Connector, or other locations and sub-locations.
- Machine Groups: The group of configured machines. To learn more, see [About Machine Groups](/zpa/about-machine-groups).
- Platforms: The user devices to which the policy applies. The available platform types are Windows, macOS, Linux, and Android. To learn more, see [Access Policy Use Cases](/zpa/access-policy-use-cases).
- Risk Scores: User risk scores from a risk source (e.g., ZIA). To learn more, see [About User Risk Scores](/zpa/about-user-risk-scores).
- SAML Attributes: User attributes obtained from the SAML assertion from an IdP. To learn more, see [About SAML Attributes](/zpa/about-saml-attributes).
- SCIM Attributes: User attributes learned via SCIM from an IdP. To learn more, see [About SCIM](/zpa/about-scim).
- SCIM Groups: SCIM groups learned via SCIM from an IdP. To learn more, [About SCIM Groups](/zpa/about-scim-groups).
- Segment Groups: The group of configured application segments. To learn more, see [About Segment Groups](/zpa/about-segment-groups).
- Workload Groups: The Workload Groups from your cloud workloads. To learn more, see [About Workload Groups](/zia/about-workload-groups).
To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).
[]These are the operands used between [criteria](/zpa/about-access-policy#criteria). Access Policy rules use AND and OR operators only.
ZPA uses an implicit OR Boolean operator between multiple application segments. For example, the following access policy rule includes three application segments. ZPA evaluates this application segment criteria as "Sales Tools OR QA Application OR All Other Services."
[See image.](#appsegex)
Similar to application segments, ZPA uses an implicit OR Boolean operator between multiple segment groups. For example, the following policy rule includes three segment groups. ZPA evaluates the segment group criteria as "AD-Servers OR Web Services Group OR Azure Application Group."
[See image.](#sgmntgrpex)
ZPA uses an explicit OR Boolean operator between application segment and segment group criteria. When a user requests access to an application, the policy rule is evaluated to check if an application segment OR its segment group are present. For example, the following policy rule includes three application segments and three segment groups:
[See image.](#appsegsgmntgrpex)
If additional criteria are included, ZPA uses an explicit AND Boolean operator between them. When a user requests access to an application, ZPA verifies the following criteria and logic:
[See image.](#morecriteriaex)
To learn more about implicit and explicit Boolean operators between and within criteria, see [Configuring Access Policies](/zpa/configuring-access-policies).