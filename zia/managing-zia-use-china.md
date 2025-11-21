# Managing ZIA Use in China
Source: https://help.zscaler.com/zia/managing-zia-use-china
PDF: https://help.zscaler.com/pdf/com/en/1402331.pdf

Zscaler's China Premium Internet Access feature provides fast and secure internet access for users residing in mainland China. The feature enables users to access international sites or applications such as Salesforce, Microsoft 365, etc. If you are looking for China Premium Service for Zscaler Private Access (ZPA), see [Managing ZPA Use in China](/zpa/managing-zpa-use-china).
Premium Services
The following premium services are available for organizations whose users work from mainland China and are required to access international sites:
- [China Premium](#china-premium-access)
- [China Premium Plus](#china-premium-access-plus)
To learn more about SLAs for China Premium Services, see [Supplemental ZIA Service Availability Agreement for the China Premium Data Centers](https://www.zscaler.com/china-premium-access-productsheet).
To learn more about ZIA in China, see [Deploying Zscaler Internet Access in China](/zia/deploying-zscaler-internet-access-china).
To access websites with DNS issues, you must forward DNS traffic to Zscaler. If the issue has been identified as DNS poisoning, Zscaler needs time to change the policy. Contact Zscaler Support for any DNS change. It takes a maximum of three days for the changes to be made.
[]China Premium Access is based on our Chinese technology partners’ IP backbone, which passes all domestically and internationally-bound traffic through the Great Firewall. Our technology partners have registered on Zscaler’s behalf all IP addresses assigned to the China Premium Access service under China’s Internet Content Provider (ICP) scheme. However, it is ultimately the responsibility of the end user customer to ensure their own compliance with all applicable Chinese laws and regulations when using the Zscaler service.
The China Premium service uses Private Service Edge hosted at a partner site within China, which has a premium Chinese internet service provider (ISP) with access to both the domestic internet in China and premium access to international websites and Software as a Service (SaaS) applications. This service allows you to break and inspect traffic within China, and use the partner premium fabric for any destination (domestic or international). There is no traffic forwarding limitation with this service. With this service, you can establish Internet Protocol Security (IPSec) or Generic Routing Encapsulation (GRE) tunnels from any endpoint to a Private Service Edge managed by Zscaler partners in China. You can use this service similar to a public Zscaler data center (DC).
![Traffic flow diagram of the China premium service](/downloads/zia/traffic-forwarding/china-premium-access/china-premium-internet-access/China-Premium.png?1663322266)
Zscaler manages the partner premium fabric.
The key benefits of this solution are:
- Shared premium bandwidth
- Multiple ingress tunnels are possible (GRE/IPSec)
- Z-Tunnel 1.0
- Z-Tunnel 2.0 (any traffic, any port)
- No traffic split is required at the branch offices
- You can break and inspect traffic within China
- Access to domestic and international traffic
- International traffic is routed via the China Great Firewall (GFW)
- Compliant with the regulations in China and [SLA](https://www.zscaler.com/china-premium-access-productsheet)
- [Backup](#china-premium-backup) is available. To enable it, contact Zscaler Support.
Enabling the Service
To enable the service for your organization, you must:
- Purchase this service and have Zscaler provision it.
- Limit the bandwidth at the source or use the Zscaler bandwidth controls to limit traffic.
Provisioning the Service
To provision the service for your organization:
-
Open a Zscaler Support ticket to provide the source tunnel IP to the China POP for GRE.
Zscaler associates the virtual IP (VIP) with the service and makes the required changes to the ZIA Public Service Edge within 48 hours.
-
Set the bandwidth limit for the IPSec/GRE tunnel to avoid exceeding the bandwidth purchased for the service.
You can view the bandwidth purchased in the purchase order.
- After your organization is provisioned, set up the tunnel to the VIP.
- Work with Zscaler Support to forward traffic and ensure that the traffic is flowing.
[]China Premium Backup
Zscaler allows you to send your traffic to an alternate site (secondary DC) within China as a redundancy to your primary DC. You can access DCs in Beijing and Shanghai and use either one as your primary DC, based on your users' location. You can also request for either of the DCs to be assigned. Zscaler reviews the situation and assigns an appropriate DC. If the primary DC (e.g., Beijing) fails, the traffic is forwarded to the secondary DC (e.g., Shanghai). You must ensure that you do not exceed the bandwidth purchased for the China Premium service. For example, if you require 100 Mbps bandwidth in Beijing, then the overall bandwidth for Shanghai and Beijing shouldn't exceed 100 Mbps.
- You can purchase backup bandwidth only if you have China Premium service. If you require China Premium Backup, Contact Zscaler Support.
- Be sure to tell the Zscaler Account team how you want to split the bandwidth between Beijing and Shanghai, or tell them the distribution of users close to Beijing and Shanghai.
When you configure and deploy the backup solution, you must:
- Define the primary and secondary DCs in the GRE/IPSec tunnel configuration (e.g., for offices in Beijing, when you forward the traffic to Zscaler Private Service Edge in Beijing, then define it as the primary DC and Shanghai as the secondary DC in the GRE/IPSec tunnel configuration).
- Define the [subcloud](/zia/about-subclouds) for both the Beijing and Shanghai DCs in the [PAC file](/zia/writing-pac-file) for remote users, so based on the users' location they are connected to the closest DC.
![Zscaler's China Premium with Backup DC](/downloads/zia/traffic-forwarding/china-premium-access/china-premium-internet-access/China%20Premium%20with%20Backup.png)
[]China Premium Access Plus connections utilize a dedicated cross-border private link that our Chinese technology partners register with the relevant Chinese government agencies via the three main Chinese telecom companies (China Telecom, China Unicom, and China Mobile). The Chinese Ministry of Industry and Information Technology (MIIT) accepts the use of VPNs for cross-border communications and connections to outside mainland China for business purposes. However, it is ultimately the responsibility of the end user customer to ensure their own compliance with all applicable Chinese laws and regulations when using the Zscaler service.
The China Premium Plus service uses Private Service Edge hosted at a partner site within China, which has a premium Chinese ISP with access to both the domestic internet in China and a dedicated link to international websites and SaaS applications. This service allows you to break and inspect traffic within China, and use the partner premium fabric for any destination (domestic or international). There is no traffic forwarding limitation with this service. This service is best suited for organizations with the highest bandwidth and user counts. You can use this service similar to a public Zscaler DC.
![Traffic flow diagram of the China Premium Plus service](/downloads/zia/traffic-forwarding/china-premium-access/china-premium-internet-access/Zscaler-China-Premium-Plus.png)
Zscaler manages the partner premium fabric.
The benefits of China Premium Access Plus are:
- Dedicated international bandwidth
- Bandwidth control option
- Ability to have multiple ingress tunnels (GRE/IPSec)
- Z-Tunnel 1.0
- Z-Tunnel 2.0 (any traffic, any port)
- No traffic split is required at the branch offices
- Break and inspect traffic within China
- Access to domestic and international traffic
- Compliant with the regulations in China and [SLA](https://www.zscaler.com/china-premium-access-productsheet)
- (Optional) Support for content filtering
- [Backup](#china-premium-plus-backup) is available. To enable it, contact Zscaler Support.
Enabling the Service
To enable the service for your organization, you must:
- Purchase this service and have Zscaler provision it.
- Limit the bandwidth at the source or use the Zscaler bandwidth controls to limit traffic.
Provisioning the Service
To provision the service for your organization:
-
Open a Zscaler Support ticket to provide the source tunnel IP to the China POP for GRE.
Zscaler associates the VIP with the service and makes the required changes to the ZIA Public Service Edge within 48 hours.
-
Set the bandwidth limit for the IPSec/GRE tunnel to avoid exceeding the bandwidth purchased for the service.
You can view the bandwidth purchased in the purchase order.
- After your organization is provisioned, set up the tunnel to the VIP.
- Work with Zscaler Support to forward traffic and ensure that the traffic is flowing.
[]China Premium Plus Backup
Zscaler allows you to send your traffic to an alternate site (secondary DC) within China as a redundancy to your primary DC. You can access DCs in Beijing and Shanghai and use either one as your primary DC, based on your users' location. You can also request for either of the DCs to be assigned. Zscaler reviews the situation and assigns an appropriate DC. If the primary DC (e.g., Beijing) fails, the traffic is forwarded to the secondary DC (e.g., Shanghai). You must ensure that you do not exceed the bandwidth purchased for the China Premium Plus service. For example, if you require 100 Mbps bandwidth in Beijing, then the overall bandwidth for Shanghai and Beijing shouldn't exceed 100 Mbps.
- You can purchase backup bandwidth only if you have China Premium Plus service. If you require China Premium Plus Backup, contact Zscaler Support.
- Be sure to tell the Zscaler Account team how you want to split the bandwidth between Beijing and Shanghai, or tell them the distribution of users close to Beijing and Shanghai.
When you configure and deploy the backup solution, you must:
- Define the primary and secondary DCs in the GRE/IPSec tunnel configuration (e.g., for offices in Beijing, when you forward the traffic to Zscaler Private Service Edge in Beijing, then define it as the primary DC and Shanghai as the secondary DC in the GRE/IPSec tunnel configuration).
- Define the [subcloud](/zia/about-subclouds) for both the Beijing and Shanghai DCs in the [PAC file](/zia/writing-pac-file) for remote users, so based on the users' location they are connected to the closest DC.
![Zscaler's China Premium Plus with Backup](/downloads/zia/traffic-forwarding/china-premium-access/china-premium-internet-access/Zscaler-China-Premium-Plus-with-Backup.png)