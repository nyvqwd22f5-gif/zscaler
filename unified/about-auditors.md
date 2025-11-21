# About Auditors
Source: https://help.zscaler.com/zia/about-auditors
PDF: https://help.zscaler.com/pdf/com/en/1399001.pdf

[Watch a video about Auditors](https://fast.wistia.net/embed/iframe/68fj7gj7xh)
Some regions have legal requirements that dictate that user names always remain obfuscated in reports and logs for admins. If admins need to view real user names, they must have an auditor grant them permission to do so.
Auditors provide the following benefits and enable you to:
- Add an additional layer of security for user name visibility to the admins.
- Control and manage who can access obfuscated user names.
- Keep track of the admins who request access to the user names.
An auditor is generally an employee from the organization who has been given special permission to serve in the role through an organizational decision-making process. A super admin can create an account for the auditor through the ZIA Admin Portal and share the credentials with the auditor. The auditor's credentials can only be used to provide admins permission to view obfuscated user names and device information. It can't be used to log in to the ZIA Admin Portal. For example, the auditor can give an admin permission to view obfuscated user names and device information through the following process:
-
An admin who has user names or device names obfuscated logs in to the ZIA Admin Portal.
A message appears in the top-right corner notifying the admin that some information is obfuscated.
[See image.](#override-msg)
-
An auditor can click **Override** and enter their credentials to reveal the obfuscated information.
[See image.](#auditor-credentials)
- The obfuscated user names and device information are made visible for the duration of the session. Obfuscation begins again the next time the admin signs in to the ZIA Admin Portal.
You can add, edit, or delete auditors at any time, but you must have a super admin [role](/zia/adding-admin-roles) and organizational [scope](/zia/about-admin-scope) to do so.
About the Auditors Page
On the Auditors page (Administration > Administrator Management > Auditors), you can do the following:
- [Add an auditor.](/zia/adding-auditors)
- Search for an auditor.
- View a list of all auditors configured for your organization. For each auditor, you can see:
- **Login ID**: The ZIA Admin Portal login ID for the auditor.
- **Name**: The name of the auditor.
- **Status**: The status of the auditor.
- **Comments**: Comments regarding the auditor, if available.
- [Modify the table and its columns.](/zia/how-do-i-use-tables-admin-portal)
- [Edit or delete an auditor.](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal)
- Click to view the [Administrators page.](/zia/about-administrators)
- Click to view the [Administrator Management page.](/zia/administrator-management-settings)
![The auditors page showing the buttons used to manage Zscaler auditors ](/downloads/zia/documentation-knowledgebase/managing-admins/about-auditors/about-auditors/ZIA-about-auditors.png)
[]![The yellow box that appears at top right-hand corner of admin’s monitor for auditor to see](/downloads/zia/documentation-knowledgebase/managing-admins/about-auditors/about-auditors/ZIA-auditor-override-mssg.png)
[]![The Auditor Override window with an auditor's email and password.](/downloads/zia/documentation-knowledgebase/managing-admins/about-auditors/about-auditors/ZIA-auditor-override-window.png)