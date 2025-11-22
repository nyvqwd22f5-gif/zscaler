# Configuring Portals Policies
Source: https://help.zscaler.com/unified/configuring-portals-policies
PDF: https://help.zscaler.com/pdf/com/en/1510141.pdf

After you have created a privileged portal and the privileged console that this policy rule applies to, and if you have set up the parameters for the Internet & SaaS Sandbox integration (optional), you need to create a portals policy. The privileged portal that you choose to assign a portals policy rule can be set to delete an uploaded file, upload an inspected file, upload an inspected sandbox, and access an uninspected file on the [Privileged Remote Access (PRA) File Transfer System pages](/unified/about-privileged-remote-access-pra-file-transfer-system).
To configure a portals policy rule:
- Go to **Policy** > **Privileged Policy** > **Portals Policy**.
- Click **Add Rule**.
The **Add Portals Policy** window appears.
- In the **Add Portals Policy** window:
- **Name**: Enter a portals policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- For **Portal Configuration**:
- **Delete Files**: Enable to allow deletion of files. By default, this field is disabled.
- **Access Uninspected Files**: Enable to allow uninspected files to be displayed in the PRA Portal. By default, this field is disabled.
- **Upload Inspection**: Select **Sandbox** to allow Internet & SaaS Sandbox integration inspection of the file. Select **Scan** to allow inspection via another format other than Sandbox. By default, this field is disabled.
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule.
[See image.](#add)
- [SAML and SCIM Attributes (or Session and User Attributes)](#SAML)
- [Privileged Portals](#portals)
- [Country Codes](#country)
- Click **Save**.
[]Choose the privileged portals you want to apply this rule to. You need to select at least one privileged portal to create the portals policy. You can search for a specific privileged portal, click **Select All** to apply the privileged portals listed, click **Clear All** to remove all selections, or click the **Delete** icon next to the selected privileged portal to remove it from your list.
[]Choose the countries to which this rule applies. You can search for a specific country, click** Select All** to apply the countries listed, click **Clear All **to remove all selections, or click the **Delete** icon next to the selected country to remove it from your list. Click **Cancel** to exit the Country Code menu.
If you are subscribed to ZIdentity for users, the **SAML and SCIM Attributes** criteria is replaced with **Session and User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
[]To use SAML or SCIM Criteria:
- []Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or Session Attributes](#saml)
- [SCIM Attributes or User Attributes](#scim)
- [SCIM Groups](#scimgrp)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is the name of the IdP configuration you [previously selected](#stepa).
[See image.](#idpcriteria)
Tto process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign).
If you added multiple attributes or groups to the policy rule, an OR Boolean operator is used between them by default. For example, if you selected FirstName and LastName, the policy rule is only applied to users with the specified FirstName OR LastName for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBooleanToggle)
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: The criteria evaluation is skipped for SAML attributes, but is continued for SCIM attributes and SCIM groups.
- AND: The policy rule is not evaluated. You must remove the criteria under SAML Attributes to process the policy rule.
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, then the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: The criteria evaluation is skipped for SCIM attributes and SCIM groups, but is continued for SAML attributes.
- AND: The policy rule is not evaluated. You must remove the criteria for SCIM attributes and SCIM groups to process the policy rule.
If you selected multiple IdPs for the policy rule, then an OR Boolean operator between them by default. For example, you can select one IdP that includes FirstName OR LastName and another IdP that includes Any SAML Attribute. In this case, the policy rule applies to a user authenticating from the first IdP if they have the specified FirstName OR LastName *or* it applies to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBoolean2)
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
[]![View identity provider, criteria, attribute ](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean2.png)
[]![Add Criteria to a portals policy in the Add Portals Policy window](/downloads/zpa/policies/privileged-remote-access-policy/configuring-portals-policies/Add%20window.png)