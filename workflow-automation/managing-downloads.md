# Managing Downloads
Source: https://help.zscaler.com/workflow-automation/managing-downloads
PDF: https://help.zscaler.com/pdf/com/en/1488336.pdf

The Downloads page allows you to download the incidents that you export on the Incidents page to a CSV file. When you export incidents from the Incidents page, the activity is transferred to the Downloads page, which logs the activity and displays the status of your download in real time. After the download process is completed, the incident file becomes a downloadable file. You can download it as a CSV file to your local system. The incident file is available to download for up to 7 days. To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
When you export numerous incidents, it takes time for the incidents to become available to download from this page. You receive an email notification when your incident file download is completed, suspended, partially completed, or has failed.
- [View Downloads](#view-downloads)
- [Download Incidents](#download-incidents)
- [Restart Download Incidents](#restart-downloads)
[]To view the downloaded incident files:
- Go to **My Activity**. The **My Activity** page appears, displaying the **Downloads** and **Bulk Actions** tabs.
-
Click the **Downloads** tab. The **Downloads** tab lists all the downloaded incident files from the** Incidents** page. For each file, you can view:
- **File Name**: The name of the incident file.
- **Generation Time**: The date and time when the admin exported the incidents on the Incidents page.
- **Expiry Date**: The expiration date and time of the incident file.
-
**Status**: The download status of the incident file. The statues are:
- **Complete**: The export action performed is successfully completed for the selected incidents, and the incident file is ready to download.
- **Partially Complete**: The export action performed is incomplete for some of the selected incidents.
- **Suspended**: The export action performed is suspended due to technical issues. Workflow Automation automatically resumes the download activity when the issue is resolved.
- **Failed**: The export action performed failed for the selected incidents.
Hover over the **Information** icon next to a status to view details of each incident file download.
[See image.](#info-icon-suspended)
- **Notes**: Additional notes or information that the admin added when exporting the incidents.
You can also search for a file using the** Search** field on the page to download it.
[See image.](#view-downloads-image)
[]To download incidents:
- Go to **My Activity**. The **My Activity** page appears, displaying the **Downloads** and **Bulk Actions** tabs.
- Click the **Downloads** tab. The **Downloads** tab lists all the downloaded incident files from the** Incidents** page.
-
In the **Actions** column, click the **Download **icon for the incident file you want to download. The incidents are downloaded to a CSV file on your local system.
[See image.](#download-incidents-image)
You can only download an incident file with the **Complete** status. If the status of the file is** Partially Complete, Suspended**, or **Failed**, you cannot download it.
[]For incident file downloads that are partially complete or failed, you can restart the action on the **Downloads** page.
To restart a download:
-
Go to **My Activity**. The **My Activity** page appears, displaying the **Downloads** and **Bulk Actions** tabs.
[See image.](#my-activity-icon)
- Click the **Downloads** tab. The **Downloads** tab lists all the downloaded incident files from the** Incidents** page.
-
Restart a download in one of the following ways:
-
For a partially complete download, click the **Resume** icon in the **Actions** column to restart downloading the pending incidents. The download restarts, and the progress is displayed in the **Status** column.
[See image.](#reume-icon)
-
For a failed download, click the **Retry** icon in the **Actions** column to restart the download. The download restarts, and the progress is displayed in the **Status** column.
[See image.](#retry-icon)
You can only restart an incident file download a maximum of three times. If you reach the maximum number of attempts, go to the **Incidents** page and perform the export action again.
[See image.](#error-message-maximum-attempts)
[]![Screenshot of the My Activity icon in the left-side navigation](/downloads/workflow-automation/getting-started/admin-portal/managing-downloads/WA-Managing-Downloads-My-Activty-Icon-Nav.png)
![Viewing the My Activity Page - Downloads page in the Workflow Automation Admin Portal](/downloads/workflow-automation/getting-started/admin-portal/managing-downloads/WA-Managing-Downloads%20-My-Activity-Page-Downloads-Tab.png)
[]
[]![Viewing the Download icon in the My Activity > Downloads page](/downloads/workflow-automation/getting-started/admin-portal/managing-downloads/WA-Managing-Downloads-My-Activity-Page-Download-Icon.png)
[]![Viewing the Downloads page showing the Information icon for a Partially Complete download](/downloads/workflow-automation/getting-started/admin-portal/managing-downloads/WA-Managing-Downloads-Partially-Complete-Info-Icon.png)
![Viewing the Downloads page showing the Resume icon for a Partially Complete download](/downloads/workflow-automation/getting-started/admin-portal/managing-downloads/WA-Managing-Downloads-Partially-Complete-Resume-Icon.png)
[]
![Viewing the Downloads page showing the Retry icon for Failed downloads](/downloads/workflow-automation/getting-started/admin-portal/managing-downloads/WA-Managing-Downloads-Failed-Retry-Icon.png)
[]
![Downloads page displaying the following message: You have reached the maximum number of attempts to resume download. Go to the Incidents page and perform the bulk action again.](/downloads/workflow-automation/getting-started/admin-portal/managing-downloads/WA-Managing-Downloads-Resume-Retry-Message-Image.png)
[]