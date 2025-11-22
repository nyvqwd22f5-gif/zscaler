# Quarantining a Device in the Admin Portal
Source: https://help.zscaler.com/unified/quarantining-device-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1532007.pdf

You can quarantine devices that are determined to be a potential threat in the Admin Portal. This could occur if a device doesn’t meet security standards, such as running malware, violating company policy, or attempting to use a stolen device. Quarantining a device limits or blocks its access to Zscaler applications.
After you quarantine a device, it can't be re-enrolled unless an admin moves it to the [Removed ](/unified/device-states-enrolled-devices)state. The device can't be used to log in again, is not available for [soft removal](/unified/soft-removing-device-admin-portal), and is eligible for hard deletion.
Quarantining a device doesn't count against the number of devices in the [device limit](/unified/removing-device-if-number-devices-limit-reached).
To quarantine a device:
- In the Admin Portal, go to **Infrastructure **>** Connectors **>** Client **>** Device Overview**.
- On the **Device Management** page, click the **View **icon of the device you want to quarantine.
- Click **Quarantine**, located at the bottom of the Zscaler Client Connector Registered Device Details page.
![Registered Device Details page Quarantine a Device ](/downloads/zscaler-client-connector/monitoring-usage/quarantining-device-zscaler-client-connector-portal/quarantine1.png)
You can unquarantine a device in the Admin Portal. The device’s state changes to [Removed](/unified/device-states-enrolled-devices) and the device can be used to log in to Zscaler Client Connector.
To unquarantine a device:
- In the Admin Portal, go to **Infrastructure **>** Connectors **>** Client **>** Device Overview**.
- On the** Device Management** page, click the **View **icon of the device you want to unquarantine.
- Click **Unquarantine**, located at the bottom of the Zscaler Client Connector Registered Device Details page.
![Registered Device Details page Unquarantine a Device ](/downloads/zscaler-client-connector/monitoring-usage/quarantining-device-zscaler-client-connector-portal/unquarantine1.png)