# Managing Outegrations
Source: https://help.zscaler.com/uvm/managing-outegrations
PDF: https://help.zscaler.com/pdf/com/en/1527726.pdf

After [creating an outegration](/uvm/creating-outegrations), you can manage and monitor it from the Outegrations page. This page provides a centralized view of all configured outegrations in your account.
Go to **Configure **> **Outegrations **to perform the following actions:
- [Edit Outegration Mapping](#outegration-edit-mapping)
- [Edit Outegration Details and Settings](#edit-outegration-settings)
- [Delete an Outegration](#outegration-delete)
- [Clone an Outegration](#outegration-clone)
- [Deactivate an Outegration](#outegration-deactivate)
- [See Activity Log](#outegration-activity-log)
[]You can edit an outegration's mapping as needed (e.g., if your external vendor schema changed).
When you open the Edit Mapping page, the system automatically retrieves the latest schema from the external vendor, if available. Any changes made to the vendor's schema are reflected on the mapping page. As a result, you might need to update the mapping to include newly added required fields.
To edit an outegration's mapping:
-
Hover over the outegration you want to edit, and click the **Edit Mapping **icon.
[See image.](#outegration-edit-mapping-icon)
The **Edit Mapping** page appears.
- Make the necessary changes and click **Save**.
[]**![mceclip0.png](/downloads/uvm/configure/outegrations/managing-outegrations/mceclip0.png)
**
[]You can edit an outegration to update its authentication, adjust the outegration visibility and behavior, or rename it for easier identification.
Edit an outegration's details or authentication cautiously to avoid connectivity disruption and potential data loss.
To edit an outegration:
-
Hover over the outegration you want to edit, and click the **Edit** icon.
[See image.](#outegration-edit-icon)
The **Edit Outegration** page appears.
- Make the necessary changes and click **Save**.
[]**![mceclip1.png](/downloads/uvm/configure/outegrations/managing-outegrations/mceclip1.png)
**
[]You can delete an outegration that is no longer in use (e.g., if your organization no longer works with the associated vendor). If your goal is to stop communication between the platform and the third-party vendor, consider deactivating the relevant outegration instead.
To delete a specific outegration:
-
Hover over the outegration you want to delete, and click the **Delete** icon.
The **Confirm Deletion** window appears.
- Click **Delete**.
To delete multiple outegrations:
- From the outegrations list, select the outegrations that you want to delete.
-
Click the **Delete** button at the top of the page.
The **Confirm Deletion** window appears.
- Click **Delete**.
[]You can clone an existing outegration to create a new one with similar configuration. This is useful when setting up multiple outegrations of the same type that share similar settings (e.g., creating separate Jira Issue Type outegrations for Bug, Feature, and Task).
To clone an outegration:
- Hover over the outegration you want to clone, and click the **Clone **icon.
[See image.](#outegration-clone-icon)
The setup page of the cloned outegration appears with the same name as the original outegration from which it was cloned.
-
Edit the cloned outegration as needed, including updating its name.
The entity type of the original outegration can't be changed when cloning an outegration.
- Click **Save**.
[]**![mceclip4.png](/downloads/uvm/configure/outegrations/managing-outegrations/mceclip4.png)
**
[]You can deactivate an outegration to halt the bidirectional data synchronization and communication between the platform and your third-party service or tool, while still keeping any setup configurations available for future use (e.g., if you're conducting a system upgrade and need to temporarily pause data syncing).
To deactivate an outegration:
- Hover over the outegration you want to deactivate, and click the **Edit** icon.
- In the **Connect** step, disable the **Active** toggle next to the outegration's Display Name.
- Click **Next**.
- Click **Map**.
- Click **Finish**.
The outegration is deactivated immediately. To reactivate it later, return to the **Edit** **Outegration **page and re-enable **Active**.
[]You can view the activity log for a specific connection and monitor updates on an outegration and its status. If a connection fails, you can view the reason it failed and fix the issue.
To view an outegration's activity log, hover over the outegration and click the **See activity log** icon.
[See image.](#outgeration-activity-log-icon)
To drill down into the details and view the connection's payload, open a specific activity log.
[]![mceclip2.png](/downloads/uvm/configure/outegrations/managing-outegrations/mceclip2.png)