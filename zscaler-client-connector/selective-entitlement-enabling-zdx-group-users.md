# Enabling ZDX for a Group of Users
Source: https://help.zscaler.com/zscaler-client-connector/selective-entitlement-enabling-zdx-group-users
PDF: https://help.zscaler.com/pdf/com/en/1355776.pdf

You can use Zscaler Service Entitlement to select which users can enroll into ZDX. To enable ZDX for only a select group of users, you must deploy Zscaler Client Connector 2.2.1 or later.
If you’re using device groups, the user must belong to both the device group and user group to avoid disconnecting ZPA services.
Enabling ZDX at a Group Level
To enable ZDX for a group of users:
- In the Zscaler Client Connector Portal, go to **Administration**.
- From the left menu, select **Zscaler Service Entitlement**.
- Click the **Zscaler Digital Experience **tab.
- To enable ZDX for only a group of users, ensure that **ZDX Enabled by Default** is disabled. If this setting is enabled, then ZDX is available for all users and you cannot assign ZDX to a group.
- Select a group of users from the drop-down menu and click **Done**. The default setting is **None**. This option means no groups have access to ZDX. This allows users to keep their current settings, allowing you to choose when to configure it for them.
These groups are defined in the ZIA Admin Portal. If you do not see your groups, ensure that groups were synced to the Zscaler Client Connector Portal. To learn more, see [Syncing Directory Groups between the ZIA Admin Portal and App Portal](/zscaler-client-connector/syncing-directory-groups-between-zscaler-admin-portal-and-app-portal).
- To enable ZDX for [device groups](/zscaler-client-connector/about-device-groups-0), select one or more groups from the **Device Groups** drop-down menu.
- Select **Logout Zscaler Client Connector when ZDX Entitlement is Enabled** to automatically log users out of Zscaler Client Connector when ZDX is enabled for a device group. Users can then log in again to enable the ZDX service. This applies to customers using ZPA only or ZPA and Zscaler Deception. When disabled, Zscaler Client Connector runs without the ZDX service until the next Zscaler Client Connector login.
![Configure ZDX user groups for Zscaler Service Entitlement](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-zdx-group-users/ZDX_Entitlement.png)
- Click **Save**.
This updates your users' devices the next time they connect. If they are already connected, the devices automatically update in 60 minutes. To manually update their devices, users can go into Zscaler Client Connector and click **Update Policy** from the **More** window. After manually refreshing, they must reauthenticate on the **Digital Experience** window.
Possible Configurations for ZDX
The following table provides possible configurations for the Zscaler Service Entitlement feature and the resulting behavior of the ZDX service:
| **ZDX Enabled by Default** | **Groups Specified** | **Behavior** |
| -------------------------- | -------------------- | ------------ |
| Enabled | N/A | ZDX service is enabled for all users |
| Disabled | No | ZDX service is not enabled for any users |
| Disabled | Yes | ZDX service is enabled only for the specified group of users |