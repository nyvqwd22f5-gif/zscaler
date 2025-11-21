# Understanding User Status Log Fields
Source: https://help.zscaler.com/zpa/understanding-user-status-log-fields
PDF: https://help.zscaler.com/pdf/com/en/1483956.pdf

The Log Streaming Service (LSS) can send User Status log information to any third-party log analytics tool. By default, the User Status log type includes the fields listed in the following table for each log template (i.e., CSV, JSON, TSV). While configuring your log receiver, you can edit the default log stream content to capture only specific fields, and create a Custom log template.
- [View an example User Status log](#UserStatusExample)
The following table includes descriptions and supported field format specifications for each field within the template. To learn more about the format specifications listed for each field, including examples, see [Log Field Format Specifications](/zpa/understanding-log-stream-content-format).
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Field | Description | Supported Field Format Specifications |
| ----- | ----------- | ------------------------------------- |
| LogTimestamp | Timestamp when the log was generated | %[OPT]s%[OPT]j%[OPT]J |
| Customer | The customer name | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Username | The user name | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| SessionID | The TLS session ID | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| SessionStatus | The status of the session. The expected values for this field are:ZPN_STATUS_AUTHENTICATED: User successfully authenticated in ZPAZPN_STATUS_AUTH_FAILED: User failed to authenticate in ZPAZPN_STATUS_DISCONNECTED: User connected from a ZPA Public Service Edge or ZPA Private Service Edge | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Version | The Zscaler Client Connector version | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ZEN | The ZPA Public Service Edge that was selected for the connection | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| CertificateCN | The certificate common name | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| PrivateIP | The private IP address of the Zscaler Client Connector | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| PublicIP | The public IP address of the Zscaler Client Connector | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Latitude | The latitude coordinate of the Zscaler Client Connector location | %[OPT]f%[OPT]o |
| Longitude | The longitude coordinate of the Zscaler Client Connector location | %[OPT]f%[OPT]o |
| CountryCode | The country code of the Zscaler Client Connector location | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| TimestampAuthentication | Timestamp in microseconds when the Zscaler Client Connector was authenticated | %[OPT]s%[OPT]j%[OPT]J |
| TimestampUnAuthentication | Timestamp in microseconds when the Zscaler Client Connector was unauthenticated | %[OPT]s%[OPT]j%[OPT]J |
| TotalBytesRx | The total bytes received | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| TotalBytesTx | The total bytes transmitted | %[OPT]d%[OPT]x%[OPT]f%[OPT]o |
| Idp | The name of the identity provider (IdP) as configured in the ZPA Admin Portal | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Hostname | The name of the device as reported by the Zscaler Client Connector | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| Platform | The platform on the device as reported by the Zscaler Client Connector | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ClientType | The client type for the request (i.e., Zscaler Client Connector, ZPA LSS, or Web Browser) | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| TrustedNetworks | The unique IDs for the trusted networks that the Zscaler Client Connector has determined for this device | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| TrustedNetworksNames | The names for the trusted networks that the Zscaler Client Connector has determined for this device | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| SAMLAttributes | The list of SAML attributes reported by the IdP | %[OPT]s%[OPT]j%[OPT]J |
| PosturesHit | The posture profiles that the Zscaler Client Connector verified for this device | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| PosturesMiss | The posture profiles that the Zscaler Client Connector failed to verified for this device | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| ZENLatitude | The latitude coordinates for the ZPA Public Service Edge | %[OPT]f%[OPT]o |
| ZENLongitude | The longitude coordinates for the ZPA Public Service Edge | %[OPT]f%[OPT]o |
| ZENCountryCode | The country code for the ZPA Public Service Edge | %[OPT]s%[OPT]j%[OPT]J%[OPT]o |
| FQDNRegistered | The status of the hostname for the client-to-client connection. The expected values for this field are true or false. | %[OPT]s |
| FQDNRegisteredError | The status of the registered hostname. The expected value if the hostname matches the regular expression is FQDN_MATCH. The expected values if the hostname does not match the regular expression are:FQDN_NO_MATCH: The hostname does not match with the configured regular expressionFQDN_BAD_SCHEMA: Client-to-client communication is disabled for the ZPA Public Service EdgeFQDN_BAD_REGEX: The configured regular expression in the ZPA Admin Portal is incorrectFQDN_TOO_MANY_REGEX: Invalid regular expression configuration due to multiple configured regular expressionsFQDN_NO_ENTRIES: Your Admin has not configured a regular expression in the ZPA Admin PortalFQDN_EMPTY: The FQDN received from the Zscaler Client Connector is null or emptyBROKER_NOT_ENABLED: Client-to-client communication is disabled for the ZPA Public Service EdgeCUSTOMER_NOT_ENABLED: Client-to-client communication is disabled for the current customer | %[OPT]s |
| City | The city of the client | %[OPT]s%[OPT]j |
| MicroTenantID | The Microtenant ID of the user accessing the application | %[OPT]s%[OPT]j |
[]{"LogTimestamp": "Fri May 31 17:34:48 2019","Customer": "ANZ Team/zdemo in beta","Username": "ZPA LSS Client","SessionID": "cKgzUERSLl09Y+ytH8v5","SessionStatus": "ZPN_STATUS_AUTHENTICATED","Version": "19.12.0-36-g87dad18","ZEN": "broker1b.pdx2","CertificateCN": "slogger1b.pdx2.zpabeta.net","PrivateIP": "","PublicIP": "34.216.108.5","Latitude": 45.000000,"Longitude": -119.000000,"CountryCode": "US","TimestampAuthentication": "2019-05-29T21:18:38.000Z","TimestampUnAuthentication": "","TotalBytesRx": 31274866,"TotalBytesTx": 25424152,"Idp": "Example IDP Config","Hostname": "DESKTOP-2K299HC","Platform": "windows","ClientType": "zpn_client_type_zapp","TrustedNetworks": "TN1_stc1","TrustedNetworksNames": "145248739466947538","SAMLAttributes": "myname:jdoe,myemail:jdoe@zscaler.com","PosturesHit": "sm-posture1,sm-posture2","PosturesMisses": "sm-posture11,sm-posture12","ZENLatitude": 47.000000,"ZENLongitude": -122.000000,"ZENCountryCode": "", "FQDNRegistered": "0","FQDNRegisteredError": "","City": "San Jose", "MicroTenantID": "145257480799129312"}