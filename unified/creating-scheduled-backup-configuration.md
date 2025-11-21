# Creating Scheduled Backup Configuration
Source: https://help.zscaler.com/zia/creating-scheduled-backup-configuration
PDF: https://help.zscaler.com/pdf/com/en/1401821.pdf

The backup configuration allows you to automatically back up policies and configuration settings. You can create a backup configuration schedule at which the [restore points](/zia/about-backup-and-restore) are automatically created at fixed intervals. An organization can have up to 12 restore points, including [manual](/zia/adding-restore-points-manually) and scheduled backups. If the number of restore points reaches a limit of 12, then the next restore point is created by removing the oldest restore point in the list. However, if the oldest restore point is a Golden Restore Point, then the next oldest restore point is removed.
To access this feature, contact your Zscaler Account team.
To create a scheduled backup configuration:
- Go to **Administration **> **Backup & Restore**.
- Click the **Backup Configuration **tab.
- Select the **Enable Scheduled Backups** option.
- Enter a name in the **Restore Point Prefix Name** field.
- In the **Schedule **section, do the following:
- **Frequency**: Select either **Weekly** or **Monthly**.
- **Date**: Select the date on which you want the restore point to be created. This field appears when the **Frequency** is selected as **Monthly**.
- **Day**: Select the day of the week when you want the restore point to be created. This field appears when the **Frequency** is selected as **Weekly**.
- **Restore Point Creation Time**: Select the time at which you want the restore point to be created.
- **Time Zone**: Select the time zone in which the scheduled backup configuration should be valid.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
![Screenshot of the Backup Configuration page.](/downloads/zia/authentication-administration/backup-restore/creating-scheduled-backup-configuration/ZIA-backup-configuration.png)