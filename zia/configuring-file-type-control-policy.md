# Configuring the File Type Control Policy
Source: https://help.zscaler.com/zia/configuring-file-type-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1398726.pdf

[Watch a video about File Type Control.](https://fast.wistia.net/embed/iframe/q5ruqghyrl)
File Type Control policies enable you to create rules to restrict the upload and download of various types of files. You can capture and store traffic blocked through this policy as PCAP files. To learn more, see [About Traffic Capture Settings](/zia/about-traffic-capture). You can also use the [recommended File Type Control policy](/zia/what-recommended-file-type-control-policy) for guidance when configuring File Type Control policies.
Policy Execution
The File Type Control rules consist of a series of logical operators between their criteria. The rules are triggered based on the result of the following logical operations between the criteria:
[File Types (`AND`) URL Categories (`AND`) Cloud Applications (`AND`) ZPA Application Segment] (`AND`) [Users (`OR`) Groups (`OR`) Departments] (`AND`) [Location Groups (`OR`) Locations] (`AND`) Time (`AND`) [Device Groups (`OR`) Devices] (`AND`) Protocols (`AND`) Device Trust Level (`AND`) Minimum File Size (`AND`) Maximum File Size.
Configuring File Type Control Policy
To configure the File Type Control policy:
-
Go to **Policy **>** File Type Control**.
[See image.](#policy-ftc)
-
Click **Add File Type Control Rule**.
The **Add File Type Control Rule** window appears.
-
In the **Add File Type Control Rule **window:
- **Rule Order**: Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, etc.), and the rule order reflects this rule’s place in the order. You can change the value, but if you’ve enabled [Admin Rank](/zia/what-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: This option appears if you enabled [Admin Rank](/zia/what-admin-rank) on the [Advanced Settings](/zia/about-advanced-settings) page. Enter a value from 0 to 7 (0 is the highest rank). Your assigned [admin rank](/zia/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule’s admin rank determines the value you can select in the rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the File Type Control rule, or use the default name.
- **Rule Status**: Choose to **Enable** or **Disable** the rule. An enabled rule is actively enforced. A disabled rule is not actively enforced but does not lose its place in the rule order. The Zscaler service skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/zia/about-rule-labels).
-
**File Types**:** **(Required) Select file types to which you want to apply the rule. You can also select **Undetectable File** under **Other** to apply the rule to unknown file types. For unknown file types, the service checks for the file type in the file header using true file type detection. If the file is still unknown, the service performs MIME type checks and tags as an unknown file type for any that fall outside of well-defined MIME types for common apps. You can select any number of file types and also search for file types. You can also select [custom file types](/zia/configuring-custom-file-types) you have previously configured.
Zscaler-defined file types are considered before custom file types and custom file types inside archives are not detected.
-
**URL Categories**: Select the [URL categories](/zia/about-url-categories) to which you want to apply the rule. The service applies the rule when users upload to or download files from sites in the selected categories. Select **Any **to apply the rule to all categories, or select any number of categories. You can also search for URL categories, or add a [custom category](/zia/adding-custom-url-categories) by clicking the **Add **icon.
You can also select [custom TLD categories](/zia/about-tld-categories) from this field.
-
**Cloud Applications**: Select any number of [cloud applications or cloud application classes](/zia/about-cloud-app-control). Selecting no value ignores the criterion in the policy evaluation. By default, this field displays the first 100 cloud applications. The subsequent 100 cloud applications are displayed when you select **Click to see more** at the bottom of the list. You can repeat this process to view the remaining cloud applications.
[See image.](#cloud-app-field-with-click-see-more)
-
**ZPA Application Segment:** Select **Any** to apply the rule to all [ZPA application segments](/zpa/configuring-application-segments), or select up to 255 ZPA application segments. You can also search for ZPA application segments. The list displays only those ZPA application segments that have the [Source IP Anchor](/zia/understanding-source-ip-anchoring) option enabled.
If you select the** Inspect App Segments** option from the list, then the configured rule applies to all the ZPA application segments paired to your ZIA tenant. This option is only available if the **SIPA App Segments** subscription is enabled for your organization.
[See image.](#zpa-application-segment-image)
- **Users**:** **Select **Any** to apply the rule to all [users](/zia/about-users), or select up to 32 users under **General Users**. If you've enabled the [Policy for Unauthenticated Traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic), you can select **Special Users** to apply this rule to all unauthenticated users, or select specific types of unauthenticated users. You can search for users or click the **Add **icon to add a new user.
- **Groups**:** **Select **Any** to apply the rule to all [groups](/zia/about-groups), or select up to 32 groups. You can search for groups or click the **Add **icon to add a new group.
-
**Departments**:** **Select** Any** to apply the rule to all [departments](/zia/about-departments), or select up to 32 departments. If you've enabled the [Policy for Unauthenticated Traffic](/zia/how-do-i-configure-policy-unauthenticated-traffic), you can select **Special Departments** to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add **icon to add a new department.
Any rule that applies to unauthenticated traffic must apply to all Groups and Departments. So, if you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, select **Any **from the drop-down menus for **Groups** and **Departments**.
-
**Locations**:** **Select **Any** to apply the rule to all [locations](/zia/about-locations), or select up to 32 locations. You can also search for a location or click the **Add **icon to add a new location.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
- **Location Groups**: Select **Any** to apply the rule to all [location groups](/zia/about-location-groups), or select up to 32 location groups. You can also search for a location group.
- **Time**: Select **Always** to apply this rule to all [time intervals](/zia/how-do-i-define-time-intervals), or select up to two time intervals. You can also search for a time interval or click the **Add **icon to add a new time interval.
- []**Protocols**: Select the protocols to which the rule applies.
- **FTP over HTTP**: Files from FTP over HTTP websites. (Requires Firewall subscription).
- **HTTP**: Files from HTTP websites.
- **HTTPS**: Files from HTTP websites encrypted by TLS/SSL.
- **Native FTP**: Files from native FTP servers. (Requires Firewall subscription).
- **Minimum/Maximum File Size**: Enter a number value between 0 and 409,600 (KB) to apply a minimum and a maximum file size limit. Entering no value ignores the criteria in the policy evaluation.
- **Active Content**: Enable the toggle button to apply the rule to files with active content. This criterion is applicable only to Microsoft Word, Microsoft Excel, Microsoft PowerPoint, and PDF file formats. The** File Types** field must be set to one of the supported file formats in order to configure this criterion.
-
**Unscannable Files**: Enable the toggle button to apply the rule only to files that the Zscaler service is unable to scan. This might occur if the file is in an unrecognized file format, excessive size, corrupted, or recursively compressed.
After enabling the **Unscannable Files** option, the corresponding file type policy only applies to those files that Zscaler is unable to scan. The policy is not applied to any other file types.
- **Password-Protected Files**: Enable the toggle button to apply the rule only to files with password protection. When enabled, only the file types that are password-protected are available. This criterion is applicable only to 7-Zip, RAR, Zip, Zipx, Password-Protected Microsoft Office Documents, Password-Protected/Encrypted Files, and PDF file types. If the toggle is not enabled, any files that are in the drop-down menu are not explicitly password-protected or encrypted.
- **Devices**: Select the [devices](/zia/about-devices) for which you want to apply the rule. You can also search for a device. Selecting no value ignores the criterion in the policy evaluation.
-
**Device Groups**: Select the [device groups](/zia/about-device-groups) for which you want to apply the rule. For Zscaler Client Connector traffic, select the appropriate group based on the device platform. Select **Cloud Browser Isolation** or **No Client Connector** to apply the rule to Isolation traffic or to traffic that is not tunneled through Zscaler Client Connector, respectively. You can also search for a device group. Selecting no value ignores the criterion in the policy evaluation.
The **Cloud Browser Isolation** group is available only if Isolation is enabled for your organization.
- []
**Device Trust Level**: Select the device trust level values (**High Trust**, **Medium Trust**, **Low Trust**, or **Unknown**) to which the rule applies. While the High Trust, Medium Trust, or Low Trust evaluation is applicable only to Zscaler Client Connector traffic, Unknown evaluation applies to all traffic. Selecting no value ignores the criterion in the policy evaluation.
The trust levels assigned to the devices are based on your [posture configurations](/client-connector/adding-zia-posture-profiles) in the Zscaler Client Connector Portal.
-
**Action**: Choose to **Allow**, **Block**, or **Caution** users from uploading or downloading files.
If Traffic Capture is enabled, the **Capture** option appears when **Block** is selected. Captured traffic is stored in PCAP files for later analysis. To enable Traffic Capture for this policy, see [Configuring Traffic Capture Settings](/zia/configuring-traffic-capture).
- **Upload/Download**: Choose whether the specified action applies to uploading files, downloading files, or both.
-
**Browser Notification Template**: (Optional) Select a browser-based EUN message from the drop-down menu to display the message on the browser when the user activity triggers the File Type Control Policy rule.
This field appears when the application access is set to either **Caution** or **Block**.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 10,240 characters.
[See image.](#add-file-type-control-rule-window)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![The File Type Control option in the left-side navigation of the ZIA Admin Portal](/downloads/zia/policies/file-type-control/configuring-file-type-control-policy/ZIA-Policy-File-Type-Control.png)
[]![The Add File Type Control Rule window in the ZIA Admin Portal](/downloads/zia/policies/file-type-control/configuring-file-type-control-policy/Add%20File%20Type%20Control%20Rule.png)
[]![ZIA Add File Type Control Rule with Click to See More in the Cloud Applications Field](/downloads/zia/policies/file-type-control/configuring-file-type-control-policy/ZIA-Add-File-Type-Control-Rule-See-More.png)
[]![The Inspect App Segments option for the ZPA Application Segment field](/downloads/zia/policies/file-type-control/configuring-file-type-control-policy/zia-configuring-file-type-control-zpa-app-segments-inspect-app-segments-option.png)