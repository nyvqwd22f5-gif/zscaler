# Viewing Restore Activities and Restore Reports
Source: https://help.zscaler.com/zpa/viewing-restore-activities-and-restore-reports
PDF: https://help.zscaler.com/pdf/com/en/1485871.pdf

After a [backup](/zpa/about-backup-and-restore) is created [manually](/zpa/adding-backups-manually) or [automatically](/zpa/creating-scheduled-backup-configurations), you can view a list of restore activities, or you can view the post-restore reports for the particular backup.
Accessing a List of Restore Activities for a Backup
To access a list of restore activities for a particular backup:
- Go to **Configuration & Control **> **Administration Control** > **Backup and Restore**.
-
In the table, locate the backup you want to view the restore activities and restore reports for, and click on the individual backup name in the **Backup Name** column.
The **Restore Activities **drawer appears.
[See image.](#restoreActivities)
- In the **Restore Activities** drawer, you can:
- Click the **Restore **icon (![zpa-restore-icon.png](/downloads/zpa/administration/backup-restore/viewing-backups-and-restore-reports/zpa-restore-icon.png)
) to open the **View Report and Restore** drawer. In the **View Report and Restore** drawer, you can [view the inconsistency reports before restoring a backup](/zpa/restoring-policies-and-configurations-backup).
- View the list of restore activities. Filter the data in the table with your selections, and then click **Apply**. For each restore activity, you can see:
- **Admin ID**: The admin ID of the admin who restored the backup.
- **Initiated At**: The time when the backup is restored.
- **Status**: The status of the restore (**Completed**, **Failure**, **In Progress**).
- Click the **View Restore Report** icon (![zpa-view-restore-report-icon.png](/downloads/zpa/administration/backup-restore/viewing-backups-and-restore-reports/zpa-view-restore-report-icon.png)
) to [view the post-restore reports of the selected backup](#ViewPostRestoreReports). The **Restore Report** drawer appears.
[]![Viewing the Restore Activities drawer ](/downloads/zpa/administration/backup-restore/viewing-restore-activities-and-restore-reports/zpa-backup-restore-activities.png)
[]Viewing the Post-Restore Reports for a Backup
In the **Restore Report** drawer, you can view the post-restore report view of the backup if the configurations were modified. You can click **Collapse All** to collapse all configurations, click on an individual configuration to see more information, or click the **Download **icon to download the full report as a CSV file. In the **Restore Report** table, you can see:
- **Configuration**: The list of configurations for the backup. Any unchanged configurations are not listed in the table.
- **Status**: The status of the configurations after the backup is restored.
[See image.](#RestoreReports)
[]![Viewing the Restore Reports drawer ](/downloads/zpa/administration/backup-restore/viewing-restore-activities-and-restore-reports/zpa-backup-post-restore-reports-drawer.png)