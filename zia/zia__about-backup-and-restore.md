# About Backup and Restore
Source: https://help.zscaler.com/zia/about-backup-and-restore
PDF: https://help.zscaler.com/pdf/com/en/1398956.pdf

[Watch a video backups and restore points.](https://fast.wistia.net/embed/iframe/vohznch7uo)
You can create a backup of policies and configuration settings and restore them using a restore point. A restore point represents the date and time when a backup was created and allows you to restore policies and configurations saved at that time. Backups can be automated using schedules or created manually on demand in the ZIA Admin Portal.
When you restore policies and configuration settings from a restore point, it overwrites all your current policies and configuration settings, including all the rules and their components (e.g., URL categories and time intervals). If your current configuration has a component that is not present in the restore point, that component is removed when the restore point is restored. Therefore, ensure that you review the policies and configurations saved in a restore point before restoring them. To learn more, see [Viewing or Restoring Policies and Configurations from a Restore Point](/zia/viewing-restoring-policies-configurations-from-restore-point).
Backup and Restore features provide the following benefits and enable you to:
- Create backups to secure your policies and configuration settings and restore them in the event of policy failure, misconfiguration, or undesired outcomes.
- Schedule automated backups to create backups periodically without manual intervention.
- Ensure compliance with your organization's Business Continuity Plans and Disaster Recovery Plans.
The policies that are included in the backup are listed as follows:
- [Rules and policies](#policies-rules)
You can back up and restore policies and configuration settings in the following scenarios:
- You want to modify your existing configuration, but do not want to commit the change without first having a backup in case the new configuration does not function as intended.
- You want a strict policy with very little tolerance for risk that you can revert to in case of a virus outbreak or if your security infrastructure suddenly changes.
- You want to schedule backups to ensure the creation of restore points periodically without any manual intervention, which helps comply with Business Continuity Plans and Disaster Recovery Plans of your organization.
An organization can have up to 12 restore points, including manual and scheduled backups. You can designate one of the restore points as the Golden Restore Point that exists indefinitely and allows you to restore the corresponding policies and configurations at any point in time. The golden restore point cannot be deleted.
- If the number of restore points reaches a limit of 12, you cannot add a new restore point manually without deleting an existing one. However, during scheduled automatic backup, the oldest restore point is removed to create the new one when the limit is exceeded. If the oldest restore point is a golden restore point, then the next oldest restore point is removed.
- For organizations with [Exact Data Match (EDM)](/zia/about-exact-data-match) or [Indexed Document Match (IDM)](/zia/about-indexed-document-match) enabled, the Backup and Restore feature doesn’t restore the [DLP](/zia/about-data-loss-prevention) policies.
About the Backup & Restore Page
[]On the Backup & Restore page (Administration > Backup & Restore), you can do the following:
- [Add a restore point manually](/zia/adding-restore-points-manually).
- View a list of all restore points that were configured for your organization. For each restore point, you can view and sort:
- **Restore Point Name**: The name of the restore point.
- **Description**: The description of the restore point, if available.
- **Created By**: The admin that created the restore point.
- **Created On**: The date and time the restore point was created.
A restore point with the **Flag** icon alongside it represents a Golden Restore Point, which is the last known good backup of policies and configuration settings. There can be only one golden restore point at any given point in time.
- Search for an existing restore point.
- [View or restore stored policies and configurations from a restore point](/zia/viewing-restoring-policies-configurations-from-restore-point).
- [Modify the display of columns in the table](/zia/how-do-i-use-tables-admin-portal).
- Click the **Backup Configuration** tab to [configure a backup schedule](/zia/creating-scheduled-backup-configuration).
![Backup & Restore page within the Admin Portal](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/about-policies/about-backup-and-restore/ZIA-backup-and-restore.png)
- [][Advanced Threat Protection policies](/zia/configuring-advanced-threat-protection-policy)
- [Bandwidth Control policies](/zia/about-bandwidth-control)
- [Browser Control policies](/zia/configuring-browser-control-policy)
- [Cloud App Control policies](/zia/about-cloud-app-control)
- [Data Loss Prevention (DLP) policies](/zia/about-data-loss-prevention)
- [DNS Control policies](/zia/about-dns-control)
- [File Type Control policies](/zia/about-file-type-control)
- [Firewall Control policies](/zia/understanding-firewall-capabilities)
- [Forwarding Control policies](/zia/about-forwarding-policies)
- [FTP Control policies](/zia/about-ftp-control)
- [IPS Control policies](/zia/about-ips-control)
- [Malware Protection policies](/zia/configuring-malware-protection-policy)
- [Mobile App Store Control policies](/zia/about-mobile-app-store-control)
- [Mobile Malware Protection policies](/zia/understanding-mobile-malware-protection)
- [SaaS Security API DLP policies](/zia/about-saas-security-api-dlp)
- [SaaS Security API Malware Detection policies](/zia/about-saas-security-api-malware-detection)
- [Sandbox policies](/zia/about-sandbox)
- [SSL Inspection policies](/zia/about-ssl-inspection)
- [URL Filtering policies](/zia/about-url-filtering)