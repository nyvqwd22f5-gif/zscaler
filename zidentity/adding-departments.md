# Adding Departments
Source: https://help.zscaler.com/zidentity/adding-departments
PDF: https://help.zscaler.com/pdf/com/en/1499356.pdf

You can add departments in the ZIdentity Admin Portal and assign the specific department to users. A user can belong to only one department.
You can manually add each department or upload a CSV file that contains a list of departments.
- [Add a Department](#zsl-adddept)
- [Import Department Information from a CSV File](#zsl-import)
[]To add a new department:
- Go to **Directory **>** Departments**.
-
Click **Add Department**.
[See image.](#zsl-deptpage)
-
In the **Add Department **window:
- **Department Name**: Enter a department name.
- **Description**: Optionally, enter additional notes or information. The content cannot exceed 10,240 characters.
[See image.](#zsl-adddeptwindow)
- Click **Save** and activate the change.
After creating the department, you can add users to it.
[]You can import up to 1,000 departments using a CSV file. If you want to add multiple users to an existing department or change the department for multiple users, use the sample CSV file template.
To import new departments or modify existing departments, using a CSV file:
- Go to **Directory **>** Departments**.
-
Click **Import CSV**.
[See image.](#zsl-importcsv)
The **Import Department** window appears.
[See image.](#zsl-importdeptwindow)
- Click **Download Sample** to download a CSV template.
- Enter your department information in the CSV file template.
- When you have the CSV file in the correct format, in the **Import Department** window, click **Browse File**.
- Locate the CSV file in your local folder, then click **Open**.
- Click **Override Existing Entries** if you want to replace the existing list of departments with those provided in the CSV file.
- Click **Import**.
-
After the CSV file is successfully imported, the **Import Department **window appears, showing the total number of records that are added.
[See image.](#zsl-importlist)
-
Check the details, then click **Close**.
The **Department page** displays the newly added departments.
[]![Adding a department](/downloads/zslogin/administration/departments/adding-departments/zid-add-department.png)
[]![Clicking Add Department button](/downloads/zslogin/administration/departments/adding-departments/zid-add-department-button.png)
[]![Clicking Import CSV button](/downloads/zslogin/administration/departments/adding-departments/zid-importcsv-button.png)
[]![The Import Department window](/downloads/zslogin/administration/departments/adding-departments/zid-import-department.png)
[]![Imported Department details](/downloads/zslogin/administration/departments/adding-departments/zid-import-department-details.png)