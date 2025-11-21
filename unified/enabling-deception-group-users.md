# Enabling Deception for a Group of Users
Source: https://help.zscaler.com/unified/enabling-deception-group-users
PDF: https://help.zscaler.com/pdf/com/en/1491126.pdf

You can use Zscaler Service Entitlement to select which users can enroll into Zscaler Deception. To enable Deception for only a select group of users, you must deploy Zscaler Client Connector Windows 3.9 or later.
Enabling Deception for User Groups
To enable Deception for a group of users:
- In the Admin Portal, go to **Administration > Entitlements > Deception**.
- To enable Deception for only a group of users, ensure that **Zscaler Deception Enabled by Default **is disabled. If this setting is enabled, Deception is available for all users and you cannot assign Deception to a group.
- Select a group of users from the **User Groups** drop-down menu and click **Done**. The default setting is **None**. This option means no groups have access to Deception and allows users to keep their current settings.
These groups are defined in the Admin Portal. If you do not see your groups, ensure that the directory groups were synced properly between Internet & SaaS and Zscaler Client Connector. To learn more, see [Syncing Directory Groups between the Internet & SaaS and Zscaler Client Connector](/unified/syncing-directory-groups-between-internet-saas-and-zscaler-client-connector).
- Select **Logout Zscaler Client Connector when Zscaler Deception Entitlement is Enabled **to automatically log users out of Zscaler Client Connector when Deception is enabled for a device group. Users can then log in again to enable the Deception service. This applies to customers using Private Applications only or Private Applications and Zscaler Deception. When disabled, Zscaler Client Connector runs without the Digital Experience Monitoring service until the next Zscaler Client Connector login.
![Zscaler Deception tab in Zscaler Service Entitlement ](/downloads/z-app/policy-administration-settings/zscaler-service-entitlement/selective-entitlement-enabling-deception-group-users/Deception_usergrps_0.png)
- Click **Save**.
Your users' devices are updated the next time they connect. If users are already connected, devices automatically update in 60 minutes. To manually update devices, users can go into Zscaler Client Connector and click **Update Policy** from the **More **window. After manually refreshing, users must reauthenticate in the Zscaler Deception Service Status window.
Possible Configurations for Deception
The following table provides possible configurations for the Zscaler Service Entitlement feature and the resulting behavior of the Zscaler Deception service:
| **Zscaler Deception Enabled by Default** | **Groups Specified** | **Behavior** |
| ---------------------------------------- | -------------------- | ------------ |
| Enabled | N/A | Deception service is enabled for all users |
| Disabled | No | Deception service disabled for users |
| Disabled | Yes | Deception service is enabled only for the specified group of users |