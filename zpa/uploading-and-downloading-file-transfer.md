# Uploading and Downloading with File Transfer
Source: https://help.zscaler.com/zpa/uploading-and-downloading-file-transfer
PDF: https://help.zscaler.com/pdf/com/en/1485546.pdf

All file transfers (both uploads and downloads) take place in a Zscaler-generated drive on your [privileged console](/zpa/about-privileged-consoles). When you click the **File Transfer** icon (![File%20Transfer%20icon_0.png](/downloads/zpa/privileged-remote-access-management/privileged-consoles/uploading-and-downloading-file-transfer/File%20Transfer%20icon_0.png)
) within a privileged console, the File Transfer window appears. In this window, you can inspect, upload, and/or download files, based on the [privileged capabilities policies](/zpa/configuring-privileged-capabilities-policies) that you have set. The Upload and Download options are disabled by default, but you can still open File Transfer and view the files. If the Upload and Download options are enabled, you can still upload and download files from the File Transfer window even if your screen is locked.
If you have the [PRA File Transfer System](/zpa/about-pra-file-system), the steps to upload and transfer files are different. To learn more, see [Uploading and Transferring Files for the PRA File Transfer System](/zpa/uploading-and-transferring-files-pra-file-system).
If you are using a Windows-based privileged console with an RDP protocol, a remote drive is automatically mounted and all transferred files are handled here. Files can be copied in and out of that drive folder. If the target Windows system has Device and Resource redirection disabled in the local group policy editor, the File Transfer feature is not possible due to the drive not being mounted with Privileged Remote Access (PRA). You must have Windows version 7 or later to use the File Transfer feature.
If you are using a privileged console with a VNC protocol, the SFTP service needs to be previously enabled on the VNC server and the authentication for SFTP needs to match the VNC configuration.
If SFTP is not configured on the VNC target, and a privileged capabilities policy with file transfer is configured for the associated privileged console, then end users cannot connect to that privileged console.
Uploading Files
To upload files:
- Go into the privileged console.
- Click the **File Transfer** icon at the bottom of the screen.
The **File Transfer** window appears.
- In the **File Transfer** window, select the files you want to upload and click **Upload**.
[See image.](#Upload)
The **Upload Progress** window appears. If you enabled **Inspect**, then the files are inspected prior to uploading. If **Inspect** is not enabled, then this step is bypassed.
When uploading a file, choose a writable directory from a local machine. If you attempt to upload files from a local machine to a non-writable directory, the upload will fail. After it fails, if you navigate from a non-writable directory to a writable directory with the File Transfer window open, and then use File Transfer to select files from a local machine to a writable directory, it also fails the first time. Additional file uploading attempts to a writable directory should succeed.
[See image.](#Uploadprogress)
- When the file upload is complete, the **Completed** step is highlighted.
If there is an issue with the file inspection, then the upload is paused and you receive a notification that the inspection wasn’t completed.
If you want to cancel an upload in progress, click **Cancel**. This stops the upload from completing.
[See image.](#Cancel)
Downloading Files
To download files:
- Go into the privileged console.
- Click the **File Transfer** icon at the bottom of the screen.
The **File Transfer** window appears.
- In the **File Transfer **window, the files that have download capabilities will have a **Download File** option to the right.
[See image.](#Download)
- Click **Download File**. The files should immediately be downloaded, and you should see a notification at the bottom left of your screen.
[]![The Upload feature in the File Transfer window within a privileged console  ](/downloads/zpa/privileged-remote-access-management/accessing-privileged-remote-access-portal/Upload%20button%20highlight.png)
[]![Upload progress bar within the Upload Progress window for File Transfer](/downloads/zpa/privileged-remote-access-management/accessing-privileged-remote-access-portal/Upload%20progress.png)
[]![Cancel button in the Upload Progress window](/downloads/zpa/privileged-remote-access-management/accessing-privileged-remote-access-portal/Cancel%20button.png)
[]![Using the download feature in the File Transfer window within a privileged console  ](/downloads/zpa/privileged-remote-access-management/accessing-privileged-remote-access-portal/Download%20button%20highlight_0.png)