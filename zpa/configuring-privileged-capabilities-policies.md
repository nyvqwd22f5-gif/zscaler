# Configuring Privileged Capabilities Policies
Source: https://help.zscaler.com/zpa/configuring-privileged-capabilities-policies
PDF: https://help.zscaler.com/pdf/com/en/1485541.pdf

After you have created a [privileged portal](/zpa/about-privileged-portals) and the [privileged console](/zpa/about-privileged-consoles) that this policy rule applies to, and if you have set up the parameters for the [Zscaler Internet Access (ZIA) Sandbox integration](/zpa/about-integrations) (optional), you need to create a [privileged capabilities policy](/zpa/about-privileged-capabilities-policy). The privileged consoles that you choose to assign a privileged capabilities policy rule can be set to inspect and upload files with or without inspection, download files, copy and paste to and from a privileged console, record privileged sessions, and provide monitor and control capabilities for live privileged sessions. If the privileged capability policy is changed while a live privileged session is in progress, the changes aren't reflected until a new live privileged session is started.
If you select the Inspect option, then the files are inspected inline with the uploading process.
To configure a privileged capabilities policy rule:
- Go to **Policy** > **Privileged Policy** > **Privileged Capabilities Policy**.
- Click **Add Rule**.
The **Add Privileged Capabilities Policy** window appears.
- In the **Add Privileged Capabilities Policy** window:
- **Name**: Enter a privileged capabilities policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: This field might or might not appear, depending on your configuration. Enable to add the selected capabilities of this privileged capabilities policy to a privileged console. If you select Disable, any capabilities selected for this privileged capability policy are not available for the associated privileged console. By default, this field is disabled. If a new policy rule is added to the privileged capabilities policy, it is automatically enabled.
- **Description**: (Optional) Enter a description.
- For **Privileged Capabilities**:
- **File Uploads**: Enable to allow uploads. Select **Inspect** to inspect uploaded files. Enable to allow uploads. By default, this field is disabled.
You can only select the Inspect option if the ZIA integration was successful.
- **File Downloads**: Enable to allow downloads. By default, this field is disabled.
If you are creating a privileged capabilities policy with a VNC-enabled privileged console and want to enable **File Uploads** or **File Downloads**, the target system needs to have SSH enabled on port 22 and must use the same credentials as used for logging into VNC.
If you are creating a privileged capabilities policy with a VNC-enabled privileged console that has SFTP disabled and you are attempting to enable **File Uploads** or **File Downloads**, the connection fails when the end user attempts to connect.
- **Clipboard Copy**: Enable to allow the copy action from a privileged console. By default, this field is disabled.
- **Clipboard Paste**: Enable to allow the paste action into a privileged console. By default, this field is disabled.
- **Record Sessions**: Enable to record a Privileged Remote Access privileged session. By default, this field is disabled.
Privileged session recording captures the screen outputs. The File Transfer and Clipboard transfers are not recorded during a privileged session recording to prevent leakage of sensitive information like passwords.
- **Share Sessions Mode**: Select **Control** to allow other users to be invited to a privileged session, and to transfer mouse and keyboard control to them. Select **Monitor** to allow permitted users, such as administrators, to join live privileged sessions. By default, this field is disabled.
- **Join Sessions Mode**: Enable to join a Privileged Remote Access privileged session. By default, this field is disabled.
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule.
[See image.](#Addwindow)
- [Applications](#apps)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
- Click **Save**.
[]Choose the application segments and segment groups to which this rule applies:
- **Application Segments**: Choose the [application segments](/zpa/about-applications), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/zpa/configuring-application-segments) appear in the menu. There is no limit to the number you can select.
If you are within a [Microtenant](/zpa/about-microtenants), you see application segments that are inherited, shared, or created in the Microtenant. If there are policies associated with the inherited application in the Default Microtenant, then that policy takes precedence over the policy configured for the same application in the Microtenant when policies are being evaluated.
If you added multiple application segments to the policy rule, ZPA uses an OR Boolean operator between them.
There are limits to the number of application segments applied to a rule. For a complete list of ranges and limitations for privileged capabilities policy rules, see [Ranges & Limitations](/zpa/ranges-limitations#Policies).
- **Segment Groups**: Choose the [segment groups](/zpa/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/zpa/configuring-segment-groups) appear in the menu. There is no limit to the number you can select.
If you added multiple segment groups to the policy rule, ZPA uses an OR Boolean operator between them.
If you are subscribed to ZIdentity for users, the **SAML and SCIM Attributes** criteria is replaced with **Session and User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
[]To use SAML or SCIM Criteria:
- []Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/about-idp/new#IdP_BothSSO). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or Session Attributes](#saml)
- [SCIM Attributes or User Attributes](#scim)
- [SCIM Groups](#scimgrp)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is the name of the IdP configuration you [previously selected](#stepa).
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
[See image.](#SAMLBoolean2)
If your [IdP configuration for SSO](/zpa/about-idp/new#IdP_BothSSO) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between policy rules.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the rule action to any user (i.e., the rule applies to all users, groups, departments, etc.).
Alternatively, choose a specific [SAML attribute](/zpa/about-samlattributes) from the drop-down menu if you want to apply the rule action to specific users, groups, departments, etc.:
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
[]![Add Criteria to a Privileged Capabilities Policy](/downloads/zpa/policies/privileged-remote-access-policy/configuring-privileged-capabilities-policies/Add%20Priv%20Capab%20Pol%20window_0.png)
[]![View identity provider, criteria, attribute ](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean2.png)