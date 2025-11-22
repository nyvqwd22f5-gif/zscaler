# Configuring VPN User Enablement
Source: https://help.zscaler.com/unified/configuring-vpn-user-enablement
PDF: https://help.zscaler.com/pdf/com/en/1532366.pdf

User enablement rules allow you to control access to VPN tunnels and set posture profile validation on users' devices. For a complete list of ranges and limitations for VPN user enablement rules, see [Ranges & Limitations](/unified/ranges-limitations#private-applications).
To configure a user enablement rule:
- Go to **Infrastructure > Private Access > Component > VPN (For Legacy Apps) > User Enablement**.
- Click **Add**.
The **Add User Enablement **window appears.
- In the** Add User Enablement **window:
- **Name**: Enter a VPN user enablement name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- For **Action**:
- **Rule Action**: Select one of the following options:
- **Allow Access**: Allows access to VPN tunnels.
- **Block Access**: Blocks access to VPN tunnels.
- **Message to User**: (Optional) Enter the message you want to display to users when the user enablement rule’s action and criteria are met. If you are blocking access, ensure that the message helps the user understand why they are being denied access.
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule, except for **Client Connector Posture Profiles** condition sets. You can add up to 10 condition sets.
- [Client Connector Posture Profiles](#postureprofile)
- [SAML and SCIM Attributes](#samlscimattribute)
[See image.](#createnewrule)
The Boolean logic used between **Criteria** is always displayed. You can always view the **Rule Action** and **Criteria** as well as the applied Boolean logic on the [User Enablement page](/zpa/about-vpn-user-enablement).
- Click **Save**.
[]To use Client Connector Posture Profiles criteria:
- Select **Client Connector Posture Profiles**.
- Select a posture profile from the drop-down menu.
- Choose the condition sets to which the user enablement rule applies. You can add up to 10 **Client Connector Posture Profiles** condition sets to the user enablement rule. Click **Add Criteria** to include additional sets. Each condition set can contain multiple posture profiles to enforce on a VPN connected user’s device. For each profile, select one of the following:
- **VERIFIED**: Zscaler Client Connector verified the VPN connected user's device against the criteria specified in the posture profile.
- **VERIFICATION FAILED**: Zscaler Client Connector was unable to verify the VPN connected user's device against the criteria specified in the posture profile.
- Click **Save**.
If you added multiple posture profile condition sets to the user enablement rule, an AND Boolean operator is used between them. Each posture profile condition set is evaluated individually.
[See image.](#PostureSetBoolean)
If you added multiple posture profiles within a posture profile condition set, an OR Boolean operator is used between them by default. However, you can toggle this to an AND operator by clicking it.
[See image.](#DevicePostureBooleanToggle)
[]To use SAML and SCIM Attributes criteria:
- Select **SAML and SCIM Attributes.**
- Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the user enablement rule.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this user enablement rule applies:
- [SAML Attributes](#saml)
- [SCIM Attributes](#scim)
- [SCIM Groups](#scimgrp)
[See image.](#idpcriteria)
If you added multiple attributes or groups to the user enablement rule, an OR Boolean operator is used between them by default. For example, if you selected **First Name** and **Last Name**, the user enablement rule is only applied to VPN connected users with the specified **First Name** OR **Last Name** for that IdP. However, you can toggle this to an AND operator by clicking it.
[See image.](#SAMLBooleanToggle)
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the user enablement rule has criteria for SAML attributes, the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: Skips evaluating the criteria for SAML attributes, but continues to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: Does not evaluate this user enablement rule. You must remove the criteria under SAML Attributes for ZPA to process the user enablement rule.
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the user enablement rule has criteria for SCIM attributes or SCIM groups, the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: Skips evaluating the criteria for SCIM attributes and SCIM groups, but continues to evaluate the criteria for SAML attributes.
- AND: Does not evaluate this user enablement rule. You must remove the criteria for SCIM attributes and SCIM groups to process the user enablement rule.
If you selected multiple IdPs for the user enablement rule, an OR Boolean operator is used between them by default. For example, you can select one IdP that includes **First Name** OR **Last Name** and another IdP that includes Any SAML Attribute. In this case, the user enablement rule applies to a user authenticating from the first IdP if they have the specified **First Name** OR **Last Name** *or* it applies to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking it.
[See image.](#SAMLBoolean2)
If your [IdP configuration for SSO](/unified/configuring-idp-single-sign) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between user enablement rules.
[]By default, the user enablement rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the user enablement rule action to any VPN connected user.
Alternatively, choose a specific [SAML attribute](/unified/about-saml-attributes) from the drop-down menu that you want to apply the rule action to:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SAML attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
[]Choose a specific SCIM attribute (e.g., departments, display name, title, etc.) from the drop-down menu to apply the rule action to:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SCIM attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
[]Choose a specific SCIM group name from the drop-down menu to apply the rule action to:
- You can search for a specific group, select a listed group, or click **Clear Selection** to remove all selected groups.
- Click **Add More** to add multiple groups, if necessary.
[]![Add User Enablement window](/downloads/zpa/configuring-vpn-user-enablement/Add%20User%20Enablement%20window.png)
[]![View identity provider, criteria, attribute](/downloads/zpa/configuring-vpn-user-enablement/idpcriteria.png)
[]![Add User Enablement window with SAML Attributes setting](/downloads/zpa/configuring-vpn-user-enablement/SAMLBooleanToggle.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean2.png)
[]![Access Policy window with Posture Profile Condition Set Boolean](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-posturesetsboolean.png)
[]![Add User Enablement window with Posture Profiles setting](/downloads/zpa/configuring-vpn-user-enablement/DevicePostureBooleanToggle.png)