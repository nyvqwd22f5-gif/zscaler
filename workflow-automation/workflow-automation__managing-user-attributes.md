# Managing User Attributes
Source: https://help.zscaler.com/workflow-automation/managing-user-attributes
PDF: https://help.zscaler.com/pdf/com/en/1503486.pdf

Workflow Automation fetches the end user information (i.e., user attributes) that is displayed in the Workflow Automation Admin Portal, such as the employee ID, email address, and manager's name, from the following two data sources:
- **SCIM**: The System for Cross-domain Identity Management is a standard protocol that you can use to manage user attributes with the Zscaler service. You can use SCIM for automatically updating user information on the Workflow Automation database to reflect changes in your user directory. To learn more, see [Understanding SCIM](/zia/understanding-scim).
- **CSV**: Comma Separated Value (CSV) is used to manually import user attributes as a `.csv` file to be displayed in the Workflow Automation Admin Portal.
On the User Attributes page, you can import the end user attributes as CSV files. Workflow Automation provides access to predefined CSV template versions and instructions on how to construct your CSV file with your organization's end user information. You can download and modify any one of the available predefined CSV template versions, based on your requirements, and import it into the Workflow Automation Admin Portal.
Only a valid CSV file that is constructed based on one of the CSV template versions and the CSV template instructions can be imported into Workflow Automation.
To view the user attributes imported through a CSV file in the Workflow Automation Admin Portal, you must select **CSV** as the primary data source and select a unique identifier on the [Account Settings](/workflow-automation/managing-account-settings) page. Otherwise, SCIM protocol is selected as the default primary data source. After you select **CSV** as the primary user data source, Workflow Automation displays only the user attributes available in the CSV file. If a user attribute is missing from the CSV file, Workflow Automation does not populate that data.
The unique identifiers (email address and employee ID) are used to identify a specific user in the CSV file. If the selected unique identifier is not available in the CSV file, Workflow Automation uses the other (unselected) unique identifier to locate the user in the CSV file. When neither unique identifier is available in the imported CSV file, Workflow Automation fetches that user information from the SCIM protocol. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
Managing User Attributes CSV Files
- [Import CSV Files](#import-csv-file)
- [View Imported CSV Files](#view-csv-file)
- [Restart CSV File Import](#restart-import)
- [Download a CSV File](#download-csv-file)
[]Importing a CSV file with numerous user attributes takes time to complete. You receive an email notification when your CSV file import into Workflow Automation is completed, partially completed, or has failed.
To import the user attributes as a CSV file:
- In the Workflow Automation Admin Portal, go to **Setup** > **User Attributes**.
- Click **Import CSV**.
- On the** Import CSV** page, complete the following sections:
- **Prerequisite**: Complete the prerequisites to import a CSV file.
- If you are importing a CSV file for the first time, you must set the primary user data source and a unique identifier for your users. To update the settings:
- Click **Account Settings**. The **Account Settings** page appears.
-
Select **CSV** as the **Primary User Data Source** and select a **Unique Identifier** for the users.
To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
- If the Primary User Data Source and the Unique Identifier are already available, then the selected settings are displayed in this section. To modify the settings:
- Click **Account Settings**. The **Account Settings** page appears.
-
Modify the **Primary User Data Source**.
After you import your first CSV file to the **User Attributes** page, you cannot change the selected Unique Identifier. To update your unique identifier settings, contact Zscaler Support. To learn more, see [Managing Account Settings](/workflow-automation/managing-account-settings).
- **How does this work?**: This section displays the high-level process of importing the CSV file of user attributes into the Workflow Automation Admin Portal.
- **Resource**: This section provides the **CSV Template Instruction** drop-down from where you can download the instructions on how to construct the user attributes CSV as a `.pdf` file. This file provides the actual user attributes, the format of the attributes, the maximum character limitations, and example values for the CSV file.
- **Recommendations for the CSV file**: This section displays the limitations and general recommendations for the user attributes CSV file. You can download any one of the CSV template versions and modify it with your organization's user information.
-
Drag and drop or select the CSV file from your local folder. Select the version type of the file and then click **Validate**. Workflow Automation validates the format of the file against the selected version. After the validation is complete, click **Import** to import the file.
[See image.](#import-csv-page-image)
If the file is empty or has incorrect data, the CSV file fails validation. You receive a link to download the errors in your file. Fix the errors and import the file again.
[See image.](#error-message-image)
After the CSV file import is complete, you can view the file on the **User Attributes **page.
[]For CSV file imports that are partially successful or failed, you can restart the import action.
To restart importing a CSV file:
- Go to the **Setup** > **User Attributes** page. The **User Attributes** page appears, listing all the CSV files uploaded.
-
For a partially complete CSV file import, under the **Actions** column, click the **Resume** icon to restart the action. The import action restarts, and the progress is displayed in the **Status** column.
[See image.](#resume-icon-image)
-
For a failed CSV file import, under the **Actions** column, click the **Retry** icon to restart the action. The import action restarts, and the progress is displayed in the **Status** column.
[See image.](#retry-icon-image)
You can only restart an import action a maximum of three times. If you reach the maximum number of attempts, import the CSV file again on the **User Attributes** page.
[See image.](#maximum-limit-restart-action)
[]To download a previously uploaded CSV file:
- Go to the **Setup** > **User Attributes** page. The **User Attributes** page appears, listing all the CSV files uploaded.
- For the CSV file you want to download, under the **Actions** column, click the** Download** icon. The CSV file is downloaded onto your local system.
[See image.](#download-icon-image)
[]To view the user attributes CSV files, go to **Setup** > **User Attributes**. The **User Attributes** page appears.
On the **User Attributes** page, you can do the following:
- Import user attributes as a CSV file.
- Search for an imported user attributes CSV file.
- View a list of imported CSV files. For each CSV file, you can view the following information:
- **File Name**: The name of the imported CSV file.
- **Imported By**: The username who imported the CSV file.
- **Initiated On**: The date and time when the CSV file import was initiated.
- **Completed On**: The date and time when the CSV file import was completed.
- **No. of New Users**: The number of users added through the CSV file.
- **No. of Updated Users**: The number of users updated through the CSV file
- **Size**: The size of the CSV file in bytes.
-
**Status**: The import status of the CSV file. The statuses are complete, partially complete, and failed.
Hover over the** Information** icon next to the status to view the details of each CSV file import.
[See image.](#information-icon-image)
- Download a previously uploaded CSV file.
- Resume importing a partially complete CSV file.
- Retry importing a failed CSV file.
- Delete a previously uploaded CSV file.
![Screenshot of the main User Attributes page](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-main-page.png)
[]![Screenshot of the Download icon on User Attributes page](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-download-icon.png)
[]![Screenshot of the Resume icon on the User Attributes page](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-partial-complete-resume-icon.png)
[]
![Screenshot of the Retry icon on the User Attributes page](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-failed-retry-icon.png)
![Information icon on the User Attributes page](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-partial-complete-information-icon_0.png)
[]
![Message - maximum number of attempts to restart action](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-max-limit-reached-message.png)
[]
![Screenshot of the error message with the download error list link in the Import CSV page](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-import-CSV-download-error-list.png)
[]
![Screenshot of the Import CSV page on the User Attributes page](/downloads/workflow-automation/data-protection/setup/managing-user-attributes/WA-managing-user-attributes-import-CSV-page.png)
[]