# Supported Versions & Feature Compatibility
Source: https://help.zscaler.com/zdx/supported-versions-feature-compatibility
PDF: https://help.zscaler.com/pdf/com/en/1433851.pdf

To begin configuring Zscaler Digital Experience (ZDX), you must first deploy the minimum required or later version of Zscaler Client Connector based on your OS.
To configure Zscaler Client Connector for your organization, see [What Is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector) and [Step-by-Step Configuration Guide for Zscaler Client Connector](/client-connector/step-step-configuration-guide-zscaler-client-connector).
Zscaler supports the latest software version and the two previous versions for Zscaler Client Connector due to the commitment of continuous improvement for Zscaler products. To learn more, see [Supported Versions](/eos-eol/supported-versions), and [Viewing and Configuring ZDX Module Upgrades](/zscaler-client-connector/viewing-and-configuring-zdx-module-upgrades).
Additional prerequisites might also be required to access or use certain features. These can include:
- [Ranges & Limitations](/zdx/ranges-limitations): To ensure the feature is supported by your subscription level.
- [ZDX Role](/zdx/adding-zdx-roles): To ensure you have the proper permissions for feature access.
To determine if a feature requires additional prerequisites, see the feature's respective help articles.
Minimum OS Version Compatibility
Each OS with a base ZDX Module version requires a compatible Zscaler Client Connector version.
| OS | Zscaler Client Connector Version | Base ZDX Module Version |
| --- | -------------------------------- | ----------------------- |
| Windows | 2.2.1 | 1.0.0 |
| macOS | 2.2.1 | 1.0.0 |
| Android | 1.12 | 1.0.0 |
| Android on ChromeOS | 1.12 | 1.0.0 |
| iOS | 3.8 | 3.6 |
If you have the base ZDX Module version with the respective Zscaler Client Connector version per OS, then you have access to the following in the ZDX Admin Portal:
- Dashboard
- Analytics
- Applications
- Users
- Configuration
- Administration
- Alerts
- Search
- Activation
- Profile
Specific features (e.g., Software Inventory) require a later version compatibility or they are not available to the OS (e.g., Software and Device Inventory is unavailable for Android).
Supported Versions & Feature Compatibility
Some ZDX features require a Zscaler Client Connector version for certain OS as indicated. The feature version compatibility is applicable to later versions (e.g., Software and Device Inventory requires a Zscaler Client Connector version 3.7.1.56 or later for Windows). If your organization does not meet the required feature version compatibility, upgrade your Zscaler Client Connector or ZDX Module as required.
[]Adaptive Mode
The required version compatibility for the [Adaptive Mode](/zdx/about-adaptive-mode) feature is:
| OS | Zscaler Client Connector Version | ZDX Module Version |
| --- | -------------------------------- | ------------------ |
| Windows | 3.4 | 2.3 |
| macOS | 3.2 | 2.3.1 |
[]Diagnostics
The [Diagnostics](/zdx/about-diagnostics) feature consists of multiple types of Diagnostics. Version compatibility is specific to the Diagnostics type and OS.
Windows
| Type | Zscaler Client Connector Version | ZDX Module Version |
| ---- | -------------------------------- | ------------------ |
| Deep Tracing | 3.1.0.103 | 2.0.0.21 |
| Hi-Fi Cloud Path | 4.2 | 4.1 |
| Bandwidth Test | 3.9 | 3.8 |
| Bandwidth Test with Destination Network Address Translation (DNAT) Details | N/A | 4.4 |
| Packet Capture Probing | 3.9 | 3.5 |
macOS
| Type | Zscaler Client Connector Version | ZDX Module Version |
| ---- | -------------------------------- | ------------------ |
| Deep Tracing | 3.0.0.144 | 2.0.0.15 |
| Hi-Fi Cloud Path | 4.5.1 | 4.4 |
| Bandwidth Testing | 4.3.1 | 3.9 |
| Packet Capture Probing | 3.6 | 3.5 |
Android and Android on ChromeOS
| Type | Zscaler Client Connector Version | ZDX Module Version for Windows |
| ---- | -------------------------------- | ------------------------------ |
| Deep Tracing | 3.7 | 3.2 |
[]Device Events Reports
The required version compatibility for the [Device Events reports](/zdx/viewing-device-events-reports) are:
| Type | OS | Zscaler Client Connector Version | ZDX Module Version |
| ---- | --- | -------------------------------- | ------------------ |
| System Crashes | Windows | 4.5 | 4.5 |
| Software Crashes | Windows | 4.5 | 4.2 |
| macOS | 4.5.1 | 4.4 |
[]Software and Device Inventory
The required version compatibility for [Device Inventory](/zdx/viewing-device-inventory), [Software Inventory](/zdx/viewing-software-inventory), and [Configuring Software Inventory Data Collection](/zdx/configuring-inventory-settings#SoftwareInventoryDataCollection) is:
| OS | Zscaler Client Connector Version | ZDX Module Version |
| --- | -------------------------------- | ------------------ |
| Windows | 3.7.1.56 | 3.3.0.50 |
| macOS | 3.6 | 3.3.2 |
[]Wi-Fi Data Collection
The required version compatibility for [Wi-Fi data collection](/zdx/configuring-inventory-settings#Wi-Fi) of the [Wi-Fi Dashboard](/zdx/monitoring-wi-fi-dashboard) is:
| OS | Zscaler Client Connector Version | ZDX Module Version |
| --- | -------------------------------- | ------------------ |
| Windows | 4.5.0.1 | 4.5.0.1 |
[]Process Inventory
The required version compatibility for [Process Inventory](/zdx/viewing-process-inventory) and [Configuring Process Inventory CPU Incidents](/zdx/configuring-inventory-settings#ProcessInventoryCPUIncidents) is:
| OS | Zscaler Client Connector Version | ZDX Module Version |
| --- | -------------------------------- | ------------------ |
| Windows | 3.9.0.189 | 3.8.0.37 |
| macOS | 3.6 | 3.5 |
[]Software Patch Inventory
The required version compatibility for [Software Patch Inventory](/zdx/viewing-software-patch-inventory) is:
| **OS** | **Zscaler Client Connector Version** | **ZDX Module Version** |
| ------ | ------------------------------------ | ---------------------- |
| Windows | 3.9 | 4.0 |
[]Self Service
The required version compatibility for [Self Service](/zdx/monitoring-self-service-dashboard) and [Configuring Self Service Settings](/zdx/configuring-self-service-settings) is:
| **OS** | **Zscaler Client Connector Version** | ZDX Module Version |
| ------ | ------------------------------------ | ------------------ |
| Windows | 4.4 | 4.0.1 |
| macOS | 4.3.1 | 3.9 |
[]ZDX Autosense for Call Quality
ZDX Autosense feature is available for [Microsoft Teams](/zdx/configuring-microsoft-teams-call-quality-zdx), [Webex](/zdx/configuring-webex-call-quality-zdx), and [Zoom](/zdx/configuring-zoom-call-quality-zdx). Version compatibility is specific to the Call Quality and OS.
Windows
| Call Quality | Zscaler Client Connector Version | ZDX Module Version |
| ------------ | -------------------------------- | ------------------ |
| Microsoft Teams | 4.3 | 3.8 |
| Webex | 4.3.0.121 | 3.8.0.80 |
| Zoom | 4.3 | 3.8 |