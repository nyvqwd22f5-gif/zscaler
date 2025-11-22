# About File Type Control
Source: https://help.zscaler.com/unified/about-file-type-control
PDF: https://help.zscaler.com/pdf/com/en/1494011.pdf

By default, the Zscaler service allows the upload and download of all file types. Use the File Type Control policy to restrict the upload and download of various types of files. For example, you can block audio (.mp3, .wav, etc.) and video files (.avi, .mp4, .mpeg, etc.) so they do not interfere with your bandwidth utilization. You can define rules to restrict the transmission of various files and apply them to individuals, groups, departments, and locations. Zscaler also has a [recommended policy](/unified/recommended-file-type-control-policy) for File Type Control.
You can also create rules for unknown file types. Zscaler performs MIME type checks for files it cannot initially identify, and any file that falls outside of well-defined MIME types for common apps is tagged as an unknown file type. To recognize the file types inside archive files, the service also scans ZIP, 7-Zip, GZIP, TAR, and RAR files.
There is a 400MB file size limitation for files that are scanned within the ZIP archive. Archived files over this size are not subject to enforcement. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#internet-saas).
You can allow, caution or block uploading, downloading or both. When you choose the Caution action, the service displays a warning before it allows the user to perform the action. When the service blocks users, it displays a notification. The content of the block notification is configured in the [End User Notification](/unified/configuring-end-user-notifications) page.
A File Type Control policy provides the following benefits and allows you to:
- Restrict the upload and download of various types of files, including unknown file types.
- Define rules to restrict the transmission of various files and apply them to individuals, groups, departments, and locations.
- Use Zscaler's recommended File Type Control policy, or create your own custom policy.
- Allow, caution, or block uploads and downloads. For blocked uploads and downloads, you can configure end user notifications to explain the action.
To see how a File Type Control policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).
About the File Type Control Page
On the File Type Control page (Policies > Access Control > Internet & SaaS > File Type Control), you can do the following:
- [Configure the File Type Control policy](/unified/configuring-file-type-control-policy).
- [View the recommended policy for File Type Control](/unified/recommended-file-type-control-policy).
- View a list of all configured File Type Control rules. For each rule, you can see the following:
- **Rule Order**: The rule order number. File Type Control rules are evaluated in ascending numerical order.
- **Admin Rank**: The assigned [admin rank](/unified/about-admin-rank) for the rule. This is visible only if admin ranking is enabled in the [Advanced Settings](/unified/configuring-advanced-settings#admin-ranking).
- **Rule Name**: The name of the rule.
- **Criteria**: The defined criteria of the rule (e.g., selected File Types, URL Categories, Users, etc.).
- **Action**: Displays if the rule status and whether the selected file types are allowed, blocked, or cautioned when uploaded and/or downloaded.
- **Label and Description**: The label and description of the policy rule, if available.
- Select one of the following **View by** option to see the File Type Control rules accordingly:
-
**Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-FTP)
-
**Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-FTP)
- Search for a configured File Type Control rule.
- Edit a configured File Type Control rule.
- Duplicate a configured File Type Control rule.
- [Modify the table and its columns](/unified/using-tables).
**![Screenshot of File Type Control page showing buttons and list used to manage Zscaler file type control policies](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/ftp-and-file-type-control/file-type-control/about-file-type-control/ZIA-File-Type-Control-Policy-Page.png)
**
[]![Screenshot of File Type Control page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/ftp-and-file-type-control/file-type-control/about-file-type-control/ZIA-File-Type-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of File Type Control page with Rule Label view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/ftp-and-file-type-control/file-type-control/about-file-type-control/ZIA-File-Type-Control-Policy-Page-Viewby-Rule-Label.png)