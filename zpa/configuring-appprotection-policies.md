# Configuring AppProtection Policies
Source: https://help.zscaler.com/zpa/configuring-appprotection-policies
PDF: https://help.zscaler.com/pdf/com/en/1484931.pdf

AppProtection policy rules enable you to implement AppProtection control. For a complete list of ranges and limitations for AppProtection policy rules, see [Ranges & Limitations](/zpa/ranges-limitations).
To configure an AppProtection policy rule:
- Go to **Policy **> **AppProtection Policy**.
- Click **Add Rule**.
The **Add AppProtection Policy** window appears.
- In the **Add AppProtection Policy** window, enter the following information:
- **Name**: Enter an AppProtection policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- For the **Action** section, choose the configuration information for the following items:
- **Rule Action**: Select **Inspection **or **Bypass Inspection**.
- **AppProtection Profile**: Choose an [AppProtection profile](/zpa/about-inspection-profiles) that is a security profile with a set of common or control specific actions.
- For the **Criteria** section, you can either:
- Copy from an existing Access Policy’s criteria by selecting **Yes** for **Copy the criteria from an existing Access Policy Rule** and choosing an existing [Access Policy](/zpa/about-access-policy). The criteria from that access policy appears. You can modify the criteria if you want to adjust it for this AppProtection policy rule.
- Choose the criteria you want to use by clicking **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule, except for Client Connector Posture Profile condition sets. You can add up to 10 condition sets.
- [Applications](#apps)
- [Client Connector Posture Profiles](#postureprofile)
- [Client Connector Trusted Networks](#networks)
- [Client Types](#client)
- [Cloud Connector Groups](#CloudConnectorGroups)
- [Machine Groups](#machinegrps)
- [Platforms](#platforms)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
[See image.](#addcriteria)
The Boolean logic used between **Criteria** is always displayed. For example, when a user requests access to an application, the policy rule is evaluated to check if an application segment OR its segment group are present AND whether any of the SAML attributes are applicable to the user making the request before it grants or denies access. You can always view the **Rule Action** and **Criteria** as well as the applied Boolean logic on the [AppProtection Policy](/zpa/about-inspection-policy) page.
- Click **Save**.
[]![Select criteria for an AppProtection policy rule in the ZPA Admin Portal](/downloads/zpa/policies/appprotection-private-application-traffic-policy-formerly-inspection/configuring-inspection-policies/Add%20AppProtection%20Policy%20window.png)
[]Choose the application segments and segment groups to which this rule applies:
- **Application Segments**: Choose the [application segments](/zpa/about-applications), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/zpa/configuring-application-segments) appear in the menu. There is no limit to the number you can select.
If you added multiple application segments to the policy rule, ZPA uses an OR Boolean operator between them.
There are limits to the number of application segments applied to a rule. For a complete list of ranges and limitations for AppProtection Policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
- **Segment Groups**: Choose the [segment groups](/zpa/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/zpa/configuring-segment-groups) appear in the menu. There is no limit to the number you can select.
If you added multiple segment groups to the policy rule, ZPA uses an OR Boolean operator between them.
[]Choose the condition sets to which the rule applies. You can add up to 10 **Client Connector Posture Profile** condition sets to the rule. Click **Add Criteria** to include additional sets.
Each condition set can contain multiple posture profiles to enforce on a user’s device. For each profile, select one of the following:
- **VERIFIED**: Zscaler Client Connector verified the user's device against the criteria specified in the posture profile.
- **VERIFICATION FAILED**: Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile.
Make sure you have [configured the posture profiles](/z-app/configuring-device-posture-profiles-zpa) within the Zscaler Client Connector Portal. The posture profiles you configure in the Zscaler Client Connector Portal appear in the drop-down menu, where you can search for a specific profile.
If you added multiple posture profile condition sets to the policy rule, ZPA uses an AND Boolean operator between them. ZPA evaluates each posture profile condition set individually.
[See image.](#img-PostureSetBoolean)
If you added multiple posture profiles within a posture profile condition set, ZPA uses an OR Boolean operator between them by default. However, you can toggle this to an AND operator by clicking on it.
[See image.](#img-DevicePostureBooleanToggle)
[]![Add Inspection Policy window with Posture Profile Condition Set Boolean](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-posturesetsboolean.png)
[]![Add Inspection Policy window with Posture Profiles setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-devicepostureboolean.png)
[]Choose the trusted networks to which the rule applies, and click **Done**. You can search for a specific trusted network, click **Select All **to have the rule apply to all trusted networks, or click **Clear Selection** to remove all selections. The trusted networks you've configured appear in the menu. There is no limit to the number you can select.
A [forwarding profile](/z-app/about-forwarding-profiles) tells Zscaler Client Connector how to treat traffic from your users' systems in different network environments for ZPA. When a user connects to a network, Zscaler Client Connector checks to determine what type of network the user is connected to.
If you added multiple trusted networks to the policy rule, ZPA uses an OR Boolean operator between them.
Make sure you have [configured your Trusted Network Criteria](/z-app/configuring-forwarding-profiles-zscaler-app) within the Zscaler Client Connector Portal. The trusted networks you configure in the Zscaler Client Connector Portal appear in the drop-down menu.
[]Choose the client types to which the rule applies, and click **Done**. You can search for a specific client type, click **Select All** to apply all client types, or click **Clear Selection** to remove all selections. The valid client types are:
- **Client Connector**: To learn more, see [What is the Zscaler Client Connector?](/z-app/what-zscaler-app)
- **Cloud Browser**: To learn more, see [About Cloud Browser Isolation](/zia/about-cloud-browser-isolation).
- **Cloud Connector**: To learn more, see [About Cloud Connectors](/zpa/about-cloud-connectors).
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
- Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/about-idp/new#IdP_BothSSO). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or Session Attributes](#saml)
- [SCIM Attributes or User Attributes](#scim)
- [SCIM Groups](#scimgroup)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is name of the IdP configuration you selected in step a.
[See image.](#img-idpcriteria)
In order for ZPA to process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
If you added multiple attributes or groups to the policy rule, ZPA uses an OR Boolean operator between them by default. For example, if you selected FirstName and LastName, the policy rule is only applied to users with the specified FirstName OR LastName for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#img-SAMLBooleanToggle)
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SAML attributes, but continues to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: ZPA does not evaluate this policy rule. You must remove the criteria under SAML Attributes for ZPA to process the policy rule.
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SCIM attributes and SCIM groups, but continues to evaluate the criteria for SAML attributes.
- AND: ZPA evaluates this policy rule. You must remove the criteria for SCIM attributes and SCIM groups for ZPA to process the policy rule.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the rule action to any user (i.e., the rule applies to all users, groups, departments, etc.).
Alternatively, choose a specific [SAML attribute](/zpa/about-saml-attributes) from the drop-down menu if you want to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SAML attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SAML Attributes** option is replaced with **Session Attributes**. The user attributes are populated from the ZIdentity Admin Portal and are used for defining various sign-on policies. To learn more, see [About Attributes](/zslogin/about-attributes) and [What Is ZIdentity?](/zslogin/what-zslogin)
[]Choose a specific SCIM attribute from the drop-down menu to apply the rule action to specific users, groups, departments, etc:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SCIM attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SCIM Attributes** option is replaced with **User Attributes**. The group attributes are populated from the ZIdentity Admin Portal and are used for defining various sign-on policies. To learn more, see [About Attributes](/zslogin/about-attributes) and [What Is ZIdentity?](/zslogin/what-zslogin)
[]Choose a specific SCIM group from the drop-down menu to apply the rule action to a specific group:
- You can search for a specific group, select a listed group, or click **Clear Selection** to remove all selected groups.
- Click **Add More** to add multiple groups, if necessary.
[]![View identity provider, criteria, attribute for an Inspection Policy rule in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Inspection Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean.png)