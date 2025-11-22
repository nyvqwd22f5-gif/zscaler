# Viewing Login Activity
Source: https://help.zscaler.com/zscaler-cellular/viewing-login-activity
PDF: https://help.zscaler.com/pdf/com/en/1518001.pdf

You can view the list of users logged in to the Zscaler Cellular Admin Portal using the Login Tracker. The Login Tracker allows you to view detailed insights into user authentication activities. It serves as a vital tool for monitoring login events, offering you a streamlined way to track user access patterns and investigate login-related events.
With the Login Tracker, you can:
- View and track login details, including user email addresses, OpenID Connect (OIDC) user IDs, and login tokens.
- Analyze user behavior or detect suspicious activities.
To view login activities:
-
In the left-side navigation, select **Login Tracker**.
The **Login Tracker **page appears.
-
On the **Login Tracker **page, you can view the list of logins to the Zscaler Cellular Admin Portal. For each login, you can see:
- **Email**: The email address of the user who logged in to the Zscaler Cellular Admin Portal.
- **OIDC User ID**: A unique identifier for the user as part of the OpenID Connect authentication.
- **Login Timestamp**: The exact timestamp of the login activity.
- **OIDC JTI**: The JSON Web Token (JWT) ID used during the authentication process.
[See image.](#login-tracker-page)
You can click the Refresh button to fetch and view the latest data.
[See image.](#refresh-button)
You can customize the table to show specific columns, limit rows per page, navigate through pages, filter the data to refine your view, or sort the columns to adjust the order of entries. To learn more, see [Filtering & Customizing Tables](/zscaler-cellular/filtering-customizing-tables).
[]![A list of login records of users with blurred sensitive information](/downloads/zscaler-cellular/network-events-and-logins-monitoring/viewing-login-activity/cellular-edge-viewing-login-activity-page.png)
[]![Login tracker page with the refresh button highlighted](/downloads/zscaler-cellular/network-events-and-logins-monitoring/viewing-login-activity/cellular-edge-viewing-login-activity-page-refresh-button.png)