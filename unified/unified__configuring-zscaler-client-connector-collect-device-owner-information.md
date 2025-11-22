# Configuring Zscaler Client Connector to Collect Device Owner Information
Source: https://help.zscaler.com/unified/configuring-zscaler-client-connector-collect-device-owner-information
PDF: https://help.zscaler.com/pdf/com/en/1495936.pdf

Zscaler Client Connector collects the device owner name from supported devices and stores it in the Admin Portal database. You can enable or disable the app from collecting device owner information, allowing for compliance with General Data Protection Regulation (GDPR).
This setting is enabled by default.
To configure whether the app collects or does not collect information:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > User Privacy**.
- On the **User Privacy** tab, select **Collect Device Owner Information**.
![Collect Device Owner Information Switch](/downloads/client-connector-collect-device-owner-info.png)
- Click **Save**.
To see the collected device owner information, go to the **Enrolled Devices** page. For any enrolled device, view the device fingerprint and locate the **Owner** field. To learn more, see [Viewing Device Fingerprint for an Enrolled Device](/unified/viewing-device-fingerprint-enrolled-device).