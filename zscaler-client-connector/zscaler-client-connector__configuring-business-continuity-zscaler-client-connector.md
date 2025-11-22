# Configuring Business Continuity in Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/configuring-business-continuity-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1514421.pdf

Business Continuity in Zscaler Private Access (ZPA) allows users to continue to access applications during ZPA-related cloud outages or Internet Service Provider (ISP) outages. You can configure Business Continuity in Zscaler Client Connector so that both enrolled and new users can connect to a Private Cloud during an outage.
To learn more, see [About Business Continuity](/zscaler-client-connector/about-business-continuity).
Business Continuity is available only for Zscaler Client Connector version 4.6 and later for Windows.
If Business Continuity is enabled, enrolled users automatically access the Private Cloud if there is an outage and continue to have access to their applications based on their app profile. During the outage, the **Update App** and **Update Policy** options are not available in the About section of the [More window in Zscaler Client Connector](/zscaler-client-connector/viewing-information-about-zscaler-client-connector).
You can also enroll new users in Zscaler Client Connector and provide access to applications during the outage even though the Zscaler Client Connector Portal and the cloud are unavailable.
Before an outage, you must download a configuration file with Business Continuity settings and a public key. You can pass the file and public key to Zscaler Client Connector in an installer option. The app can then authenticate with the Private Cloud and apply a stored app profile to the user to provide application access. The stored app profile from the configuration file is used until the config profile can be retrieved from the Zscaler back-end servers.
Configuring Business Continuity
To configure Business Continuity:
- Ensure that the Business Continuity settings are configured in the ZPA Admin Portal.
- Enable **Configure ZPA Business Continuity** in the [app profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles).
- Download the config file and copy the thumbprint from the [Business Continuity page](/zscaler-client-connector/about-business-continuity).
Enrolling a New User During an Outage
To enroll a new user during a ZPA-related cloud outage or Internet Service Provider (ISP) outage, install Zscaler Client Connector using an MDM or GPO and pass the downloaded configuration file and the public key. To learn more, see [Customizing Zscaler Client Connector with Install Options for EXE](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-exe) and [Customizing Zscaler Client Connector with Install Options for MSI](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-msi).