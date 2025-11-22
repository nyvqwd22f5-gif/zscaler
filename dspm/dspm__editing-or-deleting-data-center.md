# Editing or Deleting an On-Premises Data Center
Source: https://help.zscaler.com/dspm/editing-or-deleting-data-center
PDF: https://help.zscaler.com/pdf/com/en/1526571.pdf

You can modify or delete an on-premises data center as required.
Editing an On-Premises Data Center
To edit an on-premises data center:
- Go to **Administration **>** Configuration **>** On-Premises Data Center**.
-
Do one of the following:
-
Click **Actions** (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Edit** for the required data center.
[See image.](#ds-onprem-action-edit)
-
Click the name of the data center to go to the [On-Premises Data Center details](/dspm/about-data-center) page, then click **Actions** and select **Edit**.
[See image.](#ds-onprem-details-edit)
The **Edit Data Center** window appears.
-
In the **Edit Data Center** window, click **Proceed** to continue.
[See image.](#img_confirm-message)
-
On the **Edit On-Premises Data Center** page, update the following sections as required:
- **Business Unit**: Update the [business unit](/dspm/about-business-units) for the data center.
- **Associate Cloud Scanners for On-Premises Unmanaged Database**:
- **Association Name**: Update the name of the cloud network association.
- **Connected Cloud**: Update the cloud service provider where your data center is associated (Azure, AWS, or GCP).
- **DSPM Alias**: Update the DSPM alias for the selected cloud.
- **Connected Cloud Region**: Update the region where the cloud region is hosted.
- Click the **+ Add** button to add multiple cloud network associations for the data center.
- **Associate On-Premise Scanners for File Servers**:
- **Select On-Premises Scanner Integration**: Update the existing on-premises scanner integration to associate with the data center.
[See image.](#img-edit-onprem)
- Click **Save**.
The on-premises data center is updated.
Changes made to the on-premises data center configuration only take effect at the next scheduled scan.
[]![The on-premises data center page with information relating to the data center and cloud network association..](/downloads/dspm/administration/on-premise-data-center/editing-or-deleting-data-center/ds-onprem-dc-details-edit-details.png)
[]![Confirm editing on-premises data center window](/downloads/dspm/administration/on-premise-data-center/editing-or-deleting-data-center/edit-confirm_message.png)
[]![On-Premises Data Centers page with the Actions menu open, and showing the Edit option annotated.](/downloads/dspm/administration/on-premise-data-center/editing-or-deleting-data-center/ds-onprem-action-edit.png)
[]![On-Premises Data Center details page with a highlighted edit icon.](/downloads/dspm/administration/on-premise-data-center/editing-or-deleting-data-center/ds-onprem-dc-details-edit-menu.png)
Deleting an On-Premises Data Center
To delete an on-premises data center:
Deleting an on-premises data center is restricted if it is associated with any [unmanaged databases](/dspm/about-unmanaged-database). The **Delete** option is grayed out in such cases.
- Go to **Administration **>** Configuration **>** On-Premises Data Center**.
-
Do one of the following:
-
Click **Actions** (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Delete **for the required data center.
[See image.](#ds-onprem-action-delete)
-
Click the name of the data center to go to the [On-Premises Data Center details](/dspm/about-data-center) page, then click **Actions** and select **Delete**.
[See image.](#ds-onprem-details-delete)
The **Delete Data Center** window appears.
-
In the **Delete Data Center** window, read the message, and then enter `CONFIRM` in the text box.
[See image.](#img_delete-ds)
- Click **Delete Server**.
The on-premises data center is deleted from the DSPM Admin Portal.
[]![Unmanaged Databases page with the Actions menu open, and showing the Delete option annotated.](/downloads/dspm/administration/on-premise-data-center/editing-or-deleting-data-center/ds-onprem-action-delete.png)
[]![Unmanaged Databases details page with a highlighted delete icon.](/downloads/dspm/administration/on-premise-data-center/editing-or-deleting-data-center/ds-onprem-dc-details-delete-menu.png)
[]![Confirming deletion of an unmanaged database server](/downloads/dspm/administration/on-premise-data-center/editing-or-deleting-data-center/ds-onprem-delete-confirm.png)