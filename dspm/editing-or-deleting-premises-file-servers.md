# Editing or Deleting an On-Premises File Server
Source: https://help.zscaler.com/dspm/editing-or-deleting-premises-file-servers
PDF: https://help.zscaler.com/pdf/com/en/1532038.pdf

You can modify or delete an on-premises file server as required.
Editing an On-Premises File Server
To edit an on-premises file server:
- Go to **Administration **>** Configuration **>** Service Registration**.
- On the **Service Registration** page, select the **On-Premises File Servers** tab.
-
Do one of the following:
-
Click the **Actions** icon (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Edit** for the required file server.
[See image.](#ds-action-edit)
-
Click the name of the file server to go to the [On-Premises File Server details](/dspm/about-unmanaged-database#on-prem-tab) page, then click **Actions**, and select **Edit**.
[See image.](#ds-details-edit)
The **Edit On-Premises File Server** confirmation window appears.
-
In the **Edit On-Premises File Server** confirmation window, click **Proceed** to continue.
[See image.](#img_confirm-message)
-
In the **Edit On-Premises File Server** window, update the following sections as required:
- **File Server Information**:
- **Version** (only for **NFS** protocol): Select the NFS version to use.
- **Connection Attributes**:
- **File Server IP / Hostname**: Update the IP address or hostname of the file server.
- **Domain Name**: Update the domain name associated with the file server.
- **Port**: Update the port used for communication protocol.
- **Default Port**: SMB uses `445` and NFS uses `2049`.
- **Custom Port**: Enter a valid port number based on your configuration requirements.
- **Authentication**:
- **Username**: Update the username used to authenticate access to the file server.
-
**Password**: Update the password associated with the username.
[See image.](#img_edit)
- Click **Save**.
The on-premises file server is updated.
Changes made to the on-premises file server configuration take effect only at the next scheduled scan.
[]![The On-Premises File Server drawer with the editable fields are enabled. ](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-onprem-file-server-edit-details.png)
[]![Confirm editing On-Premises File Server window](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-file-server-edit-confirmation.png)
[]![On-Premises File Server page with the Actions menu open, and showing the Edit option annotated.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-file-server-edit.png)
[]![On-Premises File Server details page with a highlighted edit option.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-file-server-details-edit.png)
Deleting an On-Premises File Server
To delete an on-premises file server:
- Go to **Administration **>** Configuration **>** Service Registration**.
- On the **Service Registration** page, select the **Unmanaged Database** tab.
-
Do one of the following:
-
Click the **Actions** icon (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Delete **for the required file server.
[See image.](#ds-action-delete)
-
Click the name of the file server to go to the [On-Premises File Server details](/dspm/about-unmanaged-database#on-prem-tab) page, then click **Actions**, and select **Delete**.
[See image.](#ds-details-delete)
The **Delete On-Premises File Server** confirmation window appears.
-
In the **Delete On-Premises File Server** confirmation window, read the message, and then enter `CONFIRM` in the text box.
[See image.](#img_delete-db)
- Click **Delete Server**.
The on-premises file server is deleted from the DSPM Admin Portal.
[]![On-Premises File Server page with the Actions menu open, and showing the Delete option annotated.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-file-server-delete.png)
[]![On-Premises File Server details page with a highlighted delete option.](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-file-server-details-delete.png)
[]![Confirming deletion of an On-Premises File Server](/downloads/dspm/administration/premise-scanners/adding-premises-scanner-integration/ds-file-server-delete-confirmation.png)