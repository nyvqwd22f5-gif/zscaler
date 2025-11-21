# Syncing Directory Groups between the ZIA Admin Portal and Zscaler Client Connector Portal
Source: https://help.zscaler.com/zscaler-client-connector/syncing-directory-groups-between-zia-admin-portal-and-zscaler-client-connector-portal
PDF: https://help.zscaler.com/pdf/com/en/1285446.pdf

The directory [groups](/zia/about-groups) you configured in the ZIA Admin Portal are automatically available for selection within the Zscaler Client Connector Portal when you [configure an App Profile](/zscaler-client-connector/configuring-zscaler-app-profiles). This allows you to create different profiles for the various directory groups in your organization.
![Selecting a group for a Zscaler Client Connector profile policy](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/configuring-policy-and-administration-settings/syncing-directory-groups-between-zscaler-admin-portal-and-app-portal/GroupsInAppProfile.png)
The groups in the Zscaler Client Connector Portal sync with groups in the ZIA Admin Portal every three hours. In the Zscaler Client Connector Portal, you can check when the next sync will occur. You can also manually sync groups between the portals.
Checking Next Sync Time and Performing Manual Sync
- In the Zscaler Client Connector Portal, go to **Administration**.
- From the menu on the left, go to **Client Connector Support**.
- In the **Advanced Configuration **tab, you can:
- View the date and timestamp under **Next Directory Group Sync Time**.
- Manually sync directory groups between the ZIA Admin Portal and the Zscaler Client Connector Portal, by clicking **Sync Groups**.
![Check the next group sync time and perform a manual group sync](/downloads/zia/zscaler-app-support-directory-sync-status-1.4.png)
To learn more about other Zscaler Client Connector Support features, see [About Zscaler Client Connector Support](/zscaler-client-connector/about-zscaler-app-support).