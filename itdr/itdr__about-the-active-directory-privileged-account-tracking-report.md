# About the Active Directory Privileged Account Tracking Report
Source: https://help.zscaler.com/itdr/about-the-active-directory-privileged-account-tracking-report
PDF: https://help.zscaler.com/pdf/com/en/1531888.pdf

The Active Directory Privileged Account Tracking report displays suspicious login activity findings for users being tracked on the [AD Privileged Account Tracking](/itdr/about-ad-privileged-account-tracking) page. The machine learning system marks activity as suspicious based on a user's login activity trend. You can mark an activity as safe to avoid seeing the incident again for a user.
Only user accounts with the Evolving status on the [AD Privileged Account Tracking](/itdr/about-active-directory-privileged-account-tracking) page are displayed in the report.
Active Directory Privileged Account Tracking reports provide the following benefits and enable you to:
- View suspicious login activity findings of users being tracked through a single report.
- Take quick actions on critical or high-severity incidents and prevent repeated security threats.
About the Active Directory Privileged Account Tracking Report Page
On the Active Directory Privileged Account Tracking Report page (ITDR > Dashboard > AD Privileged Account Tracking), you can do the following:
- Filter Active Directory Privileged Account Tracking results by an Active Directory (AD) domain.
- View the list of suspicious login activities of user accounts being monitored. For each user login activity, you can view:
- **Created On**: The date and time of the anomalous login activity.
- **User**: The UPN (User Principal Name) of the user that performed the login activity.
- **Anomaly Title**: The title of the anomalous login activity.
- **Anomaly Description**: The description of the anomalous login activity.
- **Severity**: The severity level (**Low**, **Medium**, **High**, or **Critical**) given to an anomalous login activity by the machine learning system.
- View the user account session log details.
-
Click the **Safe **icon to mark the user activity as safe.
When the activity is marked safe, the machine learning system no longer flags that activity as suspicious for the user.
- Delete the user activity from the Active Directory Privileged Account Tracking report page.
![The AD Privileged Account Tracking report page with highlighted options.](/downloads/itdr/dashboard/about-the-active-directory-privileged-account-tracking-report/ITDR-Privileged-Account-Tracking-Report.png)