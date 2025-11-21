# Enabling Digital Experience Monitoring for a Group of Users
Source: https://help.zscaler.com/unified/enabling-digital-experience-monitoring-group-users
PDF: https://help.zscaler.com/pdf/com/en/1491116.pdf

You can use Zscaler Service Entitlement to select which users can enroll into Digital Experience Monitoring. To enable Digital Experience Monitoring for only a select group of users, you must deploy Zscaler Client Connector 2.2.1 or later.
If you’re using device groups, the user must belong to both the device group and user group to avoid disconnecting Private Applications services.
Enabling Digital Experience Monitoring at a Group Level
To enable Digital Experience Monitoring for a group of users:
- In the Admin Portal, go to **Administration > Entitlements > Digital Experience**.
- To enable Digital Experience Monitoring for only a group of users, ensure that **ZDX Enabled by Default** is disabled. If this setting is enabled, then Digital Experience Monitoring is available for all users and you cannot assign Digital Experience Monitoring to a group.
- Select a group of users from the drop-down menu and click **Done**. The default setting is **None**. This option means no groups have access to Digital Experience Monitoring. This allows users to keep their current settings, allowing you to choose when to configure it for them.
These groups are defined in the Admin Portal. If you do not see your groups, ensure that the directory groups were synced properly between Internet & SaaS and Zscaler Client Connector. To learn more, see [Syncing Directory Groups between the Internet & SaaS and Zscaler Client Connector](/unified/syncing-directory-groups-between-internet-saas-and-zscaler-client-connector).
- To enable Digital Experience Monitoring for device groups, select one or more groups from the **Device Groups** drop-down menu.
- Select **Logout Zscaler Client Connector when ZDX Entitlement is Enabled** to automatically log users out of Zscaler Client Connector when Digital Experience Monitoring is enabled for a device group. Users can then log in again to enable the Digital Experience Monitoring service. This applies to customers using Private Applications only or Private Applications and Zscaler Deception. When disabled, Zscaler Client Connector runs without the Digital Experience Monitoring service until the next Zscaler Client Connector login.
![Configure ZDX user groups for Zscaler Service Entitlement](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zdx-group-users/ZDX_Entitlement.png)
- Click **Save**.
This updates your users' devices the next time they connect. If they are already connected, the devices automatically update in 60 minutes. To manually update their devices, users can go into Zscaler Client Connector and click **Update Policy** from the **More** window. After manually refreshing, they must reauthenticate on the **Digital Experience** window.
Possible Configurations for Digital Experience Monitoring
The following table provides possible configurations for the Zscaler Service Entitlement feature and the resulting behavior of the Digital Experience Monitoring service:
| **Enabled by Default** | **Groups Specified** | **Behavior** |
| ---------------------- | -------------------- | ------------ |
| Enabled | N/A | Digital Experience Monitoring service is enabled for all users |
| Disabled | No | Digital Experience Monitoring service is not enabled for any users |
| Disabled | Yes | Digital Experience Monitoring service is enabled only for the specified group of users |