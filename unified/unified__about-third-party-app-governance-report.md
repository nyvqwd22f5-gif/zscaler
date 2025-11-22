# About the 3rd-Party App Governance Report
Source: https://help.zscaler.com/unified/about-third-party-app-governance-report
PDF: https://help.zscaler.com/pdf/com/en/1497551.pdf

An employee might go to a third-party application and log in using their corporate Google Workspace account. As the employee is logging in, the application asks for permission to access data (e.g., Read Access to Google Drive, Read Access to Gmail, etc.). When the employee grants these permissions, the application now has access to their corporate Google Workspace account; your company’s IT department has no idea this happened. This creates issues because your employees can use a number of applications they want using their corporate Google Workspace account, and some applications are not safe (e.g., if granted access to Gmail, an application can send rogue emails).
The 3rd-Party App Governance Report identifies all the third-party applications that employees are using. It shows you the date they were discovered, how many employees are using them, the state of an application, and more. The data is displayed for the tenant you select under the Tenant option. To learn more about 3rd-Party App Governance, see [What Is 3rd-Party App Governance?](/unified/what-3rd-party-app-governance)
- If you have the Advanced Posture Management license enabled, you are redirected to the 3rd-Party App Governance Admin Portal. To learn more about navigating the 3rd-Party App Governance Admin Portal, see [Accessing and Navigating the 3rd-Party App Governance Admin Portal](/unified/accessing-and-navigating-3rd-party-app-governance-admin-portal).
- If you don't have the Advanced Posture Management license enabled, the 3rd-Party App Governance Report page with an upgrade banner is visible. To upgrade to Advanced Posture Management, contact your Zscaler Account team.
The 3rd-Party App Governance Report provides the following benefits and enables you to:
- Quickly vet third-party apps before connecting them to your environment.
- Gain full visibility over first-, second-, and third-party API integrations across your business so you can uncover dangerous SaaS platform connections.
- Reduce your integrations and third-party attack surface and stop data exfiltration and breaches.
Report Sections
On the 3rd-Party App Governance page, (Analytics > Internet & SaaS > Analytics > SaaS Security Report > 3rd-Party App Governance), you can view the following:
- **Total Applications**: The total number of third-party applications.
- **Application State**: The total number of third-party applications categorized by their application state:
- **Discovered**: The number of third-party applications discovered, but no action is taken on them yet.
- **Allowed**: The number of applications explicitly allowed for use.
- **Blocked**: The number of applications explicitly blocked for use.
- **Restricted**: An admin has allowed the use of this application to specific users.
- **Reauthorized**: The number of reauthorized applications for use. (e.g., the user had explicitly blocked the application earlier).
You can change the state of an application through the [Application Information](#Application-Information) page. To get to this page, click on an application in the Applications Table, and then click **Action**.
- **Filters**: Select your filters and click **Apply **to update the page with your selections. You can click **Reset **at any time:
- **State**: Filter by the application states.
- **Permissions**: Filter the applications based on the permissions they ask for.
- **Applications Table**: The following columns appear in the table. You can sort each column:
- **Application**: The application name. When you click on an application, you’ll be redirected to the [Application Information](#Application-Information) page.
- **Date Discovered**: The date the application was discovered.
- **Number of Users**: The number of users using the application.
- **State**: The state of the application.
[See image.](#reporting-page)
[]![Third-Party Applications Page](/downloads/zia/dashboard-analytics/reports/saas-security/third-party-applications-report/Third-Party-Apps_page.png)
[]Application Information Page
The Application Information page displays information for the specific application you selected to view.
- **General**: The application’s general information, which includes its state, the number of users, and the application’s description.
- **Permissions**: The list of permissions the application is granted with.
- **Download**: Download a CSV file with all the permissions listed.
- **Users Table**: You can do the following in the Users Table:
- **Action**: Select from the following actions for all or specific users:
- **Allow Authorization for All Users**: Allow the use of this application for all users.
- **Restrict Authorization to Specific Users**: Restrict the use of this application to specific users.
When you select this option, the **Restrict Authorization to Specific Users** window will appear. Here, you can search and select users you want to authorize to use this application. When you’re done, click **Save**.
[See image.](#specific-users)
- **Revoke Authorization for All Users**: Revoke the use of this application for all users (this is the state Blocked).
[]![Restrict Authorization to Specific Users window ](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/third-party-applications-report/ZIA-6.1r-specfic-users.png)
- **Search**: Search for a specific user.
- **Columns**: View the following columns in the table:
- **User Login Name**: The login email address of the user. You can sort this column.
- **Date Last Used**: The last time (month, day, year) the user used the application. You can sort this column.
- **Access Level**: The level of access the user has to the application. They are either allowed or blocked from using the application.
![3rd-Party App Governance page](/downloads/zia/dashboard-analytics/reports/saas-security/third-party-applications-report/Third-Party-Apps-Info-page.png)