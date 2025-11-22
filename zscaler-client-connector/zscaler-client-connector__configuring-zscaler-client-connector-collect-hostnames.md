# Configuring Zscaler Client Connector to Collect Hostnames
Source: https://help.zscaler.com/zscaler-client-connector/configuring-zscaler-client-connector-collect-hostnames
PDF: https://help.zscaler.com/pdf/com/en/1333351.pdf

You can enable Zscaler Client Connector to collect the hostname information from supported devices and store it in the Zscaler Client Connector Portal database. This information is included in the CSV file when you export device fingerprint for the enrolled devices. To learn more[,](/zscaler-client-connector/about-enrolled-devices) see[ About Enrolled Devices](/zscaler-client-connector/about-enrolled-devices).
Zscaler Client Connector no longer collects the full machine hostname on devices running iOS 16 and later.
To enable or disable the app from collecting information:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left-side navigation, go to **Client Connector Support**.
- In the **User Privacy** tab, toggle the switch to enable or disable the **Collect Machine Hostname Information**.
![The Collect Machine Hostname Information switch in the Zscaler Client Connector Portal](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/user-privacy/configuring-zscaler-client-connector-collect-hostnames/Zscaler-App-User-Privacy-Collect-Machine-Hostname_1.png)
- Click **Save**.
To see the collected hostname information, go to the** Enrolled Devices **page. For any enrolled device, view the **Machine Hostname** field. To learn more, see [Viewing Device Fingerprint for an Enrolled Device](/zscaler-client-connector/viewing-device-fingerprint-enrolled-device).