# Uploading Users from a CSV File
Source: https://help.zscaler.com/unified/uploading-users-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1487761.pdf

In addition to [importing new users via your identity provider (IdP) ](/unified/importing-users-idp)or [adding users manually](/unified/adding-users-manually), you can upload users from a comma-separated values (CSV) file.
To import users from a CSV file:
- On the Users page, click **Upload CSV**.
-
In the Upload CSV dialog box, click **Download CSV Template** to download Zscaler's user template file.
The template file has the following format:
`Action,Login Name,Display Name,First Name,Last Name,Primary Email,Secondary Email,Language,Department,Timezone,Password Reset,Group Names,,
+,psmith@example.com,Priya Smith,Priya,Smith,psmith@example.com,,English (US),Engineering,(UTC+00:00) GMT,true,Group1,Group2,Group3
+,aramirez@aramirez.com,Alonso Ramirez,Alonso,Ramirez,aramirez@example.com,,English (US),Human Resource,(UTC+00:00) GMT,false,Group2,Group3,`
- Add users to the CSV file and ensure the following:
- Retain the first line of the file as the header row.
- The file name must have a .csv extension.
- In the **Action **column, enter one of the following:
- + (plus sign) To add a user, enter values in at least the **Primary Email**, **Login Name**, **First Name**. and **Last Name** columns.
- - (minus sign) to delete a user, you need only enter the **Login Name** of the user you are deleting.
- The password can be left blank if you don’t want to upload passwords in clear text.
- You can use one-time passwords to enable users to log in and set passwords.
- Each user must be on a separate line.
- Each user's email address must have a domain name that was defined in the Admin Portal.
- If the authentication method is a one-time token or one-time link, then the **Primary Email** field must contain a valid email address.
- The **Secondary Email** can specify any domain, but it must be a valid email address.
-
When you have your CSV in the correct format, drag the CSV file from your computer to the **Upload File** box and click **Save**.
Zscaler displays a message indicating whether your upload was successful. If unsuccessful, correct the file according to the requirements in the previous step. Click **Retry **when you are ready to upload a new file.
- When users are successfully uploaded, the **Users **page appears. From this page, you can add more users manually, edit them, or assign them to different roles. To learn more, see [Editing Newly Onboarded Users](/unified/editing-newly-onboarded-users).