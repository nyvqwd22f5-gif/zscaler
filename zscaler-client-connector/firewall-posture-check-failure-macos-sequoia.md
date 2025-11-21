# Firewall Posture Check Failure on macOS Sequoia
Source: https://help.zscaler.com/zscaler-client-connector/firewall-posture-check-failure-macos-sequoia
PDF: https://help.zscaler.com/pdf/com/en/1505531.pdf

Zscaler Client Connector versions for macOS have a known issue with [firewall posture checks](/zscaler-client-connector/configuring-device-posture-profiles) on macOS Sequoia. Due to changes in how macOS stores firewall configuration in macOS Sequoia, the firewall posture check for Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) fails. If you are using the firewall posture check today, it is recommended to remove the firewall posture check from the policy until a fix is available.
Customers using earlier versions of Zscaler Client Connector must upgrade to Zscaler Client Connector version 4.2.0.294, 4.3.0.237, or 4.3.1.56 to ensure the fix is applied.