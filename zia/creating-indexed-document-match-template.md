# Creating an Indexed Document Match Template
Source: https://help.zscaler.com/zia/creating-indexed-document-match-template
PDF: https://help.zscaler.com/pdf/com/en/1402026.pdf

[Watch a video on Indexed Document Matching.](https://fast.wistia.net/embed/iframe/5jnzyl383a)
Using the Index Tool, you can create, modify, or delete an Indexed Document Match (IDM) index template.
You can create up to 64 IDM templates for your organization. The largest file you can upload to an IDM template is 400 MB. You can index up to 100GB of files for your organization.
Creating an IDM Template
You can create manual or scheduled IDM templates:
- Manual IDM Templates: A manual IDM template allows you to manually upload your organization’s critical documents.
- Scheduled IDM Templates: A scheduled IDM template allows you to set up an SSH connection and schedule updates between the template and your organization’s storage server for the critical documents.
To create an IDM template:
- Go to https://<IP Address of the Index Tool VM> to access the Index Tool. Log in to the Index Tool with your ZIA Admin Portal login credentials.
[See image.](#index-tool-image)
- Click **Indexed Document Match Templates**.
- In the Indexed Document Match Templates dashboard, click **Create New Template** and then click one of the following:
- [Manual IDM Template](#manual-IDM-template)
- [Scheduled IDM Template](#scheduled-IDM-template)
After saving the template, you are redirected to the **Indexed Document Match Template** dashboard, and the tool will process the template. If the template was created properly, **Completed** is shown in the **Status** column. If the template was created, but the documents weren’t indexed yet, then **Created** is shown. If the template was not created properly, then **Error** is shown.
Once an IDM template is created, it appears on the [Indexed Document Match](/zia/about-indexed-document-match) page of the ZIA Admin Portal, where you can view the template’s details or delete it. You cannot change the template name after creation. In order to change the name, you must create a new template.
Modifying an IDM Template
You can submit new documents or delete indexed documents for manual IDM templates in the Index Tool.
In order to submit new documents or delete indexed documents for scheduled IDM templates, you must make the changes in the document server. The template will update at the scheduled time, or you can schedule an immediate update for the template in the Index Tool. To reschedule a scheduled template's update, click the **Calendar** icon in the **Actions** column.
[See image.](#scheduled-IDM-template-edit-image)
To modify a manual IDM template:
- Log in to the Index Tool.
- In the **Indexed Document Match Templates** dashboard, locate the manual template you want to modify.
In the **Template Name** column, you can click the **Search** icon to search for a specific template.
- In the **Actions** column, click the **Edit** icon.
[See image.](#manual-IDM-template-edit-image)
- In the **Manual Indexed Document Match Template**:
- If you need to submit a new document for the template, click **Upload File**. In the window that appears, drag and drop the file into the window or click **Browse** to select the file.
- If you need to delete a document from the template, locate the document in the table and click the **Delete** icon.
In the **File Name** column, you can click the **Search** icon to search for a specific file.
- Click **Save**.
[]Deleting an IDM Template
To delete a manual or scheduled IDM template:
- Log in to the Index Tool.
- In the **Indexed Document Match Templates** dashboard, locate the template you want to remove.
In the **Template Name** column, you can click the **Search** icon to search for a specific template.
- In the **Actions** column, click the **Delete** icon.
- In the confirmation window that appears, click **Delete**.
You can also delete the IDM template from the ZIA Admin Portal:
- Go to **Administration** > **Index Templates**.
- In the **Indexed Document Match** tab, locate the template you want to remove.
- Click the **Delete** icon.
[See image.](#ZIA-Admin-Portal-delete-image)
- In the confirmation window that appears, click **OK**.
[]When you first create a new manual IDM template, you can only upload one file. Once you save the template, you can edit the template to add more files.
In the **Manual Indexed Document Match Template** window:
- Enter a **Template Name**. After the template is saved, this name appears in the [Indexed Document Match](/zia/about-indexed-document-match) page in the ZIA Admin Portal.
- Click **Upload File**.
The **Select File** window appears.
- Drag and drop a file into the window or click **Choose File** to select a file.
- Click **Upload**.
[See image.](#manual-IDM-template-image)
- Click **Save**.
[]When you create a scheduled IDM template, you must set up an SSH connection between the template and your organization’s document server. You must then schedule regular updates between the template and server.
In the **Scheduled Indexed Document Match Template** window:
- Under **General**:
- Enter a **Template Name**. After the template is saved, this name appears in the [Indexed Document Match](/zia/about-indexed-document-match) page in the ZIA Admin Portal.
- For **Host**, enter the IP address or domain for the document server.
- Specify the **Port** for the document server.
- Specify the **File Path** for the directory where the documents are located in the document server.
[See image.](#scheduled-IDM-template-image-1)
- Under **SSH Configuration**:
- Click **Download** to download the SSH key.
- Copy the username. You will use this username to create a user in your document server.
- Go to your document server and complete the following steps:
- Create a user with the username you copied from the Index Tool.
- Add the downloaded SSH key to the user’s trusted keys.
- Ensure that the user has read access to the directory in the specified file path.
- Click **Verify** in the template to verify the SSH setup configuration. You cannot save the template until the setup is configured properly and verified.
[See image.](#scheduled-IDM-template-image-2)
- Under **Schedule**:
- **Repeat**: Choose if the update will repeat **Monthly**, **Weekly**, or **Daily**.
- **Every**: If you selected **Monthly** or **Weekly**, choose when in the selected period the update will repeat. For example, if you selected Weekly, you can choose to have the update happen every Friday.
- **Time**: Select what time the schedule update will happen on.
- **Time Zone**: Select the time zone your update will happen in.
- **Update Now**: Select to immediately update the template.
[See image.](#scheduled-IDM-template-image-3)
- (Optional) Enter a **Description** for the template.
- Click **Save**.
[]![Logging in to the Zscaler Index Tool](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/ZIA-Index-Tool.png)
[]![Configuring a manual Indexed Document Match template](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/ZIA-Manual-IDM-Template.png)
[]![Configuring the General fields for a scheduled Indexed Document Match template](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/ZIA-Scheduled-IDM-Template-General.png)
[]![Configuring the SSH Configuration fields for a scheduled Indexed Document Match template](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/ZIA-Scheduled-IDM-Template-SSH.png)
[]![Configuring the Schedule settings for a scheduled Indexed Document Match template](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/Scheduled-IDM-Template-Schedule-ZIA.png)
[]![The Calendar icon for rescheduling updates for a scheduled IDM template](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/ZIA-Scheduled-IDM-Template-Calendar.png)
[]![The Edit icon for updating manual IDM templates](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/ZIA-Manual-IDM-Template-Edit.png)
[]![Deleting an Indexed Document Match template in the Zscaler Internet Access (ZIA) Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-indexed-document-match/creating-indexed-document-match-template/ZIA-Delete-IDM-Template.png)