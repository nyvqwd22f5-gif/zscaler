# Verifying a User's Traffic is Being Forwarded to the Zscaler Service
Source: https://help.zscaler.com/unified/verifying-users-traffic-being-forwarded-zscaler-service
PDF: https://help.zscaler.com/pdf/com/en/1495291.pdf

To check if a user's traffic is going to the Zscaler service, on the user's device, go to [ip.zscaler.com](http://ip.zscaler.com). The My IP Address page provides details about the Zscaler cloud to which the device is sending its traffic and links to additional tools you can use to check connectivity.
Zscaler's My IP Address service ([ip.zscaler.com](http://ip.zscaler.com)) might not recognize IPv6 traffic passing through the Zscaler cloud. Exercise caution when using the My IP Address service for troubleshooting or verifying connectivity to the Zscaler cloud [when IPv6 is enabled on the client](/unified/configuring-ipv6-settings).
On the My IP Address page, you can view the following information:
- The Zscaler cloud and the location of the Internet & SaaS Public Service Edge to which your traffic is going
- The egress IP address of the Internet & SaaS Public Service Edge
- The virtual IP address of the Internet & SaaS Public Service Edge
- The Zscaler hostname of the Internet & SaaS Public Service Edge instance that is processing your traffic
- The egress IP address of the network from which the Internet & SaaS Public Service Edge receives traffic
- The IP address of your gateway
![Screenshot of ip.zscaler.com that provides labeled details about the Zscaler cloud to which the device is sending its traffic and links to](/downloads/zia/documentation-knowledgebase/troubleshooting/troubleshooting-zscaler-issues/how-can-i-check-if-users-traffic-going-zscaler/traffic_ip.zscaler.com_screenshot.png)