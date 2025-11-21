# Configuring the URL Filtering Policy
Source: https://help.zscaler.com/zia/configuring-url-filtering-policy
PDF: https://help.zscaler.com/pdf/com/en/1399426.pdf

[Watch a video about URL Filtering Policy, including how to configure policy rules](https://fast.wistia.net/embed/iframe/jqu9x18c3e)
You can add a new URL Filtering rule from the beginning or copy an existing rule and change its settings. There is also a [recommended URL Filtering policy](/zia/recommended-url-cloud-app-control-policy). You can capture and store traffic blocked through this policy as PCAP files. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture).
By default, the Cloud App Control policy takes precedence over the URL Filtering policy. If a user requests a cloud app that you explicitly allow with Cloud App Control policy, the service only applies the Cloud App Control policy and not the URL Filtering policy. For example, if you have a Cloud App Control policy rule that allows viewing Facebook, but a URL Filtering policy rule that blocks www.facebook.com, a user is still allowed to view Facebook. This is because, by default, the service does not apply the URL Filtering policy if a Cloud App Control policy rule allows the transaction.
However, this behavior changes if you enable Allow Cascading to URL Filtering in [Advanced Settings](/zia/about-advanced-settings). If you do, the service applies the URL Filtering policy even if it applies a Cloud App Control policy rule allowing the transaction. Therefore, in the preceding example, with cascading enabled, the service applies the URL Filtering policy and blocks the user from Facebook. If the example changed so that you had a Cloud Control Policy rule that blocked Facebook, while URL Filtering allowed it, Facebook is blocked even if Allow Cascading to URL Filtering was enabled. If a user requests a Cloud App for which you have not configured a Cloud App Control policy rule (for example, the user requests ebay.com, and you don't have a Cloud App Control rule for ebay.com), the service still evaluates and applies the URL Filtering policy. To see how this policy fits into the overall order of policy enforcement, see [About Policy Enforcement](/zia/about-policy-enforcement).
Non-English characters are not supported in URL Filtering, except those from the ISO/IEC 8859-1 character set.
Policy Execution
The URL Filtering rules consist of a series of logical operators between their criteria. The rules are triggered based on the result of the following logical operations between the criteria:
Source IP Groups (`AND`) Source Countries (`AND`) URL Categories (`AND`) [Users (`OR`) Groups (`OR`) Departments] (`AND`) User Risk Profile (`AND`) [Location Groups (`OR`) Locations] (`AND`) Time (`AND`) Request Methods (`AND`) Protocols (`AND`) User Agent (`AND`) [Device Groups (`OR`) Devices] (`AND`) Device Trust.
Adding a URL Filtering Rule
To add a URL Filtering rule:
- Go to** Policy **>** URL & Cloud App Control**.
-
Click **Add URL Filtering Rule**. You can also copy an existing rule by clicking the **Duplicate **icon.
The **Add URL Filtering Rule** window appears.
- In the **Add URL Filtering Rule** window, enter the **URL Filtering Rule **attributes:
-
**Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [Admin Rank](/zia/what-admin-rank), your assigned admin rank determines the rule order values you can select.
The evaluation of the policy rules stops at the first match.
- **Admin Rank**: Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/what-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the rule or use the default name.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
- Define the **Criteria**. You can either choose from the list or add an item.
- **Source IP Groups**: Select any number of [source IP groups](/zia/about-source-ip-groups). You can also search for source IP groups or click the **Add** icon to add a new [source IP group](/zia/configuring-source-ip-groups). Selecting no value ignores this criterion in the policy evaluation.
-
**Source Countries**: Select any number of source countries from which the traffic originates. You can also search for source countries. When configuring this criterion, you can either choose the **Include** option to apply the rules to the selected countries or choose the **Exclude** option to apply the rules to all the countries except those that are selected. Selecting no value ignores this criterion in the policy evaluation.
If you choose the **Exclude** option, you must select the countries you want to exclude. However, it's not mandatory to select countries if you choose the **Include** option.
-
**URL Categories**: Select any number of [URL super-categories or categories or both](/zia/about-url-categories). In this drop-down menu, you can also search for categories or click the **Add** icon to add a new [custom category](/zia/adding-custom-url-categories). Selecting no value ignores this criterion in the policy evaluation.
(Optional) Click the **Add** icon next to this field to add an additional **URL Categories **field to the criteria. The **URL Categories** fields are connected with a logical `AND` operator. This allows you to create rules that are triggered when it matches the selected categories in both the **URL Categories** fields. For example, a block rule is created with the Social Networking category selected in one of the **URL Categories **fields and the Gambling category selected in the other. If the URLs belong to both the categories (i.e., Social Networking and Gambling), only then access to the URLs is blocked.
[See image.](#url-cat-fields)
This is the only place you can select the Newly Registered and Observed Domains category. You can also select [custom TLD categories](/zia/about-tld-categories) in this field.
- **Adaptive Access Profile**: This field shows the adaptive access profile that you want to enforce for the policy. The profiles contain contextual parameters that are constantly monitored for dynamic access control. This option is currently not functional in the ZIA Admin Portal. However, you can contact your Zscaler Account team to subscribe to [Experience Center](/unified/upgrading-zscaler-experience-center) to use this feature. To learn more, see [Understanding Adaptive Access Engine](/unified/understanding-adaptive-access-engine).
- **Users**:** **Select up to 32 general or special [users](/zia/adding-user-account) or both. Select **General Users** for all authenticated users and **Special Users** for all unauthenticated users If you've enabled the [Policy for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic). You can search for users or click the** Add** icon to add a new user. Selecting no value ignores this criterion in the policy evaluation.
- **Groups**:Select up to 32 [groups](/zia/how-do-i-add-group). You can search for groups or click the **Add** icon to add a new group. Selecting no value ignores this criterion in the policy evaluation.
-
**Departments**:** **Select** **up to 32 [departments](/zia/how-do-i-add-department). If you've enabled the [Policy for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic), you can select Special Departments to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department. Selecting no value ignores this criterion in the policy evaluation.
Any rule that applies to [unauthenticated traffic](/zia/configuring-policies-for-unauthenticated-traffic) also applies to the groups and users that are selected. So, if you have chosen to apply this rule to unauthenticated traffic for the following fields:
- **Users**: Either **Departments**, **Groups**, or both are ignored in the policy evaluation if there isn't any specific selection in the respective fields.
- **Departments**: Either **Users**, **Groups**, or both are ignored in the policy evaluation if there isn't any specific selection in the respective fields.
-
**User Risk Profile**: Select the user risk score levels to which the rule applies. Selecting no value ignores the criterion in the policy evaluation.
Users are assigned a risk score based on their browsing activities. A range of risk scores is grouped as a risk score level.
By default, the following user risk score levels are available:
- **Low**: Level with user risk scores ranging from 0 to 29
- **Medium**: Level with user risk scores ranging from 30 to 59
- **High**: Level with user risk scores ranging from 60 to 79
- **Critical**: Level with user risk scores ranging from 80 to 100
Contact Zscaler Support to customize the user risk score range of these levels for your organization.
-
**Locations**:** **Select up to 32 [locations](/zia/about-locations). You can also search for a location or click the** Add** icon to add a new location. Selecting no value ignores the criterion in the policy evaluation.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
-
**Location Groups**: Select up to 32 [location groups](/zia/about-location-groups). You can also search for a location group. Selecting no value ignores this criterion in the policy evaluation.
If the values selected for **Locations** are not part of the selected **Location Groups**, then the rule triggers when either the **Locations** value or the **Location Groups** value matches. For example, If you select **London** for **Locations** and **USA** for **Location Groups**, then the rule triggers when either it matches **London** for **Locations** or **USA** for **Location Groups**.
-
**Request Methods**:** **Select the required HTTP request methods for which you want to apply the rule. You can also search for a specific HTTP request method.
[]The following HTTP request methods are available:
- **OPTIONS**: Requests for information about communication options for the specified resource.
- **GET**: Requests for and retrieves the specified resource from the server.
- **HEAD**: Requests for and retrieves only the header information from the server. This is similar to the `GET` request but does not retrieve a response body from the server.
- **POST**: Requests the specified resource to accept the data enclosed in the request message and process it according to the resource’s semantics.
- **PUT**: Requests the specified resource to create or replace the data enclosed in the request message.
- **DELETE**: Requests the server to delete the specified resource.
- **TRACE**: Requests a remote loopback of the message along the path to the target resource. This method is useful for diagnostic purposes.
- **CONNECT**: Requests an HTTP Proxy server to tunnel the TCP connection with the client.
- **PROPFIND**: Requests for and retrieves the properties of the specified resource from the server.
- **PROPPATCH**: Requests the specified resource to set or remove properties enclosed in the request message.
- **COPY**: Requests the specified resource to create a duplicate of it.
- **MOVE**: Requests the specified resource to move to the location enclosed in the request message.
- **MKCOL**: Requests the specified resource to create a new collection (directory) at the location enclosed in the request message.
- **LOCK**: Requests the server to lock the specified resource.
- **UNLOCK**: Requests the server to unlock the specified resource.
- **PATCH**: Requests the specified resource to apply partial modifications to it.
- **OTHER**: All other request methods.
This criterion is mandatory, and you must select a value for it.
- **Time**: Select **Always** to apply this rule to all [time intervals](/zia/how-do-i-define-time-intervals), or select up to two time intervals. You can also search for a time interval or click the **Add** icon to add a new time interval.
- []**Protocols**: Select the protocols to which the rule applies. Selecting no value ignores this criterion in the policy evaluation.
- **DNS Over HTTPS**: URLs that use DNS Over HTTPS.
- **FTP over HTTP**: URLs that use FTP over HTTP.
- **HTTP**: URLs that use HTTP.
- **HTTP Proxy**: URLs that use HTTP Proxy server when the client is configured in explicit proxy mode, which makes the HTTP `CONNECT` request to the proxy server to tunnel the TCP connections. The tunnel is typically set up when using TLS.
- **HTTPS**: URLs that use HTTP encrypted by TLS/SSL.
- **Native FTP**: URLs that use FTP.
- **SSL**: URLs that use SSL encryption and haven't been decrypted. For example, URLs you've [exempted from SSL Inspection](/zia/about-ssl-inspection#configure-ssl-inspection-policy).
- **Tunnel**: Encrypted URLs that use an unidentified protocol. For example, URLs from tunneling applications such as Telnet or SSH that are encapsulated in HTTP or HTTPS.
- **Tunnel SSL**: Undecodable protocol within an SSL connection.
- **WebSocket**: URLs that use WebSocket.
- **WebSocket SSL**: URLs that use WebSocket within an SSL connection.
- **User Agent**: Select any number of user agents to which the rule applies. You can also search for an agent. Selecting no value ignores this criterion in the policy evaluation.
- **Devices**: Select the [devices](/zia/about-devices) to which the rule applies. You can also search for a device. Selecting no value ignores this criterion in the policy evaluation.
-
**Device Groups**: Select the [device groups](/zia/about-device-groups) to which the rule applies. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation**, **IoT**, or **No Client Connector** to apply the rule to Isolation traffic, IoT traffic, or traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores this criterion in the policy evaluation.
The **Cloud Browser Isolation** and **IoT **groups are available only if Isolation and IoT discovery are enabled for your organization, respectively.
- **Workload Groups**: Select up to 8 [workload groups](/zia/about-workload-groups) for which you want to apply the rule. You can also search for a workload group. Selecting no value ignores the criterion in the policy evaluation.
- []
**Device Trust Level**: Select the device trust level values (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**) to which the rule applies. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. Selecting no value ignores the criterion in the policy evaluation.
The trust levels assigned to the devices are based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal.
- **HTTP Header Profiles**: Select up to 16 [HTTP header profiles](/zia/about-http-header-profile) for which you want to apply the rule. You can also search for a profile. Selecting no value ignores this criterion in the policy evaluation.
-
Define the **Rule Expiration**:
- **Enable Rule Expiration**: Enable this option to set a validity period for the rule.
- **Start Date and Time**: Select a start date and time. The rule is valid starting on this date and time.
- **End Date and Time**: Select an end date and time. The rule ceases to be valid on this date and time.
- **Time Zone**: Select the time zone in which the rule should be valid.
You can use the rule expiration feature to temporarily allow or block access for a set period of time to a category if any configured rules block or allow access to it, respectively.
After the rule expires, Zscaler either blocks or allows the traffic based on the default rules configured for your organization.
- [Select the Action for the rule.](#Action)
- (Optional) Define the notification settings:
-
**Browser Notification Template**: Select a browser-based EUN message from the drop-down menu to display the message on the browser when the user activity triggers the Cloud App Control Policy rule.
This field appears when the application access is set to either **Caution** or **Block**.
- **Description**:** **(Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of ZIA Add URL Filtering Page with Add URL Categories](/downloads/zia/documentation-knowledgebase/policies/url-filtering/configuring-url-filtering-policy/ZIA-URL-Filtering-Policy-Page-With-Add-Icon.png)
![Screenshot of ZIA Add URL Filtering Page with Two URL Categories](/downloads/zia/documentation-knowledgebase/policies/url-filtering/configuring-url-filtering-policy/ZIA-URL-Filtering-Policy-Page-Two-URL-Categories.png)
- []**Allow**:** **Select this to allow access to all sites in the selected [URL categories](/zia/about-url-categories).
-
**Daily Bandwidth Quota**: (Optional) The daily bandwidth limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. To enforce the quota on specific users, groups, or departments, Zscaler recommends that IP surrogacy is used to aid in identification. To learn more, see [About Surrogate IP](/zia/what-surrogate-ip).
In addition, if you have different policies for different groups, Zscaler recommends that you create a catch-all “any” user policy with a higher limit. This catch-all policy should only apply to unidentified users (do not use “any” user to define “all remaining groups or departments”). This is helpful if you encounter a scenario where there are a high number of unidentified users as the users have a higher combined limit, facilitating continuity of service.
If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization's time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The daily time limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
-
**HTTP Header Insertion Profile**: Appears only when you select **Allow**. Select up to 16 [HTTP header insertion profiles](/zia/about-http-header-insertion-profile) for which you want to apply the rule. You can also search for a profile. Selecting no value ignores this criterion in the policy evaluation.
- If the rule is triggered and action is set to **Allow**, then the headers from the selected profiles are inserted.
- The HTTP custom header insertion works only for custom URL categories.
-
**Caution**: Select to display an EUN that cautions users before allowing them access to the site. When you select this value, the service can either display the default EUN or redirect users to an EUN that is hosted on the site you specify in the **Redirect URL** field.
You can select this action for only one of the following request methods: **CONNECT**, **GET**, or **HEAD**.
-
[]**Daily Bandwidth Quota**: (Optional) The daily bandwidth limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. To enforce the quota on specific users, groups, or departments, Zscaler recommends that IP surrogacy is used to aid in identification. To learn more, see [About Surrogate IP](/zia/what-surrogate-ip).
In addition, if you have different policies for different groups, Zscaler recommends that you create a catch-all “any” user policy with a higher limit. This catch-all policy should only apply to unidentified users (do not use “any” user to define “all remaining groups or departments”). This is helpful if you encounter a scenario where there are a high number of unidentified users as the users have a higher combined limit, facilitating continuity of service.
If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization's time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- []**Daily Time Quota**: (Optional) The daily time limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
- []**Redirect URL**:** **(Optional) Leave the field blank to display the service's default [notification](/zia/about-acceptable-use-policy-and-end-user-notifications). If you want to redirect users to a site that hosts a custom notification, enter the site URL. The URL requires the schema (for example, https://redirect.company.com/redirectpage.cgi) and can be HTTP or HTTPS. During the redirection, all query parameters are sent to the external site to enable notification customization.
-
[]**Block**:** **Select to block access to all sites in the selected URL categories.
- **Allow Override** appears when you select **Block**. Enable this option to allow specific [users](/zia/adding-user-account) or [groups](/zia/how-do-i-add-group) to access the blocked site.
- **Override Users**:** **Select **Any** to allow the override to all users, or select up to 4 users. You can search for users or click the **Add **icon to add a new user. You cannot select users if you want to select override groups.
- **Override Groups**:** **Select **Any** to allow the override to all groups, or you can select up to 8 groups. You can search for groups or click the **Add **icon to add a new group. You cannot select groups if you want to select override users.
If you enable this option, the EUN provides the users with a link to access the blocked page. The users are then prompted to enter their single sign-on credentials or hosted database credentials based on the [Enable Identity-based Block Override](/zia/configuring-advanced-url-policy-settings#Enable-block-override) settings. The authenticated users are allowed to access the blocked page only during their current browser session. They must reauthenticate if they try to access it through another browser session.
- **Redirect URL**:** **(Optional) If you choose not to allow an override, the service blocks access and displays a notification. The service can either display the default EUN or redirect users to an EUN that is hosted on the site you specify in the **Redirect URL** field. Leave the field blank to display the service’s default [notification](/zia/about-acceptable-use-policy-and-end-user-notifications). If you want to redirect users to a site that hosts a custom notification, enter the site URL. The URL requires the schema (for example, https://redirect.company.com/redirectpage.cgi) and can be HTTP or HTTPS. During the redirection, all query parameters are sent to the external site to enable notification customization.
- **Capture**: Appears when you select **Block** while Traffic Capture is enabled. Enable this option to capture and store traffic in PCAP files. To learn more, see [Configuring Traffic Capture Settings](/zia/configuring-traffic-capture).
-
**Isolate**: Select to isolate all the traffic that matches the URL filtering rule through a remote browser. To learn more, see [What Is Isolation?](/zia/about-cloud-browser-isolation)
-
**Isolation Profile**: Appears when you select **Isolate**. You can choose the isolation profiles to which the rule applies.
Ensure to [create isolation profiles](/zia/creating-isolation-profile-cloud-browser-isolation) for your organization.
-
**Daily Bandwidth Quota**: (Optional) The daily bandwidth limit allowed for uploading and downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. To enforce the quota on specific users, groups, or departments, Zscaler recommends that IP surrogacy is used to aid in identification. To learn more, see [About Surrogate IP](/zia/what-surrogate-ip).
In addition, if you have different policies for different groups, Zscaler recommends that you create a catch-all “any” user policy with a higher limit. This catch-all policy should only apply to unidentified users (do not use “any” user to define “all remaining groups or departments”). This is helpful if you encounter a scenario where there are a high number of unidentified users as the users have a higher combined limit, facilitating continuity of service.
If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization's time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The daily time limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
This action is available only if Isolation is enabled for your organization.
- **Conditional**: Select to provide conditional access to the URL to all sites in the selected [URL categories](/zia/about-url-categories).
-
**Conditional Access**: Allows access to the selected URL categories by enforcing step-up authentication. Step-up authentication enforces stronger authentication and only provides access to sites when the authentication satisfies the additional authentication levels. In the **Authentication** **Level** field, select an authentication level from the drop-down menu. The authentication levels must be configured in the ZIdentity Admin Portal before configuring a URL filtering policy in the ZIA Admin Portal to select this option. When you try to access websites that require additional authentication, Zscaler Client Connector displays a pop-up notification prompting you to verify your access. To learn more, see [Understanding Step-Up Authentication](/zidentity/understanding-step-up-authentication).
This option is available only if your organization is provisioned with ZIdentity for end users and the [traffic forwarding method](/zia/choosing-traffic-forwarding-methods) is Zscaler Client Connector. However, if your traffic is routed via a Private Service Edge or Virtual Service Edge, conditional access is not supported and the user access to the URL category is blocked with a notification from the browser. Conditional access doesn't apply to [Isolation](/isolation/what-is-isolation) traffic. To enable this feature, you can raise a provisioning support ticket.
-
**Daily Bandwidth Quota**: (Optional) The daily bandwidth limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. To enforce the quota on specific users, groups, or departments, Zscaler recommends that IP surrogacy is used to aid in identification. To learn more, see [About Surrogate IP](/zia/what-surrogate-ip).
In addition, if you have different policies for different groups, Zscaler recommends that you create a catch-all “any” user policy with a higher limit. This catch-all policy should only apply to unidentified users (do not use “any” user to define “all remaining groups or departments”). This is helpful if you encounter a scenario where there are a high number of unidentified users as the users have a higher combined limit, facilitating continuity of service.
If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization's time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The daily time limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
-
**ICAP Receiver**: Select an ICAP receiver to forward the inbound and outbound traffic (e.g., client request and server response) of all sites in the selected URL categories to the ICAP receiver. To learn more, see [About ICAP Receivers](/zia/about-icap-receivers).
This action is available only if ICAP Receivers is enabled for your organization.