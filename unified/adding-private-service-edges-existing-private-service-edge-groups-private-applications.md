# Adding Private Service Edges to an Existing Private Service Edge Group for Private Applications
Source: https://help.zscaler.com/unified/adding-private-service-edges-existing-private-service-edge-groups-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1496541.pdf

To add a Private Service Edge to an existing Private Service Edge group for Private Applications:
- Go to the **Private Service Edges** page (Infrastructure > Private Applications > Components > Private Service Edges).
- Click **Add Private Service Edges**.
The **Add Private Service Edges** window appears.
- In the **Choose Key** tab:
- Select **Choose an existing provisioning key**.
- Select an existing provisioning key from the drop-down menu. Ensure that the key you select is associated with the appropriate Private Service Edge group. You can click **Clear Selection** to remove any selections.
[See image.](#image_key)
- Click **Next**.
- In the **Deploy Private Service Edge** tab:
- **Copy Provisioning Key**: Copy the Private Service Edge provisioning key. You will need to enter this key when you deploy the Private Service Edge to a platform.
- **Choose Platform**: Select the platform you want to deploy your Private Service Edge on and follow the instructions that appear below. To learn more, see the [Private Service Edge Deployment Guides for Supported Platforms](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
[See image.](#image_platform)
- Deploy your Private Service Edge on the chosen platform.
- Click **Done**.
[]![Choose a key for a ZPA Private Service Edge group](/downloads/zpa/private-service-edge-management/private-service-edge-groups/adding-service-edges-existing-service-edge-group/Choose%20key%20step%201.png)
[]![Select a platform for the ZPA Private Service Edge](/downloads/zpa/adding-service-edges-existing-service-edge-group/zpa-addserviceedge-currentgroup-platform.png)