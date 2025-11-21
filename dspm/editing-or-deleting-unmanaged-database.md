# Editing or Deleting Unmanaged Databases
Source: https://help.zscaler.com/dspm/editing-or-deleting-unmanaged-database
PDF: https://help.zscaler.com/pdf/com/en/1517571.pdf

You can modify or delete an unmanaged database server as required.
Editing an Unmanaged Database
To edit an unmanaged database server:
- Go to **Administration **>** Configuration **>** Service Registration**.
- On the **Service Registration** page, select the **Unmanaged Database** tab.
-
Do one of the following:
-
Click the **Actions** icon (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Edit** for the required database server.
[See image.](#ds-unmd-action-edit)
-
Click the name of the database server to go to the [Unamanaged Database details](/dspm/about-unmanaged-database#db-details) page, then Click **Actions**, and select **Edit**.
[See image.](#ds-unmd-details-edit)
The **Edit Unmanaged Database Server** window appears.
-
In the **Edit Unmanaged Database Server** window, click **Proceed** to continue.
[See image.](#img_confirm-message)
-
On the **Edit Unmanaged Database Server** page, update the following sections as required:
- **Cloud**: Update the cloud settings.
- **Database Server**: Update the database server configuration.
- **Authentication**: Update the authentication details.
- **Database Authentication**: Update the database authentication details (for HashiCorp Vault only).
[See image.](#img_edit-umdb)
- Click **Save**.
The unmanaged database server is updated.
Changes made to the database server configuration take effect only at the next scheduled scan.
[]![The Edit Unmanaged Database Server page with information relating to the cloud, database server, and authentication.](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/edit-unamanaged-db.png)
[]![Confirm editing unamanged database server window](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/confirm_message.png)
[]![Unmanaged Databases page with the Actions menu open, and showing the Edit option annotated.](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/ds-unmdaction-edit.png)
[]![Unmanaged Databases details page with a highlighted edit icon.](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/ds-unmddetails-edit.png)
Deleting an Unmanaged Database
To edit an unmanaged database server:
- Go to **Administration **>** Configuration **>** Service Registration**.
- On the **Service Registration** page, select the **Unmanaged Database** tab.
-
Do one of the following:
-
Click the **Actions** icon (![fa-action.png](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/fa-action.png)
), and select **Delete **for the required database server.
[See image.](#ds-unmd-action-delete)
-
Click the name of the database server to go to the [Unamanaged Database details](/dspm/about-unmanaged-database#db-details) page, then Click **Actions**, and select **Delete**.
[See image.](#ds-unmd-details-delete)
The **Delete Unmanaged Database Server** window appears.
-
In the **Delete Unmanaged Database Server** window, read the message, and then enter `CONFIRM` in the text box.
[See image.](#img_delete-db)
- Click **Delete Server**.
The unmanaged database server is deleted from the DSPM Admin Portal.
[]![Unmanaged Databases page with the Actions menu open, and showing the Delete option annotated.](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/ds-unmdaction-delete.png)
[]![Unmanaged Databases details page with a highlighted delete icon.](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/ds-unmddetails-delete.png)
[]![Confirming deletion of an unmanaged database server](/downloads/dspm/administration/unmanaged-database/editing-or-deleting-unmanaged-database/delete-message.png)