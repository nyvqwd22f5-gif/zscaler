# Adding an IT Services Rule for Cloud App Control
Source: https://help.zscaler.com/zia/adding-it-services-rule-cloud-app-control
PDF: https://help.zscaler.com/pdf/com/en/1400636.pdf

You can create rules to control access to specific cloud applications. Cloud apps are organized into [categories](/zia/cloud-app-categories) to facilitate defining rules for similar applications.
Many companies make use of identity and device management tools, such as Okta or AirWatch. This category allows you to create rules specifically for these and other similar services. You can also specify which applications your users are allowed to access and define a daily quote by bandwidth or time.
When users browse to these sites after their quota has been reached, the Zscaler service displays a message that explains that the content cannot be viewed because they exceeded their daily quota.
Adding a Rule for IT Services
To add a rule for IT Services:
- Go to **Policy** > **URL & Cloud App Control** > **Cloud App Control Policy**.
-
Click **Add** and select **IT Services**.
The **Add IT Services Rule** window appears.
- In the **Add IT Services Rule** window, enter the **Cloud App Control Rule** attributes:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Rank](/zia/what-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/what-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the rule or use the default name.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the Rule Order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
- Define the **Criteria**:
-
**Cloud Applications**: Select **Any** to apply the rule to all cloud applications in this category, or select any number of cloud applications. You can also search for applications.
By default, this field displays the first 100 cloud applications. The subsequent 100 cloud applications are displayed when you select **Click to see more** at the bottom of the list. You can repeat this process to view the remaining cloud applications.
[See image.](#cloud-app-field-with-click-see-more)
-
**Cloud Application Instances**: Select the cloud application instances to which the rule applies. You can select a maximum of 8 instances per rule.
The cloud application instance appears only if its parent application is selected as the cloud application.
-
**Cloud Application Risk Profile**: Select a profile to which the rule applies.
You can either select the **Cloud Application Risk Profile** or the **Cloud Applications** field for the rule.
- **Users**: Select **Any** to apply the rule to all [users](/zia/how-do-i-add-user-account), or select up to 32 users under General Users. If you've enabled the [Policy for Unauthenticated Traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic), you can select **Special Users** to apply this rule to all unauthenticated users, or select specific types of unauthenticated users. You can search for users or click the **Add** icon to add a new user.
- **Groups**: Select **Any** to apply the rule to all [groups](/zia/how-do-i-add-group), or select up to 32 groups. You can search for groups or click the **Add **icon to add a new group.
-
**Departments**:** **Select **Any** to apply the rule to all [departments](/zia/how-do-i-add-department), or select up to 32 departments. If you've enabled the [Policy for Unauthenticated Traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic), you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add **icon to add a new department.
Any rule that applies to [unauthenticated traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic) must apply to all Groups and Departments. So, if you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, select **Any **from the drop-down menus for **Groups** and **Departments**.
-
**Locations**:** **Select **Any** to apply the rule to all [locations](/zia/about-locations), or select up to 32 locations. You can also search for a location or click the **Add **icon to add a new location.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
- **Location Groups**: Select **Any** to apply the rule to all [location groups](/zia/about-location-groups), or select up to 32 location groups. You can also search for a location group.
- **Adaptive Access Profile**: This field shows the adaptive access profile that you want to enforce for the policy. The profiles contain contextual parameters that are constantly monitored for dynamic access control. This option is currently not functional in the ZIA Admin Portal. However, you can contact your Zscaler Account team to subscribe to [Experience Center](/unified/upgrading-zscaler-experience-center) to use this feature. To learn more, see [Understanding Adaptive Access Engine](/unified/understanding-adaptive-access-engine).
- **Time**:** **Select **Always** to apply this rule to all [time intervals](/zia/how-do-i-define-time-intervals), or select up to two time intervals. You can also search for a time interval or click the **Add **icon to add a new time interval.
- **Devices**: Select the [devices](/zia/about-devices) to which the rule applies. You can also search for a device. Selecting no value ignores this criterion in the policy evaluation.
-
**Device Groups**: Select the [device groups](/zia/about-device-groups) to which the rule applies. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation** or **No Client Connector** to apply the rule to the Isolation traffic or to traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores this criterion in the policy evaluation.
The **Cloud Browser Isolation** group is available only if Isolation is enabled for your organization.
- []
**Device Trust Level**: Select the device trust level values (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**) to which the rule applies. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. Selecting no value ignores the criterion in the policy evaluation.
The trust levels assigned to the devices are based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal.
- **User Agent**: Select **Any** to apply the rule to all user agents, or select any number of user agents. You can also search for an agent.
-
**User Risk Profile**: Select the user risk score levels to which the rule applies. Selecting no value ignores this criterion in the policy evaluation.
Users are assigned a risk score based on their browsing activities. A range of risk scores is grouped as a risk score level.
By default, the following user risk score levels are available:
- **Low**: Level with user risk scores ranging from 0 to 29
- **Medium**: Level with user risk scores ranging from 30 to 59
- **High**: Level with user risk scores ranging from 60 to 79
- **Critical**: Level with user risk scores ranging from 80 to 100
Contact Zscaler Support to customize the user risk score range of these levels for your organization.
- Define the **Rule Expiration**:
- **Enable Rule Expiration**: Enable this option to set a validity period for the rule.
- **Start Date and Time**: Select a start date and time. The rule is valid starting on this date and time.
- **End Date and Time**: Select an end date and time. The rule ceases to be valid on this date and time.
- **Time Zone**: Select the time zone in which the rule should be valid.
- Specify the **Action**:
-
**Application Access**: Choose one of the following options:
- [Allow](#allow)
- [Caution](#caution-action)
- [Block](#block)
- [Conditional](#conditional)
- [Isolate](#isolate)
The Isolate option is available only if Isolation is enabled for your organization.
-
**Cascade to URL Filtering**: Enable if you want to enforce the URL Filtering policy on a transaction, even after it's explicitly allowed by the Cloud App Control policy. However, the URL Filtering policy doesn't apply if the Cloud App Control policy blocks the transaction.
This field appears only when the **Allow Cascading to URL Filtering** option is disabled on the **Advanced Settings** page (**Administration** > **Advanced Settings**).
- (Optional) Define the **Notification** settings:
-
**Browser Notification Template**: Select a browser-based EUN message from the drop-down menu to display the message on the browser when the user activity triggers the Cloud App Control Policy rule.
This field appears when the application access is set to either **Caution** or **Block**.
- **End User Notification**: Appears only when a tenant profile is selected. Select **Show** to show the Zscaler Client Connector-based EUN message on endpoints when the user activity triggers the Cloud App Control Policy rule, or select **Hide** if you don't want an EUN message to appear. This field is set to **Show** by default.
- **Custom Message**: Select a custom notification message that you want to show as the Zscaler Client Connector-based EUN. This field is set to the **Default** notification message if no message is selected from the drop-down menu.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
To learn how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/zia/understanding-policy-enforcement).
[]![ZIA Add Cloud Application Rule with Click to See More in the Cloud Applications Field](/downloads/zia/documentation-knowledgebase/policies/cloud-apps/cloud-app-control-policies/adding-it-services-rule-cloud-app-control/ZIA-Add-Cloud-App-Control-Rule-IT-Services-Click-See-More.png)
[]Choose to allow the users to access the selected applications.
- **Daily Bandwidth Quota**: (Optional) The bandwidth quota includes data uploaded to and downloaded from the cloud application. To enforce the quota on each location, do not select specific users, groups, or departments. To enforce the quota on specific users, groups, or departments, [SSL Inspection](/zia/deploying-ssl-inspection) and [authentication](/zia/provisioning-and-authenticating-users) must be enabled. If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization’s time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The time quota is based on the amount of time elapsed in a session while uploading and downloading data. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
-
**Tenant Profiles**: Appears only when **Google Login Services**, **Microsoft Login Services**,** Webex Login Services**, or **Zoho Login Services** is selected as the cloud application. You can select the tenant profiles for which you want to apply the rule. To learn more, see [About Tenant Profiles](/zia/about-tenant-profiles).
For the **Microsoft Login Services** cloud application, you can select any one of the following profile types per rule:
- **Version 1**: You can select multiple profiles per rule only if the tenant directory ID and the **Allow Personal Office 365 Domains** field selection are the same for the profiles.
- **Version 2**: You can select only one profile per rule.
Ensure that the applications selected under the tenant profiles are not exempted from SSL Inspection.
[]Choose to display an EUN that cautions users before allowing them access to the selected applications.
You can select this action for only one of the following request methods: **CONNECT**, **GET**, or **HEAD**.
- **Daily Bandwidth Quota**: (Optional) The bandwidth quota includes data uploaded to and downloaded from the cloud application. To enforce the quota on each location, do not select specific users, groups, or departments. To enforce the quota on specific users, groups, or departments, [SSL Inspection](/zia/deploying-ssl-inspection) and [authentication](/zia/provisioning-and-authenticating-users) must be enabled. If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization’s time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The time quota is based on the amount of time elapsed in a session while uploading and downloading data. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
[]Choose to** **block the users from accessing the selected applications.
[]Choose to conditionally allow the users to access the selected applications.
-
**Conditional Access**: Allows access to the selected applications by enforcing step-up authentication. Step-up authentication enforces stronger authentication and only provides access to applications when the authentication satisfies the additional authentication levels. In the **Authentication** **Level** field, select an authentication level from the drop-down menu. The authentication levels must be configured in the ZIdentity Admin Portal before configuring a policy in the ZIA Admin Portal to select this option. When you try to access applications that require additional authentication, Zscaler Client Connector displays a pop-up notification prompting you to verify your access. To learn more, see [Understanding Step-Up Authentication](/zidentity/understanding-step-up-authentication).
This option is available only if your organization is provisioned with ZIdentity for end users and the [traffic forwarding method](/zia/choosing-traffic-forwarding-methods) is Zscaler Client Connector. However, if your traffic is routed via a Private Service Edge or Virtual Service Edge, conditional access is not supported and the user access to the applications is blocked with a notification from the browser. Conditional access doesn't apply to [Isolation](/isolation/what-is-isolation) traffic. To enable this feature, you can raise a provisioning support ticket.
- **Daily Bandwidth Quota**: (Optional) The bandwidth quota includes data uploaded to and downloaded from the cloud application. To enforce the quota on each location, do not select specific users, groups, or departments. To enforce the quota on specific users, groups, or departments, [SSL Inspection](/zia/deploying-ssl-inspection) and [authentication](/zia/provisioning-and-authenticating-users) must be enabled. If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization’s time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The time quota is based on the amount of time elapsed in a session while uploading and downloading data. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
[]Choose to isolate all the traffic that matches the cloud app control rule through a remote browser. To learn more, see [What Is Isolation?](/zia/about-cloud-browser-isolation)
-
**Isolation Profile**: Appears when you select **Isolate**. You can choose the isolation profiles to which the rule applies.
Ensure to [create isolation profiles](/zia/creating-isolation-profile-cloud-browser-isolation) for your organization.
- **Daily Bandwidth Quota**: (Optional) The bandwidth quota includes data uploaded to and downloaded from the cloud application. To enforce the quota on each location, do not select specific users, groups, or departments. To enforce the quota on specific users, groups, or departments, [SSL Inspection](/zia/deploying-ssl-inspection) and [authentication](/zia/provisioning-and-authenticating-users) must be enabled. If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization’s time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The time quota is based on the amount of time elapsed in a session while uploading and downloading data. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
-
**Tenant Profiles**: Appears only when **Google Login Services**, **Microsoft Login Services**,** Webex Login Services**, or **Zoho Login Services** is selected as the cloud application. You can select the tenant profiles for which you want to apply the rule. To learn more, see [About Tenant Profiles](/zia/about-tenant-profiles).
For the **Microsoft Login Services** cloud application, you can select one of the following profile types per rule:
- **Version 1**: You can select multiple profiles per rule only if the tenant directory ID and the **Allow Personal Office 365 Domains** field selection are the same for the profiles.
- **Version 2**: You can select only one profile per rule.
Ensure that the applications selected under the tenant profiles are not exempted from SSL Inspection.