# About Backup and Restore for Private Applications
Source: https://help.zscaler.com/unified/about-backup-and-restore-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1520721.pdf

This feature and its procedures are in limited availability. To learn more, contact Zscaler Support.
You can create a backup of application segments, policies, and configuration settings, and restore them using a backup. A backup represents the date and time when a backup was created and allows you to restore application segments, policies, and configurations saved at that time. Backups can be automated using schedules or created manually on demand in the Admin Portal.
When you restore application segments, policies, and configuration settings from a backup, it overwrites all your current application segments, policies, and configuration settings, including all the rules and their components. If your current configuration has a component that is not present in the backup, that component is removed when the backup is applied. Therefore, ensure that you review the policies and configurations saved in a backup before restoring them. To learn more, see [Viewing Restore Activities and Restore Reports](/unified/viewing-restore-activities-and-restore-reports).
Backup and Restore features provide the following benefits and enable you to:
- Create backups to secure your application segments, policies, and configuration settings, and restore them in the event of policy failure, misconfiguration, or undesired outcomes.
- Schedule automated backups to create backups periodically without manual intervention.
- Ensure compliance with your organization's Business Continuity Plans and Disaster Recovery Plans.
The service backs up the following policies and configuration settings:
- [Application Management](#applicationMgmt)
- [Certificate Management](#certificateMgmt)
- [Policy](#policy)
- [User Portals](#userPortals)
You can back up and restore policies and configuration settings in the following scenarios:
- You want to modify your existing configuration, but do not want to commit the change without first having a backup in case the new configuration does not function as intended.
- You want to schedule backups to ensure the creation of backups periodically without any manual intervention, which helps comply with Business Continuity Plans and Disaster Recovery Plans of your organization.
An organization can have up to 10 backups, including manual and scheduled backups. You can designate one of the backups as the golden backup that allows you to restore the corresponding policies and configurations at any point in time. The golden backup cannot be deleted.
If the number of backups reaches a limit of 10, you cannot add a new backup manually without deleting an existing one. However, during scheduled automatic backups, the oldest backup is removed to create the new one when the limit is exceeded. If the oldest backup is a golden backup, then the next oldest backup is deleted.
Backups expire after 10 days. The following icons are displayed next to the **Backup** **Name **depending on the expiration of the restore point:
- If the backup has expired, the **Restore **action is disabled.
- If the backup has less than 3 days before expiration, a yellow **Caution **icon (![zpa-yellow-caution-icon.png](/downloads/zpa/administration/backup-restore/about-backup-and-restore/zpa-yellow-caution-icon.png)
) is displayed.
About the Backup and Restore Page
The ability to create, restore, edit, or schedule a backup is not supported if your tenant has Privileged Remote Access (PRA). These actions appear grayed-out on this page. Contact Zscaler Support to disable PRA for your tenant.
On the Backup and Restore page (Administration > Backup & Restore > Private Applications), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables#filter).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- [Create a scheduled backup configuration](/unified/creating-scheduled-backup-configurations-private-applications).
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables).
- [Add a backup manually](/unified/adding-backups-manually-private-applications).
-
View a list of all backups that were configured for your organization. For each backup, you can see:
- **Backup Name**: The name of the backup. Click the backup name to open the **Restore Activities** window and view a list of restore activities applied to the selected backup by the admin, and view the restore reports for each individual backup. To learn more, see [Viewing Restore Activities and Restore Reports](/unified/viewing-restore-activities-and-restore-reports).
- **Created By**: The admin that created the backup.
- **Creation Date**: The date and time that the backup was created.
- **Expiration Date**: The expiration date for the backup.
- **Status**: The status of the backup. Statuses refresh automatically every minute.
- **Description**: The description of the backup, if available.
A backup with the **Flag** icon (![zpa-golden-restore-point-flag-icon.png](/downloads/zpa/administration/backup-restore/about-backup-and-restore/zpa-golden-restore-point-flag-icon.png)
) next to it represents a golden backup, which is the last known good backup of policies and configuration settings. There can be only one golden backup at any given point in time. If a golden backup has a failed status, then it should not be marked as a golden backup. If a golden backup has a failed status, Zscaler recommends that you delete the backup and then select a new backup with a completed status as a golden backup.
- [Edit a backup](/unified/editing-backups-private-applications).
-
[Restore stored policies and configurations from a backup.](/unified/restoring-policies-and-configurations-backup-private-applications)
You can restore policies and configurations from a backup a maximum of 10 times per day.
- [Delete a backup](/unified/deleting-backups-private-applications).
- [Modify the columns displayed in the table](/unified/using-tables).
- Display more rows or a different page of the table.
![Viewing the Backup and Restore page](/downloads/zpa/administration/backup-restore/about-backup-and-restore/zpa-backup-and-restore-page.png)
[]
- Application segments
- Browser Access
- Client Hostname Validation
- DNS Search Domains
- Segment groups
- Servers
- Server groups
The following features are unavailable for the backup and restore service:
- [AppProtection](/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-controls-profiles)
- Deception-enabled applications, segment groups, servers, server groups, and access policies.
- [Extranet application support](/unified/understanding-extranet-application-support)
- Internet & SaaS-referenced server groups. Any server groups referenced in Internet & SaaS are unavailable.
- [Privileged Remote Access (PRA)](/unified/policies/private-applications/access-control/clientless/privileged-remote-access-management)
- Zscaler-managed certificates and DNS. Browser Access applications, user portals, and PRA portals using these features are unavailable.
[]
- Browser Access certificates
[]
- Access policy
- Client forwarding policy
- Timeout policy
[]
- Portal Links
- User Portals