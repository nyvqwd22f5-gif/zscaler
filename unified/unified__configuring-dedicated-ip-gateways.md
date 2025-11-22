# Configuring Dedicated IP Gateways
Source: https://help.zscaler.com/unified/configuring-dedicated-ip-gateways
PDF: https://help.zscaler.com/pdf/com/en/1530647.pdf

You can create gateways with primary and secondary data centers to forward traffic to specific destinations. Only the data centers available on the Infrastructure > Internet & SaaS > Network Policies > Dedicated IP > IP Addresses page (i.e., the data centers that have a dedicated IP address assigned to your organization) can be selected as the primary and secondary data centers. By default, the primary data center is used to forward all traffic to the destination and the secondary data center acts as a backup in case the primary data center is unreachable.
The configured gateways are used when creating a [forwarding rule](/unified/configuring-forwarding-policy) to forward traffic to a dedicated egress IP address.
To configure a gateway:
- Go to **Infrastructure** > **Internet & SaaS** > **Network Policies** > **Dedicated IP**.
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