# Editing ZPA Private Service Edge Groups
Source: https://help.zscaler.com/zpa/editing-service-edge-groups
PDF: https://help.zscaler.com/pdf/com/en/1484491.pdf

To edit a configured ZPA Private Service Edge group:
- Go to **Configuration & Control** > **Private Infrastructure** > **Private Service Edge Management** > **Private Service Edge Groups**.
- Click the **Private Service Edge Groups** tab.
-
In the table, locate the ZPA Private Service Edge group you want to modify and click the **Edit **icon.
ZPA Private Service Edge groups that are managed by Zscaler are read only and cannot be edited.
The **Edit Private Service Edge Group** window appears.
- In the **Edit Private Service Edge Group** window, you can modify any field.
![Edit Private Service Edge Group window](/downloads/zpa/private-service-edge-management/private-service-edge-groups/editing-service-edge-groups/Editing%20ZPA%20PSE%20Group_0.png)
When you disable **Publicly Accessible** without a trusted network, the IP address of the ZPA Private Service Edge is returned to the client for both on-premises and roaming users that are located closest to the ZPA Private Service Edge. To mitigate connectivity issues for remote users who want to connect to this ZPA Private Service Edge, ensure it’s reachable over a public IP address.
- Click **Save**.