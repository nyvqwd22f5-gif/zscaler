# About Business Continuity
Source: https://help.zscaler.com/zscaler-client-connector/about-business-continuity
PDF: https://help.zscaler.com/pdf/com/en/1514406.pdf

Business Continuity in Zscaler Private Access (ZPA) allows users to continue to access applications during ZPA-related cloud outages or Internet Service Provider (ISP) outages. Zscaler Client Connector connects users to a Private Cloud to help achieve uninterrupted access without manual intervention.
To learn more, see [Understanding Business Continuity](/zpa/understanding-business-continuity) and [Configuring Business Continuity in Zscaler Client Connector](/zscaler-client-connector/configuring-business-continuity-zscaler-client-connector).
Business Continuity is available only for Zscaler Client Connector version 4.6 and later for Windows.
Business Continuity provides the following benefits and enables you to:
- Provide existing users who are enrolled in Zscaler Client Connector continual access to their approved applications during an outage.
- Enroll new users in Zscaler Client Connector and provide secure access to applications while the Zscaler Client Connector Portal and the cloud are unavailable.
About the Business Continuity Page
On the Business Continuity page (Administration > Business Continuity), you can do the following:
- View the latest Business Continuity settings from ZPA:
- **Private Cloud Controller DNS**: The initial DNS request to get the Private Cloud Controller IP addresses (e.g., any2bcp.<business_continuity_domain>).
- **Private Cloud Controller SNI**: The Server Name Indication (SNI) used to make TLS connections to the Private Cloud Controller and the ZPA Private Service Edge (e.g., c2.<business_continuity_domain> for enrolled users or c2site.<business_continuity_domain> for new users).
- **Business Continuity SP URL**: The service provider URL for the Business Continuity Domain.
- **Business Continuity SP CA Certificate**: The service provider certificate for the Business Continuity Domain.
- Click **Sync** to retrieve the latest Business Continuity settings from the ZPA Admin Portal.
- Click **Download Config** to download a configuration file with these settings to use when installing Zscaler Client Connector for users.
- Click **Copy Thumbprint** to copy the public key to use when installing Zscaler Client Connector for a new user.
![Business continuity settings](/downloads/zscaler-client-connector/zscaler-client-connector-profile-management/about-business-continuity/zclient-connector-business-continuity.png)