# Creating Scheduled Backup Configurations for Private Applications
Source: https://help.zscaler.com/unified/creating-scheduled-backup-configurations-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1520726.pdf

The backup configuration allows you to automatically back up policies and configuration settings. You can create a backup configuration schedule at which the backups are automatically created at fixed intervals. An organization can have up to 10 backups, including manual and scheduled backups. If the number of backups reaches a limit of 10, then the next backup is created by removing the oldest backup in the list. If the oldest backup is a golden backup, then the next oldest backup is removed. To learn more, see [About Backup and Restore for Private Applications](/unified/about-backup-and-restore-private-applications).
To create a scheduled backup configuration:
- Go to **Administration** > **Backup & Restore** > **Private Applications**.
- Click **Schedule**.
The **Schedule** drawer appears.
- In the **Schedule **drawer:
- **Schedule a Backup**: Enable to configure the automatic backup scheduler. This is disabled by default.
- **Backup Prefix Name**: Enter a name for the automatically created backup.
-
In the **Backup Schedule **section:
- **Frequency**: Select a frequency from the drop-down menu for when the scheduled backup is created (**Daily**, **Weekly**, **Monthly**). By default, this is set to **Monthly**.
- **Date**: Select the date on which you want the backup to be created. This field appears when the **Frequency **is selected as **Monthly**.
- **Day**: Select the day of the week when you want the backup to be created. This field appears when the **Frequency **is selected as **Weekly**.
-
**Backup Creation Time**: Select the time at which you want the backup to be created.
The creation time in the backup name for the scheduled backup configuration might differ from the creation date shown on the Backup and Restore page due to the selected time zone of the user.
- **Time Zone**: Select the time zone in which the scheduled backup configuration should be valid.
[See image.](#backupConfiguration)
- Click **Save**.
[]![Viewing the Schedule side-drawer](/downloads/zpa/administration/backup-restore/creating-scheduled-backup-configurations/zpa-backup-scheduler.png)