# Configuring Isolation Policies
Source: https://help.zscaler.com/unified/configuring-isolation-policies
PDF: https://help.zscaler.com/pdf/com/en/1492646.pdf

Isolation policy rules allow you to implement controls based on isolation profiles. For a complete list of ranges and limitations for isolation policy rules, see [Ranges & Limitations](/unified/ranges-limitations#private-applications).
To configure an access policy rule:
- Go to **Policies **> **Access Control** > **Clientless** > **Isolation Policy**.
- Click **Add Rule**.
The **Add Isolation Policy** window appears.
- In the **Add Isolation Policy** window:
- **Name**: Enter an isolation policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- For **Action**:
- **Rule Action**: Select **Allow Isolation** or **Bypass Isolation**.
- **Isolation Profile**: Select an isolation profile for the rule to use for allowing isolation. This field is required for creating an isolation policy that has the **Rule Action** set to **Allow Isolation**.
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule.
The **Client Connector Posture Profiles**, **Client Connector Trusted Networks**, and the **Machine Groups** criteria may appear in the drop-down menu, but they are not supported with **Web Browser** client type, which is required for isolation policies.
[See image.](#img-addcriteria)
- [Applications](#apps)
- [Client Types](#client)
- [Cloud Connector Groups](#cloudconnectorgroups)
- [Platforms](#platforms)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
[See image.](#img-allcriteria)
- Click **Save**.
[]Choose the application segments and segment groups to which this rule applies:
- **Application Segments**: Choose the [application segments](/unified/about-defined-application-segments), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/unified/configuring-defined-application-segments) appear in the menu. There is no limit to the number you can select.
If you added multiple application segments to the policy rule, an OR Boolean operator is used between them.
- **Segment Groups**: Choose the [segment groups](/unified/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/unified/configuring-segment-groups) appear in the menu. There is no limit to the number you can select.
If you added multiple segment groups to the policy rule, an OR Boolean operator is used between them.
[]The **Web Browser** client type is required for isolation policy rules, and it is the only client type available. It is preselected for the rule. To learn more, [About Browser Access](/unified/about-browser-access).
Rules using the **Web Browser** client type can not also use the **Client Connector Posture Profiles**, **Client Connector Trusted Networks**, and the **Machine Groups** criteria.
[]The Cloud Connector Group criteria type cannot be configured with the SAML and SCIM Attributes criteria type.
Choose the Cloud Connector groups to which the policy applies, and click **Done**. You can search for a specific Cloud Connector group, click **Select All** to apply all Cloud Connector groups, or click **Clear Selection **to remove all selections. The Cloud Connector groups you've configured appear in the menu. There is no limit to the number you can select.
If you've added multiple Cloud Connector groups to the policy rule, an AND Boolean operator is used between them.
[]Choose the platforms to which the rule applies and click **Save**. This allows you to control which applications are designated to which devices. The valid platform types are:
- Windows
- macOS
- Linux
- iOS
- Android
If you added multiple platforms to the policy rule, an OR Boolean operator is used between them.
- If you are subscribed to ZIdentity for users, the **SAML and SCIM Attributes** criteria is replaced with **Session and User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
- The SAML and SCIM Attributes criteria type cannot be configured with the Cloud Connector Group criteria type.
[]To use SAML or SCIM Criteria:
- Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or Session Attributes](#saml)
- [SCIM Attributes or User Attributes](#scim)
- [SCIM Groups](#scimgrp)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is name of the IdP configuration you selected in step a.
[See image.](#img-idpcriteria)
To process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign).
If you added multiple attributes or groups to the policy rule, then an OR Boolean operator is used between them by default. For example, if you selected FirstName and LastName, the policy rule only applies to users with the specified FirstName OR LastName for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#img-samlboolean)
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, then the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: The criteria evaluation is skipped for SAML attributes, but continues to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: This policy rule is not evaluated. You must remove the criteria under SAML Attributes to process the policy rule.
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, then the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: The criteria evaluation is skipped for SCIM attributes and SCIM groups, but continues to evaluate the criteria for SAML attributes.
- AND: This policy rule is not evaluated. You must remove the criteria for SCIM attributes and SCIM groups to process the policy rule.
If you select multiple IdPs for the policy rule, then an OR Boolean operator is used between them by default. For example, you can select one IdP that includes FirstName OR LastName and another IdP that includes Any SAML Attribute. In this case, the policy rule applies to a user authenticating from the first IdP if they have the specified FirstName OR LastName *or* it applies to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#img-2samlboolean)
If your [IdP configuration for SSO](/unified/configuring-idp-single-sign) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between policy rules.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the rule action to any user (i.e., the rule applies to all users, groups, departments, etc.).
Alternatively, choose a specific [SAML attribute](/unified/about-saml-attributes) from the drop-down menu if you want to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SAML attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SAML Attributes** option is replaced with **Session Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
[]Choose a specific SCIM attribute from the drop-down menu to apply the rule action to specific users, groups, departments, etc:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SCIM attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SCIM Attributes** option is replaced with **User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
[]Choose a specific SCIM group from the drop-down menu to apply the rule action to a specific group:
- You can search for a specific group, select a listed group, or click **Clear Selection** to remove all selected groups.
- Click **Add More** to add multiple groups, if necessary.
[]![Add Criteria to an Isolation Policy](/downloads/zpa/access-timeout-policies/isolation-policy/configuring-isolation-policies/zpa-addisolationplcy-criteria.png)
[]![View identity provider, criteria, attribute ](/downloads/zpa/access-timeout-policies/isolation-policy/configuring-isolation-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Isolation Policy window with SAML Attributes setting](/downloads/zpa/access-timeout-policies/isolation-policy/configuring-isolation-policies/zpa-policy-samlboolean.png)
[]![Add Isolation Policy window with SAML Attributes setting](/downloads/zpa/access-timeout-policies/isolation-policy/configuring-isolation-policies/zpa-policy-2samlboolean.png)
[]![Adding a new isolation policy rule within ZPA](/downloads/zpa/access-timeout-policies/isolation-policy/configuring-isolation-policies/zpa-addisolationplcy-allcriteria_0.png)