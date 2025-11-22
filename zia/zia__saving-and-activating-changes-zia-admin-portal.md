# Saving and Activating Changes in the ZIA Admin Portal
Source: https://help.zscaler.com/zia/saving-and-activating-changes-zia-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1399776.pdf

Propagating configuration changes throughout the Zscaler cloud is a two-step process:
- Make your configuration changes (e.g., adding, editing, or deleting policy rules), and then click **Save **to store the changes on the local database.
When multiple users edit a configuration setting concurrently, only the last saved configuration persists. This happens when multiple users start editing the same configuration setting before one of them has saved their changes. For example, assume User 1 adds Facebook to the list of cloud applications blocked by a social networking policy. Another user, User 2, starts editing the same networking policy simultaneously before User 1 has saved their changes and adds Twitter to the cloud applications list. Now, if User 1 saves their changes followed by User 2, the changes made by User 1 are overwritten with changes made by User 2, adding only Twitter to the cloud applications list.
- Queue the changes for activation. Activating the changes effectively pushes the configuration changes to the Central Authority (CA), which among other things, serves as the central repository for policies and configuration settings. The ZIA Public Service Edges retrieve the policies from the CA and apply them to your organization's internet traffic. Because all policies are centrally stored on the CA, the latest policies are always applied, no matter to which ZIA Public Service Edge your users connect.
Activating Changes
Ensure you're making changes to the ZIA Admin Portal in a single browser session. If you make changes across multiple browser sessions using the same admin account, activation errors might occur.
Once you activate your configuration updates, you cannot undo the Activate action. However, you can delete or modify the undesired configuration and activate it again.
To activate changes in the ZIA Admin Portal:
- Hover over the **Activation** menu near the bottom left.
[See image.](#seeimage1)
- Click **Activate**.
[See image.](#seeimage2)
If there are no other admins editing, the service sends the updates to the CA immediately. If there are multiple admins editing, the service pushes the changes to the CA after all admins activate their changes.
About the Activation Menu
The Activation menu displays your activation status and the status of other admins who are editing.
[See image.](#seeimage3)
- **My Activation Status**: Displays your activation status.
- **No Activations Pending**: You haven't saved or activated your changes.
- **Editing**: You saved your changes but haven't activated them.
- **Activation Queued**: Your activated changes are pending and haven't been pushed to the CA. This status displays when you activate your changes, and there are other admins still editing. The service pushes the changes to the CA after all admins activate their changes.
- **Currently Editing**: Lists the usernames of admins who saved their changes but haven't activated them.
- **Queued Activations**: Lists the usernames of admins with pending activations. When an admin activates their changes and there are other admins still editing, the changes are queued for activation, and the admin's username is moved to this list. A queued activation cannot be canceled.
If a ZDX admin changes their password in the ZDX Admin Portal, any ZIA admin still making changes in the ZIA Admin Portal will see the ZDX admin's queued activation.
- **Force Activate**: Immediately pushes all saved changes to the CA. Only [super admins](/zia/what-super-admin-role) can **Force Activate** changes.
The Activation menu displays the number of admins who are currently editing.
[See image.](#seeimage4)
The service automatically activates an admin's saved changes if the admin:
- is inactive for 30 minutes (duration can be configured in the [Advanced Settings](/zia/configuring-advanced-settings#session-timeout))
- logs out
[]![Screenshot of ZIA Admin Portal Activation menu](/downloads/zia/getting-started/about-admin-portal/saving-and-activating-changes-admin-portal/zia-activation-menu.png)
[]![Screenshot of ZIA Admin Portal Activate button](/downloads/zia/getting-started/about-admin-portal/saving-and-activating-changes-admin-portal/zia-activate-button.png)
[]![Screenshot of the Activation menu fields](/downloads/zia/getting-started/about-admin-portal/saving-and-activating-changes-admin-portal/zia-activation-menu-fields.png)
[]![Screenshot of the Activation menu notification number](/downloads/zia/getting-started/about-admin-portal/saving-and-activating-changes-admin-portal/zia-activation-menu-number.png)