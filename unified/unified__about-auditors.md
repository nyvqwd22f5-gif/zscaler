# About Auditors
Source: https://help.zscaler.com/unified/about-auditors
PDF: https://help.zscaler.com/pdf/com/en/1490791.pdf

Some regions have legal requirements that dictate that user names always remain obfuscated in reports and logs for admins. If admins need to view real user names, they must have an auditor grant them permission to do so.
Auditors provide the following benefits and enable you to:
- Add an additional layer of security for user name visibility to the admins.
- Control and manage who can access obfuscated user names.
- Keep track of the admins who request access to the user names.
An auditor is generally an employee from the organization who has been given special permission to serve in the role through an organizational decision-making process. A super admin can create an account for the auditor through the Admin Portal and share the credentials with the auditor. The auditor's credentials can only be used to provide admins permission to view obfuscated user names and device information. It can't be used to log in to the Admin Portal. For example, the auditor can give an admin permission to view obfuscated user names and device information through the following process:
-
An admin who has user names or device names obfuscated logs in to the Admin Portal.
A message appears in the top-right corner notifying the admin that some information is obfuscated.
[See image.](#override-msg)
-
An auditor can click **Override** and enter their credentials to reveal the obfuscated information.
[See image.](#auditor-credentials)
- The obfuscated user names and device information are made visible for the duration of the session. Obfuscation begins again the next time the admin signs in to the Admin Portal.
You can add, edit, or delete auditors at any time, but you must have a super admin [role](/unified/adding-admin-roles) and organizational [scope](/unified/about-admin-scope) to do so.
About the Auditors Page
On the Auditors page (Administration > Admin Management > Administrator Management > Internet Access Administrators > Auditors), you can do the following:
- [Add an auditor](/unified/adding-auditors).
- Search for an auditor.
- View a list of all auditors configured for your organization. For each auditor, you can see the following:
- **Login ID**: The Admin Portal login ID for the auditor
- **Name**: The name of the auditor
- **Status**: The status of the auditor
- **Comments**: Comments regarding the auditor, if available
- [Modify the table and its columns](/unified/using-tables).
- Edit or delete an auditor.
- Click to view the [Administrators](/unified/about-administrators) page.
- Click to view the [Administrator Management](/unified/understanding-administrator-management-settings) page.
![Screenshot of Auditors page showing the buttons used to manage Zscaler auditors ](/downloads/zia/documentation-knowledgebase/managing-admins/about-auditors/about-auditors/ZIA-about-auditors.png)
[]![Screenshot of yellow box that appears at top right-hand corner of admin’s monitor for auditor to see](/downloads/zia/documentation-knowledgebase/managing-admins/about-auditors/about-auditors/ZIA-auditor-override-mssg.png)
[]![Image of the Auditor Override window](/downloads/zia/documentation-knowledgebase/managing-admins/about-auditors/about-auditors/ZIA-auditor-override-window.png)