# Enabling ZPA for a Group of Users
Source: https://help.zscaler.com/zscaler-client-connector/selective-entitlement-enabling-zpa-group-users
PDF: https://help.zscaler.com/pdf/com/en/1334671.pdf

You can use Zscaler Service Entitlement to select which users can enroll into Zscaler Private Access (ZPA). Configuring ZPA using a small subset of users allows for testing before rolling out the service to all users.
To enable ZPA for only a select group of users, you must deploy Zscaler Client Connector 1.2.4 or later. However, earlier versions of Zscaler Client Connector always have ZPA enabled, regardless of the Zscaler Service Entitlement setting.
- For ZPA instances created before July 2017, ZPA is enabled for all users by default. This preserves the existing behavior of ZPA enrollment prior to the addition of the selective entitlement feature.
- For ZPA instances created after July 2017, ZPA is disabled by default. This allows you to determine when and how to provision ZPA for your users.
If you’re using device groups, the user must belong to both the device group and user group to avoid disconnecting ZPA services.
Enabling ZPA for User Groups
To enable ZPA for a group of users:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left menu, select **Zscaler Service Entitlement**.
- To enable ZPA for only a group of users, ensure that **ZPA Enabled by Default for User Tunnel **is disabled. If this setting is enabled, ZPA is available for all users and you cannot assign ZPA to a group.
**![Configure setting for ZPA Enabled by Default for User Tunnel](/downloads/z-app/policy-administration-settings/zscaler-service-entitlement/selective-entitlement-enabling-zpa-group-users/client-connector-zpa-enabled-by-default.png)
**
- Select a group of users from the drop-down menu and click **Done**. The default setting is **None**. This option means no groups have access to ZPA. This allows users to keep their current settings.
These groups are defined in the ZIA Admin Portal. If you do not see your groups, ensure that groups were synced to the Zscaler Client Connector Portal. To learn more, see [Syncing Directory Groups between the ZIA Admin Portal and App Portal](/zscaler-client-connector/syncing-directory-groups-between-zscaler-admin-portal-and-app-portal).
- Click **Save**.
This updates your users' devices the next time they connect. If they are already connected, the devices automatically update in 60 minutes. To manually update their devices, users can go into Zscaler Client Connector and click **Update Policy** from the **More** window. After manually refreshing the device, they must [reauthenticate on the **Private Access** page](/zpa/about-reauthPolicy#understandReauth).
Possible Configurations for ZPA
The following table provides possible configurations for the Zscaler Service Entitlement feature and the resulting behavior of the ZPA service:
| **ZPA Enabled by Default** | **Groups Specified** | **Behavior** |
| -------------------------- | -------------------- | ------------ |
| Enabled | N/A | ZPA service is enabled for all users |
| Disabled | No | ZPA service is not enabled for any users |
| Disabled | Yes | ZPA service is enabled only for the specified group of users |