# Web Insights Logs: Filters
Source: https://help.zscaler.com/zia/web-insights-logs-filters
PDF: https://help.zscaler.com/pdf/com/en/1401016.pdf

Filters define the traffic information that you view in your Web Insights Logs. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Also, certain filters support additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform string match, like **Advanced** **Threat Category** and others.
- There are certain filter combinations that appear together in Insights Logs when applied, but don't appear together in Insights. For example, the **Department** and **Location** filters appear together in Insights Logs when applied, but don't appear together in Insights.
- There are certain filter values where control is handed over to the firewall. For example, when the filter values are set to Tunnel or Tunnel SSL, control is handed to the firewall. The firewall completes the remaining inspection and applies a policy according to the rules. While these filter values indicate that control is handed over to the firewall, it is recommended that you always check the firewall logs to confirm the same.
Following are the web log filters you can select:
- [Adaptive Access Profile](#acp)
- [Advanced Threat Category](#ATSC)
- [ALPN Protocol](#ALPN)
- [Allowed File Type Rule](#ALLOWED_FT_POLICY)
- [App Instance Level 1](#App_inst_lev1)
- [App Instance Level 2](#App_inst_lev2)
- [App Instance Level 3](#App_inst_lev3)
- [Application Activity](#AA)
- [Application Segment](#AS)
- [Application Status](#App_Status)
- [Bandwidth Class](#BWClass)
- [Bandwidth Rule](#BWR)
- [Blocked Policy Type and Rule Name](#PTRN)
- [Bypassed Transaction](#bypassed-transaction)
- [Bypassed Transaction Event Time](#bypassed-transaction-event-time)
- [Certificate Chain Validity](#CCV)
- [Certificate Expiry](#CE)
- [Client Connection Ciphers](#CCC)
- [Client Connection TLS Version](#CCTLS)
- [Client External IP](#CEIP)
- [Client IP](#CIP)
- [Capture](#capture)
- [Client Digital Signature Proposal](#client_digital_sig_proposal)
- [Client Key Exchange Proposal](#client_key_exc_proposal)
- [Client-Side Key Exchange Algorithm](#client_side_key_exc_algo)
- [Client-Side Digital Signature Algorithm](#client_side_dig_sig_algo)
- [Client Source Port](#client-source-port)
- [Client SSL Handshake Failure Aggregate Count](#client-handshake-aggregate-count)
- [Client SSL Handshake Failure Reason](#client-handshake-reason)
- [Cloud Application](#CA)
- [Cloud Application Class](#CAC)
- [Cloud Application Policy Type and Name](#CAPTN)
- [Data Center](#DataCenter)
- [Department](#DEPT)
- [Destination IP Countries](#destination_ip_countries)
- [Device Hostname](#DH)
- [Device Model](#DM)
- [Device Name](#DN)
- [Device OS Type](#DOST)
- [Device OS Version](#DOSV)
- [Device Owner](#DO)
- [DLP Dictionary](#DLPD)
- [DLP Engine](#DLPE)
- [DLP Identifier](#DLPI)
- [DLP MD5](#DLPMD5)
- [DLP Severity](#dlp-severity)
- [Document Type](#download-document-type)
- [Domain Fronted Host Header](#DFHH)
- [Domain Fronted SNI](#DFSNI)
- [Download File Name](#download-file-name)
- [Download File Type](#download-file-type)
- [Download File Type Super Category](#download-file-type-super-category)
- [Download User-Defined File Type](#download-user-defined-file-type)
- [Enrolled Device appversion](#EDAV)
- [External Device ID](#external-device-id)
- [File Share Activity](#FSA)
- [Flow Type](#flow-type)
- [Forwarding Method](#FM)
- [Forwarding Rule](#FR)
- [Gateway IP](#GIP)
- [Gateway Name](#GN)
- [HTTP Header Insertion Profile](#HTTP_HEAD_IN_PR)
- [HTTP Header Profile](#HTTP_HEADER_PR)
- [IM Activity](#IMA)
- [Intermediate CA Protection Type](#intermediate-CA-certificates)
- [Is Destination IP Country Risky?](#is_dest_ip_country_risky)
- [Is Source IP Country Risky?](#is_source_country_risky)
- [Location](#location)
- [Location Group](#location-group)
- [Location Type](#location-type)
- [OCSP Result](#OCSPR)
- [Other DLP Rules](#otherdlprules)
- [Prompt](#prompt)
- [Prompt Classification](#prompt_classification)
- [Protocol](#Proto)
- [Received Bytes](#RB)
- [Referrer Search](#RS)
- [Request Method](#RM)
- [Request Version](#request-version)
- [Response HTTP Version](#response-version)
- [Sandbox](#SB)
- [Sandbox Action](#SBA)
- [Sandbox API Key](#apikey)
- [Sandbox MD5](#SBMD5)
- [Sent Bytes](#SBytes)
- [Server Certificate Self Signed](#SCSS)
- [Server Certificate Validation Type](#SCVT)
- [Server Certificate Validity Period](#SCVP)
- [Server Connection Ciphers](#SCCiphers)
- [Server Connection TLS Version](#SCTLS)
- [Server Destination Port](#serverdestinationport)
- [Server IP](#SIP)
- [Server-Side Key Exchange Algorithm](#server_side_kex_algo)
- [Server-Side Digital Signature Algorithm](#server_side_dig_sign_algo)
- [SHA-256](#sha256)
- [Show Delayed Logs](#SDL)
- [Social Networking Activity](#SNA)
- [Source IP Countries](#source_ip_country)
- [SSL Inspected](#SSLI)
- [SSL Policy Name](#SSLP_Rule)
- [SSL Policy Reason](#SSLPR)
- [Streaming Activity](#SA)
- [Subdocument Type](#SUB_DOC)
- [Suspicious Content](#SusC)
- [Threat Category](#TC)
- [Threat Class](#TClass)
- [Threat Name](#TName)
- [Threat Severity](#threat-severity)
- [Threat Super Category](#TSC)
- [Throttled request bytes](#TRB)
- [Throttled response bytes](#TRESB)
- [Total Bytes](#TB)
- [Traffic Forwarding](#TF)
- [Unscannable Type](#UT)
- [Upload File Name](#upload-file-name)
- [Upload File Type](#upload-file-type)
- [Upload File Type Super Category](#upload-file-type-super-category)
- [Upload User-Defined File Type](#upload-user-defined-file-type)
- [URL Category](#URLCat)
- [URL Class](#URLClass)
- [URL Filtering Policy Name](#URLFPN)
- [URL Search](#URLS)
- [URL Super Category](#URLSC)
- [User](#User)
- [User Agent](#UA)
- [Policy Action](#policy-action)
- [Webmail Activity](#WEBACTY)
- [Zscaler Client Connector Tunnel Version](#zapptunnel)
[]Use this filter to view transactions associated with an Adaptive Access profile. The default filter for this is **Any**. You can also choose to include or exclude the selected values.
[]Use this filter to view transactions in which advanced threats were detected. These advanced threats are detected by **Advanced Threat Protection**. The default option for this filter is **Any**. You can search for specific categories. You can also use the toggle to turn on **Threat Name Search** to enter all or part of the threat name in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. The following categories appear under this filter:
- **Adware/Spyware Sites**: This category refers to any detections of websites known to contain adware or spyware based on the URL/IP reputation. The URLs/IPs added in this category would be associated with distributing adware or spyware, which can collect information related to the user’s browsing activities and display unwanted advertisements without the user’s consent.
- **Any**
- **Botnet Callback**: This is the most important threat category because the Sandbox detects post-infection activity, which requires you to follow up and remediate. There are two types of detections: destination URL reputation and content IPS signature, which are both part of Advanced Threat Protection. URL reputation-based detections, especially those that match only on a domain or even an IP address, are lower fidelity and have a lower chance of the affected endpoint actually being infected by a botnet agent. This is because some indicators detect when a user happens to visit a web destination that is known to serve or be associated with malicious botnet payloads or communication, so the user is protected preinfection. The IPS signature-based detections generally match on the botnet communication pattern/protocol, so they are more likely to signal that the affected endpoint is actually infected by a botnet agent.
- **Browser Exploit**: This category refers to any detections of known exploits against web browsers. These detections are often IPS signature-based detections, so they are high fidelity.
- **Cross-site Scripting**: This category refers to any detections that try to abuse an end user via a type of injection, in which malicious scripts are injected into benign and trusted websites. Cross-site scripting (XSS) attacks occur when an attacker uses a web application to send malicious code, typically through browser-side scripting, to a different end user. These detections are often IPS signature-based detections, so they are high fidelity.
- **Crypto Mining & Blockchain**: This category refers to any detections of crypto mining or crypto jacking activity or sites associated with malicious cryptocurrency activity. General cryptocurrency websites and content are not blocked by this category, but those that are designed to abuse user's devices without their consent via browser-based scripts that mine cryptocurrency. These detections are often IPS signature-based detections with the actual scripts hiding on or behind web pages, so they are high fidelity.
- **Domain Generation Algorithm (DGA) Domains**: This category refers to the domains that are suspected to be generated using domain generation algorithms (DGA). These algorithms are used in various malware families to periodically generate a large number of domain names that can be used by malware-infected devices to connect with command and control servers in order to circumvent the identification and shutting down of malicious domains.
- **Malicious Content**: This category refers to any detections of malware or websites known to host malware and other malicious content that isn't attributed to a specific threat type or category. The detection capabilities in this category are often based upon various signature types and patterns, such as URL reputation, IPS signatures, etc.
- **Other Threat**: This is a catchall category for any detections that might not have an appropriate mapping to a specific category.
- **Peer-to-Peer**: This category refers to any detections of peer-to-peer traffic via applications such as BitTorrent, Tor, and other anonymizer or file sharing applications. These applications can be across any port. You also must have Firewall for the Zscaler service to detect and block these applications.
- **Phishing**: This category is one of the most powerful detection capabilities in the Advanced Threat Protection policy. It refers to any detections that are both URL reputation and IPS content signature-based. The ThreatLabZ operations team focuses on writing new phishing IPS signatures based on the patterns discovered and extracted from the phishing attacks observed by the Zscaler service and outside threat intelligence sources and partners. ThreatLabZ proactively scans and reviews all newly registered domains to discover new phishing and credential stealing URLs and ensure phishing IPS signature coverage for any new phishing patterns.
- **Spyware Callback**: This category refers to any detections of communication and callback traffic associated with spyware agents and data transmission. The Zscaler service detects this content using high fidelity IPS signatures that match content patterns in web traffic.
- **Suspicious Content**: This category refers to any detections from the Suspicious Content Protection (PageRisk) engine. You can configure the Zscaler service to block users from accessing web pages with a high [Page Risk Index (PRI) score](/zia/configuring-advanced-threat-protection-policy#pagerisk). The Zscaler service analyzes malicious content on a web page (e.g, injected scripts, vulnerable ActiveX, zero-pixel iFrames, etc.) and creates a Page Risk Index. The service also analyzes data from the domain (e.g., hosting country, domain age, past results, links to high-risk top-level domains, etc.) and creates a Domain Risk Index. The Page Risk and Domain Risk Index are combined to produce a single PRI score. This score is then evaluated against the value you set.
- **Suspicious Destination**: This category refers to any detections of internet activity destined to specific countries where the website IP address geographically is located and hosted from. This detection is based on the countries you decide to block access to in your policies.
- **Unauthorized Communication**: This category refers to any detections of unauthorized, tunneling, or anonymizer traffic such as IRC traffic, SSH tunneling, Tor anonymizer traffic, etc. The Zscaler service detects this content via specialized IPS content signatures that match the traffic patterns associated with this kind of communication.
- **Web Spam**: This category refers to any URL detections from web-based email spam scams and specific phishing attacks within web email content. The Zscaler service detects this content using high fidelity IPS signatures that match content patterns in web traffic.
[]Use this filter to view transactions associated with a specific ALPN protocol. The default option for this filter is **Any**. You can search for specific ALPN protocols.
[]Use this filter to view transactions associated with an allowed File Type Control Rule policy. The default option for this filter is **None**.
[]Use this filter to view discovered instances associated with an organization, domain, or tenant. Enter all or part of the instance level ID in the text field and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view discovered instances associated with a project, workspace, or site. Enter all or part of the instance ID in the text field and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view discovered instances associated with a resource type. Enter all or part of the resource name in the text field and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to limit the data to traffic associated with a specific country, as determined by the destination IP address. The default option for this filter is **None**. You can search for a specific country.
[]Use this filter to limit the data to check if the country associated with the destination IP address is risky or not.
[]Use this filter to limit data to check if the country associated with the source IP address is risky or not.
[]Use this filter to limit the data to traffic associated with a specific country, as determined by the source IP address. The default option for this filter is **None**. You can search for a specific country.
[]Use this filter to view transactions associated with an application’s activity. The default option for this filter is **Any**. You can search for a specific action on an application, such as:
- Comment
- Create
- Delete
- Download
- Edit
- File Share
- Invite
- Post
- Reaction
- Rename
- Send Mail
- Share
- Upload
- Upload/Attachments
- View
[]Use this filter to view transactions associated with a specific [application segment](/zpa/about-applications). The default option for this filter is **None**. You can search for specific application segments.
[]Use this filter to view if the cloud application is sanctioned or unsanctioned. The status is displayed as N/A if the URL is unknown and no cloud application is tagged in the transaction.
[]Use this filter to view transactions associated with a specific bandwidth class. The default option for this filter is **All**. You can search for specific classes.
[]Use this filter to view transactions associated with a specific bandwidth rule. The default option for this filter is **All**. You can search for specific rules.
[]Use this filter to see if the server certificate is signed by a Zscaler-trusted certificate authority or not. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific validations. The following validations appear under this filter:
- Fail
- Pass
[]Use this filter to see if the certificate presented by the server is valid or expired. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific answers. The following answers appear under this filter:
- No
- None
- Yes
[]Use this filter to view the cipher suite agreed upon during the SSL handshake between the client and the ZIA Public Service Edge. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific cipher suites.
The cipher suite names are listed in OpenSSL format. To view them in RFC format, use this [link](https://testssl.sh/openssl-iana.mapping.html) to map between the two notations.
[]Use this filter to see the version of TLS used for communication between the client and the ZIA Public Service Edge. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific TLS versions.
[]Use this filter to view transactions associated with the internet gateway location IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
[]Use this filter to view transactions associated with a source IP address. Enter either the internet gateway location IP address or the IP address of the client device. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
[]Use this filter to view transactions associated with the source port number from where the traffic originated. When you select this filter, enter the **From **and **To **fields to view the logs within that range. This filter is disabled by default. To enable it, contact Zscaler Support.
[]Use this filter to view the number of times the client's SSL handshake attempts have failed. You can view transactions for a certain range of aggregate counts by entering a minimum and maximum value.
[]Use this filter to view the digital signature proposed by the client in signature_algorithms extension of ClientHello message during the SSL/TLS handshake process in a transaction. The default option for this filter is **None**. The following categories appear under this filter:
- **Classical**: Use this filter to view the classical key exchange algorithm proposed by the client during the SSL/TLS handshake process.
- **Hybrid**: Use this filter to view the hybrid key exchange algorithm proposed by the client during the SSL/TLS handshake process in a transaction.
- **PQC**: Use this filter to view the pure post-quantum cryptography (PQC) key exchange algorithm proposed by the client during the SSL/TLS handshake process in a transaction.
- **None**: Use this filter to view all non-TLS related transactions.
- **Unknown**: Use this filter to view the TLS-related transaction whose value could not be determined.
[]Use this filter to view key exchange algorithms proposed by the client in supported_groups extension of ClientHello message during the SSL/TLS handshake process in a transaction. The default option for this filter is **None**. The following categories appear under this filter:
- **Classical**: Use this filter to view transactions where a client proposed a classical key exchange algorithm during the SSL/TLS handshake process.
- **Hybrid**: Use this filter to view transactions where a client proposed a hybrid key exchange algorithm during the SSL/TLS handshake process in a transaction.
- **None**: Use this filter to view all non-TLS related transactions.
- **PQC**: Use this filter to view transactions where a client proposed a pure post-quantum cryptography (PQC) key exchange algorithm during the SSL/TLS handshake process.
- **Unknown**: Use this filter to view transactions with a non-standard key exchange algorithm proposed by a client during the SSL/TLS handshake process.
[]Use this filter to view either the key exchange algorithm agreed upon during the TLS handshake between the client and the ZIA Service Edge in the case of TLS inspected traffic, or the key exchange algorithm agreed upon during the TLS handshake between the client and the server in the case of bypassed traffic. The default option for this filter is **None**.
[]Use this filter to view either the digital signature algorithm agreed upon during the TLS handshake between the client and the ZIA Service Edge in the case of TLS inspected traffic, or the digital signature algorithm agreed upon during the TLS handshake between the client and the server in the case of bypassed traffic. The default option for this filter is **None**.
[]Use this filter to view either the key exchange algorithm agreed upon during the TLS handshake between the server and the ZIA Service Edge in the case of TLS inspected traffic, or the key exchange algorithm agreed upon during the TLS handshake between the server and the client in the case of bypassed traffic. The default option for this filter is **None**.
[]Use this filter to view either the digital signature algorithm agreed upon during the TLS handshake between the ZIA Service Edge and the client in the case of TLS inspected traffic, or the digital signature algorithm agreed upon during the TLS handshake between the server and the client in the case of bypassed traffic. The default option for this filter is **None**.
[]Use this filter to view client SSL handshake failure transactions. The default option for this filter is **None**. The following SSL failure reasons appear under this filter:
- Access Denied
- Bad Cert Status Resp or Hash Value
- Bad or Unsupported Certificate
- Bad Record Mac
- Certificate Revoked or Expired
- Certificate Unknown
- Certificate Unobtainable
- Close Notify or Client TCP Reset
- Decode Error
- Decrypt Error
- Handshake Failure
- Illegal Parameter
- Insufficient Security
- Internal Error
- N/A
- No Application Protocol
- No Renegotiation
- Other Handshake Error
- Protocol Version
- Record Overflow
- Unexpected Message
- Unknown CA
- Unknown PSK Identity
- Unrecognized Name
- Unsupported Extension
- User Canceled
To learn more, refer to [RFC 2246 The TLS Protocol](https://www.ietf.org/rfc/rfc2246.html#section-7.2.2).
[]Use this filter to view transactions associated with a specific cloud app. The default option for this filter is **All**. You can search for specific apps.
- To view all the applications that appear under this filter, see [Cloud App Categories](/zia/cloud-app-categories).
The Miscellaneous <Cloud Application Category> Apps (e.g., Miscellaneous Finance Apps) option represents all the newly added lesser-known predefined applications for the category (e.g., Finance). The log displays results for each application grouped inside this option individually.
[]Use this filter to view transactions associated with a specific cloud app class. The default option for this filter is **All**. You can choose to include or exclude certain locations. You can search for specific apps. The following categories appear under this filter:
- Administration
- Collaboration and Online Meetings
- Consumer
- DNS Over HTTPS Services
- File Sharing
- General Browsing
- Hosting Providers
- Human Resources
- Instant Messaging
- IT Services
- Peer-to-Peer
- Productivity and CRM Tools
- Sales & Marketing
- Social Networking
- Streaming Media
- System & Development
- Web Mail
- Web Search
[]Use this filter to view the cloud application policy type and name that took action during the transaction. Following are the policy types that appear in this field:
- **Collaboration & Online Meetings App Control**: This refers to the [Collaboration & Online Meetings rule](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Consumer**: This refers to the [Consumer rule](/zia/adding-consumer-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **DNS Over HTTPS Services**: This refers to the [DNS Over HTTPS Services Rule](/zia/adding-dns-over-https-services-rule-cloud-app-control) for the [Could App Control policy](/zia/about-cloud-app-control).
- **File Sharing**: This refers to the [File Sharing rule](/zia/adding-file-sharing-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Finance**
- **Health Care**
- **Hosting Providers**: This refers to the [Hosting Providers rule](/zia/adding-hosting-providers-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Human Resources**: This refers to the [Human Resources rule](/zia/adding-human-resources-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Instant Messaging**: This refers to the [Instant Messaging rule](/zia/adding-instant-messaging-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **IT Services**: This refers to the [IT Services rule](/zia/adding-it-services-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Legal**
- **Productivity and CRM Tools**: This refers to the [Productivity & CRM tools rule](/zia/adding-productivity-crm-tools-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Sales & Marketing**: This refers to the [Sales & Marketing rule](/zia/adding-sales-marketing-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Social Networking**: This refers to the [Social Networking & Blogging rule](/zia/adding-social-networking-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **System & Development**: This refers to the [System & Development rule](/zia/adding-system-development-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Video Streaming**
- **Webmail**: This refers to the [Webmail rule](/zia/adding-webmail-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
[]Use this filter to limit the data to traffic associated with a specific data center.
[]Use this filter to view transactions associated with a specific department. The default option for this filter is **All**. You can search for specific departments.
[]Use this filter to view transactions associated with a specific hostname from support devices. Enter all or part of the device model in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
[]Use this filter to view transactions associated with a specific device model. Enter all or part of the device model in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions associated with a specific device name. Enter all or part of the device name in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
[]Use this filter to view transactions associated with a specific device OS type. Enter all or part of the device OS type in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions associated with a specific device OS version. Enter all or part of the device OS version in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions associated with a specific device owner. Enter all or part of the device owner in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
[]Use this filter to see which transactions contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **All**. You can search for specific DLP dictionaries.
[]Use this filter to view transactions in which data leakage was detected. The default option for this filter is **Any**. You can search for specific DLP engines.
[]Use this filter to search for the transactions using this DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. Use it as a filter to locate the exact transaction. You can search for specific DLP identifiers.
[]Use this filter to view transactions associated with a specific enrolled device app version. Enter all or part of the enrolled device app version in the text field and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions associated with a specific external device ID. Enter all or part of the device model in the text field and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to see the MD5 hash for the file that triggered the DLP rule. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing the MD5 hash of the file is sent to your auditors. Use it as a filter to locate the exact transaction. You can search for specific DLP MD5 hashes.
[]Use this filter to view transactions associated with a specific triggered DLP rule's severity. You can choose to include or exclude certain severities. The following severities appear under this filter:
- Information
- Low
- Medium
- High
[]Use this filter to see the HTTP/S transactions that indicate domain fronting due to an FQDN mismatch: between the request URL and the request's host header, or between the SNI (Server Name Indication) and the inner request's host header.
[]Use this filter for the SSL/TLS connection's Server Name Indication (SNI) in cases that the HTTPS request host header doesn't match the SNI. SSL Inspection must be enabled for this field to be populated.
[]Use this filter to limit the data to traffic associated with a specific upload or download document type. The following types appear under this filter:
- Corporate Finance
- Corporate Legal
- Court Form
- DMV
- Immigration
- Insurance
- Invoice
- Legal
- Medical Information
- None
- Real Estate
- Resume
- Tax
- Technical
- Unknown
[]Use this filter to limit the data to traffic associated with a specific downloaded file name. Enter all or part of the URL in the text field and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to limit the data to traffic associated with a specific downloaded file type.
[]Use this filter to limit the data to traffic associated with a specific user-defined downloaded file type. The default option for this filter is **None**.
[]Use this filter to view transactions in which a specific file type was downloaded. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Any
- Archive
- Audio
- Database
- Executable
- Image
- Microsoft Office
- Mobile
- Online Gaming
- Open Office Files
- Other
- Other Documents
- Other Microsoft
- Source Code
- Streaming Media
- Video
- Web Content
[]Use this filter to view transactions associated with file sharing activities. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **File Sharing**. From the **File Sharing Activity** filter, the default option is **All**. You can search for specific activities. The following activities appear under the **Streaming** **Activity **filter:
- All
- Upload
- View
[]Use this filter to view transactions by their flow type. Choose one from the following:
- Direct
- Intranet
- Loopback
- Unclassified
- VPN
- VPN Tunnel
- ZIA
- ZPA
[]Use this filter to view transactions for a specific forwarding method. You can select from the ones listed under this filter.
[]Use this filter to view transactions for a specific forwarding rule. You can select from the ones listed under this filter.
[]Use this filter to view transactions for a specific gateway IP. You can search for specific gateway IPs.
[]Use this filter to view transactions for a specific gateway name. You can select from the ones listed under this filter.
[]Use this filter to view transactions associated with a HTTP header insertion profile. The default option for this filter is **None**.
[]Use this filter to view transactions associated with a HTTP header profile. The default option for this filter is **Any**.
[]Use this filter to view transactions associated with instant messaging applications. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Instant Messaging**. For the** IM Activity** filter, the default option is **Any**. You can search for specific activities. The following activities appear under the** IM Activity** filter:
- All
- Receive File
- Receive Message
- Send File
- Send Message
[]Use this filter to view the transactions associated with intermediate CA certificates. The default option for this filter is **None**. The following intermediate CA protection types appear under this filter:
- HSM Protection
- N/A
- Software Protection
[]Use this filter to view transactions associated with a specific location. The default option for this filter is **All**. You can search for specific locations. You can choose to include or exclude certain locations.
[]Use this filter to view transactions associated with a specific location group. The default option for this filter is **None**. You can search for specific location groups.
[]Use this filter to view transactions associated with a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
[]Use this filter to see if the certificate status verification using OCSP failed or passed. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific results. The following results appear under this filter:
- Good
- None
- Revoked
- Unknown
[]Use this filter to view the blocked policy and rule that took action during the transaction. Following are the policy types that appear in this field:
- **Advanced Threat Protection**: This refers to the [Advanced Threat Protection policy](/zia/configuring-advanced-threat-protection-policy).
- **Collaboration & Online Meetings App Control**: This refers to the [Collaboration & Online Meetings rule](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Consumer**: This refers to the [Consumer rule](/zia/adding-consumer-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Data Loss Prevention**: This refers to the [Data Loss Prevention policy](/zia/about-data-loss-prevention).
- **DNS**: This refers to the [DNS Control policy](/zia/about-dns-control).
- **DNS Over HTTPS Services**: This refers to the [DNS Over HTTPS Services Rule](/zia/adding-dns-over-https-services-rule-cloud-app-control) for the [Could App Control policy](/zia/about-cloud-app-control).
- **File Sharing**: This refers to the [File Sharing rule](/zia/adding-file-sharing-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **File Type Control**: This refers to the [File Type Control policy](/zia/about-file-type-control).
- **Firewall Filtering**: This refers to the [Firewall Control policy](/zia/about-firewall-control).
- **Hosting Providers**: This refers to the [Hosting Providers rule](/zia/adding-hosting-providers-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Human Resources**: This refers to the [Human Resources rule](/zia/adding-human-resources-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Instant Messaging**: This refers to the [Instant Messaging rule](/zia/adding-instant-messaging-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Intrusion Prevention**
- **IT Services**: This refers to the [IT Services rule](/zia/adding-it-services-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Malware Protection**: This refers to the [Malware Protection policy](/zia/configuring-malware-protection-policy).
- **Mobile App Store Control**: This refers to the [Mobile App Store Control policy](/zia/about-mobile-app-store-control).
- **NAT Control**: This refers to the [NAT Control policy](/zia/about-nat-control).
- **Productivity and CRM Tools**: This refers to the [Productivity & CRM tools rule](/zia/adding-productivity-crm-tools-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Sales & Marketing**: This refers to the [Sales & Marketing rule](/zia/adding-sales-marketing-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Sandbox**: This refers to the [Sandbox policy](/zia/about-sandbox).
- **Social Networking**: This refers to the [Social Networking & Blogging rule](/zia/adding-social-networking-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **System & Development**: This refers to the [System & Development rule](/zia/adding-system-development-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **URL Filtering**: This refers to the [URL filtering policy](/zia/about-url-filtering).
- **Video Streaming**
- **Webmail**: This refers to the [Webmail rule](/zia/adding-webmail-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
[]Use this filter to view transactions that bypassed the Zscaler Client Connector.
[]Use this filter to view transactions that bypassed the Zscaler Client Connector within the specified time period.
[Capture: ]Use this filter to limit the data to view transactions that were captured into a PCAP file.
[]Improve the visibility of protocols that traverse within Zscaler’s cloud. The following information is shown:
- **DNS over HTTPS**: Transactions from sites that are used for DNS resolution over an encrypted and secure connection with [DNS Over HTTPS Services](/zia/adding-dns-over-https-services-rule-cloud-app-control).
- **FTP**: Transactions from native FTP servers.
- **FTP over HTTP**: Transactions from FTP over HTTP websites.
- **HTTP**: Transactions from HTTP websites.
- **HTTP Proxy**: Transactions from HTTP CONNECT requests destined to a ZIA Public Service Edge IP address.
- **HTTPS**: HTTPS transactions that have been inspected.
- **SSL**: Transactions from SSL/TLS connections that have not been inspected. For example, hosts you've [exempted from SSL inspection](/zia/about-ssl-inspection#configure-ssl-inspection-policy).
- **Tunnel**: Transactions from unidentified encrypted traffic. For example, tunneling applications (e.g., Telnet or SSH) that are encapsulated in HTTP or HTTPS.
- **Tunnel SSL**: Undecodable protocol within an SSL connection.
- **WebSocket**: Transactions from WebSocket websites.
- **WebSocket SSL**: Transactions from WebSocket websites encrypted by SSL.
[]Use this filter to view transactions based on the number of bytes a destination web server returned for an HTTP request. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0–1KB
- 1KB–100KB
- 100KB–1MB
- 1MB–5MB
- 5MB–10MB
- 10MB–50MB
- 50MB–100MB
- Above 100MB
- Custom
[]Use this filter to find transactions associated with a referrer URL, which is the URL from which an HTTP request originated. Enter all or part of the URL in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions associated with the web traffic of an HTTP request method. Choose **GET** to see transactions only for HTTP requests to retrieve data, or choose **POST** to see transactions only for HTTP requests to submit data to be processed. Post requests include email that was sent through webmail or posting on a social networking site or blog.
- Baselinecontrol
- Bcopy
- Bdelete
- Bmove
- Bpropfind
- Bproppatch
- Checkin
- Checkout
- Connect
- Copy
- Delete
- Get
- Head
- Invalid
- Label
- Lock
- Mailpost
- Merge
- Mkactivity
- Mkcol
- Mkworkspace
- Move
- Notify
- Options
- Poll
- Post
- Propfind
- Proppatch
- Put
- Report
- Reqmod
- Respmod
- Search
- Subscribe
- Trace
- Uncheckout
- Unlock
- Unsubscribe
- Update
- Versioncontrol
[]Use this filter to see the request version of HTTP used for communication between the client and the server. The default option for this filter is **None**. You can search for specific versions. The following versions appear under this filter:
- 1.0
- 1.1
- 2.0
- None
[]Use this filter to see the response version of HTTP used for communication between the client and the server. The default option for this filter is **None**. You can search for specific versions. The following versions appear under this filter:
- 1.0
- 1.1
- 2.0
- None
[]Use this filter to view file downloads based on the Sandbox result. The default option for this filter is **Any**. You can search for specific results The following results appear under this filter:
- **Sandbox Adware**:** **View known malicious results. This category refers to any malicious file sample installing persistent components to push advertising content to the user’s device. Often, these advertisements are unwanted and can lead to spyware or other grayware-oriented privacy violations.
- **Sandbox Anonymizer**:** **View known malicious results. This category refers to any malicious file sample exhibiting behavior consistent with anonymizer programs, such as Tor Browser or other VPN services, that essentially make a user’s internet activity untraceable.
- **Sandbox Benign**:** **View known non-malicious results. This is a catchall category for any non-malicious file sample with a Sandbox Threat Score equal to or less than 70. The Zscaler service refers to file samples that have a score between 40 and 70 as “suspicious” because they might need additional review.
- **Sandbox Malware**:** **View known malicious results. This is a catchall category for any malicious file sample that doesn't fall under the other Sandbox categories. Most Sandbox-classified file samples aren't clearly known to be a specific threat or malware family-oriented because there aren't specific signatures or indicators to categorize the file. Instead the Zscaler service categorizes the file based on an aggregation of the file’s OS and application behaviors and network activity.
- **Sandbox Suspicious**: This category refers to files that exhibit some malicious behaviors but are not fully classified as malware.
- **Sent for Analysis**: View unknown results that have been sent to the Sandbox for behavioral analysis.
[]Use this filter to view file downloads based on the Sandbox action. The default option for this filter is **Blocked**. You can search for specific results The following results appear under this filter:
- Blocked
- Quarantined
- Sent for Analysis
[]Use this filter to view sandbox API file submissions based on the specified Sandbox API Token. The default option for this filter is **Any**. You can filter by any combination of created token names.
[]Use this filter to view file download transactions based on the file hash value (MD5). Enter all or part of the MD5 in the text field and **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions based on the size, in bytes, of the HTTP request that was sent to the destination web server. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0–1KB
- 1KB–100KB
- 100KB–1MB
- 1MB–5MB
- 5MB–10MB
- 10MB–50MB
- 50MB–100MB
- Above 100MB
- Custom
[]Use this filter to see if the certificate presented by the Origin Content Server (web server) to the ZIA Public Service Edge was self-signed. The default option for this filter is **None**. The following options appear under this filter:
- No
- None
- Yes
[]Use this filter to view the validation type for the certificate presented by the server to the ZIA Public Service Edge. The default option for this filter is **None**. The following options appear under this filter:
- Domain Validation
- Extended Validation
- None
- Organization Validation
[]Use this filter to view the validity duration of the certificate presented by the server to the ZIA Public Service Edge (i.e. How long is the certificate valid for?). The default option for this filter is **None**. The following options appear under this filter:
- 0–3 months
- 3–12 months
- More than 12 months
- None
[]Use this filter to view the cipher suite agreed upon during the SSL handshake between the ZIA Public Service Edge and the server. The default option for this filter is **None**. You can search for specific cipher suites.
The cipher suite names are listed in OpenSSL format. To view them in RFC format, use this [link](https://testssl.sh/openssl-iana.mapping.html) to map between the two notations.
[]Use this filter to see the version of TLS used for communication between the ZIA Public Service Edge and the server. The default option for this filter is **None**. You can search for specific versions. The following versions appear under this filter:
- SSL 2.0
- SSL 3.0
- TLS 1.0
- TLS 1.1
- TLS 1.2
- TLS 1.3
[]Use this filter to view transactions associated with a destination server. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
[]Use this filter to view any delayed logs.
[]Use this filter to display the hash of identical files.
[]Use this filter to view transactions associated with social networking sites. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Social Networking**. From the **Social Networking Activity** filter, the default option is **All**. You can search for specific activities. The following activities appear under the** Social Networking Activity** filter:
- All
- Publish
- View
[]Use this filter to view SSL inspected transactions. Select to view decrypted SSL transactions. Deselect to view SSL transactions that weren't decrypted.
[]Use this filter to view the [SSL Inspection Policy](/zia/about-ssl-inspection-policy) rule that was applied to the transaction. The default option for this filter is **Any**.
[]Use this filter to view SSL policy reason transactions. The default option for this filter is **None**. The following SSL inspection policy actions appear under this filter:
- Blocked
- Inspected
- N/A
- Not inspected because of failed client SSL handshake
- Not inspected because of HSM error
- Not inspected because of mutual TLS authentication
- Not inspected because of O365 bypass
- Not inspected because of SSL policy
- Not inspected because of UCaaS bypass
- Not inspected because of undecryptable traffic
- Not inspected because of Zscaler best practices
- Not inspected because of Zscaler service domains
[]Use this filter to view transactions associated with streaming media. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Streaming Media**. From the **Streaming** filter, the default option is **All**. You can search for specific activities. The following activities appear under the **Streaming** **Activity **filter:
- All
- Listen
- Upload
[]Use this filter to limit the data to traffic associated with a specific upload or download subdocument type. The default option for this filter is **Any**.
[]Use this filter to view transactions based on the “raw” Page Risk Index score of a URL; it filters based on the Suspicious Content [column](/zia/web-insights-logs-columns). You can view transactions for a certain range of Page Risk Index scores by entering a minimum and maximum value. The value ranges are from 0 to 100. To learn more about the Suspicious Content Protection (Page RiskTM), see [About Advanced Threat Protection](/zia/configuring-advanced-threat-protection-policy).
[]Use this filter to view transactions associated with a specific threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. You can also use the toggle to turn on **Threat Name Search** to enter all or part of the threat name in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. The following categories appear under this filter:
- **Any**
- **Adware**: This category refers to any detections of adware-related installers or content through file reputation or signature matching (e.g., antivirus or YARA). Adware is software that persistently serves ads to the user and increases the risk of installing spyware or other unwanted software.
- **Archive Bomb**: This category refers to any detections of archive bomb-related content through file reputation or signature matching (e.g., antivirus). An archive bomb is a ZIP or other archive file that was small when compressed or recursively compressed/archived several times; however, when expanded, the file can become extremely large. It can overwhelm antivirus scanning engines or the user’s device by completely filling the hard disk or memory.
- **Backdoor**: This category refers to any detections of backdoor-related installer payloads or content through file reputation or signature matching (e.g., antivirus or YARA). Backdoors are software that allow the attackers to gain remote network access to devices for future exploitation.
- **Benign**: This category refers to any clean file.
- **Boot Virus**: This category refers to any detections of viruses that embed themselves into the boot sectors of users' devices. The Zscaler service detects boot virus-related content through file reputation or signature matching (e.g., antivirus).
- **Dialer**: This category refers to any detections of dialer software that infects users' devices and enables outbound dialing for malicious purposes. The Zscaler service detects dialer-related content through file reputation or signature matching (e.g., antivirus).
- **Downloader**: This category refers to any detections of malware that downloads additional botnets or other malicious payloads on users' devices. The Zscaler service detects downloader-related content through file reputation or signature matching (e.g., antivirus or YARA).
- **Exploit**: This category refers to any detections of various exploits and exploit-related content through file reputation or signature matching (e.g., antivirus or YARA).
- **Macro Virus**: This category refers to any detections of macro viruses and other related content through file reputation or signature matching (e.g., antivirus or YARA).
- **MalwareTool**: This category refers to any detections of malware tools used to generate viruses, exploits, or denial-of-service (DoS) attacks through file reputation or signature matching (e.g., antivirus).
- **Misdisinfection**: This category refers to any file detections that another security service tried to disinfect but failed to do so completely because there are traces of malware in the file. The Zscaler service detects this content through file reputation or signature matching (e.g., antivirus).
- **Other Malware**: This category refers to any malware detections that don't fit into the more specific malware categories. The Zscaler service detects other malware content through file reputation or signature matching (e.g., antivirus).
- **Other Spyware**: This category refers to any spyware detections that don't fit into the more specific malware or spyware categories. The Zscaler service detects other spyware content through file reputation or signature matching (e.g., antivirus).
- **Other Virus**: This category refers to any viruses that don't fit into the more specific malware categories. The Zscaler service detects other viruses through file reputation or signature matching (e.g., antivirus).
- **Password Stealer**: This category refers to any detections of password stealing payloads, installers, or related content through file reputation or signature matching (e.g., antivirus).
- **Privacy Risk**: This category refers to any detections of content, installers, or programs that are related to data exfiltration or attempt to access sensitive data. The Zscaler service detects privacy risks through file reputation or signature matching (e.g., antivirus).
- **Proxy**: This category refers to any malware detections that allow unauthorized connections to occur with the infected device. This type of malware allows a person to use the infected device to attack other devices, send spam, or impersonate your device. The Zscaler service detects proxy-related content through file reputation or signature matching (e.g., antivirus).
- **Ransomware (Virus)**: This category refers to any detections of ransomware installers, agents, or related content through file reputation, signature matching (e.g., antivirus or YARA), or machine learning model techniques.
- **Sandbox Adware**: This category refers to any known malicious Sandbox file detections that install persistent components to push advertising content to users' devices. Often, these advertisements are unwanted and can lead to spyware or other grayware-oriented privacy violations.
- **Sandbox Anonymizer**: This category refers to any known malicious Sandbox file detections that exhibit behavior consistent with anonymizer programs, such as Tor Browser or other VPN services, that essentially make a user’s internet activity untraceable.
- **Sandbox Malware**: This is a catchall category for any known malicious Sandbox file detections that don't fall under the other Sandbox categories. Most Sandbox-classified files aren't clearly known to be a specific threat or malware family-oriented because there aren't specific signatures or indicators to categorize the file. Instead, the Zscaler service categorizes the file based on an aggregation of the file’s OS and application behaviors and network activity.
- **Sandbox Offensive Security** **Tools**: This category refers to the threat actors that can use offensive security tools for malicious reasons. They can also be used by cyber security professionals.
- **Sandbox Ransomware**: This category refers to the type of malware that prevents or limits users from accessing their system, either by locking the system or by locking the users' files, until a ransom is paid.
- **Sent for Analysis**: This category refers to any unknown file detections that have been sent to the Sandbox for behavioral analysis.
- **Trojan**: This category refers to any detections of trojan installers or related content through file reputation, signature matching (e.g., antivirus or YARA), or machine learning model techniques.
- **Suspicious**: This category refers to files that exhibit some malicious behaviors but are not fully classified as malware.
- **Unrecognized Virus**: This category refers to any suspected viruses that don't fall under a specific virus family. The Zscaler service detects this content through signature matching (e.g., antivirus).
- **Unwanted Application**: This category refers to any detections of applications that are potentially unwanted, such as password crackers or other grayware software applications. The Zscaler service detects unwanted applications through file reputation or signature matching (e.g., antivirus or YARA).
- **Worm**: This category refers to any detections of worms, which are stand-alone malware files that replicate themselves in order to spread to other devices. They often use a computer network to propagate themselves. The Zscaler service detects worms through file reputation or signature matching (e.g., antivirus or YARA).
[]Use this filter to view transactions associated with a specific threat class. The default option for this filter is **Advanced Threats**. You can search for specific classes. You can also use the toggle to turn on **Threat Name Search** to enter all or part of the threat name in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. The following classes appear under this filter:
- Advanced Threats
- Sandbox
- Viruses & Spyware
[]Use this filter to enter all or part of the threat name in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions associated with a specific threat severity. The default option for this filter is **None**. The following severities appear under this filter:
- Critical
- High
- Medium
- Low
[]Use this filter to view transactions associated with a specific threat super category. The default option for this filter is **None**. You can search for specific categories. The following categories appear under this filter:
- Malware
- Sandbox
- Spyware
- Virus
[]Use this filter to view transactions based on the total size of the throttled requests. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0–1KB
- 1KB–100KB
- 100KB–1MB
- 1MB–5MB
- 5MB–10MB
- 10MB– 50MB
- 50MB–100MB
- Above 100MB
- Custom
[]Use this filter to view transactions based on the total size of the throttled response. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0–1KB
- 1KB–100KB
- 100KB–1MB
- 1MB–5MB
- 5MB–10MB
- 10MB–50MB
- 50MB–100MB
- Above 100MB
- Custom
[]Use this filter to view transactions based on the total size of the HTTP request and response. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0–1KB
- 1KB–100KB
- 100KB–1MB
- 1MB–5MB
- 5MB–10MB
- 10MB–50MB
- 50MB–100MB
- Above 100MB
- Custom
[]Use this filter to limit the data to traffic associated with a specific traffic forwarding mechanism. The following appear under this filter:
- GRE
- IPSec Tunnel
- NAT Control
- PAC File
- PAC File over GRE Tunnel
- PAC File over IPSec Tunnel
- Policy Based Forwarding
- Zscaler Client Connector
- Zscaler Client Connector over GRE Tunnel
- Zscaler Client Connector over IPSEC Tunnel
- ZPA Microtunnels (M-Tunnels)
[]Use this filter to limit data to traffic associated with a specific unscannable file type. The following appear under this filter:
- **Encrypted File**: Encrypted or password-protected (e.g., GZIP, PDF)
- **Undetectable File**: Unable to determine the file type, based on multiple methods.
- **Unscannable File**: Unscannable (e.g., corrupt archive)
[]Use this filter to limit the data to traffic associated with a specific uploaded file name. Enter all or part of the URL in the text field and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to limit the data to traffic associated with a specific uploaded file type.
[]Use this filter to limit the data to traffic associated with a specific user-defined uploaded file type. The default option for this filter is **None**.
[]Use this filter to view transactions in which a specific file type was uploaded. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Any
- Archive
- Audio
- Database
- Executable
- Image
- Microsoft Office
- Mobile
- Online Gaming
- Open Office Files
- Other
- Other Documents
- Other Microsoft
- Source Code
- Streaming Media
- Video
- Web Content
[]Use this filter to view transactions associated with a specific URL category. The default option for this filter is **Any**. You can search for specific categories. You can choose to include or exclude certain categories.
[]Use this filter to limit the data to a specific URL class. The default option for this filter is **All**. You can search for specific classes. The following classes appear under this filter:
- All
- Bandwidth Loss
- Business Use
- General Surfing
- Legal Liability
- Privacy Risk
- Productivity Loss
[]Use this filter to view transactions for specific URL filtering policy names. You can select from the ones listed under this filter.
[]Use this filter to find transactions associated with specific URLs.
To use this filter:
- Do one of the following:
- Click **URL** and enter all or part of the URL (e.g., `http://www.zscaler.com/products-user-security.php`).
- Click **Path** and enter all or part of the path information (e.g., `products-user-security.php`).
- Click **Host** and enter all or part of the host name (e.g., `www.zscaler.com`).
- Click **Domain** and enter all or part of the domain name (e.g., `zscaler).`
- Choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- Click **Download (.csv) **or **Display**.
-
Click **Apply Filter**.
For optimized and accelerated results, the ZIA Admin Portal might show recommendations to switch between **URL**, **Path**, **Host**, and **Domain **based on your seach inputs. You can choose to **Apply Recommentation**, **Ignore **it,** **or **Cancel **the search. For example, if you select **URL** and enter `www.zscaler.com` in the Search field, the ZIA service shows a recommendation pop-up window to search it as **Host** to minimize the processing time in generating the logs.
[See image.](#url-search-recommendation)
The search results are displayed in the portal or downloaded as a CSV file.
[]Use this filter to view transactions associated with a specific URL super category. The default option for this filter is **All**. You can search for specific categories. The following categories appear under this filter:
- All
- Adult Material
- Business and Economy
- Custom
- Drugs
- Education
- Entertainment/Recreation
- Gambling
- Games
- Government and Politics
- Health
- Illegal or Questionable
- Information Technology
- Internet Communication
- Job/Employment Search
- Militancy/Hate and Extremism
- Miscellaneous
- News and Media
- Religion
- Security
- Shopping and Auctions
- Social and Family Issues
- Society and Lifestyle
- Special Interests/Social Organizations
- Sports
- Tasteless
- Travel
- User-Defined
- Vehicles
- Violence
- Weapons/Bombs
[]Use this filter to view the transactions of a specific user. The default option for this filter is **All**. You can search for specific users. You can choose to include or exclude certain users. By default, user-related traffic data includes locations and users.
[]Use this filter to find transactions associated with the user-agent string that the browser included in its GET request. The user-agent string contains browser and system information that the destination server can use to provide appropriate content.
- The service lists the commonly-used user agents in the **Known** category. To find a user-agent string, click the **Known **tab and scroll or use the Search function to find the user-agent string in this category.
- If the user-agent string is not found, click **Unknown** and enter all or part of the user-agent string in the text field and choose** Contains**, **Exact**, **Ends With**, or **Starts With**. (Example: **Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:18.0) Gecko/20100101 Firefox/18.0**)
[]Use this filter to view transactions based on the service's action. The default option for this filter is **All**. You can search for specific actions. The following categories appear under this filter:
- **All**: View all transactions. This is the default option.
- **Allow**: View allowed transactions.
- **Allowed - No Active Content**: View download transactions of unknown PDF or Microsoft Office files that are allowed because they are classified as benign in [Sandbox static analysis](/zia/configuring-sandbox-policy#first-time-action).
- **Allowed and No Scan**: View download transactions of unknown files that were allowed but not scanned due to your [configured Sandbox policy](/zia/configuring-sandbox-policy#first-time-action).
- **Allowed with caution**: View allowed transactions where the service displayed a caution notification.
- **Block**: View blocked transactions.
- **Blocked - Tenant Restricted**: View blocked transactions because of your configured [Tenant Restriction ](/zia/about-tenant-profiles)policies.
- **Blocked with caution**: View blocked transactions where the service displayed a caution notification.
- **Isolate**: View transactions sent for isolation by [Isolation.](/isolation/what-isolation)
[]Use this filter to view transactions associated with webmail applications. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Web Mail**. From the **Webmail Activity** filter, the default option is **All**. You can search for specific activities. The following activities appear under the **Webmail** **Activity **filter:
- All
- Send
- Send Attachment
- View
[]Use this filter to view transactions associated with a specific Zscaler Client Connector tunnel version, listed under this filter.
[]Use this filter to limit the data to traffic associated with a specific server destination port. You can specify individual ports and a range of ports, from 0 to 65535.
This filter is disabled by default. To enable the filter, contact Zscaler SupportZscaler Support.
[]Use this filter to view the data to activities associated with DLP rules that are evaluated, but no action was taken based on the rule. To populate this field, you must enable the **Evaluate All Rules** mode for inline DLP rule evaluation in the [DLP Advanced Settings](/zia/configuring-dlp-advanced-settings#RuleEvaluation) page (Administration > DLP Advanced Settings). To learn more, see [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled#EvaluateAllRules).
[]Use this filter to view prompts entered by users across the various generative AI applications. You can also use the toggle to turn on prompt search to enter all or part of the prompt in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
[]Use this filter to view transactions associated with a specific category of prompts entered by users across the various Gen AI applications. You can choose to include or exclude the selected values. The default option for this filter is **Any**. The following categories appear under this filter:
- Art and Culture
- Blogs and Social Media
- Code Generation
- Corporate Finance
- Corporate Legal
- Customer Service Success
- Education
- Government and Politics
- Jobs Employment HR
- Marketing
- News and Media
- PII
- Religion
- Sales/Support Apps
- Shopping and Retail
- Source Code
- Tax
- Technology
- Threat
- Travel and Vehicles
- Unknown
[]![Recommendation window for URL Search Filter](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/web-insights-logs-filters/ZIA6.2r-URL-search-filter-recommendation-window.png)