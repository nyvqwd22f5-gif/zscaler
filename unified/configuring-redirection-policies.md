# Configuring Redirection Policies
Source: https://help.zscaler.com/zpa/configuring-redirection-policies
PDF: https://help.zscaler.com/pdf/com/en/1485831.pdf

You can configure redirection policy rules to prefer ZPA Private Service Edges based on country code, client type, and SAML and SCIM criteria. You can specify the method used (Default, Preferred, or Always) for selecting ZPA Private Service Edge groups to redirect to.
To configure a redirection policy rule:
- Go to **Policy **> **Redirection Policy**.
-
Click **Add Rule**.
Redirection policy rules that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
The **Add Redirection Policy** window appears.
- In the** Add Redirection Policy **window:
- **Name**: Enter a redirection policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule. You can add up to 10 condition sets.
[See image.](#addcriteria)
- [Client Types](#client)
- [Country Codes](#CountryCodes)
- [SAML and SCIM Attributes](#samlscimattribute)
The Boolean logic used between **Criteria** is always displayed. For example, when a user requests access to an application, the policy rule is evaluated to check if an application segment OR its segment group are present AND whether any of the SAML attributes are applicable to the user making the request before it grants or denies access. You can always view the **Rule Action** and **Criteria** as well as the applied Boolean logic on the [Access Policy page](/zpa/about-accesspolicy).
[See image.](#AddRedirectionPolicyWindow)
- For **Private Service Edge Groups**:
- For **Private Service Edge Selection Method**, choose the method used for selecting the ZPA Private Service Edge groups to redirect to:
- **Default**: Use the current ZPA Service Edge selection algorithm.
- **Preferred**: Redirect users to the selected ZPA Private Service Edge groups if available, with ZPA Public Service Edges as a fallback.
- **Always**: Always redirect users to the selected ZPA Private Service Edge groups if available and prevent the use of ZPA Public Service Edges. If there are no active ZPA Private Service Edges available in the selected ZPA Private Service Edge groups, then users are redirected to a ZPA Public Service Edge.
- For **Private Service Edge Groups**, if **Preferred **or **Always **is selected, select one or more Private Service Edge groups from the drop-down menu.
[See image.](#privateserviceedgegroups)
- Click **Save**.
[]Choose the client types to which the rule applies. You can search for a specific client type, click **Select All** to apply all client types, or click **Clear Selection** to remove all selections. The valid client types are:
You cannot use Branch Connector or Cloud Connector client types if the **Private Service Edge Selection Method** is **Always**.
- **Branch Connector**: To learn more, see [About Branch Connectors](/zpa/about-branch-connectors).
- **Client Connector**: To learn more, see [What Is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector)
- **Client Connector Partner**: To learn more, see [About Partner Devices](/client-connector/about-partner-devices).
- **Cloud Connector**: To learn more, see [About Cloud Connectors](/zpa/about-cloud-connectors).
- **Machine Tunnel**: To learn more, see [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels).
If you added multiple client types to the policy rule, ZPA uses an OR Boolean operator between them.
Rules using the **Web Browser** or **ZIA Service Edge** client types additionally can't use posture profiles or trusted networks criteria. The posture profiles or trusted networks criteria only work with **Client Connector**. Rules using the **Branch Connector**, **Cloud Connector**, or **Machine Tunnel** client types additionally can't use SAML and SCIM attributes criteria.
[]Choose one or more countries to which the rule applies. You can search for a specific country code, click **Select All** to apply all country codes, or click **Clear Selection **to remove all selections. The country codes you've configured appear in the menu. There is no limit to the number you can select.
If you've added multiple country codes to the policy rule, ZPA uses an AND Boolean operator between them.
[]To use SAML or SCIM criteria:
- Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for user SSO. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes](#saml)
- [SCIM User Attributes](#scim)
- [SCIM Group Attributes](#scimgrp)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is the name of the IdP configuration you selected in step a.
[See image.](#idpcriteria)
In order for ZPA to process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
If you added multiple attributes or groups to the policy rule, ZPA uses an OR Boolean operator between them by default. For example, if you selected a first name and last name attribute, the policy rule is only applied to users with the specified first name OR last name for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBooleanToggle)
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SAML attributes, but continues to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: ZPA does not evaluate this policy rule. You must remove the criteria under SAML Attributes for ZPA to process the policy rule.
If the corresponding [IdP setting](/zpa/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, ZPA evaluates the rule differently depending on the Boolean operator between the criteria:
- OR: ZPA skips evaluating the criteria for SCIM attributes and SCIM groups, but continues to evaluate the criteria for SAML attributes.
- AND: ZPA does not evaluate this policy rule. You must remove the criteria for SCIM attributes and SCIM groups for ZPA to process the policy rule.
If you selected multiple IdPs for the policy rule, ZPA uses an OR Boolean operator between them by default. For example, you can select one IdP that includes a first name OR last name attribute and another IdP that includes Any SAML Attribute. In this case, the policy rule applies to a user authenticating from the first IdP if they have the specified first name OR last name *or* it applies to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBoolean2)
If your [IdP configuration for SSO](/zpa/configuring-idp-single-sign) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between policy rules.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the rule action to any user (i.e., the rule applies to all users, groups, departments, etc.).
Alternatively, choose a specific [SAML attribute](/zpa/about-saml-attributes) from the drop-down menu if you want to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SAML attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
[]Select a specific SCIM user attribute from the drop-down menu to apply the rule action to specific users, groups, departments, etc:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SCIM attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
[]Choose a specific SCIM group from the drop-down menu to apply the rule action to a specific group:
- You can search for a specific group, select a listed group, or click **Clear Selection** to remove all selected groups.
- Click **Add More** to add multiple groups, if necessary.
[]![Add Redirection Policy window with Add Criteria drop-down.](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-redirection-policies-doc-47558/add-redirection-policy-phase-2-criteria-drop-down-1.png)
[]![View identity provider, criteria, attribute ](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-redirection-policies-doc-47558/add-redirection-policy-phase-2-saml-scim-callout-1-b.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-redirection-policies-doc-47558/add-redirection-policy-phase-2-saml-scim-callout-3a-2.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-redirection-policies-doc-47558/add-redirection-policy-phase-2-saml-scim-callout-3b-5.png)
[]![Add Redirection Policy window.](/downloads/zpa/policies/redirection-policy/configuring-redirection-policies/AddRedirectionPolicy-02.png)