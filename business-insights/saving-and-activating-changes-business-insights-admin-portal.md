# Saving and Activating Changes in the Business Insights Admin Portal
Source: https://help.zscaler.com/business-insights/saving-and-activating-changes-business-insights-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1473096.pdf

Propagating configuration changes throughout the Zscaler cloud is a two-step process:
- Make your configuration changes (e.g., adding, editing, or deleting admins), and save the changes on the local database.
When multiple users edit a configuration setting concurrently, only the last saved configuration persists.
- Queue the changes for activation. Activating the changes effectively pushes the configuration changes to the [Central Authority](/zia/understanding-zscaler-cloud-architecture) (CA) which, among other things, serves as the central repository for policies and configuration settings. The Public Service Edges retrieve the policies from the CA and apply them to your organization's internet traffic.
Activating Changes
Ensure you're making changes to the Business Insights Admin Portal in a single browser session. If you make changes across multiple browser sessions using the same admin account, activation errors can occur.
After you activate your configuration updates, you cannot undo them. However, you can delete or modify the undesired configuration and activate it again.
To activate changes in the Business Insights Admin Portal
- Hover over the **Activation** menu in the left-side navigation.
- Click **Activate**.
If there are no other admins editing, the Zscaler service sends the updates to the CA immediately. If there are multiple admins editing, the service pushes the changes to the CA after all admins activate their changes.
About the Activation Menu
The **Activation **menu displays your activation status and the status of other admins who are editing as follows:
- **My Activation Status**: Displays your activation status as:
- **No Activations Pending**: You haven't saved or activated your changes.
- **Editing**: You saved your changes but haven't activated them.
- **Activation Queued**: Your activated changes are pending and haven't been pushed to the CA. This status displays when you activate your changes, and there are other admins still editing. The Zscaler service pushes the changes to the CA after all admins activate their changes.
- **Currently Editing**: Lists the usernames of admins who saved their changes but haven't activated them.
- **Queued Activations**: Lists the usernames of admins with pending activations. When an admin activates their changes and there are other admins still editing, the changes are queued for activation, and the admin's username is moved to this list. A queued activation cannot be canceled.
- **Force Activate**: Immediately pushes all saved changes to the CA. Only super admins can Force Activate changes.
The **Activation **menu also displays the number of admins who are currently editing.
The Zscaler service automatically activates an admin's saved changes if the admin is inactive for 30 minutes or logs out of the portal.