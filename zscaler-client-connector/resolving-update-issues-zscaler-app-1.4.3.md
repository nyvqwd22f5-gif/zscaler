# Resolving Update Issues to Zscaler Client Connector 1.4.3
Source: https://help.zscaler.com/zscaler-client-connector/resolving-update-issues-zscaler-app-1.4.3
PDF: https://help.zscaler.com/pdf/com/en/1334636.pdf

Starting on December 4th, 2018 at 3:00PM PST, users on Zscaler Client Connector  versions earlier than 1.4.3 will see **Connection Error** in the **Private Access** section of Zscaler Client Connector and will be unable to connect to ZPA. You must update Zscaler Client Connector to version 1.4.3 on your users’ devices before December 4th in order to avoid application access issues.
Zscaler Client Connector 1.4.3 is available for download from your organization's [Zscaler Client Connector Portal](/zscaler-client-connector/downloading-zscaler-app). If you do not see this version in your Zscaler Client Connector Portal, contact Zscaler Support.
If Zscaler Client Connector is unable to update, refer to the following recommendations:
- The most common issues are usually due to antivirus software on the device. So, check the antivirus software logs to investigate this as a probable cause. Also, ensure that Zscaler Client Connector 1.4.3 installer is placed on the allowlist in the antivirus software.
- For MDM, SCCM, and GPO-based upgrades, check the settings, configurations, installation parameters, and groups of impacted users and devices.
- For Zscaler Client Connector Portal based updates, ensure that user devices are able to connect to Amazon CloudFront to download the new version. Make sure users can ping and telnet into d32a6ru7mhaq0c.cloudfront.net from their devices.
- Ensure the local firewall on the device is allowing access to CloudFront.
- Ensure the network firewall is allowing access to the CloudFront domain or subnet (i.e., d32a6ru7mhaq0c.cloudfront.net).
- A full list of IPs can be found on your Zscaler cloud IPs page. So your firewall should be white-listing one of the following IPs:
- [config.zscaler.com/zscaler.net/zscaler-app](http://config.zscaler.com/zscaler.net/zscaler-app)
- [config.zscaler.com/zscloud.net/zscaler-app](http://config.zscaler.com/zscloud.net/zscaler-app)
- [config.zscaler.com/zscalerone.net/zscaler-app](http://config.zscaler.com/zscalerone.net/zscaler-app)
- [config.zscaler.com/zscalertwo.net/zscaler-app](http://config.zscaler.com/zscalertwo.net/zscaler-app)
- [config.zscaler.com/zscalerthree.net/zscaler-app](http://config.zscaler.com/zscalerthree.net/zscaler-app)
- Ensure there are no configuration errors on Zscaler Client Connector Portal.
After following the above recommendations, if you still cannot resolve your CloudFront access issues, you can use your MDM, SCCM, or GPO to update the remaining devices. If you are using MDM, SCCM, or GPO to update devices that have not yet upgraded, you must use the same installation parameters that were used during the original Zscaler Client Connector installation.
- If you are experiencing update issues on a macOS that was running version 1.4.0.187, it will not update from Zscaler Client Connector Portal. You must use your MDM to update, and be sure to use the same installation parameters used in the original Zscaler Client Connector installation.