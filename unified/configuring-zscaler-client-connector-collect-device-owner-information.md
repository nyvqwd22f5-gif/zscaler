# Configuring Zscaler Client Connector to Collect Device Owner Information
Source: https://help.zscaler.com/zscaler-client-connector/configuring-zscaler-client-connector-collect-device-owner-information
PDF: https://help.zscaler.com/pdf/com/en/1333326.pdf

Zscaler Client Connector  collects the device owner name from supported devices and stores it in the Zscaler Client Connector Portal database. You can enable or disable the app from collecting device owner information, allowing for compliance with General Data Protection Regulation (GDPR).
This setting is enabled by default.
To configure whether the app collects or does not collect information:
- In the Zscaler Client Connector Portal, go to **Administration**.
- From the menu on the left, go to** Client Connector Support**.
- Click the **User Privacy** tab.
- Select the **Collect Device Owner Information** switch.
![The Collect Device Owner Information Switch in the Zscaler Client Connector Portal](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/user-privacy/configuring-zscaler-client-connector-collect-device-owner-information/Zscaler-App-User-Privacy-Collect-Owner-Info_0.png)
- Click **Save**.
To see the collected device owner information, go to the **Enrolled Devices** page. For any enrolled device, view the device fingerprint and locate the **Owner** field. To learn more, see [Viewing Device Fingerprint for an Enrolled Device](/zscaler-client-connector/viewing-device-fingerprint-enrolled-device).