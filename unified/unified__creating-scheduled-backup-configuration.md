# Creating Scheduled Backup Configuration
Source: https://help.zscaler.com/unified/creating-scheduled-backup-configuration
PDF: https://help.zscaler.com/pdf/com/en/1495161.pdf

The backup configuration allows you to automatically back up policies and configuration settings. You can create a backup configuration schedule at which the [restore points](/unified/about-backup-and-restore) are automatically created at fixed intervals. An organization can have up to 12 restore points, including [manual](/unified/adding-restore-points-manually) and scheduled backups. If the number of restore points reaches a limit of 12, then the next restore point is created by removing the oldest restore point in the list. However, if the oldest restore point is a Golden Restore Point, then the next oldest restore point is removed.
To access this feature, contact your Zscaler Account team.
To create a scheduled backup configuration:
- Go to **Administration **> **Backup & Restore **> **Scheduled Backup Configuration**.
- Select **Enabled **for the** Scheduled Backups** option.
- Enter a name in the **Backup Prefix Name** field.
- In the **Backup** **Schedule **section, do the following:
- **Frequency**: Select either **Weekly** or **Monthly**.
- **Date**: Select the date on which you want the restore point to be created. This field appears when the **Frequency** is selected as **Monthly**.
- **Day**: Select the day of the week when you want the restore point to be created. This field appears when the **Frequency** is selected as **Weekly**.
- **Backup Creation Time**: Select the time at which you want the restore point to be created.
- **Time Zone**: Select the time zone in which the scheduled backup configuration should be valid.
- Click **Save** and activate the change.
![ZIA Admin Portal Backup Configuration page](/downloads/unified/administration/internet-saas/backup-restore/creating-scheduled-backup-configuration/Unified-Scheduled-Backup-Configuration.png)