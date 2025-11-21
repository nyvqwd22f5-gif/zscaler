# Zscaler Client Connector Resource Usage
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-client-connector-resource-usage
PDF: https://help.zscaler.com/pdf/com/en/1333281.pdf

When Zscaler Client Connector is installed on your device, it uses system resources such as memory, CPU, and battery. For mobile devices, the app uses cellular data when you are not connected to Wi-Fi.
Android, Android on ChromeOS, and iOS
For the Android, Android on ChromeOS, and iOS versions of Zscaler Client Connector, you can expect the app to:
- Use approximately 20 MB of storage space for installation.
- Use between 10 and 20% of your device's battery life.
The battery usage applications on these platforms are not entirely accurate. They measure battery drain over time and look at which processes ran during that usage. However, because Zscaler Client Connector always forwards traffic, its perceived battery usage percentage can be much higher. The best way to measure battery drain is to leave the device running with and without Zscaler Client Connector, and time how long it takes the battery to drain to a certain percentage.
Other external factors can affect battery life. For example, in an area with poor cellular reception, the device's radio consumes more power in an attempt to receive a better signal.
Windows and macOS
For the Windows and macOS versions of Zscaler Client Connector, you can expect the app to:
- Use approximately 200 MB of disk for installation and additional space for logging. The amount of MB used for logging depends on what you defined for log retention.
- Have no noticeable impact on your device's battery life.
- Use between 70 to 150 MB of RAM. The RAM usage may be higher on VDI systems.
- Use between 0 to 5% CPU, which can increase temporarily when Zscaler Client Connector processes traffic.
Linux
For Linux, you can expect the app to use:
- Approximately 181 MB of storage space for installation.
- Approximately 0.5% of RAM.
- 0 to 5% CPU when idle and 7 to 15% CPU during traffic.