# Editing Private Service Edge Groups for Private Applications
Source: https://help.zscaler.com/unified/editing-private-service-edge-groups-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1496546.pdf

To edit a configured Private Service Edge group:
- Go to the **Private Service Edge Groups** page (Infrastructure > Private Applications > Components > Service Edge Groups).
-
In the table, locate the Private Service Edge group you want to modify and click the **Edit **icon.
Private Service Edge groups that are managed by Zscaler are read only and cannot be edited.
The **Edit Private Service Edge Group** window appears.
-
In the **Edit Private Service Edge Group** window, you can modify any field.
![Edit Private Service Edge Group window](/downloads/zpa/private-service-edge-management/private-service-edge-groups/editing-service-edge-groups/Editing%20PSE%20Group%20Commercial%20version.png)
When you disable **Publicly Accessible** without a trusted network, the IP address of the Private Service Edge is returned to the client for both on-premises and roaming users that are located closest to the Private Service Edge. To mitigate connectivity issues for remote users who want to connect to this Private Service Edge, ensure it’s reachable over a public IP address.
- Click **Save**.