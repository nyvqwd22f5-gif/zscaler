# About Active Directory Privileged Account Tracking
Source: https://help.zscaler.com/itdr/about-active-directory-privileged-account-tracking
PDF: https://help.zscaler.com/pdf/com/en/1531887.pdf

The Active Directory (AD) Privileged Account Tracking page monitors anomalous user login activity for users or groups that you can track. These users are monitored, and their suspicious login activities are listed in the [Active Directory Privileged Account Tracking report](/itdr/about-ad-privileged-account-tracking-report).
AD Privileged Account Tracking provides the following benefits and enables you to:
- Monitor user activity to detect suspicious behavior early.
- Manually add a user or group of users to track their accounts apart from default privileged user accounts.
About the AD Privileged Account Tracking Page
On the AD Privileged Account Tracking page (ITDR > Manage > AD Privileged Account Tracking), you can do the following:
- View the total number of default privileged user accounts being monitored.
- View the total number of user accounts being monitored that were added by an admin.
- View the total number of default and user-defined accounts being monitored.
- Filter AD Privileged Account Tracking results by an AD domain.
- [Add a user account to monitor](/itdr/adding-user-privileged-account-tracking-active-directory).
- View the list of user accounts being monitored. For each user account, you can view:
- **Created On**: The date and time when the user account was added for tracking.
- **Object ID**: The unique identifier for an object. Displays the user principal name (UPN) for a user, or the distinguished name for a group.
- **Type**: The object type (user or group).
- **Is Privileged**: Indicates if the AD user account is privileged or not.
- **Is Data Collected**: Indicates if the data is collected for training the machine learning system to track user behavior.
- **Reason**: The reason why the object was added to the tracking list.
- **Training Status**: The status of the user account in the matching learning system. Statuses include:
- **Not Trained**: The machine learning system has not yet started learning the user's behavior patterns.
- **Data Gathering**: The machine learning system is currently collecting data to begin learning the user's behavior.
- **Evolving**: The machine learning system has completed learning the user's behavior and is adapting to recognize new patterns.
- **Tracking**: Enable or disable the tracking for the user account.
-
View the user account details, including **UPN **and **Last Successful Training Date**.
The** Last Successful Training Date** details appear only for the **Evolving **status.
- Delete the user account from the tracking list.
![AD Privileged Account Tracking page with highlighted options. ](/downloads/itdr/scan-configuration/active-directory-privileged-account-tracking/about-active-directory-privileged-account-tracking/ITDR-Privileged-Account-Tracking.png)