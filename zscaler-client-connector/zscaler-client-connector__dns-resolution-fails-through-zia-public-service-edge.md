# DNS Resolution Fails through the ZIA Public Service Edge
Source: https://help.zscaler.com/zscaler-client-connector/dns-resolution-fails-through-zia-public-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1532622.pdf

Zscaler Client Connector version 4.0 for Android has a known issue where DNS resolution through the ZIA Public Service Edge would sometimes fail if DNS domains aren’t added to the Domain Inclusion field in [App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
As a workaround, you can specify a wildcard (*) in the Domain Inclusion field in [App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles):
- In the Zscaler Client Connector Portal, go to **App Profiles** and select **Android**.
- Click **Add Android Policy**. The **Add Android Policy** window appears.
- In the **Traffic Steering** section, click the **DNS **tab.
- In the **Domain Inclusion** field, enter a wildcard (*) to have Zscaler Client Connector tunnel all DNS domains through Zscaler Internet Access (ZIA).