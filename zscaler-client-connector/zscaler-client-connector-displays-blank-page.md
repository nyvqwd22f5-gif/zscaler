# Zscaler Client Connector Displays Blank Page
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-client-connector-displays-blank-page
PDF: https://help.zscaler.com/pdf/com/en/1505346.pdf

Zscaler Client Connector versions 4.3, 4.4, and 4.5 for Windows have a known issue if WebView2 is enabled where embedded web pages can appear blank if display settings have changed or if displays are attached or removed from the system. The issue affects SAML authentication during login, reauthentication, acceptable use policy, license agreement, data loss protection notifications, and self-service notifications.
You can temporarily resolve the issue by restarting the application (terminate the ZSATray.exe process via Task Manager) or restarting the system. The issue is fixed on Zscaler Client Connector version 4.3.0.255, version 4.4.0.346, and version 4.5.0.296 for Windows.