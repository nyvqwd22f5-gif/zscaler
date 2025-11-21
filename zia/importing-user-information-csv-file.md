# Importing User Information from a CSV File
Source: https://help.zscaler.com/zia/importing-user-information-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1401101.pdf

You can import up to 3,000 users using a CSV file.
To edit and import a CSV file :
- Go to **Administration** > **User Management**.
- Click **Sample Import CSV file** to download the user information template. When configuring the CSV file, ensure the following:
- The file name must have a `.csv` extension.
- The first line of the file is the header row.
- Each user must be on a separate line.
- Each user's email address must have a domain name that was defined in the ZIA Admin Portal. If the authentication method is a one-time token or one-time link, then either this field or the **Temp auth email** field must contain a valid email address.
- Enter your user information in the CSV file template in the following format so that the Zscaler service successfully imports the CSV file:
- **Action**: Enter one of the following:
- Enter `+` to add a new user or modify an existing one. When adding a user, **Email-ID**, **User Name**,** Dept**,** **and **Group** must be filled in. A user can belong to up to 128 groups.
- Enter `-` to delete an existing user. When deleting a user, only **Email-ID** is required.
-
**Email-ID**: Enter a user ID. The user ID consists of a user name and domain name in email format. Enter the user name and any domain name for your organization that is available on the Zscaler service. The email-ID must be in the form of an email address. It does not have to be a valid email address, but it must be unique, and its domain must belong to the organization.
The **Email-ID** field allows values of alphanumeric characters and certain special characters up to a maximum of 127 characters. This field corresponds to the email field in the API. However, the data validation in the API supports a broader range of characters.
-
**User Name**: Enter a display name for the user. Typically, the full name of the user. This appears when choosing users for policies.
The **User Name** field allows values containing UTF-8 characters up to a maximum of 127 characters.
- **Dept**: Enter the department that the user belongs to. [Departments](/zia/about-departments) are used in policies and reports. A user can belong to only one department.
-
**Password**: Enter the user’s password. If you selected **Form-Based** when [configuring the default authentication profile](/zia/configuring-default-authentication-profile), the password must follow the guidelines that you defined. If you selected **One-time Token** or **One-time Link** as the **Temporary Authentication** method, you can leave this field blank.
If the **Password **field is left blank, users must log in to the Zscaler service for the first time using a one-time token or one-time link.
-
**Status**: Enter one of the following user statuses:
- Enter `Enabled` to enable the user.
- Enter `Disabled` to disable the user.
Disabling a user with the same user name as an [admin](/zia/about-administrators) also disables the admin.
- **Comments**: (Optional) Enter additional notes or information. The content cannot exceed 10,240 characters.
-
**Temp auth e-mail**: Enter a valid email address for temporary authentication.
Users are sent the one-time token or one-time link to this email address and are able to log in. If you use a one-time token, they are prompted to create a new password. The temporary email address can have any domain name, but it must be a valid email address. The email is sent when you click **Send Authentication E-mail **on the Authentication Default Settings page. To learn more, see [Configuring a One-Time Token or One-Time Link](/zia/configuring-one-time-token-or-one-time-link).
- **Groups**: Enter the groups that the user belongs to. Enter each group beyond the first in a new column. [Groups](/zia/about-groups) are used in policies. You can control access to apps based on user groups.
-
After you have configured the CSV file in the correct format, click **Import**.
The **Import Users** window appears.
-
In the **Import Users** window:
- **Override Existing Entries**: Select this checkbox if you want to update any existing user information (e.g., group, password, and department). Do not select this option if you only want to add new users.
- **Choose File**: Click this and select the CSV file, then click **Open**.
[See image.](#import-users-window)
Review your CSV file and ensure that there is no duplication. If you attempt to add a new user that already exists without selecting this option, the Zscaler service displays an error message.
- Click **Import**.
- After the CSV file is successfully imported, click **Close**.
[]![The Import Users window with the option to Override Existing Entries and Upload a CSV file](/downloads/zia/authentication-administration/provisioning-authenticating-users/user-management/users/importing-user-information-csv-file/ZIA-import-users-window.png)