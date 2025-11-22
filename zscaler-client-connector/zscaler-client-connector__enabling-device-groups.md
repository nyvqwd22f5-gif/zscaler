# Enabling Device Groups
Source: https://help.zscaler.com/zscaler-client-connector/enabling-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1531080.pdf

This option applies to Zscaler Client Connector version 3.7 and later for Android and Zscaler Client Connector version 4.4 and later for iOS.
The Use Device Groups in Service Entitlement feature allows Zscaler service to be enabled selectively only on managed devices that meet specific posture configurations during enrollment, ensuring enforcement of policies solely on company-controlled devices. Applies to Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), and Zscaler Digital Experience (ZDX). Zscaler Client Connector evaluates device posture during enrollment and keep-alive intervals, dynamically enabling or disabling services based on user groups and device group configurations set in the Zscaler Client Connector Portal.
- [Android](#android)
- [iOS](#ios)
[]To enable **Use Device Groups in Service Entitlement **for Android:
- In the Zscaler Client Connector Portal, go to **Administration** > **Platform Settings**.
- Click the **Android** tab.
- Enable **Use Device Groups in Service Entitlement**.
![Platform Settings Use Device Groups in Service Entitlement](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-platform-settings/Platform_Settings_Use%20Device%20Groups_Android.png)
[]To enable **Use Device Groups in Service Entitlement **for iOS:
- [Create Device Groups](/zscaler-client-connector/create-device-groups).
- In the Zscaler Client Connector Portal, go to **Administration** > **Platform Settings**.
- Click the **iOS** tab.
- Enable **Use Device Groups in Service Entitlement**.
- Click **Save**.
- Follow the applicable directions for enabling Zscaler Service Entitlements based on Device Groups. To learn more, see [About Zscaler Service Entitlement](/zscaler-client-connector/about-zscaler-service-entitlement).
![ios platform settings](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-device-groups-doc-60440/platform-settings-ios_0.png)