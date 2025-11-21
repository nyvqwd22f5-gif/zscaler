# Adding a VPN Service Name
Source: https://help.zscaler.com/zscaler-client-connector/adding-vpn-service-name
PDF: https://help.zscaler.com/pdf/com/en/1458721.pdf

By default, traffic that is bypassed from Zscaler Client Connector is not logged. When you enable and configure flow logging in [App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles) and select **VPN **to capture traffic logs for bypassed data, you must add a VPN service name to classify traffic flow into a VPN tunnel if the VPN service is not already listed.
Contact Zscaler Support to enable this feature.
You can view existing VPN service names in the **VPN Services for Flow Logging** list.
To add VPN services in the Zscaler Client Connector Portal:
- Go to **Administration **> **Client Connector Support**.
- Click the **Endpoint Integration** tab.
- In the **VPN Services for Flow Logging** field, enter the VPN service name. The name can be up to 65 characters.
![VPN Services for Flow Logging on Endpoint Integration tab in the Zscaler Client Connector Portal ](/downloads/VPN_Services_for_Flow_Logging.png)
- Press `Enter` to add another VPN service.
- When you're finished adding VPN services, click **Save**.