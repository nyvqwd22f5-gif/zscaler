# Configuring Browser Protection Policies
Source: https://help.zscaler.com/zpa/configuring-browser-protection-policies
PDF: https://help.zscaler.com/pdf/com/en/1485641.pdf

The Browser Protection policy rules enable you to implement Browser Protection control.
To configure a Browser Protection policy rule:
- Go to **Policy** > **Security Policy** > **Browser Protection Policy**.
- Click **Add Rule**.
The **Add Browser Protection Policy** window appears.
- In the **Add Browser Protection Policy** window, enter the following information:
- **Name**: Enter a Browser Protection policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- For the **Action** section, choose the configuration information for the following items:
- **Rule Action**: Select **Monitor** or **Do Not Monitor**.
- **Browser Protection Profile**: Choose a Browser Protection profile that is a security profile with a set of common or control-specific actions.
- For the **Criteria **section, you can choose the criteria you want to use by clicking **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule, except for Client Connector Posture Profile condition sets. You can add up to 10 condition sets.
- [Applications](#apps)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
- [User Portals](#Userportal)
The Boolean logic used between Criteria is always displayed. For example, when a user requests access to an application, the policy rule is evaluated to check if an application segment, its segment group, OR user portals are present AND whether any of the SAML attributes are applicable to the user making the request before it grants or denies access. You can always view the Rule Action and Criteria as well as the applied Boolean logic on the Browser Protection Policy page.
- Click **Save**.
[]Choose the application segments and segment groups to which this rule applies:
- **Application Segments**: Choose the [application segments](/zpa/about-applications), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/zpa/configuring-application-segments) appear in the menu. There is no limit to the number you can select.
If you added multiple application segments to the policy rule, ZPA uses an OR Boolean operator between them.
There are limits to the number of application segments applied to a rule. For a complete list of ranges and limitations for Browser Protection Policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
- **Segment Groups**: Choose the [segment groups](/zpa/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/zpa/configuring-segment-groups) appear in the menu. There is no limit to the number you can select. If you added multiple segment groups to the policy rule, ZPA uses an OR Boolean operator between them.
If you selected the **Applications** criteria option, you cannot also select the **User Portals** criteria option.
If you are subscribed to ZIdentity for users, the **SAML and SCIM Attributes** criteria is replaced with **Session and User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
[]To use SAML or SCIM Criteria:
- Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/about-idp/new#IdP_BothSSO). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or User Attributes](#saml)
- [SCIM Attributes or Group Attributes](#scim)
- [SCIM Groups](#scimgroup)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is name of the IdP configuration you selected in step a.
[See image.](#img-idpcriteria)
For ZPA to process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
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
[]**User Portals**: Choose the user portals, and click **Done**. You can search for a specific user portal, click **Select All** to apply all user portals, or click **Clear Selection** to remove all selections. The user portals you've configured appear in the menu. There is no limit to the number you can select. If you add multiple application segments to the policy rule, ZPA uses an OR Boolean operator between them.
If you selected the **User Portals** criteria option, you cannot also select the **Applications** criteria option.