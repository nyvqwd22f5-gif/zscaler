# Configuring Business Continuity Settings
Source: https://help.zscaler.com/zpa/configuring-business-continuity-settings
PDF: https://help.zscaler.com/pdf/com/en/1507016.pdf

Business Continuity provides access to your applications during ZPA-related cloud outages or Internet Service Provider (ISP) outages. Configuring the [Business Continuity settings](#bcsettings) in ZPA is the first step in enabling Business Continuity for your organization. To learn more about additional prerequisites and an overview of the feature, see [Understanding Business Continuity](/zpa/understanding-business-continuity).
[]FQDN or SNI in Business Continuity
Business Continuity requires DNS servers hosted in your organization's infrastructure to resolve the fully qualified domain names (FQDNs).
If you are using [Zscaler-managed Business Continuity](/zia/understanding-zscaler-managed-business-continuity-cloud), this section can be skipped as Zscaler provides a Business Continuity domain (e.g., tenant_name.zpa.zsbcs.net).
The following table shows examples of FQDNs that are used in Business Continuity.
-
-
-
-
-
| Component | FQDN |
| --------- | ---- |
| Zscaler Client Connector | The initial DNS request to get the Private Cloud Controller IP addresses (e.g., `any2bcp.<business_continuity_domain>`)The TLS connection to the Private Cloud Controller for IdP redirection (e.g., `bcpsp.<business_continuity_domain>`)The TLS connection to the Private Cloud Controller for the SAML request (e.g., `bcpsp-<pcc gid>.<business_continuity_domain>`) |
| ZPA Private Service Edges and App Connectors | The DNS request to get the Private Cloud Controller's IP address is `co2bcp.<business_continuity_domain>` for App Connectors and `pb2bcp.<business_continuity_domain>` for ZPA Private Service Edges.Based on the DNS resolution, the ZPA Private Service Edge or App Connectors establish a TLS connection to the Private Cloud Controller. |
The following table shows examples of Server Name Indication (SNI) that are used in Business Continuity.
-
-
-
-
| Component | SNI |
| --------- | --- |
| Zscaler Client Connector TLS connections to the Private Cloud Controller | Enrolled users' SNI is `c2.<business_continuity_domain>`New users' SNI is `c2site.<business_continuity_domain>` |
| Zscaler Client Connector TLS connections to the ZPA Private Service Edge | Enrolled users' SNI is `c2.<business_continuity_domain>`New users' SNI is `c2site.<business_continuity_domain>` |
[]Configuring Business Continuity Settings
To configure Business Continuity settings for ZPA:
- Go to **Configuration & Control **> **Business Continuity **> **Settings**.
- On the **Settings** page, configure the following Business Continuity settings as needed:
- [General Information](#generalInfo)
- [Configuration Backup](#configBackup)
- [Control Channel Recovery](#controlChannelRecovery)
- [Business Continuity IdP Configuration](#idpConfiguration)
- [Service Provider Information](#service-provider)
- Click **Save**.
-
[]**Business Continuity Domain**: Enter a valid domain name for Business Continuity. The **Business Continuity Domain **is used by the following components:
- Zscaler Client Connector to contact the Private Cloud Controller and ZPA Private Service Edges (e.g., any2bcp.<business_continuity_domain>, c2site.<business_continuity_domain> for new users, and c2.<business_continuity_domain> for enrolled users)
- App Connectors for control channel to Private Cloud Controller (e.g., co2bcp.<business_continuity_domain>)
- ZPA Private Service Edges for control channel to Private Cloud Controller (e.g., pb2bcp.<business_continuity_domain>)
- Private Cloud Controllers for authenticating users and validating assertions received from the IdP (e.g., bcpsp.<business_continuity_domain>)
- A Business Continuity SP FQDN is generated per Private Cloud Controller for the authentication of users in Business Continuity (e.g., bcpsp-<pccgid>.<business_continuity_domain>)
To learn more, see [FQDN or SNI in Business Continuity](#fqdnsnibc).
Changing the **Business Continuity Domain **initiates a new enrollment process for Private Cloud Controllers, and updates the **SP Assertion Consumer Service URL** and **Entity ID**.
-
**New User Enrollment**: Enable to enroll new users during Business Continuity.
Mutual TLS authentication between users and ZPA Private Service Edges is not supported for new user enrollment during Business Continuity.
[]**Configuration Backup**: Enable to back up configuration data used by App Connectors and Private Service Edges to an SQLite database, configuration files (image snapshots, metadata, and version number), and configuration snapshots (cryptographic and configuration files) used by the Private Cloud Controller. By default, this is disabled.
-
**Maximum Number of Backups**: Enter the maximum number of backup copies to retain, and ensure that there is enough disk space to store the selected number of backups. The default is 15 backups, and a maximum of 100 backups can be created.
Ensure that you provision enough disk space to store the selected number of backups.
-
**Backup Path**: Enter the path to store backups of database and configuration files for the Private Cloud Controller. A new drive must be mounted, or an NFS/SMB must be shared for the backup path.
If you change the backup path, ensure that the path is owned by `zscaler:zscaler`. For example, if you change the backup path to `/home/backup` then you need to ensure that the `zscaler` user has Read/Write permissions to `/home/backup`. To add the `zscaler` user as the owner of the backup path, enter the following command: `chown zscaler:zscaler /home/backup`.
- **Backup Frequency**: Select how frequently a backup occurs (**Hourly**, **Daily**, or **Weekly**). By default, **Daily** is selected.
- **Backup Schedule**: Select when to create a backup copy based on the backup frequency selected.
- For **Hourly**, select a range between 4, 8, 12, and 24 hours. By default, **8 Hours** is selected. The Private Cloud Controller calculates the hours based on the time backups are enabled.
- For **Daily**, select a time based on a 15-minute interval. By default, **12 AM** is selected.
- For **Weekly**, select a day and time. By default, **Sunday at 12 AM** is selected.
The backup schedule is based on the time zone of the Private Cloud Controller.
To learn more about restoring Private Cloud Controller backups, see [Restoring Private Cloud Controller Backups](/zpa/restoring-private-cloud-controller-backups).
- []**Maximum Wait Time to Enter Business Continuity Mode (App Connectors and Private Service Edges)**: Enter an integer to specify the duration (in minutes or hours) that App Connectors and ZPA Private Service Edges must wait before switching to Business Continuity. You can select the duration as **Minute(s)** or **Hour(s) **from the drop-down menu. By default, **2 Minute(s)** is selected. The minimum limit for this field is 1 minute. The maximum limit for this field is 8 hours, or 480 minutes.
- **Switch Users to Public Cloud**: Select **Time-Based **to switch users to the public cloud after the maximum wait time to exit Business Continuity. Select **Automatic** to switch users to the public cloud when there are no active connections. By default, this is disabled.
- **Maximum Wait Time to Exit Business Continuity Mode (Users)**: Enter an integer to specify the duration (in minutes, hours, or days) that ZPA Private Service Edges must wait before sending a message to Zscaler Client Connector to try and re-establish the control and data channel to the ZTE. You can select the duration as **Minute(s)**, **Hour(s)**, or **Day(s) **from the drop-down menu. By default, **60 Minute(s)** is selected. The minimum supported value is 10 minutes. The maximum limit for this field is 7 days, 168 hours, or 10,080 minutes. This field is visible only after **Switch Users to Public Cloud** is enabled.
- []**Existing IdP for Authentication**: Select this option to use the same IdP configuration that is configured for user authentication for normal operations under **Authentication > User Authentication > IDP Configuration**. To learn more, see [About IdP Configuration](/zpa/about-idp-configuration).
- **New IdP for Authentication**: Select this option to configure a new IdP for authenticating users in Business Continuity. If you select a new IdP, complete the following:
- **IdP Metadata File**: Upload the IdP metadata file used to authenticate users for Business Continuity. Click **Upload** **File** to navigate to the IdP metadata file.
- **IdP Certificate**: The uploaded IdP certificate. Click the **Copy **icon to copy the IdP certificate to your clipboard. This field is autopopulated with the IdP certificate details from your IdP configuration.
- **Single Sign-On URL**: The single sign-on URL for the IdP configuration. Click the **Copy** icon to copy the single sign-on URL to your clipboard. This field is autopopulated with the single sign-on URL details from your IdP configuration.
- **IdP Entity ID**: The IdP entity ID for the IdP configuration. Click the **Copy **icon to copy the IdP entity ID to your clipboard. This field is autopopulated with the IdP entity ID from your IdP configuration.
-
[]If you selected an existing IdP under **Business Continuity IdP Configuration**, the **Assertion Consumer Service URL** and **Entity ID** fields are populated with the user authentication IdP configuration information to use in Business Continuity.
[See image.](#BusinessContinuity-ExistingIdP)
-
If you selected a new IdP under **Business Continuity IdP Configuration**, provide the following information:
- **Metadata**: The service provider metadata based on your IdP configuration and the entered **Business Continuity Domain**. Click **Download Metadata **to download the service provider metadata.
- **Assertion Consumer Service URL**: The service provider URL based on the entered **Business Continuity Domain**. This text is read-only. Click the **Copy **icon to copy the service provider URL.
- **Certificate**: The service provider certificate based on the entered **Business Continuity Domain**. Click **Download Certificate** to download the service provider certificate.
- **Entity ID**: The service provider entity ID based on the entered **Business Continuity Domain**. Click the **Copy **icon to copy the service provider entity ID.
[See image.](#BusinessContinuity-NewIdP)
[]
![Viewing the Business Continuity Settings Page with Existing IdP Selected](/downloads/zpa/business-continuity-management/configuring-business-continuity-settings/zpa-configuring-business-continuity-settings_0.png)
[]
![Viewing the Business Continuity Settings Page with New IdP Selected](/downloads/zpa/business-continuity-management/configuring-business-continuity-settings/zpa-business-continuity-settings-new-idp_1.png)