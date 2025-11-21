# Configuring Privileged Credentials Policies
Source: https://help.zscaler.com/zpa/configuring-privileged-credentials-policies
PDF: https://help.zscaler.com/pdf/com/en/1485576.pdf

After you create a [privileged console](/zpa/about-privileged-consoles) and a [privileged credential](/zpa/about-privileged-credentials) or a [privileged credential pool](/zpa/about-privileged-credential-pools) that this policy rule applies to, you need to create a [privileged credentials policy](/zpa/about-privileged-credentials-policy).
To configure a privileged credentials policy rule:
- Go to **Policy** > **Privileged Policy** > **Privileged Credentials Policy**.
- Click **Add Rule**.
The **Add Privileged Credentials Policy** window appears.
- In the **Add Privileged Credentials Policy** window:
- **Name**: Enter a privileged credentials policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- For **Privileged Credentials**: Select if you want to assign a privileged credential or a privileged credential pool of multiple credentials for this policy.
- **Credential**: Select the privileged credential you want to use for this policy rule.
- **Credential Pool**: Select the privileged credential pool you want to use for this policy rule.
If you are within a [Microtenant](/zpa/about-microtenants), you only see the privileged credentials that are created for the Microtenant.
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule.
[See image.](#addprivcredpol)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
- Click **Save**.
If you are subscribed to ZIdentity for users, the **SAML and SCIM Attributes** criteria is replaced with **Session and User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
[]To use SAML or SCIM Criteria:
- Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/about-idp/new#IdP_BothSSO). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or Session Attributes](#saml)
- [SCIM Attributes or User Attributes](#scim)
- [SCIM Groups](#scimgrp)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is the name of the IdP configuration you selected in step a.
[See image.](#idpcriteria)
For ZPA to process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
If you added multiple attributes or groups to the policy rule, ZPA uses an OR Boolean operator between them by default. For example, if you selected FirstName and LastName, the policy rule is only applied to users with the specified FirstName OR LastName for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBooleanToggle)
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SAML attributes, but continues to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: ZPA does not evaluate this policy rule. You must remove the criteria under SAML Attributes for ZPA to process the policy rule.
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SCIM attributes and SCIM groups, but continues to evaluate the criteria for SAML attributes.
- AND: ZPA does not evaluate this policy rule. You must remove the criteria for SCIM attributes and SCIM groups for ZPA to process the policy rule.
If you selected multiple IdPs for the policy rule, ZPA uses an OR Boolean operator between them by default. For example, you can select one IdP that includes FirstName OR LastName and another IdP that includes Any SAML Attribute. In this case, the policy rule applies to a user authenticating from the first IdP if they have the specified FirstName OR LastName *or* it applies to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking on it.
If you use the Any SAML attribute option in your privileged credential, it won't be applied to the related privileged console.
[See image.](#SAMLBoolean2)
If your [IdP configuration for SSO](/zpa/about-idp/new#IdP_BothSSO) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between policy rules.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. You need to select specific SAML attributes.
If you keep the default Any SAML attribute option the privileged credential won't be applied to the related privileged console.
Choose a specific [SAML attribute](/zpa/about-samlattributes) from the drop-down menu to apply the rule action to specific users, groups, departments, etc.:
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
[]![Add Criteria to a Privileged Credentials Policy](/downloads/zpa/policies/privileged-remote-access-policy/configuring-privileged-credentials-policies/Add%20Priv%20Cred%20Policy_0.png)
[]![View identity provider, criteria, attribute ](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean2.png)