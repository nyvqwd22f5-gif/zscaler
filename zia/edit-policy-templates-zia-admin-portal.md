# Edit Policy Templates in the ZIA Admin Portal
Source: https://help.zscaler.com/zia/edit-policy-templates-zia-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1499676.pdf

You can edit a policy template with different policies on the ZIA Admin Portal from the [Policy Template page](/zia/about-policy-template). You can save and synchronize policies for multiple tenants under multiple clouds.
To edit a policy template on ZIA:
- Go to the **Policy Template **page.
-
Click the **Edit Policy Template on ZIA **icon to redirect to the ZIA Admin Portal.
[See image.](#edit-image)
-
On the ZIA Admin Portal page, you can:
- [Add URL Filtering Rule](#add-url-filtering-rule)
- [Add URL Categories](#custom-url-category)
- [Edit URL Filtering and URL Categories](/zia/editing-items)
- [Delete URL Filtering and URL Categories](/zia/editing-items)
To learn more, see [Add URL Filtering Rule](/zia/configuring-url-filtering-policy), [About URL Filtering](/zia/about-url-filtering), [Add URL Categories](/zia/configuring-custom-url-categories), and [About URL Categories](/zia/about-url-categories).
[]![Policy Template Page](/downloads/zia/zscaler-management-portal-partners/administration/edit-policy-template-zia-admin-portal/Edit%20on%20ZIA.png)
[]You can add a new URL Filtering rule, copy an existing rule, or change its settings.
To add a URL Filtering Rule:
- Go to** Policy **>** URL & Cloud App Control**.
-
Click **Add URL Filtering Rule**. You can also copy an existing rule by clicking the **Duplicate **icon.
The **Add URL Filtering Rule** window appears.
The fields such as Rule Label, Source IP Groups, Users, Groups, Departments, Locations, Location Groups, Devices, Device Groups, Device Trust Level, and HTTP Header Profiles in the URL Filtering Rule are not synchronized with the user and are not editable.
-
In the **Add URL Filtering Rule** window:
-
**Rule Order**: Select the rule order from the drop-down menu. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order.
This option is only editable if you enable **Allow Policy Rule Reorder **in the Partner Portal (Policy Template > Add Policy Template > Allow Policy Rule Reorder).
- **Rule Name**: Enter a unique name for the rule or use the default name.
- **Rule Status**: An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The service skips it and moves to the next rule.
- **URL Categories**: Select the URL categories, or search for the categories from the drop-down menu.
-
**Request Methods**:** **Select the required HTTP request methods for which you want to apply the rule. You can also search for a specific HTTP request method.
The following HTTP request methods are available:
- **OPTIONS**: Requests for information about communication options for the specified resource.
- **GET**: Requests for and retrieves the specified resource from the server.
- **HEAD**: Requests for and retrieves only the header information from the server. This is similar to the `GET` request but does not retrieve a response body from the server.
- **POST**: Requests the specified resource to accept the data enclosed in the request message and processes the data according to the resource’s semantics.
- **PUT**: Requests the specified resource to create or replace the data enclosed in the request message.
- **DELETE**: Requests the server to delete the specified resource.
- **TRACE**: Requests a remote loop-back of the message along the path to the target resource. This method is useful for diagnostic purposes.
- **CONNECT**: Requests an HTTP Proxy server to tunnel the TCP connection with the client.
- **OTHER**: All other request methods.
This criterion is mandatory, and you must select a value for it.
- **Time**: Select **Always** to apply this rule to all [time intervals](/zia/how-do-i-define-time-intervals), or select up to two time intervals.
- **Protocols**: Select the protocols to which the rule applies. Selecting no value ignores this criterion in the policy evaluation.
- **DNS Over HTTPS**: URLs that use DNS Over HTTPS.
- **FTP over HTTP**: URLs that use FTP over HTTP.
- **HTTP**: URLs that use HTTP.
- **HTTP Proxy**: URLs that use the HTTP Proxy server when the client is configured in explicit proxy mode, which makes the HTTP `CONNECT` request to the proxy server to tunnel the TCP connections. The tunnel is typically set up when using TLS.
- **HTTPS**: URLs that use HTTP encrypted by TLS/SSL.
- **Native FTP**: URLs that use FTP.
- **SSL**: URLs that use SSL encryption and haven't been decrypted. For example, URLs you've [exempted from SSL inspection](/zia/about-ssl-inspection#configure-ssl-inspection-policy).
- **Tunnel**: Encrypted URLs that use an unidentified protocol. For example, URLs from tunneling applications such as Telnet or SSH that are encapsulated in HTTP or HTTPS.
- **Tunnel SSL**: Undecodable protocol within an SSL connection.
- **WebSocket**: URLs that use WebSocket.
- **WebSocket SSL**: URLs that use WebSocket within an SSL connection.
- **User Agent**: Select any number of user agents to which the rule applies. You can also search for an agent. Selecting no value ignores this criterion in the policy evaluation.
- **Enable Rule Expiration**: Enable this option to set a validity period for the rule.
- **Start Date and Time**: Select a start date and time. The rule is valid starting on this date and time.
- **End Date and Time**: Select an end date and time. The rule ceases to be valid on this date and time.
- **Time Zone**: Select the time zone in which the rule is valid.
- [Select the **Action** for the rule.](#action-rule)
- **Description**:** **(Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
[See image.](#add-url-filtering-rule-image)
- Click **Save & Sync.**
- []**Allow**:** **Select this to allow access to all sites in the selected [URL categories](/zia/about-url-categories).
-
**Daily Bandwidth Quota**: (Optional) The daily bandwidth limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. To enforce the quota on specific users, groups, or departments, Zscaler recommends that IP surrogacy is used to aid in identification. To learn more, see [About Surrogate IP](/zia/what-surrogate-ip).
In addition, if you have different policies for different groups, Zscaler recommends that you create a catch-all “any” user policy with a higher limit. This catch-all policy should only apply to unidentified users (do not use “any” user to define “all remaining groups or departments”). This is helpful if you encounter a scenario where there are a high number of unidentified users as the users have a higher combined limit, facilitating continuity of service.
If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization's time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The daily time limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
-
**Caution**: Select to display an End User Notification (EUN) that cautions users before allowing them access to the site. When you select this value, the service can either display the default EUN or redirect users to an EUN that is hosted on the site you specify in the **Redirect URL** field.
You can select this action for only one of the following request methods: **CONNECT**, **GET**, or **HEAD**.
-
**Daily Bandwidth Quota**: (Optional) The daily bandwidth limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. To enforce the quota on specific users, groups, or departments, Zscaler recommends that IP surrogacy is used to aid in identification. To learn more, see [About Surrogate IP](/zia/what-surrogate-ip).
In addition, if you have different policies for different groups, Zscaler recommends that you create a catch-all “any” user policy with a higher limit. This catch-all policy should only apply to unidentified users (do not use “any” user to define “all remaining groups or departments”). This is helpful if you encounter a scenario where there are a high number of unidentified users as the users have a higher combined limit, facilitating continuity of service.
If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization's time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The daily time limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
- **Redirect URL**:** **(Optional) Leave the field blank to display the service's default [notification](/zia/about-acceptable-use-policy-and-end-user-notifications). If you want to redirect users to a site that hosts a custom notification, enter the site URL. The URL requires the schema (for example, https://redirect.company.com/redirectpage.cgi) and can be HTTP or HTTPS. During the redirection, all query parameters are sent to the external site to enable notification customization.
-
**Block**:** **Select to block access to all sites in the selected URL categories.
- **Allow Override** appears when you select **Block**. Enable this option to allow specific [users](/zia/adding-user-account) or [groups](/zia/how-do-i-add-group) to access the blocked site.
- **Override Users**:** **Select **Any** to allow the override to all users, or select up to 32 users. You can search for users or click the **Add **icon to add a new user. You cannot select users if you want to select override groups.
-
**Override Groups**:** **Select **Any** to allow the override to all groups, or you can select up to 32 groups. You can search for groups or click the **Add **icon to add a new group. You cannot select groups if you want to select override users.
The default limit of users and groups is expandable. To increase the limits, please contact your sales or accounts team.
If you enable this option, the EUN provides the users with a link to access the blocked page. The users are then prompted to enter their single sign-on credentials or hosted database credentials based on the [Enable Identity-based Block Override](/zia/configuring-advanced-url-policy-settings#Enable-block-override) settings. The authenticated users are allowed to access the blocked page only during their current browser session. They must re-authenticate if they try to access it through another browser session.
- **Redirect URL**:** **(Optional) If you choose not to allow an override, the service blocks access and displays a notification. The service can either display the default EUN or redirect users to an EUN that is hosted on the site you specify in the **Redirect URL** field. Leave the field blank to display the service’s default [notification](/zia/about-acceptable-use-policy-and-end-user-notifications). If you want to redirect users to a site that hosts a custom notification, enter the site URL. The URL requires the schema (for example, https://redirect.company.com/redirectpage.cgi) and can be HTTP or HTTPS. During the redirection, all query parameters are sent to the external site to enable notification customization.
- **Capture**: Appears when you select **Block** while Traffic Capture is enabled. Enable this option to capture and store traffic in packet capture (PCAP) files. To learn more, see [Configuring Traffic Capture Settings](/zia/configuring-traffic-capture).
-
**Isolate**: Select to isolate all the traffic that matches the URL filtering rule through a remote browser. To learn more, see [What Is Isolation?](/zia/about-cloud-browser-isolation).
-
**Isolation Profile**: Appears when you select **Isolate**. You can choose the Isolation profiles to which the rule applies.
Ensure you [create Isolation profiles](/zia/creating-isolation-profile-cloud-browser-isolation) for your organization.
-
**Daily Bandwidth Quota**: (Optional) The daily bandwidth limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. To enforce the quota on specific users, groups, or departments, Zscaler recommends that IP surrogacy is used to aid in identification. To learn more, see [About Surrogate IP](/zia/what-surrogate-ip).
In addition, if you have different policies for different groups, Zscaler recommends that you create a catch-all “any” user policy with a higher limit. This catch-all policy should only apply to unidentified users (do not use “any” user to define “all remaining groups or departments”). This is helpful if you encounter a scenario where there are a high number of unidentified users as the users have a higher combined limit, facilitating continuity of service.
If a user comes from a [known location](/zia/about-locations), the quota is reset at midnight based on the location time zone; for remote users, the quota is reset based on the organization's time zone. The minimum value you can enter is 10 MB and the maximum value is 100,000 MB.
- **Daily Time Quota**: (Optional) The daily time limit allowed for uploading and/or downloading data from the [URL categories](/zia/about-url-categories) before the websites are blocked. The session idle times are ignored. The minimum value you can enter is 15 minutes and the maximum value is 600 minutes.
This action is available only if Isolation is enabled for your organization.
[]![Add URL Filtering Rule window ](/downloads/zia/policies/url-filtering/configuring-custom-url-categories/Add%20URL%20Filtering%20Rule.png)
[]You can add a new URL category, view an existing URL category, or change its settings.
To add a custom URL category:
- Go to **Administration **>** URL Categories**.
-
Click **Add URL Category**.
The **Add URL Category **window appears.
-
In the **Add URL Category **window:
- **Name**: Enter a name for the new category. Category names can only contain alphanumeric characters, underscores, hyphens, dots, parentheses, and spaces.
- **URL Super Category**: Select the URL super category that you want the custom category to belong to from the drop-down menu.
-
**Administrator Operational Scope**: Select the operational scope for this category.
This option is only available for categories where the URL Super Category is **User-Defined**.
You can select multiple operational scopes and when there is more than one scope, OR logic is used to find a match.
Select from the following scopes:
- **Any**: Any admin can manage this category. If your organization does not have granular access requirements for custom URL categories, select **Any** as the scope. You can then control which admins are able to manage custom categories through admin roles.
- **Organization**: Admins whose scope is Organization can manage this category.
- **Location Group**: Admins with one or more of the selected location groups in their scope can manage this category.
- **Location**: Admins with one or more of the selected locations in their scope can manage this category.
Admins that have an operational scope over location groups that include one or more of the selected locations can also manage this category. However, they cannot change the operational scope of the category.
- **Department**: Admins with one or more of the selected departments in their operational scope can manage this category.
If there are any operational scopes that you don't see, they are not part of your administrative operational scope.
You can only delete a custom category that belongs to the **User-Defined **URL Super Category if your administrator scope is identical to the scope of the custom category.
-
**Custom URLs**:** **Enter the URLs or IP addresses you want to add to this custom category and click **Add Items**.
This field supports IPv6 addresses either in full or short form (e.g., 2041:0000:140f:0000:0000:0000:875b:131b or 2041:0000:140f::875b:131b).
Add URLs or IP addresses to this field if you want to override the category or create your own denylist or allowlist of URLs or IP addresses.
URLs or IP addresses added to Custom URLs do not remain mapped to the category in the Zscaler URL database, also called the parent category. So these URLs or IP addresses are covered by policies that reference this specific custom category, but not by policies that reference their parent category. For example, if you enter www.amazon.com, then this site is no longer covered by policies that reference its parent URL category (Online Shopping).
To add multiple entries, press `Enter` after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window appears.
To learn how to find the parent category of a given URL, see [Looking up URLs in the ZIA Admin Portal](/zia/lookup-urls-admin-portal). For guidance on entering URLs, see the [URL format guidelines](/zia/url-format-guidelines).
-
**URLs Retaining Parent Category**: Enter the URLs or IP addresses you want to add to this custom category and click **Add Items**.
This field supports IPv6 addresses either in full or short form (e.g., 2041:0000:140f:0000:0000:0000:875b:131b or 2041:0000:140f::875b:131b).
URLs retaining parent category remain mapped to their parent category. So these URLs or IP addresses are covered by policies that reference the parent category and this custom category. For example, if you enter www.amazon.com, then this site is covered by policies that reference this custom category and its parent URL category (Online Shopping).
To add multiple entries, press `Enter` after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window appears.
If you add already categorized URLs or IP addresses to the **Miscellaneous or Unknown** category in the **URLs retaining parent category** field, the system only categorizes URLs or IP addresses under the pre-existing URL category and not under the **Miscellaneous or Unknown** category. For example, if you add www.blogs.com belonging to the **Blogs** category to the **Miscellaneous or Unknown** category in the **URLs retaining parent category** field, and if you had a policy that blocked the **Miscellaneous or Unknown** category, then www.blogs.com is not blocked as it's categorized under the pre-existing **Blogs** category and not under the **Miscellaneous or Unknown** category.
-
**Custom Keywords**: Enter keywords that you want to add to this custom category and click **Add Items**.
To add multiple entries, press `Enter` after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
URLs that match the keywords are added to the custom category but are not retained under their original parent category. For example, if you create a custom URL category that includes "gambling" as a custom keyword, a site like www.gambling.com is only covered by policies that reference this custom category. It's not covered by policies that reference its parent URL category (Gambling).
Policies including custom keywords trigger if the keyword is a full or partial match of the URI. For example, if you had a policy that blocked a URL category that included "gambling," then www.gambling101.com and www.gambling.com would both be blocked. In addition, as custom keywords apply to the entire URI, if you go to www.google.com and search for "gambling," the search results are blocked since the word "gambling" appears in the URI (https://www.google.com/search?q=*gambling*&oq=*gambling*&aqs=chrome..69i57j0l4.2767j0j8&sourceid=chrome&ie=UTF-8).
Custom keywords must be between 3 and 255 characters.
-
**Keywords Retaining Parent Category**: Enter the keywords you want to add to this custom category and click **Add Items**.
To add multiple entries, press **Enter** after each entry. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
URLs that match the keywords are added to the custom category and also retained under their original parent category. For example, if you create a custom URL category that includes "gambling" as a keyword retaining parent category, a site like www.gambling.com is covered by policies that reference this custom category as well as by policies that reference its parent URL category (Gambling).
Policies, including keywords retaining the parent category, trigger if the keyword is a full or partial match of the URI.
Keywords retaining the parent category must be between 3 and 255 characters.
Adding keywords in the URLs belonging to the **Miscellaneous or Unknown** category to the **Keywords retaining parent category** in a URL category only categorizes the URLs under the respective URL category and not under **Miscellaneous or Unknown**.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 256 characters.
[See image.](#add-custom-image)
- Click **Save & Sync**.
[]![Add URL Category window](/downloads/zia/zscaler-management-portal-partners/getting-started/management-portal/edit-policy-template-zia-admin-portal/Add%20URL%20Category.png)