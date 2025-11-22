# Understanding Alternative Cloud Domains
Source: https://help.zscaler.com/zscaler-client-connector/understanding-alternative-cloud-domains
PDF: https://help.zscaler.com/pdf/com/en/1529036.pdf

In China, only a content provider who is serving content from mainland China is required to have an Internet Content Provider (ICP) license. Zscaler does not generate or serve content in mainland China or offer additional encryption services. However, when a Zscaler Client Connector user in China connects to a Zscaler server also located in China, the connection might be blocked because the cloud on which your organization is provisioned is not registered in China.
You can use an alternative cloud domain registered in China that can override the default cloud domain when connecting to the Zscaler Internet Access (ZIA) service and the Zscaler Private Access (ZPA) service.
Prerequisites
Make sure the following prerequisites are met:
- Ensure Zscaler Client Connector is upgraded to one of the following versions:
- Zscaler Client Connector version 4.4 or later for Windows
- Zscaler Client Connector version 4.2 or later for macOS
- If you use ZIA with Zscaler Tunnel (Z-Tunnel) 2.0, configure a forwarding profile with these settings:
- A Tunnel Driver Type of Packet Filter-Based (Zscaler Client Connector for Windows only)
- A forwarding profile action of Tunnel.
- A Tunnel Version Selection of Z-Tunnel 2.0
How it works
When a Zscaler Client Connector user in China connects to the Zscaler service, Zscaler Client Connector determines whether an alternative cloud domain is configured as part of the Service Edge Discovery. Zscaler Client Connector then uses the alternative cloud domain that was discovered to connect to the ZIA Service Edge and ZPA Service Edge.
Zscaler Client Connector automatically connects to the alternative cloud domain if you use a compatible version of the app. If required, you can disable this feature for your organization by contacting Zscaler Support.
Connecting to Specific ZIA Public Service Edges
If you use Zscaler Client Connector version 4.7 or later for Windows, Zscaler Client Connector locates the alternative cloud name in the default return statement of the PAC file associated with the app profile. If the PAC file uses the `${GATEWAY_FX}` macro or a similar macro, the PAC server replaces the macro with the alternative cloud domain along with the ZIA Public Service Edge IP address and port.
If the return statement does not include an alternative domain, Zscaler Client Connector uses the alternative domain in the HTTP response header of the PAC file and connects based on the Zscaler Client Connector location (and not the Service Edge location).