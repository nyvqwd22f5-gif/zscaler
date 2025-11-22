# NSS Feed Output Format: Endpoint DLP Logs
Source: https://help.zscaler.com/unified/nss-feed-output-format-endpoint-dlp-logs
PDF: https://help.zscaler.com/pdf/com/en/1497826.pdf

The Endpoint Data Loss Prevention (DLP) Nanolog Streaming Service (NSS) feed specifies the data from the Endpoint DLP logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample Endpoint DLP log.](#sample-logs)
The following tables display information about the Endpoint DLP log fields and possible values for those fields.
Fields that support obfuscation are documented in the following tables with the prefix `o` (e.g., `%s{ouser}`). To obfuscate a field, manually add the prefix `o` before the field name in the Feed Output Format in the Admin Portal.
Date/Time
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{time} | The log time (i.e., when a transaction is logged by the Zscaler Nanolog) | Mon Oct 16 22:55:48 2023 |
| %s{rtime} | The feed time (i.e., when a transaction is received by the NSS from the Nanolog) | Mon Oct 16 22:55:48 2023 |
| %s{eventtime} | The event time (i.e., when an event is intercepted and evaluated by the DLP service). An event (e.g., file copied to local drive) can be classified as an activity or as an incident, if it violates a DLP rule. | Mon Oct 16 22:55:48 2023 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 16 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2023 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
Scan Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %llu{scantime} | The scan time in milliseconds | 1210 |
| %u{numdlpengids} | The number of DLP engines hit | 12 |
| %u{numdlpdictids} | The number of DLP dictionaries hit | 8 |
| %llu{recordid} | The unique record identifier | 2 |
| %llu{scanned_bytes} | The scanned item (file or text) size in bytes | &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
290812 |
| %llu{dlpidentifier} | The unique DLP identifier | 12 |
User Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{user} | The username | TempUser |
| %s{ouser} | The obfuscated version of the username. This displays a random string. |  |
| %s{department} | The name of the department | TempDept |
| %s{odepartment} | The obfuscated version of the department name. This displays a random string. |  |
Device Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{devicename} | The device name | Dev 1 |
| %s{odevicename} | The obfuscated version of the device name. This displays a random string. |  |
| %s{devicetype} | The device type | WinUser |
| %s{deviceostype} | The device OS type | Windows |
| %s{deviceplatform} | The device platform | Windows |
| %s{deviceosversion} | The device OS version | Win-11 |
| %s{devicemodel} | The device model | Model-2022 |
| %s{deviceappversion} | The device application version | Ver-2199 |
| %s{deviceowner} | The device owner | Administrator |
| %s{odeviceowner} | The obfuscated version of the device owner. This displays a random string. |  |
| %s{devicehostname} | The device host name | Host |
| %s{odevicehostname} | The obfuscated version of the device host name. This displays a random string. |  |
Data Center Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | Georgia |
| %s{datacentercity} | The city where the data center is located | Atlanta |
| %s{datacentercountry} | The country where the data center is located | US |
File Information
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{filesrcpath} | The file source path | source_path |
| %s{ofilesrcpath} | The obfuscated version of the file source path. This displays a random string. |  |
| %s{filedstpath} | The file destination path | dest_path |
| %s{ofiledstpath} | The obfuscated version of the file destination path. This displays a random string. |  |
| %s{filemd5} | The file MD5 hash | 938c2cc0dcc05f2b68c4287040cfcf71 |
| %s{filesha} | The file SHA256 hash | 076085239f3a10b8f387c4e5d4261abf8d109aa641be35a8d4ed2d775eb09612 |
| %s{filetypename} | The file type | exe64 |
| %s{filetypecategory} | The file type category | PLS File (pls) |
| %s{filedoctype} | The file document type | Medical |
| %s{itemtype} | The item (file or text) type | email_attachment |
| %s{srctype} | The source type | network_share |
| %s{dsttype} | The destination type | personal_cloud_storage |
| %s{itemname} | The item name | endpoint_dlp |
| %s{oitemname} | The obfuscated version of the item name. This displays a random string. |  |
| %s{itemsrcname} | The item source name | endpoint |
| %s{oitemsrcname} | The obfuscated version of the item source name. This displays a random string. |  |
| %s{itemdstname} | The item destination name | nanolog |
| %s{oitemdstname} | The obfuscated version of the item destination name. This displays a random string. |  |
DLP Information
-
-
-
-
-
-
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{dlpengnames} | The DLP engine names | &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
dlpengine |
| %s{odlpengnames} | The obfuscated version of the DLP engine names. This displays a random string. |  |
| %s{dlpdictnames} | The DLP dictionary names | [dlp] |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names. This displays a random string. |  |
| %s{dlpcounts} | &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
The number of hits for each of the DLP dictionaries | &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
[12,13] |
| %s{confirmaction} | The confirmation action by the user | confirm |
| %s{actiontaken} | The action taken by Endpoint DLP | allow |
| %s{severity} | The severity of the event. An event is either an incident or a sensitive activity. An incident violates an Endpoint DLP rule and the severity (High, Medium, Low, Info) is based on the rule that was violated. A sensitive activity does not violate a rule and is reported for visibility (Info). | High SeverityMedium SeverityLow SeverityInfo Severity |
| %s{triggeredrulelabel} | The DLP rule that was triggered. &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
An event can trigger multiple rules, out of which the DLP service applies the most restrictive rule. The applied rule is the "triggered" rule, while the other rules are stored as "other" rules (i.e., `%s{otherrulelabels}`). | configured_rule |
| %s{otriggeredrulelabel} | The obfuscated version of the triggered DLP rule. This displays a random string. |  |
| %s{otherrulelabels} | The labels of other rules that were triggered. See `%s{triggeredrulelabel}`. | [none] |
| %s{ootherrulelabels} | The obfuscated version of the other rule labels. This displays a random string. |  |
| %s{logtype} | The type of record | dlp_incidentsensitive_activity |
| %s{channel} | The channel | Network Drive Transfer |
| %s{activitytype} | The activity type | email_sent |
| %s{expectedaction} | The expected action by Endpoint DLP | block |
| %s{zdpmode} | The ZDP mode | block mode |
| %s{addinfo} | &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
Additional information | File already open by another application |
| %s{confirmjust} | &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
The confirmation action justification by the user | My manager approved it |
b64 Fields
A SIEM can have parsing issues whenever a string field has non-printable or delimiter characters. For that reason, the Zscaler service has URL encoding for URL fields like URL, Referer, and Hostname. There are several other fields that have the same parsing issue, but URL encoding is not suitable. Such fields are encoded using b64.
Turning on b64 encoding for all supported fields may result in approximately a 20% drop in performance.
The following fields have been added as b64 fields:
- b64user
- b64department
- b64devicename
- b64deviceowner
- b64devicehostname
- b64itemname
- b64itemsrcname
- b64itemdstname
- b64dlpengnames
- b64filesrcpath
- b64filedstpath
- b64dlpdictnames
- b64otherrulelabels
- b64triggeredrulelabel
Hex-Encoded Fields
The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than or equal to 0x20, or greater than or equal to 0x7F, is encoded as `%HH`. This ensures that your SIEM can parse the URLs that contain control characters. For example, a `\n` character in a URL is encoded as `%0A`, and a space is encoded as `%20`.
The following fields have been added as hex-encoded fields:
- euser
- edepartment
- edevicename
- edeviceowner
- edevicehostname
- eitemname
- eitemsrcname
- eitemdstname
- edlpengnames
- efilesrcpath
- efiledstpath
- edlpdictnames
- eotherrulelabels
- etriggeredrulelabel
[]"Tue May 30 18:07:54 2023","7239038846486118403","ZDP","Unknown","","txt","b29e01ed4bde24b0f8edb1fd4816e982","Credit Cards: Detect leakage of credit card information","10","5 or more Credit Card Numbers","Network Drive Transfer","Confirm Allow","High Severity","NA"