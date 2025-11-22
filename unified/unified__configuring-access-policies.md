# Configuring Access Policies
Source: https://help.zscaler.com/unified/configuring-access-policies
PDF: https://help.zscaler.com/pdf/com/en/1492051.pdf

Access policy rules enable you to implement role-based access control. For a complete list of ranges and limitations for access policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
To configure an access policy rule:
- Go to the **Access Policy** page (Policies > Access Control > Private Applications > Access Policy).
- Click **Add Rule**.
The **Add Access Policy** window appears.
[See image.](#addcriteria)
- In the** Add Access Policy **window:
- **Name**: Enter an access policy name. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- For **Action**:
-
**Rule Action**: Select one of the following options:
- **Allow Access**: Allows access to applications.
- **Block Access**: Blocks access to applications.
- **Conditional Access**:** **Allows access to sensitive resources for step-up authentication, and is only an option if you are subscribed to ZIdentity. Step-up authentication enforces stronger authentication and only provides access to applications when the authentication matches the additional authentication levels. The **Allow with Privileged Approval** checkbox is only an option if you have been given Privileged Remote Access (PRA) and is primarily targeted for PRA-enabled application segments. Contact Zscaler Support for more information. Click the **Step-Up Authentication Level** checkbox to select an authentication level from the drop-down menu. The authentication levels must be configured in the Admin Portal before configuring an access policy. If a user is not at the defined authentication level, they are prompted to reinforce their authentication level. If the authentication level matches, then the user can access their resources. To learn more, see [Understanding Step-Up Authentication](/unified/understanding-step-authentication).
By default, access to [applications](/unified/about-defined-application-segments) and [segment groups](/unified/about-segment-groups) is blocked for users until you configure policy rules that explicitly allow access. So, you only need to configure policy rules to block access for specific circumstances or to require approval. For example, if you want to allow access to all applications in your organization for most users but block access for some users, you can configure one policy rule that blocks access for those specific users while another rule allows access to all other users. A first-match principle is used when evaluating policies, so for this scenario, you must list the block rule before the allow rule. To learn more about use cases that call for policy rules that block access, see [Access Policy Configuration Examples](/unified/access-policy-configuration-examples).
-
**Pop-up Message to User**: (Optional) Enter the message you want to display to users when the policy rule’s action and criteria are met. If you are blocking access, ensure that the message helps the user understand why they are being denied access.
This field is only visible if Rule Action is set to Block Access. This setting only affects the behavior of the pop-up notification for the end user. A notification is still received in the Notifications window of Zscaler Client Connector. This feature is only supported for Zscaler Client Connector version 4.7 for Windows.
-
For **Traffic Steering**, under **App Connector Selection Method**: Select **All App Connector groups for the application** or **Specific App Connector, Extranet Resources, or Server groups for the application**.
**Extranet Resources** appears in these options if your organization has the Extranet Application Support feature enabled. To learn more, see [About Extranet](/unified/about-extranet).
- **Connector Type**: If you select **Specific App Connector, Extranet Resources, or Server groups for the application**, choose a connector option:
-
Select App Connector, and then choose which App Connector groups, server groups, or a mixture of both you want the access policy to use.
The maximum limit of selected App Connector groups is 48. If **All App Connector groups for the application** is selected and there are more than 48 configured for your organization, then only 48 App Connector groups are used. This limit applies to newly created or edited policy rules after March 4, 2024.
-
Select **Extranet**, and then choose a partner, location group, and/or location you want the access policy to use.
For extranet, there is a maximum of 10 location groups and 50 locations per policy. Additionally, some features in application segments are not available for extranet. To learn more, see [Configuring Defined Application Segments](/unified/configuring-defined-application-segments).
- For **Criteria**, click **Add Criteria** to add any of the available criteria types. The drop-down menu only displays criteria that are not already in use by the rule, except for **Client Connector Posture Profile** condition sets. You can add up to 10 condition sets.
- [Applications](#apps)
- [Branch Connector Groups](#bcgroups)
- [Chrome Enterprise Browser](#chrome)
- [Client Connector Posture Profiles](#postureprofile)
- [Client Connector Trusted Networks](#networks)
- [Client Types](#client)
- [Cloud Connector Groups](#CloudConnectorGroups)
- [Country Codes](#CountryCodes)
- [Locations](#locations)
- [Machine Groups](#machinegrps)
- [Platforms](#platforms)
- [Risk Scores](#riskscores)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
- [Workload Groups](#workloadgroups)
[See image.](#createnewrule)
The Boolean logic used between **Criteria** is always displayed. For example, when a user requests access to an application, the policy rule is evaluated to check if an application segment OR its segment group are present AND whether any of the SAML attributes are applicable to the user making the request before it grants or denies access. You can always view the **Rule Action** and **Criteria** as well as the applied Boolean logic on the [Access Policy page](/unified/about-access-policy).
- Click **Save**.
[]Choose the application segments and segment groups to which this rule applies:
- **Application Segments**: Choose the [application segments](/unified/about-defined-application-segments), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/unified/configuring-defined-application-segments) appear in the menu. There is no limit to the number you can select.
If you added multiple application segments to the policy rule, an OR Boolean operator is used between them.
There are limits to the number of application segments applied to a rule. For a complete list of ranges and limitations for Access Policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
- **Segment Groups**: Choose the [segment groups](/unified/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/unified/configuring-segment-groups) appear in the menu. There is no limit to the number you can select.
If you added multiple segment groups to the policy rule, an OR Boolean operator is used between them.
[]Choose the Branch Connector groups to which the rule applies. You can search for a specific Branch Connector group, click **Select All Displayed** to apply all Branch Connector groups, or click **Clear All** to remove all selections.
[]Enable Chrome Enterprise Browser to verify users that are accessing private applications via the Chrome Enterprise browser.
Make sure you have configured [Chrome Enterprise Browser Connector settings](/unified/configuring-chrome-enterprise-browser-connector-settings) to allow the Chrome Enterprise browser to integrate.
When enabled, you can also select a [configured Chrome posture profile](/unified/configuring-chrome-posture-profiles) to evaluate criteria for access to private applications.
[]Choose the condition sets to which the rule applies. You can add up to 10 **Client Connector Posture Profile** condition sets to the rule. Click **Add Criteria** to include additional sets.
Each condition set can contain multiple posture profiles to enforce on a user’s device. For each profile, select one of the following:
- **VERIFIED**: Zscaler Client Connector verified the user's device against the criteria specified in the posture profile.
- **VERIFICATION FAILED**: Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile.
Make sure you have [configured the posture profiles](/unified/configuring-device-posture-profiles) within the Zscaler Client Connector Portal. The posture profiles you configure in the Zscaler Client Connector Portal appear in the drop-down menu, where you can search for a specific profile.
If you added multiple posture profile condition sets to the policy rule, an AND Boolean operator is used between them. Each posture profile condition set is evaluated individually.
[See image.](#PostureSetBoolean)
If you added multiple posture profiles within a posture profile condition set, an OR Boolean operator is used between them by default. However, you can toggle this to an AND operator by clicking on it.
[See image.](#DevicePostureBooleanToggle)
[]Choose the trusted networks to which the rule applies, and click **Done**. You can search for a specific trusted network, click **Select All **to have the rule apply to all trusted networks, or click **Clear Selection** to remove all selections. The trusted networks you've configured appear in the menu. There is no limit to the number you can select.
A forwarding profile tells Zscaler Client Connector how to treat traffic from your users' systems in different network environments. When a user connects to a network, Zscaler Client Connector checks to determine what type of network the user is connected to.
If you added multiple trusted networks to the policy rule, an OR Boolean operator is used between them.
Make sure you have [configured your Trusted Network Criteria](/unified/configuring-forwarding-profiles-zscaler-client-connector) within the Zscaler Client Connector Portal. The trusted networks you configure in the Zscaler Client Connector Portal appear in the drop-down menu.
[]Choose the client types to which the rule applies, and click **Done**. You can search for a specific client type, click **Select All** to apply all client types, or click **Clear Selection** to remove all selections. The valid client types are:
- **Client Connector**
- **Client Connector Partner**: To learn more, see [About Partner Devices](/unified/about-partner-devices).
- **Cloud Browser**
- **Cloud Connector**: To learn more, see [About Cloud Connectors](/unified/cloud-connector-management).
- **Branch Connector**: To learn more, see [About Branch Connectors](/unified/branch-connector-management).
- **Machine Tunnel**: To learn more, see [About Machine Tunnels](/unified/about-machine-tunnels).
Access policies can be configured with posture profile criteria for the client type machine tunnel if your end-user device is version 3.9 and later.
- **Web Browser**: To learn more, see [About Browser Access](/unified/about-browser-access).
- **Service Edge**: To learn more, see [Understanding Source IP Anchoring](/unified/understanding-source-ip-anchoring-direct).
If you added multiple client types to the policy rule, an OR Boolean operator is used between them.
Rules using the **Web Browser** or **Service Edge** client types additionally can't use posture profiles or trusted networks criteria. The posture profiles or trusted networks criteria only work with **Client Connector**.
[]The Cloud Connector Group criteria type cannot be configured with the SAML and SCIM Attributes criteria type.
Choose the Cloud Connector groups to which the policy applies, and click **Done**. You can search for a specific Cloud Connector group, click **Select All** to apply all Cloud Connector groups, or click **Clear Selection **to remove all selections. The [Cloud Connector groups you've configured](/zpa/about-cloud-connector-groups) appear in the menu. There is no limit to the number you can select.
If you've added multiple Cloud Connector groups to the policy rule, an AND Boolean operator is used between them.
[]Choose the Branch Connector, Cloud Connector, or other locations and sub-locations to which the rule applies. You can search for a specific Branch Connector, Cloud Connector, or other location, click **Select All Displayed** to apply all locations and sub-locations, or click **Clear All** to remove all selections.
Locations and sub-locations are displayed in the following format:
-
Location without a sub-location:
![Location without a sub-location](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/location-location-type-zia-cloud-03.png)
-
Location with a sub-location:
![Viewing the location criteria](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/sub-location-parent-location-location%20type-zia-cloud-name-04.png)
Location types include:
- **BC **- Branch Connector
- **CC **- Cloud Connector
- **NONE **- Locations other than Branch Connector or Cloud Connector. NONE location types are also used in [Source IP Anchoring configurations](/unified/understanding-source-ip-anchoring-direct), where traffic is routed from these locations to Private Applications.
[]Choose the countries to which this rule applies. You can search for a specific country, click **Select All** to apply the countries visibly listed, click **Clear All** to remove all selections, or click the delete icon to the right of a selected country to remove it from your list. There is no limit to the number you can select. Click **Cancel** to exit the Country Code menu.
The Country Codes criteria type is not supported in [Browser Access](/unified/about-browser-access) or [Privileged Remote Access Applications](/unified/about-privileged-remote-access-applications).
[]Choose the Machine groups to which this rule applies, and click **Done**. You can search for a specific Machine group, click **Select All** to apply all groups, or click **Clear Selection** to remove all selections. The [Machine groups you've configured](/unified/about-machine-groups) appear in the menu. There is no limit to the number you can select.
If a Machine group is selected, **Machine Tunnel** as a client type is also required.
[]Choose the platforms to which the rule applies and click **Save**. This allows you to control which applications are designated to which devices. The valid platform types are:
- Windows
- macOS
- Linux
- iOS
- Android
If you added multiple platforms to the policy rule, an OR Boolean operator is used between them.
[]Select one or more risk scores and click **Save**. Click **Select All** to apply all the risk scores listed, or **Clear All** to remove all selections. Click **Cancel **to exit the Risk Scores menu.
- If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SAML and SCIM Attributes** criteria is replaced with **Session and User Attributes**.
- The SAML and SCIM Attributes criteria type cannot be configured with the Cloud Connector Group criteria type.
[]To use SAML or SCIM Criteria:
- Click **Select IdP** and choose the identity provider (IdP) configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/unified/about-idp-configuration). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or Session Attributes](#saml)
- [SCIM Attributes or User Attributes](#scim)
- [SCIM Groups](#scimgrp)
These criteria appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is the name of the IdP configuration you selected in step a.
[See image.](#idpcriteria)
In order to process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/unified/about-idp-configuration).
If you added multiple attributes or groups to the policy rule, an OR Boolean operator is used between them by default. For example, if you selected FirstName and LastName, the policy rule is only applied to users with the specified FirstName OR LastName for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBooleanToggle)
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: Skips evaluating the criteria for SAML attributes, but continues to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: Does not evaluate this policy rule. You must remove the criteria under SAML Attributes to process the policy rule.
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, the rule is evaluated differently depending on the Boolean operator between the criteria:
- OR: Skips evaluating the criteria for SCIM attributes and SCIM groups, but continues to evaluate the criteria for SAML attributes.
- AND: Does not evaluate this policy rule. You must remove the criteria for SCIM attributes and SCIM groups to process the policy rule.
If you selected multiple IdPs for the policy rule, an OR Boolean operator is used between them by default. For example, you can select one IdP that includes FirstName OR LastName and another IdP that includes Any SAML Attribute. In this case, the policy rule applies to a user authenticating from the first IdP if they have the specified FirstName OR LastName *or* it applies to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBoolean2)
If your [IdP configuration for SSO](/unified/about-idp-configuration) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between policy rules.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the rule action to any user (i.e., the rule applies to all users, groups, departments, etc.).
Alternatively, choose a specific [SAML attribute](/unified/about-saml-attributes) from the drop-down menu if you want to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SAML attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SAML Attributes** option is replaced with **Session Attributes**. The user attributes are populated from the Admin Portal and are used for defining various sign-on policies.
[]Choose a specific SCIM attribute from the drop-down menu to apply the rule action to specific users, groups, departments, etc:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SCIM attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SCIM Attributes** option is replaced with **User Attributes**. The group attributes are populated from the Admin Portal and are used for defining various sign-on policies.
[]Choose a specific SCIM group from the drop-down menu to apply the rule action to a specific group:
- You can search for a specific group, select a listed group, or click **Clear Selection** to remove all selected groups.
- Click **Add More** to add multiple groups, if necessary.
[]
This feature is in Limited availability. Contact Zscaler Support to learn more.
Choose a specific workload group from the drop-down menu to apply the rule action to. To learn more, see [About Workload Groups](/unified/about-workload-groups).
If Workload Group is selected, Cloud Connector as a client type is required.
[]![Add Access Policy window](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/Criteria%20types_0.png)
[]![Add Criteria to an Access Policy](/downloads/zpa/policies/access-policy/configuring-access-policies/zpa-add-access-policy-window-conditional-access.png)
[]![View identity provider, criteria, attribute ](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean.png)
[]![Add Access Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-policy-samlboolean2.png)
[]![Add Access Policy window with Posture Profile Condition Set Boolean](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-posturesetsboolean.png)
[]![Add Access Policy window with Posture Profiles setting](/downloads/zpa/documentation-knowledgebase/policies/access-policy/configuring-access-policies/zpa-accesspolicy-devicepostureboolean.png)