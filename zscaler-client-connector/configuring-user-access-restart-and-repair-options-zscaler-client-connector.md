# Configuring User Access to the Restart and Repair Options for Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/configuring-user-access-restart-and-repair-options-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1340876.pdf

Users can troubleshoot the app by clicking **Restart Service** or **Repair App f**rom the **More** window of Zscaler Client Connector.
The **Repair App** feature is only available for Windows.
![The Restart Service and Repair App options on the Zscaler Client Connector](/downloads/tech-pubs-drafts/configuring-user-access-restart-repair-options-zscaler-client-connector/Repair_Restart-750.png)
Restarting Zscaler Client Connector doesn't impact security enforcement. However, you can click **Restart Service **only once within a 30-second period for Zscaler Client Connector version 3.8 and later for Android and Zscaler Client Connector version 3.8 and later for Android on ChromeOS. When users select **Repair App**, the app attempts to repair itself by reinstalling app drives and services.
Using **Restart Service** or **Repair App** causes Zscaler Client Connector to fail-open briefly. Disable access if this is not ideal.
To configure user access to these options:
- In the Zscaler Client Connector Portal, go to **Administration** and select **Client Connector Support**.
- On the **App Supportability** tab, click **Enable End User to Restart Services and Repair App**.
- Click **Save**.
![The Enable End User to Restart Services and Repair App switch](/downloads/tech-pubs-drafts/configuring-user-access-restart-repair-options-zscaler-client-connector/Portal-Enable_Repair-Restart.png)