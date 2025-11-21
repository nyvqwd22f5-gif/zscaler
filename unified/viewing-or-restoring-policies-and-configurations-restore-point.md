# Viewing or Restoring Policies and Configurations from a Restore Point
Source: https://help.zscaler.com/unified/viewing-or-restoring-policies-and-configurations-restore-point
PDF: https://help.zscaler.com/pdf/com/en/1495166.pdf

When you restore policies and configuration settings from a [restore point](/unified/about-backup-and-restore), it overwrites all your current policies and configuration settings, including all the rules and their components, such as URL categories and time intervals. If your current configuration has a component that is not in the restore point, such as a URL category, that component is removed when the restore point is restored. Therefore, you might want to review the policies in the restore point before restoring it.
This article covers the following topics:
- [Viewing stored policies](#view-policies-configuration)
- [Verifying and restoring policies and configuration from a restore point](#restore-policies-configuration)
[]To view policies in a restore point:
- Go to** Administration **>** Backup & Restore > Internet & SaaS Applications**.
-
Locate the **Restore Point Name** within the table and click the **Edit **icon.
The **Edit Restore Point **window appears.
- In the **Edit Restore Point **window, click the **View Stored Policy **button to see the stored policies. On the **Stored Policies **tab:
- Select any of the stored policies listed by type (e.g., Sandbox, Firewall Control, DLP, etc.) to see their rules.
- Click **Expand All **to** **expand all policies and see the rules under the respective policy. You can also click the **View **icon to see the rule's configuration.
- Click **Collapse All **to collapse all the expanded policies.
- Click **Back **to go back to the **Backup & Restore** page.
All the stored policies that appear here are read-only.
[]If the restore point was created before some of the additional features were introduced, then that legacy restore point can only be used to restore the policies and configurations that have been persisted in it. Applying a legacy restore point does not override policies and configurations that were not supported in the platform version at the time of the restore point creation.
To verify and restore policies and configurations from a restore point:
- Go to** Administration **>** Backup & Restore > Internet & SaaS Applications**.
-
Locate the **Restore Point Name** within the table and click the **Edit **icon.
The **Edit Restore Point **window appears.
-
In the **Edit Restore Point **window, click the **Verify and Restore **button to** **restore the policies and configurations from the restore point.
This action verifies certain conditions (e.g., ensuring that all provisioned static IP addresses in the restore point are still associated with the current tenant, ensuring that the expiration timestamp for all certificates persisted in the restore point, etc.) before applying the restore point.