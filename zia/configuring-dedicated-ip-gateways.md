# Configuring Dedicated IP Gateways
Source: https://help.zscaler.com/zia/configuring-dedicated-ip-gateways
PDF: https://help.zscaler.com/pdf/com/en/1499511.pdf

You can create gateways with primary and secondary data centers to forward traffic to specific destinations. Only the data centers available on the Dedicated IP > IP Addresses page (i.e., the data centers that have a dedicated IP address assigned to your organization) can be selected as the primary and secondary data centers. By default, the primary data center is used to forward all traffic to the destination and the secondary data center acts as a backup.
The configured gateways are used when creating a [forwarding rule](/zia/configuring-forwarding-policy) to forward traffic to a dedicated egress IP address.
When dedicated IP addresses are allocated to your organization, the Zscaler service automatically creates a default gateway. To learn more, see [About Dedicated IP Gateways](/zia/about-dedicated-ip-gateways).
To configure a gateway:
- Go to **Administration** > **Dedicated IP** > **Gateways**.
-
Click **Add Gateway**.
The **Add Gateway** window appears.
-
In the **Add Gateway** window:
- **Name**: Enter a name for the gateway.
- **Primary Data Center**: From the drop-down menu, select the location of the primary data center. This field lists only the data centers for which a dedicated IP address is provisioned by Zscaler.
-
**Secondary Data Center**: From the drop-down menu, select the location for the secondary data center. This field lists only the data centers for which a dedicated IP address is provisioned by Zscaler.
Select **Auto **to allow the Zscaler service to automatically assign a data center based on geographical proximity to the Zscaler Public Service Edge servicing the traffic.
- **Description**: (Optional) Enter additional notes or information about the gateway.
[See image.](#add-gateway-image)
- Click **Save** and activate the change.
[]
![Add Gateway window on the Dedicated Ip > gateways page](/downloads/zia/policies/forwarding-control/dedicated-ip/configuring-dedicated-ip-gateways/zia-configuring-dedicated-ip-gateways-add-gateway.png)