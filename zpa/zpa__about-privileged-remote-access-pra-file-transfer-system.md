# About the Privileged Remote Access (PRA) File Transfer System
Source: https://help.zscaler.com/zpa/about-privileged-remote-access-pra-file-transfer-system
PDF: https://help.zscaler.com/pdf/com/en/1508956.pdf

If a user has the PRA File Transfer System feature enabled, they can click on the[ PRA File Transfer System icon on the PRA Portal page](/zpa/accessing-privileged-remote-access-portal). The user can manage and view uploaded files on the My Files and Uninspected Files tabs. The admin must also configure a portals policy to enable the following actions: deleting a file, accessing uninspected files, uploading an inspected file (via [DI scan](/zia/sandbox-submission-api#/zscsb/discan-post) or Sandbox). The visibility of the files displayed on the Uninspected Files page are dependent on the user's permissions. You can view the analytics of the uploaded inspected files on the [Files page](/zpa/accessing-privileged-remote-access-files).
The PRA File Transfer System provides the following benefits and enables you to:
- View files that have been inspected and uploaded.
- View files that have been inspected and flagged as malicious content.
- View files that are pending inspection.
[]About the My Files Page
On the My Files page (PRA Portal > Files icon > My Files), you can do the following:
- Click the** Home Page** icon to go to the PRA Portal Home page.
- Select the listed icons as mentioned in [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal).
- Filter the information that appears in the table. By default, no filters are applied. The characters & and + cannot be used in the PRA Portal search field.
- Refresh the table.
- [Upload a file.](/zpa/uploading-and-transferring-files-pra-file-system) You can upload up to 10 files for each privileged portal.
- View a list of the uploaded files. For each file, you can see:
- **File Name**: The name of the uninspected file. Only the following characters can be used when naming a file: & $ , _ - ! @ ( ) [ ]= ' ~ ;
- **Size**: The size of the file. You can upload a file with a maximum limit of up to 1 GB.
- **Last Updated**: The date and time that the file was most recently updated.
- **Detected File Type**: The file type detected during inspection.
- **Status**: Displays one of the following inspection status types for the ZIA Integration inspection process:
- **Uploading**: The file is uploading.
- **Pending**: The file is pending inspection.
- **Uninspected**: The file was not inspected. The uninspected file is added to the **Uninspected Files** page.
- **Success**: The file inspection was completed and no malicious content or malware was found.
- **Error**: There was an error during the upload of the file.
- **Malicious**: The file was found to be malicious during inspection.
The status of the uploading process can be tracked in the bottom right window. If you click **Cancel**, a window appears to confirm the cancellation. If you cancel a file upload, the file won't appear on the **My Files** page.
![Upload status window on the My Files page](/downloads/zpa/privileged-remote-access-management/privileged-portals/about-pra-file-system/Upload%20status%20window_0.png)
- Download the file. When you select this option, the download is shown in the top-right of your browser after the download is complete. You can view the download in your system's Downloads folder.
- Delete the file. You will receive a confirmation window before the file is deleted. You can't delete the file if it is being uploaded or if it contains malicious content.
- Adjust the table settings.
- Go to the [Uninspected Files](#uninspect) page to manage files that have been uploaded but haven't been inspected.
![The My Files page in the PRA File Transfer System section of a PRA privileged portal](/downloads/zpa/privileged-remote-access-management/privileged-portals/about-pra-file-system/My%20Files%20page%20w%20steps_1.png)
[]About the Uninspected Files Page
On the Uninspected Files page (PRA Portal > Files icon > My Files), you can do the following:
- Select the **Home Page** icon to go to the PRA Portal Home page.
- Select the listed icons as mentioned in [Accessing a Privileged Remote Access Portal](/zpa/accessing-privileged-remote-access-portal).
- Filter the information that appears in the table. By default, no filters are applied.
- Refresh the table.
- View a list of all the uninspected files. For each file, you can see:
- **File Name**: The name of the uninspected file.
- **Size**: The size of the file. You can upload a file with a maximum limit of up to 1 GB.
- **Last Updated**: The date and time that the file was most recently updated.
- **User**: The email of the user that uploaded the file.
- Download the uninspected files.
- Adjust the table settings.
- Go to the [My Files](#my) page to manage files that have been uploaded and inspected.
![The Uninspected Files page in the PRA File Transfer System section of a PRA privileged portal](/downloads/zpa/privileged-remote-access-management/privileged-portals/about-pra-file-system/Uninspected%20Files%20page%20w%20steps.png)