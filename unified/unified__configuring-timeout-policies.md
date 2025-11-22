# Configuring Timeout Policies
Source: https://help.zscaler.com/unified/configuring-timeout-policies
PDF: https://help.zscaler.com/pdf/com/en/1492071.pdf

Timeout policy rules enable you to implement access control based on when a user must reauthenticate and how long a user's application session is idle. To learn more, see [About Timeout Policy](/unified/about-timeout-policy).
For a complete list of ranges and limits for timeout policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
To configure a timeout policy rule:
- Go to the **Timeout Policy** page (Policies > Access Control > Private Applications > Timeout Policy).
- Click **Add Rule**.
The **Add Timeout Policy** window appears.
- In the **Add Timeout Policy** window:
- **Name**: Enter a timeout policy rule name. The name cannot contain special characters, with the exception of hyphens (-) and underscores ( _ ).
- **Description**: (Optional) Enter a description for the policy rule.
- For **Timeouts**:
- **Authentication Timeout**: Specify the time interval used to determine when a user must reauthenticate in order to access an application.
You can only use the **Authentication Timeout** setting within your policy rule if your users are running Zscaler Client Connector version 1.2.1 or later.
- The Zscaler Client Connector certificates have a validity of 365 days from the date of enrollment. If the authentication timeout is set to **Never**, users are only prompted to re-enroll to renew device certificates. To renew device certificates, click **Authenticate **in the **Private Access** screen. In some cases, the certificate renewal might fail because of connectivity issues to the identity provider (IdP). If this occurs, you might need to log out (request a logout password from your administrator if required) and log back in to renew the certificate.
If you are using VMware’s Unified Access Gateway (UAG) for application access, you must create a separate rule and set the **Authentication Timeout** to **Never**.
- If you want to specify a time interval, select **Specific Interval**, then enter a value for the number of **Days(s)**, **Hours(s)**, or **Minute(s)**. The **Authentication Timeout** must be at least 10 minutes.
The reauthentication time interval is based on the SAML assertion's issue date. Typically, identity providers (IdPs) issue assertions using a timestamp that is in the past by approximately 5 minutes. This is done in order to account for possible inconsistent time and date settings on the systems verifying the assertion. In addition, if a configuration change is made on an IdP that also causes a change to the SAML assertion, then the updated assertion is applied to policies after the user reauthenticates.
- **Message to User**: (Optional) Enter the message you want to display to users when they need to reauthenticate based on the **Authentication Timeout** setting. Ensure the message helps the user identify the application that requires reauthentication.
- **Idle Connection Timeout**: Specify how long a user's application session will remain idle before the connection is ended.
- If **Default **is selected:
- For an open TCP session, the timeout is 2 hours.
- For a half-closed TCP session, the default timeout is 6 minutes.
- For a fully-closed TCP session, the session is terminated immediately by default.
- For a UDP session, the default timeout is 60 seconds.
- The idle timeout can be changed for open TCP sessions to reduce resource load on App Connectors and servers. If your App Connectors run out of connections due to port exhaustion or if the application server does not handle idle timeouts well, set an explicit idle timeout.
- If you want to specify a time interval other than the default, select **Specific Interval**, then enter a value for the number of **Days(s)**, **Hours(s)**, or **Minute(s)**. The **Idle Connection Timeout** interval must be at least 10 minutes. For example, in the image below, reauthentication would be required every 2 days. Idle sessions would be closed after 10 minutes, but would not require reauthentication unless the reauthentication timeout was also exceeded.
- For **Criteria**, click **Add Criteria** to add one of the available criteria types. The drop-down menu will only display criteria that are not already in use by the rule, except for **Client Connector Posture Profile** condition sets. You can add up to 10 condition sets.
[See image.](#addcriteria)
- [Applications](#apps)
- [Client Connector Posture Profiles](#postureprofile)
- [Client Types](#client)
- [Platforms](#platforms)
- [SAML and SCIM Attributes or Session and User Attributes](#samlscimattribute)
[See image.](#createnewrule)
The Boolean logic used between **Criteria **is always displayed. For example, when a user requests access to an application, the policy rule is evaluated to check if an any of the SAML attributes are applicable to the user making the request AND if any segment group AND client types are present, before it determines whether reauthentication is required. You can always view the rule's **Action** and **Criteria** as well as the applied Boolean logic on the [Timeout Policy page](/unified/about-timeout-policy).
- Click **Save**.
[]Choose the application segments and segment groups to which this rule applies:
- **Application Segments**: Choose the [application segments](/unified/about-defined-application-segments), and click **Done**. You can search for a specific application segment, click **Select All** to apply all applications segments, or click **Clear Selection** to remove all selections. The [application segments you've configured](/unified/configuring-defined-application-segments) appear in the menu. There is no limit to the number you can select.
If you added multiple application segments to the policy rule, an OR Boolean operator is used between them.
There are limits to the number of application segments applied to a rule. For a complete list of ranges and limitations for Timeout Policy rules, see [Ranges & Limitations](/unified/ranges-limitations).
- **Segment Groups**: Choose the [segment groups](/unified/about-segment-groups), and click **Done**. You can search for a specific segment group, click **Select All** to apply all segment groups, or click **Clear Selection** to remove all selections. The [segment groups you've configured](/unified/configuring-segment-groups) appear in the menu. There is no limit to the number you can select.
If you added multiple segment groups to the policy rule, an OR Boolean operator is used between them.
[]Choose the condition sets to which the rule applies. You can add up to 10 **Client Connector Posture Profile** condition sets to the rule. Click **Add Criteria** to include additional sets.
Each condition set can contain multiple posture profiles to enforce on a user’s device. For each profile, select one of the following:
- **VERIFIED**: Zscaler Client Connector verified the user's device against the criteria specified in the posture profile.
- **VERIFICATION FAILED**: Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile.
Make sure you have configured the posture profiles within the Zscaler Client Connector Portal. The posture profiles you configure appears in the drop-down menu where you can search for a specific profile.
If you added multiple posture profile condition sets to the policy rule, an AND Boolean operator is used between them. Each posture profile condition is evaluated individually.
[See image.](#PostureSetBoolean)
If you added multiple posture profiles within a posture profile condition set, an OR Boolean operator is used between them by default. However, you can toggle this to an AND operator by clicking on it.
[See image.](#PostureBooleanToggle)
[]Choose the client types to which the rule applies, and click **Done**. You can search for a specific client type, click **Select All** to apply all client types, or click **Clear Selection** to remove all selections. The valid client types are:
If you added multiple client types to the policy rule, an OR Boolean operator is used between them.
Rules using the **Web Browser** or **Internet & SAAS Service Edge** client types can not also use posture profiles. The posture profile criteria only works with **Client Connector**.
- **Client Connector**:
- **Cloud Browser**:
The recommended time interval for the Cloud Browser client type is one day. Once the user is authenticated, the session timeout value is the minimum timeout across all timeout policies configured though. After the timeout happens, the user will need to reauthenticate to access applications via Cloud Browser Isolation.
- **Web Browser**: To learn more, see [About Browser Access](/unified/about-browser-access).
- **ZIA Service Edge**: To learn more, see [About Source IP Anchoring](/unified/understanding-source-ip-anchoring-direct).
[]Choose the platforms to which the rule applies and click **Save**. This allows you to control which applications are designated to which devices. The valid platform types are:
- Windows
- macOS
- Linux
- iOS
- Android
If you added multiple platforms to the policy rule, an OR Boolean operator is used between them.
If you are subscribed to ZIdentity for users, the **SAML and SCIM Attributes** criteria is replaced with **Session and User** **Attributes**.
[]To use SAML or SCIM Criteria:
- Click **Select IdP** and choose the IdP configuration you want to include in the policy rule. The IdP must be configured for **User** SSO. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign). If you need to include multiple IdPs in the policy rule, click **Select IdP** again.
- Click **Select SAML and SCIM Criteria** to add the criteria to which this rule applies:
- [SAML Attributes or Session Attributes](#saml)
- [SCIM Attributes or User Attributes](#scim)
- [SCIM Groups](#scimgrp)
These criteria will appear under **SAML and SCIM Attributes** > **<IdP Name>**, where **<IdP Name>** is name of the IdP configuration you selected in step a.
[See image.](#idpcriteria)
In order to process SAML and SCIM criteria in a rule, you must enable the **SAML Attributes for Policy** setting for SAML and the **SCIM Attributes and Groups for Policy** setting for SCIM when configuring an IdP. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign).
If you added multiple attributes or groups to the policy rule, an OR Boolean operator is used between them by default. For example, if you selected FirstName and LastName, the policy rule will only be applied to users with the specified FirstName OR LastName for that IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBooleanToggle)
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SAML Attributes for Policy**) is disabled for SAML, but the policy rule has criteria for SAML attributes, the rule will be evaluated differently depending on the Boolean operator between the criteria:
- OR: Skip evaluating the criteria for SAML attributes, but will continue to evaluate the criteria for SCIM attributes and SCIM groups.
- AND: Will not evaluate this policy rule. You must remove the criteria under SAML Attributes in order to process the policy rule.
If the corresponding [IdP setting](/unified/configuring-idp-single-sign) (**SCIM Attributes and Groups for Policy**) is disabled for SCIM, but the policy rule has criteria for SCIM attributes or SCIM groups, will be evaluted differently depending on the Boolean operator between the criteria:
- OR: Skip evaluating the criteria for SCIM attributes and SCIM groups, but will continue to evaluate the criteria for SAML attributes.
- AND: Will not evaluate this policy rule. You must remove the criteria for SCIM attributes and SCIM groups in order to process the policy rule.
If you selected multiple IdPs for the policy rule, an OR Boolean operator is used between them by default. For example, you can select one IdP that includes FirstName OR LastName and another IdP that includes Any SAML Attribute. In this case, the policy rule will apply to a user authenticating from the first IdP if they have the specified FirstName OR LastName *or* it will apply to any user authenticating from the second IdP. However, you can toggle this to an AND operator by clicking on it.
[See image.](#SAMLBoolean2)
If your [IdP configuration for SSO](/unified/configuring-idp-single-sign) includes SAML attributes or SCIM attributes from multiple IdPs, Zscaler recommends that you do not use the AND Boolean operator between policy rules.
[]By default, the policy rule for **SAML Attributes** is set to **Any SAML attribute**. Keep this if you want to apply the rule action to any user (i.e., the rule will apply to all users, groups, departments, etc.).
Alternatively, choose a specific SAML attribute from the drop-down menu if you want to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SAML attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SAML Attributes** option is replaced with **Session Attributes**. The user attributes are populated from the Admin Portal and are used for defining various sign-on policies.
[]Choose a specific SCIM attribute from the drop-down menu to apply the rule action to specific users, groups, departments, etc.:
- You can search for a specific attribute, select a listed attribute, or click **Clear Selection** to remove all selected attributes.
- After you make a selection, enter the SCIM attribute value (i.e., the users to whom the rule applies) in the text field that appears.
- Click **Add More** to add multiple attributes, if necessary.
If you are subscribed to ZIdentity for users, the **SCIM Attributes** option is replaced with **User Attributes**. The group attributes are populated from the Admin Portal and are used for defining various sign-on policies.
[]Choose a specific SCIM group from the drop-down menu to apply the rule action to a specific group:
- You can search for a specific group, select a listed group, or click **Clear Selection** to remove all selected groups.
- Click **Add More** to add multiple groups, if necessary.
[]![Add Timeout Policy window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/timeout-policy/configuring-timeout-policies/Timeout%20Policies%20criteria%20list_1.png)
[]![Add Criteria to a Timeout Policy](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/timeout-policy/configuring-timeout-policies/zpa-timeoutpolicy-addcriteria.png)
[]![View identity provider, criteria, attribute ](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/timeout-policy/configuring-timeout-policies/zpa-accesspolicy-idp-criteria-attribute.png)
[]![Add Timeout Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/timeout-policy/configuring-timeout-policies/zpa-policy-samlboolean.png)
[]![ Add Timeout Policy window with SAML Attributes setting](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/timeout-policy/configuring-timeout-policies/zpa-policy-samlboolean2.png)
[]![Add Timeout Policy window with Posture Profile Condition Set Boolean](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/timeout-policy/configuring-timeout-policies/zpa-policies-posturesetsboolean.png)
[]![Add Timeout Policy window with Posture Profiles setting](/downloads/zpa/documentation-knowledgebase/access-timeout-policies/timeout-policy/configuring-timeout-policies/zpa-policies-devicepostureboolean.png)