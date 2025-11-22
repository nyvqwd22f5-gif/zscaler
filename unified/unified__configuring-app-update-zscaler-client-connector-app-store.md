# Configuring an App Update in the Zscaler Client Connector App Store
Source: https://help.zscaler.com/unified/configuring-app-update-zscaler-client-connector-app-store
PDF: https://help.zscaler.com/pdf/com/en/1495491.pdf

Zscaler regularly releases new versions of Zscaler Client Connector. As an admin, you can decide what app version is used by your organization by configuring a Zscaler Client Connector app update. You can configure an app update to control which version (if any) is available when the app is automatically updated or when end users manually update the app.
You can configure an app update only for Windows, macOS, and Linux. Updates for iOS and Android are controlled by the App Store and Google Play or your MDM solution.
After your users enroll with Zscaler Client Connector, the app automatically checks every two hours to see if an updated version is available and automatically updates the app if one is available. Alternatively, the user can click **Update App** in the **More** window to check for and install any available updates.
[See image](#ZCC-App)
You can configure an app update for selected groups that's rolled out at the same time, or configure a phased rollout that gradually upgrades devices for selected groups.
With a phased rollout, admins can test a new build before deploying an update to all users. The admin can pause a phased rollout to address issues or modify the version or schedule. View the phased rollout progress on the Client Connector App Store page.
[See image](#Client-Connector-App-Store-Page)
[][]![Client Connector App Store Page Slow Rollout](/downloads/client-connector-app-store-phased-rollout.png)
The following app update options are available:
- [Configure an App Update](#configure-auto-update)
- [Edit an App Update](#edit-rollout)
- [No App Update](#no-update)
- [Edit the Default Policy](#edit-grp-policy)
Before you can configure an app update for a release, you must first enable a build.
- []To enable builds on the New Releases tab:
- In the Admin Portal, go to **Infrastructure > Common Resources > Client Connector Deployment > Platform Releases**.
- Click the **New Releases** tab and select a platform.
- Click **Enable Build **for the Zscaler Client Connector versions you want to configure for an app update.
- Click **Save**.
[See image](#new-releases)
Confirm the versions you enable on the **Registered Devices** tab, not the **New Releases** tab.
- To configure an app update for a release, click **Add App Store Group Policy **on the **Update Settings** tab.
[See image](#add-config)
-
In the **Add App Store Group Policy** window, select from the following settings:
- From the** Groups** drop-down menu, select the groups to which you want to apply this configuration.
- [Groups are synced](/unified/syncing-directory-groups-between-internet-saas-and-zscaler-client-connector) from Internet & SaaS.
- If a group is already configured for an app update, that group cannot be added to subsequent app updates until the pending app update is complete.
- In the **Windows - Version to Install**, **macOS - Version to Install**, and **Linux - Version to Install** drop-down menus, select the Zscaler Client Connector version you want automatically updated on your users' devices.
- When multiple versions are configured for the same OS, and a user belongs to more than one group in those configurations, the latest version is updated for that user.
- If any devices are already upgraded to a later version, you cannot roll out an update for an earlier version.
- For Zscaler Client Connector version 3.7 and later for Windows, enable or disable **Use 64-Bit Installer for Windows **to install the 64-bit build on devices.
- (Optional) Click in the **Apply From Timestamp (in UTC)** field and select a date and time from the calendar to define a time and date for your auto-update to start. If this field is left blank, the app automatically checks for a new update during the next cycle, which is every two hours, and updates automatically.
-
**Roll Out Type**: Select one of the following methods to deploy an app update:
- **Phased Rollout**: Enable this option to deploy the selected Zscaler Client Connector versions to the selected groups in a [gradual rollout.](#table) The rollout process begins according to the scheduled date and is completed within 7 days.
- **Mass Rollout**: Enable this option to deploy the selected Zscaler Client Connector versions to the selected groups at the same time.
To pause a phased rollout, click the **Pause **(![Pause-Client-Connector.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-app-update-zscaler-client-connector-app-store-doc-45501-doc-49543/Pause-Client-Connector.png)
)** **icon. To resume the rollout, click the **Play** (![Play-Client-Connector.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-app-update-zscaler-client-connector-app-store-doc-45501-doc-49543/Play-Client-Connector.png)
) icon. The phased rollout resumes from the point where you paused it.
- Click **Save**.
[See image](#add-config2)
- In the **Group Based Version Rollout - Confirmation** window, click **Proceed**.
[]
| **Day** | **Percentage of Devices Upgraded** |
| ------- | ---------------------------------- |
| 1 | 1 |
| 2 | 2 |
| 3 | 5 |
| 4 | 10 |
| 5 | 20 |
| 6 | 50 |
| 7 | 100 |
[]You can edit an app update, including a phased rollout that's in progress.
- Edit a Zscaler Client Connector version update:
- On the Client Connector App Store page, click the **Edit **icon (![pencil-icon.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-app-update-zscaler-client-connector-app-store-doc-45501-doc-49543/pencil-icon.png)
) for the rollout you want to edit.
- Make the desired changes in the **Edit App Store Group Policy **window.
- Click **Save**.
- Edit a phased rollout: You can pause a phased rollout to modify the configuration and then resume the phased rollout. The phased rollout resets to day one after you resume it.
- On the Client Connector App Store** **page, click the **Pause **icon (![Pause-Client-Connector.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-app-update-zscaler-client-connector-app-store-doc-45501-doc-49543/Pause-Client-Connector.png)
) for the phased rollout you want to modify.
- In the **Pause Rollout** window, click **OK**.
- Click the **Edit **icon (![pencil-icon.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-app-update-zscaler-client-connector-app-store-doc-45501-doc-49543/pencil-icon.png)
).
- Make the desired changes in the **Edit App Store Group Policy** window.
- Click **Save**.
- Click **Proceed **in the **Confirm **window to restart the phased rollout.
- Click **Proceed** in the** Group Based Version Rollout - Confirmation** window.
[]When you disable a Zscaler Client Connector update, Zscaler Client Connector never automatically updates on your users' devices. Your organization takes full responsibility for updating the app using its own mechanism (for example, using a GPO policy to do a fresh install of a desired version).
To disable the Zscaler Client Connector app update option:
- In the Admin Portal, go to **Infrastructure > Common Resources > Client Connector Deployment > Platform Releases**. Make sure you're on the **Update Settings** tab.
- Click **Add App Store Group Policy**.
[See image](#disable)
-
Select from the following settings in the **Add App Store Group Policy** window:
- From the** Groups** drop-down menu, select the groups to which you want to apply this configuration.
- [Groups are synced](/unified/syncing-directory-groups-between-internet-saas-and-zscaler-client-connector) from Internet & SaaS.
- If a group is already configured for an app update, that group cannot be added to subsequent app updates until the pending app update is complete.
- In the **Windows - Version to Install**, **macOS - Version to Install**, and **Linux - Version to Install** drop-down menus, select **Disable**.
- Click **Save**.
[See image](#add-config3)
- In the **Group Based Version Rollout - Confirmation** window, click **Proceed**.
[]You can edit the default app store group policy, which allows you to specify a Zscaler Client Connector app update option per OS. The default app store group policy applies to all groups that aren’t explicitly specified in your group policies.
Edit the default app store group policy:
- In the Admin Portal, go to **Infrastructure > Common Resources > Client Connector Deployment > Platform Releases**. Make sure you are on the **Update Settings** tab.
- Locate the group policy named **ALL**, and then click the **Edit** **(**![pencil-icon.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-app-update-zscaler-client-connector-app-store-doc-45501-doc-49543/pencil-icon.png)
) icon.
[See image](#default-policy)
- In the **Windows - Version to Install**, **macOS - Version to Install**, and **Linux - Version to Install **drop-down menus, select one of the following options:
- **Latest**: Zscaler Client Connector automatically updates to the latest version.
- **Disable**: Zscaler Client Connector never updates on its own. Your organization is responsible for updating the app.
- **Version to Install**: The version to which you want Zscaler Client Connector to automatically update.
- For Zscaler Client Connector version 3.7 and later for Windows, enable **Use 64-Bit Installer for Windows** to install the 64-bit build on devices.
- (Optional) Click in the** Apply From Timestamp (in UTC)** field and select a date and time from the calendar to define a time and date for your auto-update to start. If this field is left blank, the app automatically checks for a new update during the next cycle, which is every two hours, and updates automatically.
- Click **Save**.
[See image](#add-config4)
- In the **Group Based Version Rollout - Confirmation** window, click **Proceed**.
[]![Zscaler Client Connector app](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-update-settings-zscaler-client-connector-combine-sections/ZCC-App.png)
[]![Client Connector App Store page](/downloads/client-connector-app-store-edit-default-policy.png)
[]![Client Connector App Store Update Settings tab](/downloads/client-connector-app-store-add-group-policy.png)
[]![Client Connector App Store page](/downloads/client-connector-app-store-add-group-policy.png)
[]![Enable Build in the Client Connector App Store](/downloads/client-connector-app-store-enable-build.png)
[]![Add an app update in the App Store](/downloads/client-connector-app-store-add-group-policy-window.png)
[]![Add an app update in the App Store](/downloads/client-connector-app-store-add-group-policy-no-update.png)
[]![Edit an app update in the App Store](/downloads/client-connector-app-store-edit-default-policy-window.png)