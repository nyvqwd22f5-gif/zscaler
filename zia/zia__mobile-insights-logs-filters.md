# Mobile Insights Logs: Filters
Source: https://help.zscaler.com/zia/mobile-insights-logs-filters
PDF: https://help.zscaler.com/pdf/com/en/1401076.pdf

Filters define the traffic information that you view in your Mobile Insights Logs. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Also, certain filters support additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform string match, like **Advanced Threat Category** and others.
There are certain filter combinations that appear together in Insights Logs when applied, but don't appear together in Insights. For example, the **Department** and **Location** filters appear together in Insights Logs when applied, but don't appear together in Insights.
Following are the mobile log filters you can select:
- [Advanced Threat Category](#Adv-Threat-Super-Cat)
- [Certificate Chain Validity](#Cert-Chain-Validity)
- [Certificate Expiry](#Cert-Expiry)
- [Client Connection Ciphers](#Client-Connect-Ciphers)
- [Client Connection TLS Version](#Client-Connect-TLS-Ver)
- [Client External IP](#Client-Ext-IP)
- [Client IP](#Client-IP)
- [Cloud Application](#Cloud-App)
- [Cloud Application Class](#Cloud-App-Class)
- [Department](#Department)
- [DLP Dictionary](#DLP-Dictionary)
- [DLP Engine](#DLP-Engine)
- [File Type Category](#File-Type-Cat)
- [File Type Super Category](#File-Type-Super-Cat)
- [IM Activity](#IM-Activity)
- [Location](#Location)
- [Location Group](#Location-Group)
- [Location Type](#location-type)
- [Mobile Action](#Mobile-Action)
- [Mobile Application](#Mobile-App)
- [Mobile Application Category](#Mobile-App-Cat)
- [Mobile Application Class](#Mobile-App-Class)
- [Mobile Application Search](#Mobile-App-Search)
- [Mobile Device Type](#Mobile-Device-Type)
- [OSCP Result](#OSCP-Result)
- [Policy Type and Rule Name](#Policy-Type-Rule-Name)
- [Protocol](#Protocol)
- [Received Bytes](#Received-Bytes)
- [Referrer Search](#Referrer-Search)
- [Request Method](#Request-Method)
- [Sandbox](#Sandbox)
- [Sandbox Action](#Sandbox-Action)
- [Sandbox MD5](#Sandbox-MD5)
- [Sent Bytes](#Sent-Bytes)
- [Server Certificate Self Signed](#Svr-Cert-Self-Signed)
- [Server Certificate Validation Type](#Svr-Cert-Valid-Type)
- [Server Certificate Validity Period](#Svr-Cert-Valid-Per)
- [Server Connection Ciphers](#Svr-Connect-Ciphers)
- [Server Connection TLS Version](#Svr-Connect-TLS-Ver)
- [Server IP](#Svr-IP)
- [Show Delayed Logs](#Show-Delayed-Logs)
- [Social Networking Activity](#SN-Activity)
- [SSL Inspected](#SSL-Inspected)
- [Streaming Activity](#Streaming-Activity)
- [Threat Category](#Threat-Cat)
- [Threat Class](#Threat-Class)
- [Threat Super Category](#Threat-Super-Cat)
- [Total Bytes](#Total-Bytes)
- [Traffic Forwarding](#Traffic-Forwarding)
- [URL Category](#URL-Category)
- [URL Class](#URL-Class)
- [URL Search](#URL-Search)
- [URL Super Category](#URL-Super-Cat)
- [User](#User)
- [User Agent](#User-Agent)
- [Webmail Activity](#Webmail-Activity)
[]Use this filter to view transactions in which advanced threats were detected. These advanced threats are detected by **Advanced Threat Protection**. The default option for this filter is **Any**. You can search for specific categories. You can also use the toggle to turn on **Threat Name Search** to enter all or part of the threat name in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. The following categories appear under this filter:
- **Adware/Spyware Sites**: This category refers to any detections of websites known to contain adware or spyware based on the URL/IP reputation. The URLs/IPs added in this category would be associated with distributing adware or spyware, which can collect information related to the user’s browsing activities and display unwanted advertisements without the user’s consent.
- **Any**
- **Botnet Callback**: This is the most important threat category because the Sandbox detects post-infection activity, which requires you to follow up and remediate. There are two types of detections: destination URL reputation and content IPS signature, which are both part of Advanced Threat Protection. URL reputation-based detections, especially those that match only on a domain or even an IP address, are lower fidelity and have a lower chance of the affected endpoint actually being infected by a botnet agent. This is because some indicators detect when a user happens to visit a web destination that is known to serve or be associated with malicious botnet payloads or communication, so the user is protected preinfection. The IPS signature-based detections generally match on the botnet communication pattern/protocol, so they are more likely to signal that the affected endpoint is actually infected by a botnet agent.
- **Browser Exploit**: This category refers to any detections of known exploits against web browsers. These detections are often IPS signature-based detections, so they are high fidelity.
- **Cross-site Scripting**: This category refers to any detections that try to abuse an end user via a type of injection, in which malicious scripts are injected into benign and trusted websites. Cross-site scripting (XSS) attacks occur when an attacker uses a web application to send malicious code, typically through browser-side scripting, to a different end user. These detections are often IPS signature-based detections, so they are high fidelity.
- **Crypto Mining & Blockchain**: This category refers to any detections of crypto mining or crypto jacking activity or sites associated with malicious cryptocurrency activity. General crypto currency websites and content aren't blocked by this category, but those that are designed to abuse user's devices without their consent via browser-based scripts that mine cryptocurrency. These detections are often IPS signature-based detections with the actual scripts hiding on or behind web pages, so they are high fidelity.
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
[]Use this filter to see if the server certificate is signed by a Zscaler-trusted certificate authority or not. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific validations. The following validations appear under this filter:
- No
- None
- Yes
[]Use this filter to see if the certificate presented by the server is valid or expired. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific answers. The following answers appear under this filter:
- No
- None
- Yes
[]Use this filter to view the cipher suite agreed upon during the SSL handshake between the client and the ZIA Public Service Edge. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific cipher suites.
The cipher suite names are listed in OpenSSL format. To view them in RFC format, use this [link](https://testssl.sh/openssl-iana.mapping.html) to map between the two notations.
[]Use this filter to see the version of TLS used for communication between the client and the ZIA Public Service Edge. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific TLS versions.
[]Use this filter to view transactions associated with the internet gateway location IP address.
[]Use this filter to view transactions associated with a source IP address. Enter either the internet gateway location IP address or the IP address of the client device. You can enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
[]Use this filter to view transactions associated with a specific application. The default option for this filter is **All**. You can search for specific applications.
[]Use this filter to view transactions associated with a specific app class. The default option for this filter is **All**. You can search for specific apps.
- To view all the applications that appear under this filter, see [Cloud App Categories](/zia/cloud-app-categories).
[]Use this filter to view transactions associated with a specific department. The default option for this filter is **All**. You can search for specific departments.
[]Use this filter to see which transactions contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **All**. You can search for specific DLP dictionaries.
[]Use this filter to view transactions in which data leakage was detected. The default option for this filter is **Any**. You can search for specific DLP engines.
[]Use this filter to view transactions in which a file was either uploaded or downloaded. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Any
- Autocad Drawing (dwg)
- AVI Files (avi)
- Bitmap (bmp)
- Bzip2 (bz, bz2)
- Cab Archive (Cab)
- CATIA Graphical Representation File
- Dicom files
- Executable Scripts (py, sh, bat)
- Flash Video (flv)
- Game Boy Advance Files (gba)
- Gif Files
- GZIP (gzip, gz)
- HTML Help (chm)
- HTTP Form data
- iPhone Application File (ipa)
- Ipt files
- ISO Archive (Iso)
- Java Applet (jar, class)
- JavaScript (js)
- Jpeg Files
- Kml files
- Microsoft Excel (xls, xlsx, xlsm, xlam, xlsb, slk)
- Microsoft Installer (msi)
- Microsoft MDB (mdb)
- Microsoft Outlook Message (msg)
- Microsoft PowerPoint (ppt, pptx, pptm, potx, ppsx)
- Microsoft RTF (rtf)
- Microsoft Word (doc, docx, docm, dotx)
- MKV Files
- MP3 Files (mp3)
- MP4 Files (mp4)
- MPEG Video (mpeg, mpg)
- MS PST
- Nintendo DS Files (3ds, nds)
- Ogg Vorbis (ogg)
- Password Protected / Encrypted
- PDF Documents (pdf)
- Photoshop (psd)
- PlayStation Files (psx)
- Png Files
- Postscript (ps, eps)
- QuickTime Video (mov, qt)
- RAR Files (rar)
- Sega 32X Files (32x)
- SLDPRT File
- Stuffit Archive (stuffit_sit, stuffit)
- Tar (tgz, gtar, tar)
- Tiff files
- Undetectable File
- WAV Files (wav)
- webM Files
- WebP Files
- Window Meta Files (wmf)
- Windows Executables (exe, exe64)
- Windows Library (dll64, dll, ocx, sys, scr)
- Windows Media Video (wmv)
- Windows Shortcut (lnk)
- XBox Files (xipo, xtfo, xbeh)
- XPS
- ZIP (zip)
- ZIP w/Suspicious Script File (js, vbs, svg, ps1, hta, cmd, lnk)
[]Use this filter to view transactions in which a specific file type was either uploaded or downloaded. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Any
- Archive
- Audio
- Executable
- Image
- Microsoft Office
- Mobile
- Other
- Other Documents
- Video
- Web Content
[]Use this filter to view transactions associated with instant messaging applications. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Instant Messaging**. For the** IM Activity** filter, the default option is **Any**. You can search for specific activities. The following activities appear under the** IM Activity** filter:
- All
- Receive File
- Receive Message
- Send File
- Send Message
[]Use this filter to view transactions associated with a specific location. The default option for this filter is **All**. You can search for specific locations.
[]Use this filter to view transactions associated with a specific location group. The default option for this filter is **None**. You can search for specific location groups.
[]Use this filter to view transactions associated with a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
[]Use this filter to view transactions according to the action taken by the service for mobile device traffic. The default **All**, which displays all transactions. The following answers appear under this filter:
- All
- Allow
- Block
[]Use this filter to view transactions associated with a specific mobile application. The default option for this filter is **All**. You can search for specific applications. The following applications appear under this filter:
- All
- AccuWeather
- Adobe Reader
- ABC
- Amazon
- Android Native Email
- Android Weather
- AndroidZip Filemanager
- Angry Birds
- Angry Birds Rio
- Apple Maps
- Apple Music
- Audible for Android
- Aviary Effects
- Aviary Frames
- Aviary Stickers
- Bank of America Mobile Banking
- Barcode Scanner
- Bump
- Calorie Counter and Diet Tracker
- CBS Sports
- Chase Mobile(SM)
- Chrome
- CNN
- cPro Craigslist client for iPad
- Craigslist
- CVS Pharmacy
- Dominos Pizza USA
- Dropbox
- Duolingo
- eBay
- Epocrates
- ESPN Fantasy Football
- ESPN ScoreCenter
- Etsy
- Evernote
- Facebook
- Facebook Messenger
- Flipboard
- Gmail
- Go Launcher
- Google Android
- Google Drive
- Google Maps
- Google Play Movies & TV
- Google Search
- Google Translate
- Google+ Local
- GooglePlay Books
- Groupon
- Hangouts
- Home Depot Style Guide
- Hulu Plus
- iBooks
- iHeartRadio
- iOS email
- iPharmacy Drug Guide
- iTunes U
- Khan Academy
- Kindle
- Linkedin
- Lumosity
- Medscape
- Mint.com Personal Finance
- MX Player
- NetFlix
- NFL Mobile
- Nike+ running
- Nook
- NYT
- OfficeMobile
- Officesuit Viewer
- OpenTable
- Opera
- PAC-MAN Lite
- Pandora
- Paper Toss
- PayPal
- Pinterest
- Pizza Hut
- Quickoffice
- Redbox
- Ringtone Maker
- RunKeeper
- Safari
- Safari To Go
- Saks Fifth Avenue for iPad
- Shazam
- SkyMall
- Skype
- SpeechSynthesis Data Installer
- Speed Anatomy Quiz
- Spotify
- Starbucks
- talking tom
- Tattoo Designs
- TED
- Temple Run
- The Weather Channel
- theChive
- Touchdown
- Twitter
- Urbanspoon
- USA Today
- uTorrent Beta - Torrent App
- Viber
- Visual Anatomy Free
- Vitamio Plugin ARMv7
- WatchESPN
- Waze Social GPS
- Weather Bug
- Weight Watchers Mobile
- Wells Fargo Mobile
- WhatAPP Messenger
- XfinityTM TV Player
- Yahoo Messenger
- Yahoo Weather
- YahooMail
- YouTube
- Zillow Real Estate & Rentals
- Zscaler Safebrowser
[]Use this filter to view transactions associated with a specific mobile application category. The default option for this filter is **All**. You can search for specific categories. The following categories appear under this filter:
- All
- Adware
- Browser
- Business
- Catalogs
- Communication
- Device Information
- Dining/Restaurant
- Education
- Email
- Enterprise
- Entertainment
- Finance
- Games
- Geolocation
- Health
- Insecure Communication
- Libraries
- Lifestyle
- Malware App
- Medical Information
- Miscellaneous or Unknown
- Music
- News & Media
- Online Shopping
- Others
- PII
- Productivity
- Social Networking & Blogging
- Sports
- Streaming Media
- Third Party Communication
- Tools & Utilities
- Travel
- Vulnerable App
- Weather
- weRead
[]Use this filter to view transactions associated with a specific mobile application class. The default option for this filter is **All**. You can search for specific classes. The following classes appear under this filter:
- All
- General
- Privacy
- Security
[]Use this filter to find transactions associated with a specific mobile application. Enter all or part of the application name in the text field and choose **Contains**, **Starts With**, **Ends With**, or **Exact Match**.
[]Use this filter to view transactions associated with a specific mobile device. The default option for this filter is **All**. You can search for specific device types. The following device types appear under this filter:
- All
- Apple iPad
- Apple iPad Mini
- Apple iPhone
- Apple iPod
- Google Android
- iOS (Other)
- Nexus
- Others
- Samsung Galaxy S
- Samsung Note
- Samsung Others
- Windows Mobile
- Windows Touch
[]Use this filter to see if the certificate status verification using OCSP failed or passed. This filter applies to SSL inspected traffic. The default option for this filter is **None**. You can search for specific results. The following results appear under this filter:
- Good
- None
- Revoked
- Unknown
[]Use this filter to view the policy and rule that took action during the transaction. Following are the policy types that appear in this field:
- **Advanced Threat Protection**
- **Collaboration & Online Meetings App Control**: This refers to the [Collaboration & Online Meetings rule](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Consumer**: This refers to the [Consumer rule](/zia/adding-consumer-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Data Loss Prevention**: This refers to the [Data Loss Prevention policy](/zia/about-data-loss-prevention).
- **DNS**: This refers to [DNS Control policy](/zia/about-dns-control).
- **File Sharing**: This refers to the [File Sharing rule](/zia/adding-file-sharing-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **File Type Control**: This refers to the [File Type Control policy](/zia/about-file-type-control).
- **Firewall Filtering**: This refers to the [Firewall Control policy](/zia/about-firewall-control).
- **Hosting Providers**: This refers to the [Hosting Providers rule](/zia/adding-hosting-providers-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Instant Messaging**: This refers to the [Instant Messaging rule](/zia/adding-instant-messaging-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Intrusion Prevention**
- **IT Services**: This refers to the [IT Services rule](/zia/adding-it-services-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Mobile App Store Control**: This refers to the [Mobile App Store Control policy](/zia/about-mobile-app-store-control).
- **NAT Control**: This refers to the [NAT Control policy](/zia/about-nat-control).
- **Productivity and CRM Tools**: This refers to the [Productivity & CRM tools rule](/zia/adding-productivity-crm-tools-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Sales & Marketing**: This refers to the [Sales & Marketing rule](/zia/adding-sales-marketing-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Sandbox**: This refers to the [Sandbox policy](/zia/about-sandbox).
- **Social Networking/Blogging**: This refers to the [Social Networking & Blogging rule](/zia/adding-social-networking-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **Streaming Media**: This refers to the [Streaming Media rule](/zia/adding-streaming-media-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **System & Development**: This refers to the [System & Development rule](/zia/adding-system-development-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
- **URL Filtering**: This refers to the [URL filtering policy](/zia/about-url-filtering).
- **Webmail**: This refers to the [Webmail rule](/zia/adding-webmail-rule-cloud-app-control) for the [Cloud App Control policy](/zia/about-cloud-app-control).
[]Improve the visibility of protocols that traverse within Zscaler’s cloud. The following information is shown:
- **DNS over HTTPS**:Transactions from DNS over HTTPS websites.
- **FTP over HTTP**: Transactions from FTP over HTTP websites.
- **HTTP**: Transactions from HTTP websites.
- **HTTP Proxy:**Transactions from HTTP proxy servers.
- **HTTPS**: HTTPS transactions that have been inspected.
- **SSL**:Transactions from SSL/TLS connections that have not been inspected. For example, hosts you've [exempted from SSL inspection](/zia/about-ssl-inspection#configure-ssl-inspection-policy).
- **Tunnel**: Transactions from unidentified encrypted traffic. For example, tunneling applications (e.g., Telnet or SSH) that are encapsulated in HTTP or HTTPS.
- **Tunnel SSL**: Undecodable protocol within an SSL connection.
- **WebSocket**: Transactions from WebSocket websites.
- **WebSocket SSL**: Transactions from WebSocket websites encrypted by SSL.
[]Use this filter to view transactions based on the number of bytes a destination web server returned for an HTTP request. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0 - 1KB
- 1KB - 100KB
- 100KB - 1MB
- 1MB - 5MB
- 5MB - 10MB
- 10MB - 50MB
- 50MB - 100MB
- Above 100MB
- Custom
[]Use this filter to find transactions associated with a referrer URL, which is the URL from which an HTTP request originated. Enter all or part of the URL in the text field and choose **Contains**, **Starts With**, **Ends With**, or **Exact Match**.
[]Use this filter to view transactions associated with the web traffic of an HTTP request method. Choose **GET** to see transactions only for HTTP requests to retrieve data, or choose **POST** to see transactions only for HTTP requests to submit data to be processed. Post requests include email that was sent through webmail or posting on a social networking site or blog. The following request methods appear under this filter:
- appe
- Baselinecontrol
- Bcopy
- Bdelete
- Bmove
- Bpropfind
- Checkin
- Checkout
- Connect
- connect
- Copy
- cwd
- Delete
- Get
- Head
- invalid
- Label
- list
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
- retr
- Search
- stor
- Subscribe
- Trace
- Uncheckout
- Unlock
- Unsubscribe
- Update
- Versioncontrol
[]Use this filter to view file downloads based on the Sandbox result. The default option for this filter is **Any**. You can search for specific results The following results appear under this filter:
- **Sandbox Adware**:** **View known malicious results. This category refers to any malicious file sample installing persistent components to push advertising content to the user’s device. Often, these advertisements are unwanted and can lead to spyware or other grayware-oriented privacy violations.
- **Sandbox Anonymizer**:** **View known malicious results. This category refers to any malicious file sample exhibiting behavior consistent with anonymizer programs, such as Tor Browser or other VPN services, that essentially make a user’s internet activity untraceable.
- **Sandbox Benign**:** **View known non-malicious results. This is a catchall category for any non-malicious file sample with a Sandbox Threat Score equal to or less than 70. The Zscaler service refers to file samples that have a score between 40 and 70 as “suspicious” because they might need additional review.
- **Sandbox Malware**:** **View known malicious results. This is a catchall category for any malicious file sample that doesn't fall under the other Sandbox categories. Most Sandbox-classified file samples aren't clearly known to be a specific threat or malware family-oriented because there aren't specific signatures or indicators to categorize the file. Instead the Zscaler service categorizes the file based on an aggregation of the file’s OS and application behaviors and network activity.
- **Sandbox Suspicious**: This category refers to files that exhibit some malicious behaviors but are not fully classified as malware.
- **Sent for Analysis**: View unknown results that have been sent to the Sandbox for behavioral analysis.
[]Use this filter to view file downloads based on the Sandbox action. The default option for this filter is **None**. You can search for specific results. The following results appear under this filter:
- None
- Blocked
- Quarantined
- Sent for Analysis
[]Use this filter to view file download transactions based on the file hash value (MD5). Enter all or part of the MD5 in the text field and choose **Contains**, **Starts With**, **Ends With**, or **Exact Match**.
[]Use this filter to view transactions based on the size, in bytes, of the HTTP request that was sent to the destination web server. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0 - 1KB
- 1KB - 100KB
- 100KB - 1MB
- 1MB - 5MB
- 5MB - 10MB
- 10MB - 50MB
- 50MB - 100MB
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
- 0-3 months
- 3-12 months
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
[]Use this filter to view transactions associated with a destination server. Specify an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text field.
[]Use this filter to view any delayed logs.
[]Use this filter to view transactions associated with social networking sites. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Social Networking**. From the **Social Networking Activity** filter, the default option is **All**. You can search for specific activities. The following activities appear under the** Social Networking Activity** filter:
- All
- Publish
- View
[]Use this filter to view SSL inspected transactions. Select to view decrypted SSL transactions. Deselect to view SSL transactions that weren't decrypted.
[]Use this filter to view transactions associated with streaming media. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Streaming Media**. From the **Streaming** filter, the default option is **All**. You can search for specific activities. The following activities appear under the **Streaming** **Activity **filter:
- All
- Listen
- Upload
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
- **Ransomware**: This category refers to any detections of ransomware installers, agents, or related content through file reputation, signature matching (e.g., antivirus or YARA), or machine learning model techniques.
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
[]Use this filter to view transactions associated with a specific threat class.The default option for this filter is **Advanced Threats**. You can search for specific classes. The following classes appear under this filter:
- Advanced Threats
- Sandbox
- Viruses & Spyware
[]Use this filter to view transactions associated with a specific threat super category. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Any
- Malware
- Sandbox
- Spyware
- Virus
[]Use this filter to view transactions based on the total size of the HTTP request and response. The default option for this filter is **All Sizes**. You can search for specific sizes. The following sizes appear under this filter:
- All Sizes
- 0 - 1KB
- 1KB - 100KB
- 100KB - 1MB
- 1MB - 5MB
- 5MB - 10MB
- 10MB - 50MB
- 50MB - 100MB
- Above 100MB
- Custom
[]Use this filter to limit the data to traffic associated with a specific traffic forwarding mechanism. The following appear under this filter:
- GRE Tunnel
- IPSec Tunnel
- NAT Control
- PAC File
- PAC File over GRE Tunnel
- PAC File over IPSec Tunnel
- Policy Based Forwarding
- Zscaler Client Connector
- Zscaler Client Connector over GRE Tunnel
- Zscaler Client Connector over IPSEC Tunnel
[]Use this filter to view transactions associated with a specific URL category. The default option for this filter is **All**. You can search for specific categories.
[]Use this filter to limit the data to a specific URL super category. The default option for this filter is **All**. You can search for specific classes. The following classes appear under this filter:
- All
- Adv. Security Risk
- Bandwidth Loss
- Business Use
- General Surfing
- Legal Liability
- Privacy Risk
- Productivity Loss
[]Use this filter to find transactions associated with a specific URL.
- Choose a URL type to filter by:
- Click **URL** and enter all or part of the URL.
- For example: http://www.zscaler.com/products-user-security.php
- Click **Path** and enter all or part of the path information.
- For example: products-user-security.php
- Click **Host** and enter all or part of the host name.
- For example: www.zscaler.com
- Click **Domain** and enter all or part of the domain name.
- For example: Facebook
- Choose **Contains**, **Starts With**,** Ends With**,** **or **Exact Match**.
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
- Microsoft 365
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
[]Use this filter to view the transactions of a specific user. The default option for this filter is **All**. You can search for specific users. By default, user-related traffic data includes locations and users.
[]Use this filter to find transactions associated with the user-agent string that the browser included in its GET request. The user-agent string contains browser and system information that the destination server can use to provide appropriate content.
- The service lists the commonly-used user agents in the **Known** category. To find a user-agent string, click the **Known **tab and scroll or use the Search function to find the user-agent string in this category.
- If the user-agent string is not found, click **Unknown** and enter all or part of the user-agent string in the text field and choose** Contains**, **Starts With**,** Ends With**,** **or **Exact Match**. (Example: **Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:18.0) Gecko/20100101 Firefox/18.0**)
[]Use this filter to view transactions associated with webmail applications. When you select this filter, the dialog automatically adds the **Cloud Application Class** filter set to **Web Mail**. From the **Webmail Activity** filter, the default option is **All**. You can search for specific activities. The following activities appear under the **Webmail** **Activity **filter:
- All
- Send
- Send Attachment
- View