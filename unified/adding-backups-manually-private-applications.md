# Adding Backups Manually for Private Applications
Source: https://help.zscaler.com/unified/adding-backups-manually-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1520741.pdf

You can back up and restore a set of policies and configuration settings, and save up to 10 backups. To learn more, see [About Backup and Restore for Private Applications](/unified/about-backup-and-restore-private-applications).
To add a backup:
- Go to **Administration** > **Backup & Restore** > **Private Applications**.
- Click **Add Backup**.
The **Add Backup** window appears.
-
In the **Add Backup** window:
- **Name**: Enter a name to identify the backup.
- **Golden Backup**: Enable this option if you want to set the backup as the golden backup. A golden backup is the last known good backup of the policies and configuration settings. There can be only one golden backup at any given point in time.
- **Description**: (Optional) Enter additional notes or information.
[See image.](#addRestorePoint)
- Click **Save**.
If the number of backups reaches a limit of 10, you cannot add a new backup manually without deleting an existing one.
After a backup is created manually or automatically, you can view a list of backups applied to the particular restore point by the admin, or you can view the post-restore reports for each individual backup. To learn more, see [Viewing Restore Activities and Restore Reports](/unified/viewing-restore-activities-and-restore-reports).
[]
![Viewing the Add Backup window](/downloads/zpa/administration/backup-restore/adding-restore-points-manually/zpa-add-backup.png)