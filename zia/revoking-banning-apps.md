# Revoking and Banning Apps
Source: https://help.zscaler.com/zia/revoking-banning-apps
PDF: https://help.zscaler.com/pdf/com/en/1450431.pdf

Depending on the platform (i.e., Google or Microsoft), you can revoke or ban an app for all users in your organization:
- Revoke (supported by Google): Removes all permissions granted for the app. This does *not* prevent users from installing the app and giving consent in the future. You can use the app [classification](/zia/classifying-apps) and [policies](/zia/3rd-party-app-governance-policies) to prevent users from reinstalling the app.
- Ban (supported by Microsoft): Blocks access to the app, preventing users from using the app in the future.
You can also revoke an app for individual users. Banning an app for individual users is not currently supported.
- [Revoke or Ban an App for All Users](#revoke-app-all-users)
- [Revoke an App for Individual Users](#revoke-app-individual-user)
After you ban or revoke an application, its status changes in 3rd-Party App Governance. To learn more about application status, see [App Panel Header](/zia/about-app-panel#app-panel-header).
[]You can revoke or ban an app for all users in the App Inventory or the App Panel header.
- [Revoke or Ban an App in the App Inventory](#revoke-ban-app-inventory)
- [Revoke or Ban an App in the App Panel Header](#revoke-ban-app-panel)
[]To revoke or ban an app:
- In the left-side navigation, go to **Inventory**.
- In the App Inventory, go to the** Automated Workflow** column and the app that you want to revoke or ban for all users.
- In the drop-down menu, click **Revoked/Banned**.
[See image.](#apptotal-inventory-revoke-ban)
A confirmation window appears displaying the summary of the app that you want to revoke or ban.
[See image.](#apptotal-inventory-revoke-ban-summary)
- Select the** Send email to notify users **checkbox to notify users that the app has been revoked or banned.
- Select the email address from which you want to send the email. You can view the default email to be sent, but you cannot edit it.
You cannot send emails when revoking domain-wide applications that are authorized at the organization level for all users.
- (Optional) If the app has a risk finding, mark it appropriately (e.g., **Dismissed**).
- Click **Revoke/Ban**.
You can update the Automated Workflow of multiple apps simultaneously. To learn more, see [Taking Bulk Actions on Apps](/zia/taking-bulk-actions-on-apps).
[]To revoke or ban an app:
- Select the app that you want to revoke or ban for all users.
The App Panel opens.
- In the **Automated Workflow **drop-down menu, located in the App Panel header, click **Revoked/Banned**.
[See image.](#apptotal-app-panel-revoke-ban)
A confirmation window appears displaying the summary of the app that you want to revoke or ban.
- Select the** Send email to notify users **checkbox to notify users that the app has been revoked or banned.
- Select the email address from which you want to send the email. You can view the default email to be sent, but you cannot edit it.
You cannot send emails when revoking domain-wide applications that are authorized at the organization level for all users.
- (Optional) If the app has a risk finding, mark it appropriately (e.g., **Dismissed**).
- Click **Revoke/Ban**.
[]You can revoke an app for individual users on the Access tab in the App Panel or in the User Panel.
From the Access tab in the App Panel:
- Select the app that you want to revoke for a user.
The App Panel opens.
- Click the **Access** tab.
[See image.](#app-panel-access-tab)
- Under **Authorized User Accounts**, click the **Column Menu** icon next to the user, then select **Revoke**.
[See image.](#apptotal-revoke-access-panel)
From the Access tab in the User Panel:
- Select the user.
The User Panel opens.
- On the **Access** tab, click the **Column Menu** icon next to the app, then select **Revoke**.
[See image.](#apptotal-revoke-user-panel)
[]![Automated Workflow menu ](/downloads/zia/policies/data-loss-prevention/3rd-party-app-governance/using-3rd-party-app-governance/revoking-banning-apps/Automated_Workflow_Inventory.png)
[]![Automated Workflow menu in the App Panel header](/downloads/zia/policies/data-loss-prevention/3rd-party-app-governance/using-3rd-party-app-governance/revoking-banning-apps/Automated_Workflow_AppPanel.png)
[]![Revoke / Ban app summary in the App Inventory](/downloads/tech-pubs-drafts/zia-draft-articles/revoking-and-banning-apps-draft-doc-56952/RevokeBan_Confirmation_0.png)
[]![Screenshot of the Access tab in the App Panel header](/downloads/zia/apptotal/how/general/revoke-ban-app/app_panel_access_tab.png)
[]![Screenshot of revoking an individual user's access to an app](/downloads/zia/apptotal/how/general/revoke-ban-app/apptotal_app_panel_access_revoke.png)
[]![Screenshot of revoking an individual user's access to an app](/downloads/zia/apptotal/how/general/revoke-ban-app/apptotal_user_panel_access_revoke.png)