# Saving and Activating Changes in the Admin Portal
Source: https://help.zscaler.com/unified/saving-and-activating-changes-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1498291.pdf

When making configuration changes in the Admin Portal that must be propagated across the Zscaler cloud (e.g., adding, deleting, or editing policy rules), you must activate the changes before they can take effect.
Propagating configuration changes is a two-step process:
- Make your configuration changes (e.g., adding, editing, or deleting policy rules) and then click **Save **to store the changes in the local database.
Saving your changes is important in the event that multiple users are editing a configuration setting concurrently, because only the last saved configuration persists. For example, assume User 1 adds Facebook to the list of cloud applications blocked by a social networking policy. Another user, User 2, starts editing the same networking policy simultaneously before User 1 has saved their changes and adds Twitter to the cloud applications list. Now, if User 1 saves their changes followed by User 2, the changes made by User 1 are overwritten with changes made by User 2, adding only Twitter to the cloud applications list.
- Queue the changes for activation.
Activating the changes pushes the configuration changes to the Central Authority (CA), which among other things, serves as the central repository for policies and configuration settings.
Activating Changes
Ensure you're making changes to the Admin Portal in a single browser session. If you make changes across multiple browser sessions using the same admin account, activation errors might occur.
To activate queued configuration changes in the Admin Portal:
- On the top navigation menu, click the **Activation** icon on the right.
[See image.](#seeimage1)
- Click **Activate**.
[See image.](#seeimage2)
After you activate your configuration updates, you cannot undo the Activate action. However, you can delete or modify the undesired configuration and activate it again.
If there are no other admins editing, the service sends the updates to the CA immediately. If there are multiple admins editing, the service pushes the changes to the CA after all admins activate their changes.
About the Activation Menu
The Activation menu displays your activation status. It also displays the number and status of other admins who are currently editing.
[See image.](#seeimage3)
- **My Activation Status**: Displays your activation status.
- **No pending changes to activate**: You haven't saved or activated your changes.
- **Editing**: You saved your changes but haven't activated them.
- **Activation queued**: Your activated changes are pending and haven't been pushed to the CA. This status displays when you activate your changes, and there are other admins still editing. The service pushes the changes to the CA after all admins activate their changes.
- **Currently Editing**: Lists the usernames of admins who saved their changes but haven't activated them.
- **Queued Activations**: Lists the usernames of admins with pending activations. When an admin activates their changes and there are other admins still editing, the changes are queued for activation, and the admin's username is moved to this list. A queued activation cannot be canceled.
- **Force Activate**: Immediately pushes all saved changes to the CA. Only [super admins](/unified/adding-internet-saas-super-admins) and full admins can **Force Activate** changes.
The service automatically activates an admin's saved changes if the admin:
- is inactive for 30 minutes (duration can be configured in the [Advanced Settings](/unified/configuring-advanced-settings))
- logs out
[][![Activation icon](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/saving-and-activating-changes-admin-portal/activate-icon.png)
](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/saving-and-activating-changes-admin-portal/activate-icon.png)
[][![Activation menu](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/saving-and-activating-changes-admin-portal/activation-menu-activate.png)
](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/saving-and-activating-changes-admin-portal/activation-menu-activate.png)
[][![Activation menu](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/saving-and-activating-changes-admin-portal/activation-menu.png)
](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/saving-and-activating-changes-admin-portal/activation-menu.png)