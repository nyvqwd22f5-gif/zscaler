# Enabling Remote Assistance
Source: https://help.zscaler.com/zia/enabling-remote-assistance
PDF: https://help.zscaler.com/pdf/com/en/1399216.pdf

At times, Zscaler Support might need access to your organization's ZIA Admin Portal for a limited period to troubleshoot issues. With Remote Assistance, you can allow Zscaler Support to securely and remotely log in to your ZIA Admin Portal. This can be done with either view-only or full [admin](/zia/about-administrators) privileges. You do not need to create new admin accounts or share passwords to enable access for either option.
This procedure allows Zscaler Support to access the ZIA Admin Portal until the specified date.
To enable remote assistance:
- Log in to the Admin Portal.
- Go to **Help **>** Remote Assistance**.
[See image.](#HelpWithRemoteAssist_Img)
- In the **Remote Assistance** window, select your access preferences and **User Name Visibility**.
- Select **Enable View-Only Access**, **Enable Full Access**, or both.
After enabling your access preferences, select the amount of time you want the access enabled. Zscaler recommends that you set the length to the maximum 90 days when choosing view-only access and at least two days when choosing full access.
- Select either **Obfuscated** or **Visible **for the **User Name** field. By default, this field is set to **Visible**.
The user names are obfuscated automatically for all the SSO users if the **User Name** field is set to **Obfuscated**.
The SSO users cannot change this setting. Only admin users with [Remote Assistance Management](/zia/adding-admin-roles#remote-assist) enabled for their role can make changes in the **Remote Assistance** window.
- Select either **Obfuscated** or **Visible **for the **Device Information** field. By default, this field is set to **Visible**.
The device information (i.e., device name, device hostname, and device owner) are obfuscated automatically for all the SSO users if the **Device Information** field is set to **Obfuscated**.
The SSO users cannot change this setting. Only admin users with [Remote Assistance Management](/zia/adding-admin-roles#remote-assist) enabled for their role can make changes in the **Remote Assistance** window.
[See image.](#RemoteAssistance_Img)
To learn more about user name obfuscation, view [Obfuscating User Names for Admins](/zia/obfuscating-user-names-admins).
-
Click **Save**.
After Remote Assistance is enabled, the ZIA Admin Portal displays a message alerting users that Remote Assistance is enabled until the access time expires or Remote Assistance is disabled.
[]![Screenshot of Help menu in Zscaler UI highlighting Remote Assistance option](/downloads/zia/troubleshooting/enabling-remote-assistance/zia-select-remote-assistance.png)
[]![Screenshot of the remote assistance options ](/downloads/zia/troubleshooting/enabling-remote-assistance/ZIA-6.2-Remote-Assistance%20(1).png)