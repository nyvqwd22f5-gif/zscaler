# Adding a VPN Trusted Network Adapter Name
Source: https://help.zscaler.com/zscaler-client-connector/configuring-vpn-trusted-network-adapter-criteria
PDF: https://help.zscaler.com/pdf/com/en/1404736.pdf

If your VPN isn't from a common vendor and the NIC adapter text doesn't match what is usually detected, you can add the name of your VPN so Zscaler Client Connector can accurately detect a VPN Trusted Network.
To add VPN adapter names in the Zscaler Client Connector Portal:
- In the Zscaler Client Connector Portal, go to **Administration**.
- From the left-side navigation, click **Client Connector Support**.
- Click the **Endpoint Integration** tab.
- In the **VPN Trusted Network Adapter Criteria **field, type the VPN adapter vendor name. Press `Enter` to add another VPN.
- When you're finished adding VPNs, click **Save**.
You can remove hard-coded VPN adapter names by clicking the **Delete **icon next to the VPN name.
![Use the VPN Trusted Network Adapter Criteria to add a VPN adapter strings](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/endpoint-integration/configuring-vpn-trusted-network-adapter-criteria/VPN_Trusted_Network_Adapter_EndPoint.png)
When policies are updated on devices, new VPN adapter names are sent to Zscaler Client Connector. On the next network change or when services start, Zscaler Client Connector detects the new VPN adapter as a trusted network.