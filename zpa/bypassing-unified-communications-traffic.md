# Bypassing Unified Communications Traffic
Source: https://help.zscaler.com/zpa/bypassing-unified-communications-traffic
PDF: https://help.zscaler.com/pdf/com/en/1483991.pdf

Unified communications (UC) traffic for off-network and on-network users should use edge servers, externally accessible Session Border Controllers (SBCs), or UC gateways. These deployment models are recommended by UC vendors (for example, Skype for Business). Zscaler highly recommends adopting one of these UC deployment models to provide the best performance. Zscaler also recommends not sending UC traffic to ZPA, as this has the potential to add latency and jitter to the communication.
If you are using a wildcard for [dynamically discovering applications](/zpa/about-application-discovery) or are using an IP subnet to discover applications through ZPA (e.g. using *.company.com or 10.0.0.0/8), you must define the UC traffic applications and [configure bypass settings](/zpa/how-do-i-configure-and-corporate-network-settings) in order to exclude the hosts from being discovered.
To bypass unified communications traffic:
- Go to **Resource Management **>** Application Management **>** Application Segments **>** Defined Application Segments**.
- Click **Add Application Segment**.
The **Add Application Segment** window appears.
- In the **Add Application Segment** window, under **1. Define Applications**:
- For **Applications**:
- Enter the domain names and IP addresses for the UC applications you want ZPA to bypass
- For **Zscaler Client Connector Access**:
- **Bypass**: Select **Always**
In following example, UC traffic for Skype is bypassed for *.safemarch.com:
![Define Application section of Add Application Segment window](/downloads/zpa/documentation-knowledgebase/knowledge-base/bypassing-unified-communications-traffic/zpa-newapplication-bypassuc.png)
- Complete the configuration for the new application as detailed in [Configuring Application Segments](/zpa/about-application/onboard).
To learn more, see [Configuring Bypass Settings](/zpa/how-do-i-configure-and-corporate-network-settings).