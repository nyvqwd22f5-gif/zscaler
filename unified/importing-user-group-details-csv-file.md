# Importing User Group Details from a CSV File
Source: https://help.zscaler.com/unified/importing-user-group-details-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1505431.pdf

You can import up to 1,000 user groups into ZIdentity at one time by using CSV files. Ensure that the CSV file is in a Zscaler-supported format before importing.
To import a CSV file:
- Go to **Administration **> **Identity **> **ZIdentity **> **User Groups**.
-
Click **Import** **CSV**.
[See image.](#zsl-importg)
- In the **Import Groups** window, click **Download** **Sample** to download the template.
-
Enter the user group details in the CSV file template in the following format so that the Admin Portal successfully imports the CSV file:
- Retain the first line of the file, which is the header row. You can see the **Action**, **Name**, **Description** and **Disabled** columns.
- The file name must have a .csv extension.
- Enter one of the following for **Action**:
- `+ `(plus sign) to add a new group. When adding a user group, fill in the **Name **column. You can optionally enter your comments under the **Description** column.
- - (minus sign) to delete a user group. When deleting a user group, fill in the **Name **column.
Each user group must be on a separate line.
- (Optional) Seelct **Override Existing Entries** if you want to update your existing user group details, delete users, or add new user groups. Do not select this option if you only want to add new groups. If you attempt to add a group that already exists and this option is not selected, an error message is displayed stating that an identical group cannot be imported. If this occurs, review your CSV file and ensure that there is no duplication.
- Save the CSV file in your local folder.
-
In the **Import Groups** window, click **Browse File**.
[See image.](#zsl-importgroups)
- Browse and select the CSV file, then click **Open**.
-
Click **Import.** The CSV file is successfully imported.
The user groups are displayed on the **User Groups** page.
[]![Clicking the Import CSV button](/downloads/zslogin/administration/user-groups/importing-group-details-csv-file/zid-import-csv-button.png)
[]![Importing user group details](/downloads/zslogin/administration/user-groups/importing-group-details-csv-file/zid-import-groups.png)