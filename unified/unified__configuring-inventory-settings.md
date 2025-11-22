# Configuring Inventory Settings
Source: https://help.zscaler.com/unified/configuring-inventory-settings
PDF: https://help.zscaler.com/pdf/com/en/1493351.pdf

The Inventory Settings page enables admins to configure the settings for data collection for Software Inventory, Software Patch Inventory, Wi-Fi data collection, or Process Inventory.
Minimum versions of Zscaler Client Connector and ZDX Module are required. The versions required for Experience Center are the same as listed for Zscaler Digital Experience (ZDX). To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
[See image.](#inventory)
[]
![Configure data collection for specific features](/downloads/zdx/administration/configuring-inventory-settings/ZDX-Configure-InventorySettings.png)
[]Configuring Software Inventory Data Collection
If Collect Software Inventory Data is enabled, Zscaler collects software inventory data. To learn more, see [Viewing Software Inventory](/unified/viewing-software-inventory).
To configure data collection for Software Inventory:
- Go to **Policies **>** Digital Experience Monitoring **>** Inventory Settings**.
- Enable **Collect Software Inventory Data**.
- Click **Save**.
[]Configuring Software Patch Inventory Data Collection
If Collect Patch Inventory Data is enabled, Zscaler collects the current distribution of software patches on user devices as inventory data. To learn more, see [Viewing Software Patch Inventory](/unified/viewing-software-patch-inventory).
To configure data collection for Software Patch Inventory:
- Go to **Policies **>** Digital Experience Monitoring **>** Inventory Settings**.
- Enable **Collect Patch Inventory Data**.
- Click **Save**.
[]Configuring Wi-Fi Data Collection
You can opt for Wi-Fi data collection to collect the signal strength and retransmission rate to identify low-performing Wi-Fi devices. To learn more, see [Monitoring the Wi-Fi Dashboard](/unified/monitoring-wi-fi-dashboard).
To configure Wi-Fi data collection:
- Go to **Policies **>** Digital Experience Monitoring **>** Inventory Settings**.
- Enable **Use Signal Strength and Retransmission Rate for Wi-Fi Data Collection**.
- Click **Save**.
[]Configuring Process Inventory CPU Incidents
Process Inventory monitors the number of CPU Incidents that exceed the CPU Usage threshold (e.g., CPU Usage > 10%) for a duration of 5 minutes. To learn more, see [Viewing Process Inventory](/unified/viewing-process-inventory).
- Go to **Policies **>** Digital Experience Monitoring **>** Inventory Settings**.
- Enter a CPU Usage threshold between `0` and `100`%.
- Click **Save**.