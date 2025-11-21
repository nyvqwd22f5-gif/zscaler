# NSS Feed Output Format: SaaS Security Logs
Source: https://help.zscaler.com/zia/nss-feed-output-format-saas-security-logs
PDF: https://help.zscaler.com/pdf/com/en/1401651.pdf

Some sections in this article include table pagination. Use the Search function in those tables to find your desired field.
The SaaS Security Nanolog Streaming Service (NSS) feed specifies the data from the SaaS Security logs that the NSS sends to the security information and event management (SIEM) system. You can configure an NSS feed by including one or more fields. The fields and their values display in the NSS feed output.
- [View a sample SaaS Security log.](#nss-feed-output-saas-security-example)
The following tables display information about the SaaS Security log fields and possible values for those fields.
Fields that support obfuscation are documented in the following tables with the prefix `o` (e.g., `%s{ofileid}`). To obfuscate a field, manually add the prefix `o` before the field name in the Feed Output Format in the ZIA Admin Portal.
Collaboration
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{orulelabel} | The obfuscated name of the rule that triggered on the session or aggregated sessions | 3399565100 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPCOLLABOfflineCASBAVPCOLLAB |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 13 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2025 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{owner} | The username or email address of the user who performs the transaction | john.smith@example.com |
| %s{oowner} | The obfuscated username or email address of the user who performs the transaction | 6200694987 |
| %s{department} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %s{any_incident} | Indicates whether the transaction was an incident or not | Yes|No |
| %s{extownername} | The file owners (inside or outside your organization) who are not provisioned to Zscaler Internet Access (ZIA) | jane@yahoo.com |
| %s{oextownername} | The obfuscated version of the file owners (inside or outside your organization) who are not provisioned to ZIA | 753148 |
| %s{msgid} | The message ID assigned by the application | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{omsgid} | The obfuscated version of the message ID assigned by the application | 53002959807956407282 |
| %s{internal_recptnames} | The names of the internal recipients | john@yahoo.com|doe@gmail.com |
| %s{ointernal_recptnames} | The obfuscated version of the internal recipient names | 243561|779116 |
| %s{external_recptnames} | The names of the external recipient names | jane@yahoo.com|roe@gmail.com |
| %s{oexternal_recptnames} | The obfuscated version of the external recipient names | 753148|091212 |
| %s{sharedchannel_hostname} | The hostname of the shared channel | google.com |
| %s{osharedchannel_hostname} | The obfuscated version of the hostname of the shared channel | 63897110953 |
| %s{sender} | The sender's email | johndoe@slack.com |
| %s{osender} | The obfuscated version of the sender's email | 9854901 |
| %s{channel_name} | The name of the channel | demo-ops |
| %s{ochannel_name} | The obfuscated version of the channel name | 9769110 |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names | 10831489 |
| %s{dlpenginenames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %s{odlpenginenames} | The obfuscated version of the DLP engine names | 4094304256 |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{dlpdictcount} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{company} | The company name | Zscaler |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{otenant} | The obfuscated version of the SaaS application tenant | 8794487099 |
| %s{applicationname} | The name of the sanctioned SaaS application | Slack |
| %s{upload_doctypename} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
CRM
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{orulelabel} | The obfuscated name of the rule that triggered on the session or aggregated sessions | 3399565100 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPCRMOfflineCASBAVPCRM |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 13 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2025 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{owner} | The username or email address of the user who performs the transaction | john.smith@example.com |
| %s{oowner} | The obfuscated username or email address of the user who performs the transaction | 6200694987 |
| %s{department} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %d{num_internal_collab} | The number of internal collaborators | 8 |
| %d{num_external_collab} | The number of external collaborators | 8 |
| %s{objectname} | The name of the object logged | resolve issue |
| %s{objecttype} | The type of the object logged | task |
| %s{file_msg_id} | The file/message ID assigned by the application | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{ofile_msg_id} | The obfuscated file/message ID assigned by the application | 53002959807956407282 |
| %s{filetypecategory} | The category of the file type | executable |
| %s{hostname} | The hostname of the recorded internal URL | www.servicenow.com |
| %s{ohostname} | The obfuscated version of the hostname | 803951 |
| %s{fullurl} | The SaaS Security public URL used to access a shared file | zscaler2.box.com/v/123456789010 |
| %s{ofullurl} | The obfuscated version of the full URL | 30521954 |
| %s{extownername} | The file owners (inside or outside your organization) who are not provisioned to Zscaler Internet Access (ZIA) | jane@yahoo.com |
| %s{oextownername} | The obfuscated version of the file owners (inside or outside your organization) who are not provisioned to ZIA | 753148 |
| %s{internal_collabnames} | The names of internal collaborators | john@yahoo.com|doe@gmail.com |
| %s{ointernal_collabnames} | The obfuscated version of the internal collaborator names | 243561|779116 |
| %s{external_collabnames} | The names of external collaborators | jane@yahoo.com|roe@gmail.com |
| %s{oexternal_collabnames} | The obfuscated version of external collaborator names | 753148|091212 |
| %d{filesize} | The size of the file in bytes | 4061912 |
| %s{file_msg_mod_time} | The last modification time of the file/message | Tue Feb 6 17:25:08 2024 |
| %s{filepath} | The file path | var/www/html/index.html |
| %s{component} | The type of component recorded | Message |
| %s{sha} | The SHA-256 hash for the file | ceeedc88dc02cd599865e89696f2bc33a049dc823a698183d429b9bc65735a3a |
| %s{collabscope} | The collaboration scope and permissions for SaaS application tenant files | External Collaborators - ViewInternal Collaborators - EditPrivate - Edit |
| %s{filemd5} | The MD5 hash for the file | 3ce0e6d87e586b7e898b624e4a7cf4ef |
| %s{filename} | The name of the suspicious file detected by the Data at Rest Scanning policy | test.pdf |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names | 10831489 |
| %s{dlpenginenames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %s{odlpenginenames} | The obfuscated version of the DLP engine names | 4094304256 |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{dlpdictcount} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{company} | The company name | Zscaler |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{otenant} | The obfuscated version of the SaaS application tenant | 8794487099 |
| %s{applicationname} | The name of the sanctioned SaaS application | Salesforce |
| %s{upload_doctypename} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
Email
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{orulelabel} | The obfuscated name of the rule that triggered on the session or aggregated sessions | 3399565100 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPEMailOfflineCASBAVEMail |
| %d{filescantimems} | The amount of time (in milliseconds) the Data at Rest Scanning policy took to scan content within the tenant | 2128 |
| %d{filedownloadtimems} | The download time (in milliseconds) of the suspicious file detected by the Data at Rest Scanning policy | 1469 |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 13 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2025 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{owner} | The username or email address of the user who performs the transaction | john.smith@example.com |
| %s{oowner} | The obfuscated username or email address of the user who performs the transaction | 6200694987 |
| %s{department} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %s{any_incident} | Indicates whether the transaction was an incident or not | Yes|No |
| %s{attchcomponentfilenames} | The name of the suspicious file detected by the Data at Rest Scanning policy | test.pdf |
| %s{oattchcomponentfilenames} | The obfuscated version of the name of the suspicious file detected by the Data at Rest Scanning policy | 8794487099 |
| %s{attchcomponentfilesizes} | The size of the file in bytes | 6721 |
| %s{attchcomponentfiletypes} | The component file type | executable |
| %s{attchcomponentmd5s} | The component file MD5 | 3ce0e6d87e586b7e898b624e4a7cf4ef |
| %s{is_inbound} | Indicates whether the email was sent or received or not | Yes|No |
| %s{messageid} | The message ID assigned by the application | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{omessageid} | The obfuscated version of the message ID assigned by the application | 62006949870624054738 |
| %d{msgsize} | The size of the message in bytes | 4061912 |
| %d{num_ext_recpts} | The number of external recipients | 8 |
| %d{num_int_recpts} | The number of internal recipients | 8 |
| %d{repochtime} | The time at which the transaction was recorded in epoch | 1578128400 |
| %s{rtime} | The time at which the transaction was recorded | Wed Nov 26 06:13:01 2025 |
| %s{externalownername} | The file owners (inside or outside your organization) who are not provisioned to Zscaler Internet Access (ZIA) | jane@yahoo.com |
| %s{oexternalownername} | The obfuscated version of the file owners (inside or outside your organization) who are not provisioned to ZIA | 753148 |
| %s{extrecptnames} | The names of external recipients | jane@yahoo.com|roe@gmail.com |
| %s{oextrecptnames} | The obfuscated version of the names of external recipients | 091212|753148 |
| %s{intrecptnames} | The names of internal recipients | jane@yahoo.com|roe@gmail.com |
| %s{ointrecptnames} | The obfuscated version of the names of internal recipients | 091212|753148 |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names | 10831489 |
| %s{dlpenginenames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %s{odlpenginenames} | The obfuscated version of the DLP engine names | 4094304256 |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{dlpdictcount} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{company} | The company name | Zscaler |
| %d{companyid} | The numeric ID given to a company by Zscaler | 98210 |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{otenant} | The obfuscated version of the SaaS application tenant | 8794487099 |
| %s{applicationname} | The name of the sanctioned SaaS application | Gmail |
| %s{upload_doctypename} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
File
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{orulelabel} | The obfuscated name of the rule that triggered on the session or aggregated sessions | 3399565100 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPFileOfflineCASBAVFile |
| %d{filescantimems} | The amount of time (in milliseconds) the Data at Rest Scanning policy took to scan content within the tenant | 2128 |
| %d{filedownloadtimems} | The download time (in milliseconds) of the suspicious file detected by the Data at Rest Scanning policy | 1469 |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 13 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2025 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{user} | The username or email address of the user who performs the transaction. If an internet gateway location is specified and authentication is not required, this field displays the name of the gateway location. | john.smith@example.com |
| %s{ouser} | The obfuscated username or email address of the user who performs the transaction | 6200694987 |
| %s{department} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %s{fileid} | The file ID value in a string format | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{ofileid} | The obfuscated version of the file ID value in a string format | 4673175314 |
| %s{filename} | The name of the suspicious file detected by the Data at Rest Scanning policy | test.pdf |
| %s{filetypename} | The type of file that was either uploaded or downloaded | exepdfppt |
| %s{filesource} | The source location of the files containing sensitive data that were detected by the Data at Rest Scanning DLP or Malware Detection policy | /All Files/10.65.1.220_2/compressed/test |
| %d{filesize} | The file size | 6721 |
| %s{lastmodtime} | The file modification time. The date and time when a Data at Rest Scanning DLP policy modified the collaboration scope for SaaS application tenant files. | Wed Nov 26 06:13:01 2025 |
| %d{epochlastmodtime} | The file modification time in epoch format |  |
| %s{filemd5} | The MD5 hash for the file | 3ce0e6d87e586b7e898b624e4a7cf4ef |
| %s{fullurl} | The SaaS Security public URL used to access a shared file | zscaler2.box.com/v/123456789010 |
| %s{ofullurl} | The obfuscated version of the SaaS Security public URL used to access a shared file | 30521954 |
| %s{suburl} | The URI portion of the full URL | /123456789010 |
| %s{hostname} | The hostname of the recorded internal URL | www.servicenow.com |
| %s{ohostname} | The obfuscated version of the hostname | 803951 |
| %s{extownername} | The file owners (inside or outside your organization) who are not provisioned to Zscaler Internet Access (ZIA) | jane@yahoo.com |
| %s{oextownername} | The obfuscated version of the file owners (inside or outside your organization) who are not provisioned to ZIA | 753148 |
| %s{intcollabnames} | The names of the internal collaborators on the file | john@yahoo.com|doe@gmail.com |
| %s{ointcollabnames} | The obfuscated version of the names of the internal collaborators on the file | 243561|779116 |
| %s{extcollabnames} | The names of the external collaborators on the file | jane@yahoo.com|roe@gmail.com |
| %s{oextcollabnames} | The obfuscated version of the names of the external collaborators on the file | 753148|091212 |
| %s{intcollab_groups} | The group of collaborators within your organization with whom the user shares assets. The field can have up to 8 values separated by a vertical line ("|") | priyanshu internal|priyanshu external|priyanshu different owner-member|priyanshu internal duplicate|priyanshu non user |
| %s{ointcollab_groups} | The obfuscated version of the group of collaborators within your organization with whom the user shares assets. The field can have up to 8 values separated by a vertical line ("|") | 2386907809385095456|2386907809401872672|2386907802690920736|2386907809418649888|2386907809485758752 |
| %s{extcollab_groups} | The group of collaborators outside your organization with whom the user shares assets. The field can have up to 8 values separated by a vertical line ("|") | priyanshu external internal|Priyanshu Nested Group Lev98 |
| %s{oextcollab_groups} | The obfuscated version of the group of collaborators outside your organization with whom the user shares assets. The field can have up to 8 values separated by a vertical line ("|") | 2386907809368318240|2386907809989075232 |
| %s{collabscope} | The collaboration scope and permissions for SaaS application tenant files | External Collaborators - ViewInternal Collaborators - EditPrivate - Edit |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names | 10831489 |
| %s{dlpenginenames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %s{odlpenginenames} | The obfuscated version of the DLP engine names | 4094304256 |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{dlpdictcount} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{company} | The company name | Zscaler |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{otenant} | The obfuscated version of the SaaS application tenant | 8794487099 |
| %s{applicationname} | The name of the sanctioned SaaS application | Box |
| %s{upload_doctypename} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
| %s{last_edit_user} | The user who last modified the file that triggered the DLP violation | john@yahoo.com |
| %s{last_share_user} | The user who last shared the file that triggered the DLP violation | john@yahoo.com |
| %s{last_shared_on} | The date and time when the file was shared | Mon Oct 29 07:18:01 2025 |
Gen AI
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %d{ss} | Seconds (0–59) | 48 |
| %d{mm} | Minutes (0–59) | 55 |
| %d{hh} | Hours (0–23) | 22 |
| %s{day} | The day of the week | Mon |
| %d{dd} | The day of the month (1–31) | 13 |
| %s{mon} | The name of the month | Oct |
| %d{mth} | The month of the year | 10 |
| %d{yyyy} | Year | 2025 |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %s{company} | The company name | Zscaler |
| %s{owner} | The username or email address of the internal or external user who performs the transaction | john.smith@example.comjane@yahoo.com |
| %s{username} | The username or email address of the internal user who performs the transaction. If an internet gateway location is specified and authentication is not required, this field displays the name of the gateway location. | john.smith@example.com |
| %s{extusername} | The username or email address of the external user who performs the transaction | jane@yahoo.com |
| %s{departmentname} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{appname} | The name of the sanctioned SaaS application | ChatGPT |
| %s{any_incident} | Indicates whether the transaction was an incident or not | Yes|No |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPGENAIOfflineCASBAVPGENAI |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{dlpdictcnts} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{dlpengnames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{sender_type} | The type of sender (i.e., bot, system, or user) | Bot |
| %s{botname} | The name of the bot | PREDEFINED_GPT |
| %s{component} | The type of component recorded | Message |
| %s{msgid} | The message ID assigned by the application | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{filename} | The name of the suspicious file detected by the Data at Rest Scanning policy | test.pdf |
| %s{filetype} | The type of file that either uploaded or downloaded | exepdfppt |
| %s{file_doctype} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
| %d{filesize} | The size of the file in bytes | 4061912 |
| %s{filemd5} | The MD5 hash for the file | 3ce0e6d87e586b7e898b624e4a7cf4ef |
| %s{filesha} | The SHA-256 hash for the file | ceeedc88dc02cd599865e89696f2bc33a049dc823a698183d429b9bc65735a3a |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %d{scan_time} | The amount of time (in milliseconds) the Data at Rest Scanning policy took to scan content within the tenant | 2128 |
| %d{download_time} | The download time (in milliseconds) of the suspicious file detected by the Data at Rest Scanning policy | 1469 |
| %d{scanid} | The unique identifier of the scan defined in the Historic Scan Configuration | 2 |
| %d{runid} | The unique identifier of the run (i.e., when a scan is stopped and started) | 27 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{upload_doc_subtype} | The subtype of the document uploaded or downloaded during the transaction | Financial Statements: Income Statements (Profit and Loss Statements) |
ITSM
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{orulelabel} | The obfuscated name of the rule that triggered on the session or aggregated sessions | 3399565100 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPITSMOfflineCASBAVPITSM |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 13 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2025 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{owner} | The username or email address of the user who performs the transaction | john.smith@example.com |
| %s{oowner} | The obfuscated username or email address of the user who performs the transaction | 6200694987 |
| %s{department} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %d{num_internal_collab} | The number of internal collaborators | 8 |
| %d{num_external_collab} | The number of external collaborators | 8 |
| %s{objectname} | The name of the object logged | resolve issue |
| %s{objecttype} | The type of the object logged | task |
| %s{file_msg_id} | The file/message ID assigned by the application | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{ofile_msg_id} | The obfuscated file/message ID assigned by the application | 53002959807956407282 |
| %s{filetypecategory} | The category of the file type | executable |
| %s{hostname} | The hostname of the recorded internal URL | www.servicenow.com |
| %s{ohostname} | The obfuscated version of the hostname | 803951 |
| %s{fullurl} | The SaaS Security public URL used to access a shared file | zscaler2.box.com/v/123456789010 |
| %s{ofullurl} | The obfuscated version of the full URL | 30521954 |
| %s{extownername} | The file owners (inside or outside your organization) who are not provisioned to Zscaler Internet Access (ZIA) | jane@yahoo.com |
| %s{oextownername} | The obfuscated version of the file owners (inside or outside your organization) who are not provisioned to ZIA | 753148 |
| %s{internal_collabnames} | The names of internal collaborators | john@yahoo.com|doe@gmail.com |
| %s{ointernal_collabnames} | The obfuscated version of the internal collaborator names | 243561|779116 |
| %s{external_collabnames} | The names of external collaborators | jane@yahoo.com|roe@gmail.com |
| %s{oexternal_collabnames} | The obfuscated version of external collaborator names | 753148|091212 |
| %d{filesize} | The size of the file in bytes | 4061912 |
| %s{file_msg_mod_time} | The last modification time of the file/message | Tue Feb 6 17:25:08 2024 |
| %s{filepath} | The file path | var/www/html/index.html |
| %s{component} | The type of component recorded | Message |
| %s{sha} | The SHA-256 hash for the file | ceeedc88dc02cd599865e89696f2bc33a049dc823a698183d429b9bc65735a3a |
| %s{filemd5} | The MD5 hash for the file | 3ce0e6d87e586b7e898b624e4a7cf4ef |
| %s{filename} | The name of the suspicious file detected by the Data at Rest Scanning policy | test.pdf |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names | 10831489 |
| %s{dlpenginenames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %s{odlpenginenames} | The obfuscated version of the DLP engine names | 4094304256 |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{dlpdictcount} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{company} | The company name | Zscaler |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{otenant} | The obfuscated version of the SaaS application tenant | 8794487099 |
| %s{applicationname} | The name of the sanctioned SaaS application | ServiceNow |
| %s{upload_doctypename} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
Public Cloud Storage
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{orulelabel} | The obfuscated name of the rule that triggered on the session or aggregated sessions | 3399565100 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPSTORAGEOfflineCASBAVPSTORAGE |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 13 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2025 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{owner} | The username or email address of the user who performs the transaction | john.smith@example.com |
| %s{oowner} | The obfuscated username or email address of the user who performs the transaction | 6200694987 |
| %s{department} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %s{hostname} | The hostname of the recorded internal URL | www.servicenow.com |
| %s{ohostname} | The obfuscated version of the hostname | 803951 |
| %s{fullurl} | The SaaS Security public URL used to access a shared file | zscaler2.box.com/v/123456789010 |
| %s{ofullurl} | The obfuscated version of the full URL | 30521954 |
| %s{extownername} | The file owners (inside or outside your organization) who are not provisioned to Zscaler Internet Access (ZIA) | jane@yahoo.com |
| %s{oextownername} | The obfuscated version of the file owners (inside or outside your organization) who are not provisioned to ZIA | 753148 |
| %s{collabnames} | The names of the collaborators | john@gmail.com|doe@yahoo.com |
| %s{ocollabnames} | The obfuscated version of the names of the collaborators | 243561|779116 |
| %d{numcollab} | The number of collaborators | 8 |
| %d{bucketid} | The bucket ID | 26 |
| %s{bucketname} | The bucket name |  |
| %s{obucketname} | The obfuscated version of the bucket name | 87944 |
| %s{bucketowner} | The bucket owner |  |
| %s{obucketowner} | The obfuscated version of the bucket name | 87099 |
| %s{fileid} | The file ID value in a string format | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{ofileid} | The obfuscated version of the file ID value in a string format | 4673175314 |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names | 10831489 |
| %s{dlpenginenames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %s{odlpenginenames} | The obfuscated version of the DLP engine names | 4094304256 |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{dlpdictcount} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{company} | The company name | Zscaler |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{otenant} | The obfuscated version of the SaaS application tenant | 8794487099 |
| %s{applicationname} | The name of the sanctioned SaaS application | Amazon S3 |
| %s{upload_doctypename} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
Repository
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
| Field | Description | Example |
| ----- | ----------- | ------- |
| %s{datacenter} | The name of the data center | CA Client Node DC |
| %s{datacentercity} | The city where the data center is located | Sa |
| %s{datacentercountry} | The country where the data center is located | US |
| %s{policy} | The Data at Rest Scanning policy rule action | NoneRevoke Sharing/Make PrivateFailed to revoke Sharing/Make PrivateMake internal sharing read onlyQuarantine Malware |
| %s{rulelabel} | The name of the rule that triggered on the session or aggregated sessions | DLP-Rule-1 |
| %s{orulelabel} | The obfuscated name of the rule that triggered on the session or aggregated sessions | 3399565100 |
| %s{ruletype} | The type of policy that took action during the transaction | OfflineCASBDLPREPOOfflineCASBAVPREPO |
| %s{time} | The time and date of the transaction. This excludes the time zone. | Mon Oct 13 22:55:48 2025 |
| %s{tz} | The time zone. This is the same as the time zone you specified when you configured the NSS feed. | GMT |
| %02d{ss} | Seconds (0–59) | 48 |
| %02d{mm} | Minutes (0–59) | 55 |
| %02d{hh} | Hours (0–23) | 22 |
| %02d{dd} | The day of the month (1–31) | 13 |
| %02d{mth} | The month of the year | 10 |
| %04d{yyyy} | Year | 2025 |
| %s{mon} | The name of the month | Oct |
| %s{day} | The day of the week | Mon |
| %d{epochtime} | The time of the incident in epoch format | 1578128400 |
| %d{recordid} | The unique record identifier for each log | 7353686396818817024 |
| %s{owner} | The username or email address of the user who performs the transaction | john.smith@example.com |
| %s{oowner} | The obfuscated username or email address of the user who performs the transaction | 6200694987 |
| %s{department} | The user's department. If authentication is not required and the traffic comes from a location specified in the service, this field displays the name of the gateway location. | Sales |
| %d{num_external_collab} | The number of external collaborators | 8 |
| %s{fileid} | The file ID value in a string format | 196a3d797bfee07fe4596b69f4ce1141 |
| %s{ofileid} | The obfuscated version of the file ID value in a string format | 4673175314 |
| %s{filetypecategory} | The category of the file type | executable |
| %s{extownername} | The file owners (inside or outside your organization) who are not provisioned to Zscaler Internet Access (ZIA) | jane@yahoo.com |
| %s{oextownername} | The obfuscated version of the file owners (inside or outside your organization) who are not provisioned to ZIA | 753148 |
| %s{internal_collabnames} | The names of internal collaborators | john@yahoo.com|doe@gmail.com |
| %s{ointernal_collabnames} | The obfuscated version of the internal collaborator names | 243561|779116 |
| %s{external_collabnames} | The names of external collaborators | jane@yahoo.com|roe@gmail.com |
| %s{oexternal_collabnames} | The obfuscated version of external collaborator names | 753148|091212 |
| %d{filesize} | The size of the file in bytes | 4061912 |
| %s{filepath} | The file path | var/www/html/index.html |
| %s{sha} | The SHA-256 hash for the file | ceeedc88dc02cd599865e89696f2bc33a049dc823a698183d429b9bc65735a3a |
| %s{filemd5} | The MD5 hash for the file | 3ce0e6d87e586b7e898b624e4a7cf4ef |
| %s{filename} | The name of the suspicious file detected by the Data at Rest Scanning policy | test.pdf |
| %s{dlpdictnames} | The Data Loss Prevention (DLP) dictionary names | Credit Cards|Gambling|MRN Numbers |
| %s{odlpdictnames} | The obfuscated version of the DLP dictionary names | 10831489 |
| %s{dlpenginenames} | The DLP engine names | HIPAA|PCI|Social Security Numbers |
| %s{odlpenginenames} | The obfuscated version of the DLP engine names | 4094304256 |
| %d{dlpidentifier} | The DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. | 6646484838839025669 |
| %s{dlpdictcount} | The number of hits for each of the DLP dictionaries that were matched in the transaction. This displays a string field separated by a vertical line ("|"). | 4|5|1|2 |
| %s{severity} | The severity level of the incident detected by the Data at Rest Scanning DLP policy | HighMediumLowInformation |
| %s{malware} | If the service detects a threat in the transaction, it displays the virus or spyware type, if applicable | WormTrojanRansomware |
| %s{malwareclass} | If the service detects a threat in the transaction, it displays the virus and spyware super category, if applicable | NoneVirusSpywareOther MalwareAdvance threatBehavior Analysis |
| %s{threatname} | If the service detects a threat in the transaction, it displays the name of the threat | EICAR Test File |
| %s{company} | The company name | Zscaler |
| %s{tenant} | The sanctioned SaaS application tenant integrated with the Zscaler service | QA-Tenant |
| %s{otenant} | The obfuscated version of the SaaS application tenant | 8794487099 |
| %s{applicationname} | The name of the sanctioned SaaS application | GitHub |
| %s{upload_doctypename} | The type of document uploaded or downloaded during the transaction | Corporate FinanceCourt FormDMVInsuranceLegal |
| %s{projectname} | The name of the project | Purchase Service |
| %s{reponame} | The name of the repository | purchase-rest-service |
Base64 Fields
A SIEM can have parsing issues whenever a string field has non-printable or delimiter characters. For that reason, the Zscaler service has URL encoding for URL fields like URL, Referer, and Hostname. There are several other fields that have the same parsing issue, but URL encoding is not suitable. Such fields are encoded using b64.
Turning on b64 encoding for all supported fields may result in approximately a 20% drop in performance.
The following are b64 fields:
- b64objectname
- b64filename
- b64hostname
- b64fullurl
- b64internal_collabnames
- b64external_collabnames
- b64intcollab_groups
- b64extcollab_groups
- b64filepath
- b64internal_recptnames
- b64external_recptnames
- b64channel_hostname
- b64sender
- b64projectname
- b64reponame
- b64bucketname
- b64bucketower
- b64collabnames
- b64filesource
- b64owner
- b64attchcomponentfilenames
- b64attchcomponentfilesizes
- b64attchcomponentfiletypes
- b64attchcomponentmd5s
- b64department
- b64dlpdictnames
- b64dlpenginenames
- b64extownername
- b64extrecptnames
- b64intrecptnames
- b64rulelabel
- b64tenant
- b64threatname
Hex-Encoded Fields
The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than or equal to 0x20, or greater than or equal to 0x7F, is encoded as `%HH`. This ensures that your SIEM can parse the URLs that contain control characters. For example, a `\n` character in a URL is encoded as `%0A`, and a space is encoded as `%20`.
The following are hex-encoded fields:
- efilename
- efilepath
- efullurl
- ehostname
- einternal_collabnames
- eexternal_collabnames
- eobjectname
- eprojectname
- ereponame
- ebucketname
- ebucketowner
- ecollabnames
- efilesource
- eowner
- eattchcomponentfilenames
- eattchcomponentfiletypes
- edepartment
- edlpdictnames
- edlpenginenames
- eextownername
- eextrecptnames
- eintrecptnames
- ethreatname
- esender
[]"Wed Aug 17 15:35:15 2022","7132869149011804161","pthalla","sp-new-tenant","admin@zslr.onmicrosoft.com","p_dept","SHAREPOINT","sanity2022-08-16 14-03.pdf","/sites/tanya/Shared%20Documents/Activity","01565bf41f1cb993d69334f409835293","malpdf","Quarantine Malware","None","None","None","Unknown URL","Tue Aug 16 14:03:13 2022","537","435"