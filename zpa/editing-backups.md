# Editing Backups
Source: https://help.zscaler.com/zpa/editing-backups
PDF: https://help.zscaler.com/pdf/com/en/1485856.pdf

To edit a [backup](/zpa/about-backup-and-restore):
- Go to **Configuration & Control** > **Administration Control** > **Backup and Restore**.
- Locate the **Backup Name** within the table and click the **Edit** icon.
The **Edit Backup** window appears.
-
In the **Edit Backup** window, you can only modify the following fields:
- **Name**: The name of the backup.
- **Golden Backup**: Enable or disable the Golden Backup. A golden backup is the last known good backup of the policies and configuration settings. There can only be one golden backup at any given time.
- **Description**: The description of the backup.
[See image.](#editRestorePoint)
- Click **Save**.
If the backup status has failed, it can't be marked as a golden backup.
[]![Edit Backup window](/downloads/zpa/administration/backup-restore/editing-restore-points/zpa-edit-backup.png)