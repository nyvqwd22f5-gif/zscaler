# Configuring Zscaler Client Connector to Collect Hostnames
Source: https://help.zscaler.com/unified/configuring-zscaler-client-connector-collect-hostnames
PDF: https://help.zscaler.com/pdf/com/en/1495941.pdf

You can enable Zscaler Client Connector to collect the hostname information from supported devices and store it in the Admin Portal database. This information is included in the CSV file when you export device fingerprint for the enrolled devices. To learn more[,](/z-app/about-enrolled-devices) see[ About Enrolled Devices](/unified/about-enrolled-devices).
Zscaler Client Connector no longer collects the full machine hostname on devices running iOS 16 and later.
To enable or disable the app from collecting information:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > User Privacy**.
- In the **User Privacy** tab, toggle the switch to enable or disable the **Collect Machine Hostname Information**.
![Collect Machine Hostname Information Switch](/downloads/client-connector-collect-machine-hostname.png)
- Click **Save**.
To see the collected hostname information, go to the** Enrolled Devices **page. For any enrolled device, view the **Machine Hostname** field. To learn more, see [Viewing Device Fingerprint for an Enrolled Device](/unified/viewing-device-fingerprint-enrolled-device).