# Viewing Information About Zscaler Endpoint DLP on Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/viewing-information-about-zscaler-endpoint-dlp-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1464141.pdf

This article provides an overview of the Data Protection window on Zscaler Client Connector. This window features connectivity information and troubleshooting steps for the Data Protection feature on Windows and macOS devices.
![Data Protection window](/downloads/client-connector/end-user-guide/viewing-information-about-zscaler-endpoint-dlp-zscaler-client-connector/data-protection-on-zcc.jpg)
Connectivity
-
**Service Status**: Displays the app connection status. Click **Turn Off** if you want to disable the Data Protection service while remaining logged in to the app. The Data Protection service is disabled until you click **Turn On**. You can disable the service using the [Password to Disable Endpoint DLP](/zscaler-client-connector/configuring-zscaler-client-connector-profiles#windows) in App Profiles or by using a One-Time Password (OTP).
Admins can access an OTP code from the Zscaler Client Connector Portal:
- Go to **Enrolled Devices **> **Device Details**.
-
Under **Compliance Status**, copy the password listed under **Disable Endpoint DLP OTP**.
[See image.](#disable-otp)
- **Product Version: **Displays the current version of the Data Protection feature.
Troubleshoot
-
**Request exemption**: Users that are blocked by the Endpoint DLP due to a rule violation can request to be exempted from the block action, and instead be monitored. Clicking this option prompts you to enter a password.
Admins can access an OTP code from the Zscaler Client Connector Portal:
- Go to **Enrolled Devices **> **Device Details**.
- Under **Compliance Status**, copy the password listed under **Disable Endpoint DLP OTP**.
The OTP also works if you are in offline mode. Exemptions are granted for 12 hours.
- **Update DLP Policy**: Click to manually refresh your endpoint DLP policy. The DLP policy refreshes every 15 minutes. If you want to update immediately, click **Update DLP Policy**.
- **Open Quarantine Folder**: Contains the files that moved to this folder as a result of a block action for the personal cloud storage rules (e.g., Dropbox) or by other channels where the file source information is missing (e.g., copying an extract ZIP file to a removable storage device).
[]![Disable Endpoint DLP OTP](/downloads/client-connector/end-user-guide/viewing-information-about-zscaler-endpoint-dlp-zscaler-client-connector/OTP-in-enrolled-device.jpg)