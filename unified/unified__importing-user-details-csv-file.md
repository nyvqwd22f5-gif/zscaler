# Importing User Details from a CSV File
Source: https://help.zscaler.com/unified/importing-user-details-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1505401.pdf

You can import up to 1,000 users into ZIdentity at one time by using CSV files.
Ensure that the CSV file is in a Zscaler-supported format before importing.
To import a CSV file that includes user details:
- Go to **Administration **> **Identity **> **ZIdentity **> **Users**.
-
Click **Import CSV**.
[See image.](#zsl-csvbutton)
- In the **Import Users** window, click **Download** **Sample** to download the template.
-
Enter the user details in the CSV file template in the following format:
- Retain the first line of the file, which is the header row.
- The file name must have a .csv extension.
- Enter one of the following for **Action**:
- **+** (plus sign): To add a user, fill in the **Primary Email**, **Login Name**,** First Name**, **Last Name** columns. A user can belong to up to 128 groups.
- **-** (minus sign): To delete a user, fill in the **Login Name **column.
- The password can be left blank if you don’t want to upload passwords in clear text.
- You can use one-time passwords to enable users to log in and set passwords.
- Each user must be on a separate line.Each user's email address must have a domain name that was defined in the portal.
- If the authentication method is a one-time token or one-time link, then this **Primary Email** field must contain a valid email address.
- The **Secondary Email** can specify any domain, but it must be a valid email address.
- (Optional) Select **Override Existing Entries** if you want to update the existing user details, delete users, or add new users. Do not select this option if you only want to add new users. If you attempt to add a user that already exists and this option is not selected, an error message is displayed, stating that identical users cannot be imported. If this occurs, review your CSV file and ensure that there is no duplication.
- Save the CSV file in your local folder.
-
In the** Import Users **window, click **Browse File**.
[See image.](#zsl-importuserdetails)
- Browse your folders and select the CSV file, then click **Open**.
-
Click **Import**. The CSV file is successfully imported.
The user details are displayed on the **Users** page.
[]![Clicking the Import CSV button](/downloads/zslogin/administration/users/importing-user-details-csv-file/zid-import-csv-button.png)
[]![Importing user details](/downloads/zslogin/administration/users/importing-user-details-csv-file/zid-import-users.png)