# Configuring Client Forwarding Policies
Source: https://help.zscaler.com/zpa/configuring-client-forwarding-policies
PDF: https://help.zscaler.com/pdf/com/en/1484381.pdf

Client forwarding policy rules enable you to define when application requests are forwarded to ZPA from Zscaler Client Connector. For a complete list of ranges and limits for client forwarding policy rules, see [Ranges & Limitations](/zpa/ranges-limitations).
For application segments, the Bypass setting takes precedence over any new client forwarding policy rule. To learn more, see [Configuring Bypass Settings](/zpa/configuring-bypass-settings).
To configure a client forwarding policy rule:
- Go to **Policy **> **Client Forwarding Policy**.
- Click **Add Rule**.
The **Add Client Forwarding Policy** window appears.
-
In the** Add Client Forwarding Policy **window:
Proper configuration for Source IP Anchoring in ZPA requires the following Client Forwarding Policies for domain-based and IP address-based applications:
- For IP address-based applications, select the **Only Forward Allowed Applications** rule action for Source IP Anchoring segment groups.
- For domain-based applications, configure the following rules:
- Rule 1: Enable the **Bypass ZPA** rule action for both **Segment Groups** and **Client Types** > **Client Connector**.
- Rule 2: Enable the **Forward to ZPA** rule action for both **Segment Groups** and **Client Types** >** ZIA Service Edge**.
See [Understanding Source IP Anchoring Direct](/zpa/understanding-source-ip-anchoring-direct) for Client Forwarding Policy rules during a Source IP Anchoring Direct event.
- **Name**: Enter a client forwarding policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- For **Action**, under **Rule Action**, select one of the following options:
- **Bypass ZPA**: If selected, applications are marked and bypassed for ZPA, and Zscaler Client Connector does not send application requests to ZPA. This setting is the equivalent of selecting **Always** for the **Bypass** setting within an application segment. To learn more, see [Configuring Application Segments](/zpa/about-application/onboard#tab1).
The Bypass ZPA action is not port specific. When selected, applications are marked and bypassed for ZPA on all ports.
- **Only Forward Allowed Applications**: If you only want Zscaler Client Connector to learn about and forward traffic for applications that a user is allowed to access, select this action. The list of applications that the user has access to is determined by the access policy. To learn more, see [About Access Policy](/zpa/about-access-policies). When Zscaler Client Connector sets up a connection to ZPA, the service determines the list of applications that a user is allowed to access and only downloads this list to Zscaler Client Connector for forwarding traffic to ZPA. For other applications that are not present on the list, Zscaler Client Connector forwards requests for them on the local network. So, requests for these applications are not logged in ZPA.
- **Forward to ZPA**: If selected, Zscaler Client Connector forwards application requests to ZPA. This includes requests to applications that the user is not authorized to access. This is selected by default.
If you have multiple client forwarding policies with both **Bypass ZPA** and **Forward to ZPA** rules for a given domain with different ports, the **Bypass ZPA** rule action takes precedence.
- For **Criteria**, click **Add Criteria** to add one of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule, except for **Client Connector Posture Profile** condition sets. You can add up to 10 condition sets.
[See image.](#addcriteria)
- [Applications](#apps)
- [Branch Connector Groups](#bcgroups)
- [Client Connector Posture Profiles](#postureprofile)
- [Client Connector Trusted Networks](#networks)
- [Client Types](#clients)
- [Cloud Connector Groups](#CloudConnectorGroups)
- [Machine Groups](#machinegrps)
- [Platforms](#platforms)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
[See image.](#createnewrule)
The Boolean logic used between **Criteria** is always displayed. For example, when a user requests access to an application, the policy rule is evaluated to check if an application segment OR its segment group are present AND whether any of the SAML attributes are applicable to the user making the request before it grants or denies access. You can always view the **Rule Action** and **Criteria** as well as the applied Boolean logic on the [Client Forwarding Policy page](/zpa/about-client-forwarding-policy).
- Click **Save**.
[]Choose the application segments and segment groups to which this rule applies:
- **Application Segments**: Choose the [application segments](/zpa/about-applications), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/zpa/configuring-application-segments) appear in the menu. There is no limit to the number you can select.
If you added multiple application segments to the policy rule, ZPA uses an OR Boolean operator between them.
There are limits to the number of application segments applied to a rule. For a complete list of ranges and limitations for Client Forwarding Policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
- **Segment Groups**: Choose the [segment groups](/zpa/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/zpa/configuring-segment-groups) appear in the menu. There is no limit to the number you can select.
If you added multiple segment groups to the policy rule, ZPA uses an OR Boolean operator between them.
[]Choose the Branch Connector groups to which the rule applies. You can search for a specific Branch Connector group, click **Select All Displayed** to apply all Branch Connector groups, or click **Clear All** to remove all selections.
[]Choose the condition sets to which the rule applies. You can add up to 10 **Client Connector Posture Profile** condition sets to the rule. Click **Add Criteria** to include additional sets.
Each condition set can contain multiple posture profiles to enforce on a user’s device. For each profile, select one of the following options:
- **VERIFIED**: Zscaler Client Connector verified the user's device against the criteria specified in the posture profile.
- **VERIFICATION FAILED**: Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile.
Make sure you have [configured the posture profiles](/z-app/configuring-device-posture-profiles-zpa) within the Zscaler Client Connector Portal. The posture profiles you configure in the Zscaler Client Connector Portal appear in the drop-down menu, where you can search for a specific profile.
If you added multiple posture profile condition sets to the policy rule, ZPA uses an AND Boolean operator between them. ZPA evaluates each posture profile condition set individually.
[See image.](#PostureSetBoolean)
If you added multiple posture profiles within a posture profile condition set, ZPA uses an OR Boolean operator between them by default. However, you can toggle this to an AND operator by clicking on it.
[See image.](#DevicePostureBooleanToggle)
[]Choose the trusted networks to which the rule applies, and click **Done**. You can search for a specific trusted network, click **Select All** to apply to all trusted networks, or click **Clear Selection** to remove all selections. The trusted networks you've configured appear in the menu. There is no limit to the number you can select.
Your users must be running Zscaler Client Connector version 2.1.0 to apply this criteria to your policy rule.
If you added multiple trusted networks to the policy rule, ZPA uses an OR Boolean operator between them. Client forwarding policies must delegate each app profile to its intended trusted network.
Make sure you have [configured your Trusted Network Criteria](/z-app/configuring-forwarding-profiles-zscaler-app) within the Zscaler Client Connector Portal. The trusted networks you configure in the Zscaler Client Connector Portal appear in the drop-down menu.
[]Choose the client types to which the rule applies, and click Done. You can search for a specific client type, click **Select All** to apply all client types, or click **Clear Selection** to remove all selections. The valid client types are:
- **Branch Connector**: To learn more, see [About Branch Connectors](/zpa/about-branch-connectors).
- **Client Connector**: To learn more, see [What is the Zscaler Client Connector?](/z-app/what-zscaler-app)
- **Cloud Browser**: To learn more, see [About Cloud Browser Isolation](/zia/about-cloud-browser-isolation).
- **Machine Tunnel**: To learn more, see [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels).
- **Web Browser**: To learn more, see [About Browser Access](/zpa/about-BrowserAccess).
- **ZIA Service Edge**: To learn more, see [About Source IP Anchoring](/zia/about-source-ip-anchoring).
If you added multiple client types to the policy rule, ZPA uses an OR Boolean operator between them.
Rules using the **Web Browser** or **ZIA Service Edge** client types can not also use posture profiles or trusted networks criteria. The posture profiles or trusted networks criteria only work with **Client Connector**.
[]The Cloud Connector Group criteria type cannot be configured with the SAML and SCIM Attributes criteria type.
Choose the Cloud Connector groups to which the policy applies, and click **Done**. You can search for a specific Cloud Connector group, click **Select All** to apply all Cloud Connector groups, or click **Clear Selection **to remove all selections. The [Cloud Connector groups you've configured](/zpa/about-cloud-connector-groups) appear in the menu. There is no limit to the number you can select.
If you've added multiple Cloud Connector groups to the policy rule, ZPA uses an AND Boolean operator between them.
[]Choose the Machine groups to which this rule applies, and click **Done**. You can search for a specific Machine group, click **Select All** to apply all groups, or click **Clear Selection** to remove all selections. The [Machine groups you've configured](/zpa/about-machine-groups) appear in the menu. There is no limit to the number you can select.
If a Machine group is selected, **Machine Tunnel** as a client type is required as well.
[]Choose the platforms to which the rule applies and click **Save**. This allows you to control which applications are designated to which devices. The valid platform types are:
- Windows
- macOS
- Linux
- iOS
- Android
If you added multiple platforms to the policy rule, ZPA uses an OR Boolean operator between them.
- If you are subscribed to ZIdentity for users, the **SAML and SCIM Attributes** criteria is replaced with **Session and User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
- The SAML and SCIM Attributes criteria type cannot be configured with the Cloud Connector Group criteria type.
[]To use SAML or SCIM Criteria:
- Click **Select IdP** and choose the IdP configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/about-idp/new#IdP_BothSSO). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or User Attributes](#saml)
- [SCIM Attributes or Group Attributes](#scim)
- [SCIM Groups](#scimgrp)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is name of the IdP configuration you selected in step a.
[See image.](#idpcriteria)
For ZPA to process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
If you added multiple attributes or groups to the policy rule, ZPA uses an OR Boolean operator between them by default. For example, if you selected FirstName and LastName, the policy rule only applies to users with the specified FirstName OR LastName for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBooleanToggle)
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SAML attributes, but continues to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: ZPA does not evaluate this policy rule. You must remove the criteria under SAML Attributes for ZPA to process the policy rule.
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SCIM attributes and SCIM groups, but continues to evaluate the criteria for SAML attributes.
- AND: ZPA does not evaluate this policy rule. You must remove the criteria for SCIM attributes and SCIM groups for ZPA to process the policy rule.
If you selected multiple IdPs for the policy rule, ZPA uses an OR Boolean operator between them by default. For example, you can select one IdP that includes FirstName OR LastName and another IdP that includes Any SAML Attribute. In this case, the policy rule applies to a user authenticating from the first IdP if they have the specified FirstName OR LastName *or* it applies to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBoolean2)
If your [IdP configuration for SSO](/zpa/about-idp/new#IdP_BothSSO) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between policy rules.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the rule action to any user (i.e., the rule applies to all users, groups, departments, etc.).
Alternatively, choose a specific [SAML attribute](/zpa/about-samlattributes) from the drop-down menu if you want to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SAML attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SAML Attributes** option is replaced with **Session Attributes**. The user attributes are populated from the ZIdentity Admin Portal and are used for defining various sign-on policies. To learn more, see [About Attributes](/zslogin/about-attributes) and [What Is ZIdentity?](/zslogin/what-zslogin)
[]Choose a specific SCIM attribute from the drop-down menu to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SCIM attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SCIM Attributes** option is replaced with **User Attributes**. The group attributes are populated from the ZIdentity Admin Portal and are used for defining various sign-on policies. To learn more, see [About Attributes](/zslogin/about-attributes) and [What Is ZIdentity?](/zslogin/what-zslogin)
[]Choose a specific SCIM group from the drop-down menu to apply the rule action to a specific group:
- You can search for a specific group, select a listed group, or click **Clear Selection** to remove all selected groups.
- Click **Add More** to add multiple groups, if necessary.
[]![Add Client Forwarding Policy window](/downloads/zpa/access-timeout-policies/client-forwarding-policy/configuring-client-forwarding-policies/Client%20Forwarding%20criteria%20list.png)
[]![Add Criteria to a Client Forwarding Policy](/downloads/zpa/access-timeout-policies/client-forwarding-policy/configuring-client-forwarding-policies/zpa-clientforwardingolicy-addcriteria.png)
[]![View identity provider, criteria, attribute ](/downloads/zpa/access-timeout-policies/client-forwarding-policy/configuring-client-forwarding-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Client Forwarding Policy window with SAML Attributes setting](/downloads/zpa/access-timeout-policies/client-forwarding-policy/configuring-client-forwarding-policies/zpa-policy-samlboolean.png)
[]![Add Client Forwarding Policy window with SAML Attributes setting](/downloads/zpa/access-timeout-policies/client-forwarding-policy/configuring-client-forwarding-policies/zpa-policy-samlboolean2.png)
[]![Add Client Forwarding Policy window with Posture Profile Condition Set Boolean](/downloads/zpa/access-timeout-policies/client-forwarding-policy/configuring-client-forwarding-policies/zpa-policies-posturesetsboolean.png)
[]![Add Client Forwarding Policy window with Posture Profiles setting](/downloads/zpa/access-timeout-policies/client-forwarding-policy/configuring-client-forwarding-policies/zpa-policies-devicepostureboolean.png)