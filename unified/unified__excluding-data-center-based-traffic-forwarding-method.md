# Excluding a Data Center Based on Traffic Forwarding Method
Source: https://help.zscaler.com/unified/excluding-data-center-based-traffic-forwarding-method
PDF: https://help.zscaler.com/pdf/com/en/1495251.pdf

If a Zscaler data center (DC) is having a service-affecting issue, you can disable all IPSec VPN tunnels terminating at a virtual IP (VIP) address of the affected DC directly from the Admin Portal. With this action, you trigger a failover from primary to secondary tunnels at the endpoint on your organization’s premises, ensuring business continuity and connectivity resilience.
In the event of service disruptions, [Zscaler Trust Portal](https://trust.zscaler.com/) incidents, disasters, etc., you can exclude DCs from service based on the traffic forwarding method. In the Admin Portal, you select the DC and the duration of the DC exclusion, which can be renewed after it expires or edited as needed.
The DC is restored for service to your organization when the configured exclusion expires or if you take action before the expiration. When a DC is restored for service, existing VPN tunnels can re-establish to the DC and new VPN tunnels can be established.
To add a DC exclusion:
- Go to **Infrastructure **>** Internet & SaaS **> **Traffic Forwarding > DC Exclusion**.
-
Click **+ DC Exclusion**.
The **Add DC Exclusion **window appears.
- In the **Add DC Exclusion** window:
- **Data Center**: Select a DC.
- **Traffic Forwarding Method**: This is the traffic forwarding method (e.g., IPSec VPN tunnels) to be disabled for the DC.
- **Begin Time (UTC Time)**: Set the date and time at which the DC exclusion begins and tunnels are disabled for the DC. You can set the exclusion to begin within a month from the current date. The time is displayed in Coordinated Universal Time (UTC). Set the **Begin Time** at least 5 minutes from the current time (e.g., if the current time is 11:30 a.m. UTC, set the **Begin Time** to 11:35 a.m. UTC.)
- **Expiration Time (UTC Time)**: Set the date and time at which the DC exclusion expires and tunnels are re-enabled for the DC. You can set the expiration within 15 days from the **Begin Time**. The time is displayed in Coordinated Universal Time (UTC). Set the **Expiration Time** at least 2 hours from the **Begin Time** (e.g., if the **Begin Time** is 11:30 a.m. UTC, set the **Expiration Time** to 1:30 p.m. UTC.)
- **Description**: (Optional) Enter a description of the DC exclusion.
[See image.](#img-zia-add-dc-exclusion)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
When the DC exclusion expires, a warning message appears, prompting you to edit the exclusion period, if required. You can edit the exclusion period before it expires as needed.
[See image.](#img-zia-dc-exclusion-expiration)
[]![Screenshot of Add DC Exclusion configuration window in the ZIA Admin Portal](/downloads/zia/traffic-forwarding/excluding-data-center-based-traffic-forwarding-method/zia-dc-exclusion.png)
[]![Screenshot of DC exclusion expiration in the ZIA Admin Portal](/downloads/zia/traffic-forwarding/excluding-data-center-based-traffic-forwarding-method/zia-dc-exclusion-expiration.png)