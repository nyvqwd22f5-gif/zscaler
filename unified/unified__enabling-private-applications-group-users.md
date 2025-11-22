# Enabling Private Applications for a Group of Users
Source: https://help.zscaler.com/unified/enabling-private-applications-group-users
PDF: https://help.zscaler.com/pdf/com/en/1491086.pdf

You can use Zscaler Service Entitlement to select which users can enroll into Private Applications. Configuring Private Applications using a small subset of users allows for testing before rolling out the service to all users.
To enable Private Applications for only a select group of users, you must deploy Zscaler Client Connector 1.2.4 or later. However, earlier versions of Zscaler Client Connector always have Private Applications enabled, regardless of the Zscaler Service Entitlement setting.
- For Private Applications instances created before July 2017, Private Applications is enabled for all users by default. This preserves the existing behavior of Private Applications enrollment prior to the addition of the selective entitlement feature.
- For Private Applications instances created after July 2017, Private Applications is disabled by default. This allows you to determine when and how to provision Private Applications for your users.
If you’re using device groups, the user must belong to both the device group and user group to avoid disconnecting Private Applications services.
Enabling Private Applications for User Groups
To enable Private Applications for a group of users:
- In the Admin Portal, go to **Administration > Entitlements > Private Access**.
- To enable Private Applications for only a group of users, ensure that **ZPA Enabled by Default for User Tunnel **is disabled. If this setting is enabled, Private Applications is available for all users and you cannot assign Private Applications to a group.
****![Configure setting for ZPA Enabled by Default for User Tunnel](/downloads/z-app/policy-administration-settings/zscaler-service-entitlement/selective-entitlement-enabling-zpa-group-users/client-connector-zpa-enabled-by-default.png)
****
- Select a group of users from the drop-down menu and click **Done**. The default setting is **None**. This option means no groups have access to Private Applications. This allows users to keep their current settings.
These groups are defined in the Admin Portal. If you do not see your groups, ensure that the directory groups were synced properly between Internet & SaaS and Zscaler Client Connector. To learn more, see [Syncing Directory Groups between the Internet & SaaS and Zscaler Client Connector](/unified/syncing-directory-groups-between-internet-saas-and-zscaler-client-connector).
- Click **Save**.
This updates your users' devices the next time they connect. If they are already connected, the devices automatically update in 60 minutes. To manually update their devices, users can go into Zscaler Client Connector and click **Update Policy** from the **More** window. After manually refreshing the device, they must reauthenticate on the **Private Access** page.
Possible Configurations for Private Applications
The following table provides possible configurations for the Zscaler Service Entitlement feature and the resulting behavior of the Private Applications service:
| **Enabled by Default for User Tunnel** | **Groups Specified** | **Behavior** |
| -------------------------------------- | -------------------- | ------------ |
| Enabled | N/A | Private Applications service is enabled for all users |
| Disabled | No | Private Applications service is not enabled for any users |
| Disabled | Yes | Private Applications service is enabled only for the specified group of users |