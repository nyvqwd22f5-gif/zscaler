# Saving and Activating Changes
Source: https://help.zscaler.com/cloud-branch-connector/saving-and-activating-changes
PDF: https://help.zscaler.com/pdf/com/en/1420411.pdf

Propagating configuration changes throughout the Zscaler Cloud & Branch Connector Admin Portal is a two-step process:
- Make your configuration changes (e.g., adding, editing, or deleting policy rules), and then select **Save **to store the changes on the local database.
- Queue the changes for activation. Activating the changes effectively pushes the configuration changes to the Central Authority (CA), which serves as the central repository for policies and configuration settings.
Activating Changes
Ensure you're making changes to the portal in a single browser session. If you make changes across multiple browser sessions using the same admin account, activation errors can occur.
To activate changes in the Cloud & Branch Connector Admin Portal:
- Hover over **Activation** on the left-side navigation.
[See image.](#seeimage1)
- Select **Activate**.
[See image.](#seeimage2)
If there are no other admins editing, the service sends the updates to the CA immediately. If there are multiple admins editing, the service pushes the changes to the CA after all admins activate their changes.
Navigating the Activation Menu
The Activation menu displays:
- **My Activation Status**: Displays your activation status.
- **No Activations Pending**: You haven't saved or activated your changes.
- **Editing**: You saved your changes but haven't activated them.
- **Activation Queued**: Your activated changes are pending and haven't been pushed to the CA. This status displays when you activate your changes, and there are other admins still editing. The service pushes the changes to the CA after all admins activate their changes.
- **Currently Editing**: Lists the usernames of admins who saved their changes but haven't activated them.
- **Queued Activations**: Lists the usernames of admins with pending activations. When an admin activates their changes and there are other admins still editing, the changes are queued for activation, and the admin's username is moved to this list. A queued activation cannot be canceled.
[See image.](#seeimage3)
The service automatically activates an admin's saved changes if the admin:
- Is inactive for 30 minutes
- Logs out
- Closes the browser
[]![Activation menu in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/getting-started/admin-portal/saving-and-activating-changes-cloud-connector-admin-portal/Saving%20and%20Activating%201.png)
[] ![Activate button in the Zscaler Cloud & Branch Connector Admin Portal Activation Menu ](/downloads/cloud-connector/getting-started/admin-portal/saving-and-activating-changes-cloud-connector-admin-portal/Saving%20and%20Activating%202.png)
[] ![Activation Menu in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/getting-started/admin-portal/saving-and-activating-changes-cloud-connector-admin-portal/Saving%20and%20Activating%203.png)