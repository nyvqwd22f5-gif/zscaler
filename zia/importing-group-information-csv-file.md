# Importing Group Information from a CSV File
Source: https://help.zscaler.com/zia/importing-group-information-csv-file
PDF: https://help.zscaler.com/pdf/com/en/1401111.pdf

You can import up to 3,000 user groups onto Zscaler at one time by using CSV files. Ensure that the CSV file is in a Zscaler-supported format before importing.
To create and import a Zscaler-supported CSV file:
- Go to **Administration** > **User Management**.
- Click the **Groups** tab.
- To create your CSV file:
-
Download the group information template by clicking the **Sample Import CSV file** button.
[See image.](#csvdown)
- Open and update the sample CSV file with your group information. Ensure that the group information is in the following format to successfully import the file:
- Retain the first line of the file, which is the header row. You will see **Action**, **Name**, and **Comments** columns.
-
Enter each group entry in a separate row:
- To add a new group, enter `+` under the **Action** column and the group name under the **Name **column. You can optionally enter your comments under the **Comments** column.
- To remove a group, enter `-` under the **Action** column and the group name under the **Name** column.
[See image.](#csvsample)
- When your CSV file is ready to import, click **Import**.
- In the **Import Groups** window:
- Click **Choose file**.
- Browse and select the CSV file, then click **Open**.
- Click **Import**.
[See image.](#Import-Groups-Window)
- After the CSV file is successfully imported, click **Close**.
[]![Download Sample Import CSV file ](/downloads/zia/authentication-administration/provisioning-authenticating-users/user-management/groups/importing-group-information-csv-file/CSVfile_button.png)
[]![Sample CSV File](/downloads/zia/authentication-administration/provisioning-authenticating-users/user-management/groups/importing-group-information-csv-file/CSVfile_code.png)
[]![Import Groups Window](/downloads/zscaler-tech-pubs-style-guide/draft-articles/importing-group-information-csv-file-draft/Import-Groups.png)