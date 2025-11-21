# About File Type Control
Source: https://help.zscaler.com/zia/about-file-type-control
PDF: https://help.zscaler.com/pdf/com/en/1398721.pdf

[Watch a video about File Type Control.](https://fast.wistia.net/embed/iframe/q5ruqghyrl)
By default, the Zscaler service allows the upload and download of all file types. Use the File Type Control policy to restrict the upload and download of various types of files. For example, you can block audio (.mp3, .wav, etc.) and video files (.avi, .mp4, .mpeg, etc.) so they do not interfere with your bandwidth utilization. You can define rules to restrict the transmission of various files and apply them to individuals, groups, departments, and locations. Zscaler also has a [recommended policy](/zia/what-recommended-file-type-control-policy) for File Type Control.
You can also create rules for unknown file types. Zscaler performs MIME type checks for files it cannot initially identify, and any file that falls outside of well-defined MIME types for common apps is tagged as an unknown file type. To recognize the file types inside archive files, the Zscaler service also scans ZIP, 7-Zip, GZIP, TAR, and RAR files.
There is a 400MB file size limitation for file scanning. To learn more, see [Ranges & Limitations](/zia/ranges-limitations).
You can allow, caution or block uploading, downloading or both. When you choose the Caution action, the Zscaler service displays a warning before it allows the user to perform the action. When the Zscaler service blocks users, it displays a notification. The content of the block notification is configured in the [End User Notification](/zia/about-acceptable-use-policy-and-end-user-notifications) page.
A File Type Control policy provides the following benefits and allows you to:
- Restrict the upload and download of various types of files, including unknown file types.
- Define rules to restrict the transmission of various files and apply them to individuals, groups, departments, and locations.
- Use the Zscaler recommended File Type Control policy, or create your own custom policy.
- Allow, caution, or block uploads and downloads. For blocked uploads and downloads, you can configure end user notifications to explain the action.
To see how a File Type Control policy fits into the overall order of policy enforcement, see [How does the Zscaler service enforce policies?](/zia/how-does-zscaler-service-enforce-policies)
About the File Type Control Page
On the File Type Control page (Policy > File Type Control), you can do the following:
- [Configure the File Type Control policy](/zia/how-do-i-configure-file-type-control-policy).
- [View the recommended policy for File Type Control](/zia/what-recommended-file-type-control-policy).
- View a list of all configured File Type Control rules. For each rule, you can see the following:
- **Rule Order**: The rule order number. File Type Control rules are evaluated in ascending numerical order.
- **Admin Rank**: The assigned [admin rank](/zia/about-admin-rank) for the rule. This is visible only if admin ranking is enabled in the [Advanced Settings](/zia/about-advanced-settings#admin-ranking).
- **Rule Name**: The name of the rule.
- **Criteria**: The defined criteria of the rule (e.g., selected File Types, URL Categories, Users, etc.).
- **Action**: Displays if the rule status and whether the selected file types are allowed, blocked, or cautioned when uploaded and/or downloaded.
- **Label and Description**: The label and description of the policy rule, if available.
- Select one of the following **View by** option to see the File Type Control rules accordingly:
- **Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-FTP)
- **Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-FTP)
- Search for a configured File Type Control rule.
- [Edit a configured File Type Control rule](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Duplicate a configured File Type Control rule](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
**![Screenshot of File Type Control page showing buttons and list used to manage Zscaler file type control policies](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/ftp-and-file-type-control/file-type-control/about-file-type-control/ZIA-File-Type-Control-Policy-Page.png)
**
[]![Screenshot of File Type Control page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/ftp-and-file-type-control/file-type-control/about-file-type-control/ZIA-File-Type-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of File Type Control page with Rule Label view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/ftp-and-file-type-control/file-type-control/about-file-type-control/ZIA-File-Type-Control-Policy-Page-Viewby-Rule-Label.png)