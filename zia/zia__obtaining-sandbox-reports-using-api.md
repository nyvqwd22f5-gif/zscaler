# Obtaining Sandbox Reports Using API
Source: https://help.zscaler.com/zia/obtaining-sandbox-reports-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400811.pdf

Sandbox Report API resources are only accessible to Sandbox subscribers.
Sandbox Report API resources allow you to get a Sandbox Detail Report for any file that was sent for analysis from any organization on Zscaler cloud. Zscaler stores Sandbox Detail Reports for all files that were detonated within Sandbox. Therefore, information such as the threat name, threat score, category, etc. is available within a report. However, the sample file itself and any potentially sensitive information such as screenshots or filenames are removed
To learn more, see [About Sandbox](/zia/about-sandbox).
Determining your Quota for the Sandbox Report API
The resource access quota for retrieving Sandbox Detail Reports is restricted to 3,000 requests per day, with a [rate limit](/zia/understanding-rate-limiting) of 2/sec and 1,000/hour.
Getting the Sandbox Report API quota allows you to monitor your organization's used, unused, and allocated quota on a daily basis. To determine your quota, send a `GET` request to `/sandbox/report/quota`. For example, in Python:
conn.request("GET", "/api/v1/sandbox/report/quota", headers=headers)
To learn more, see Sandbox Report in the [API Reference](/zia/sandbox-report).
Getting a Full or Summary Sandbox Detail Report
To get a full (i.e., complete) or summary Sandbox Detail Report, send a `GET` request to `/sandbox/report/{md5Hash}` and specify whether the `details` parameter should be `full` or `summary`. For example, in Python, you would use the following code to get a `summary` report:
conn.request("GET", "/api/v1/sandbox/report/8350dED6D39DF158E51D6CFBE36FB012?details=summary", headers=headers)
`GET /sandbox/report/{md5Hash}` returns a report only if the MD5 file was analyzed previously. If a report for a requested MD5 does not exist, the request still counts against your quota.
To learn more about the API endpoint, see [API Reference](/zia/sandbox-report).
A Sandbox Detail Report always provides the following information:
- `Status`: The summary status of the file analysis, which includes one of the following values:
- `COMPLETED`: The file analysis was completed
- `NODYNAMIC`: The file analysis was completed, but dynamic analysis was not performed
- `INPROGRESS`: The file analysis is in progress
- `NOTFOUND`: The MD5 hash was not found
For example (value highlighted in green):
"Summary": {
"Status": "COMPLETED",
"Category": "SCRIPT",
"FileType": "CMD",
"Start Time": 1509567511,
"Duration": 454557,
"Analysis": "0",
"Url": "",
"TimeUnit": "ms",
"StartTime": "Nov 1, 2017 1:18:31 PM"
},
- `Category`: The summary category of the analyzed file, which includes one of the following values:
- `SCRIPT`
- `PDF`
- `ANDROID`
- `ARCHIVE`
- `JAR`
- `DOCS`
- `FLASH`
- `EXECS`
- `OTHER`
- `ANY`
For example (value highlighted in green):
"Summary": {
"Status": "COMPLETED",
"Category": "SCRIPT",
"FileType": "CMD",
"Start Time": 1509567511,
"Duration": 454557,
"Analysis": "0",
"Url": "",
"TimeUnit": "ms",
"StartTime": "Nov 1, 2017 1:18:31 PM"
},
- `Type`: The classification type of the analyzed file, which includes one of the following values:
- `MALICIOUS`
- `SUSPICIOUS`
- `BENIGN`
For example (value highlighted in green):
"Classification": {
"Type": "MALICIOUS",
"Category": "MALWARE_BOTNET",
"Score": 86,
"Max Score": 100,
"DetectedMalware": ""
},
- `Category`: The classification category of the analyzed file, which includes one of the following values:
- `BENIGN`
- `SUSPICIOUS`
- `ADWARE`
- `MALWARE_BOTNET`
- `ANONYMIZER_P2P`
For example (value highlighted in green):
"Classification": {
"Type": "MALICIOUS",
"Category": "MALWARE_BOTNET",
"Score": 86,
"Max Score": 100,
"DetectedMalware": ""
},
A summary Sandbox Detail Report only includes `Summary`, `Classification`, and `FileProperties` information.
- [Summary Sandbox Detail Report Example for a MALICIOUS File](#SummaryReportExample)
[]
{
"Summary": {
"Summary": {
"Status": "COMPLETED",
"Category": "EXECS",
"FileType": "DLL",
"StartTime": 1522111841,
"Duration": 481690
},
"Classification": {
"Type": "MALICIOUS",
"Category": "MALWARE_BOTNET",
"Score": 82,
"DetectedMalware": "Win32/TrojanDownloader.Banload.TNJ trojan"
},
"FileProperties": {
"FileType": "DLL",
"FileSize": 2358272,
"MD5": "b3b13c2fe5710507612106cb11ceced3",
"SHA1": "6f30404f8b30812758acc06455bc95348c86f9f2",
"Sha256": "c77ab4c60b73c8f8135d54162813ab7c63432058f17ff00754d5fd547c22db76",
"Issuer": "",
"DigitalCerificate": "",
"SSDeep": "49152:mQU0HSp/RcGuBLe/PESBbFVZ86MfBWPvGZxnBGVV3NcKRLFcTOJP:mQUn6LsPQp6vkoiKt",
"RootCA": ""
}
}
}
A full Sandbox Detail Report includes the same information as in a summary report, and also includes `System Summary`, `Networking`, and other information specific to the analyzed file.
- [Full Sandbox Detail Report Example for a MALICIOUS File](#FullReportExample)
[]
{
"Full Details": {
"Summary": {
"Status": "COMPLETED",
"Category": "SCRIPT",
"FileType": "CMD",
"Start Time": 1509567511,
"Duration": 454557,
"Analysis": "0",
"Url": "",
"TimeUnit": "ms",
"StartTime": "Nov 1, 2017 1:18:31 PM"
},
"Classification": {
"Type": "MALICIOUS",
"Category": "MALWARE_BOTNET",
"Score": 86,
"Max Score": 100,
"DetectedMalware": ""
},
"File Properties": {
"File Type": "CMD",
"File Size": 9810,
"MD5": "8350ded6d39df158e51d6cfbe36fb012",
"SHA1": "f4dd1d176975c70ba8963ebc654a78a6e345cfb6",
"Sha256": "aff2d40828597fbf482753bec73cc9fc2714484262258875cc23c7d5a7372cee",
"Issuer": "",
"Digital Cerificate": "",
"SSDeep": "192:+cgNT7Zj4tvl2Drc+gEakjqBT1W431lXXH1TR8J:InZjevl2Drc+gEakmBT44rXVR8J",
"RootCA": ""
},
"System Summary": [
{
"Risk": "LOW",
"Signature": "Allocates memory within range which is reserved for system DLLs",
"Signature Sources": [
"",
"76E70000 page execute and read and write",
"76E70000 page execute and read and write",
"76E70000 page execute and read and write",
"76E70000 page execute and read and write",
"76F90000 page execute and read and write",
"76F90000 page execute and read and write",
"76F90000 page execute and read and write",
"76F90000 page execute and read and write"
]
},
{
"Risk": "LOW",
"Signature": "Classification label",
"Signature Sources": [
"",
"mal68.winCMD@53/26@0/0"
]
},
{
"Risk": "LOW",
"Signature": "Creates files inside the user directory",
"Signature Sources": [
"",
"C:\\Users\\win_7_64bit\\Desktop\\WlanTraces"
]
},
{
"Risk": "LOW",
"Signature": "Found command line output",
"Signature Sources": [
""
]
},
{
"Risk": "LOW",
"Signature": "Queries the cryptographic machine GUID",
"Signature Sources": [
"",
"HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Cryptography MachineGuid"
]
},
{
"Risk": "LOW",
"Signature": "Reads software policies",
"Signature Sources": [
"",
"HKEY_USERS\\Software\\Policies\\Microsoft\\Windows\\Safer\\CodeIdentifiers"
]
},
{
"Risk": "LOW",
"Signature": "Sample sleeps for a long time",
"Signature Sources": [
""
]
},
{
"Risk": "LOW",
"Signature": "Spawns processes",
"Signature Sources": [
"",
"C:\\Windows\\SysWOW64\\cmd.exe ",
"C:\\Windows\\SysWOW64\\cmd.exe ",
"C:\\Windows\\SysWOW64\\cmd.exe ",
"C:\\Windows\\SysWOW64\\find.exe ",
"C:\\Windows\\SysWOW64\\find.exe ",
"C:\\Windows\\SysWOW64\\logman.exe ",
"C:\\Windows\\SysWOW64\\netsh.exe ",
"C:\\Windows\\SysWOW64\\whoami.exe "
]
},
{
"Risk": "LOW",
"Signature": "Uses an in-process (OLE) Automation server",
"Signature Sources": [
"",
"HKEY_LOCAL_MACHINE\\SOFTWARE\\Classes\\Wow6432Node\\CLSID\\{03837525-098B-11D8-9414-505054503030}\\InprocServer32"
]
}
],
"Networking": [
{
"Risk": "MODERATE",
"Signature": "Uses ipconfig to modify the Windows network settings",
"Signature Sources": [
"",
"C:\\Windows\\SysWOW64\\ipconfig.exe "
]
},
{
"Risk": "HIGH",
"Signature": "Uses netsh to modify the Windows network and firewall settings",
"Signature Sources": [
"",
"C:\\Windows\\SysWOW64\\netsh.exe "
]
}
],
"Security Bypass": [
{
"Risk": "LOW",
"Signature": "Checks for kernel debuggers",
"Signature Sources": [
"",
"KernelDebuggerInformation"
]
},
{
"Risk": "LOW",
"Signature": "Executes massive amount of sleeps in a loop",
"Signature Sources": [
"",
"-60000ms >= -60000ms",
"-60000ms >= -60000ms",
"-60000ms >= -60000ms",
"-60000ms >= -60000ms",
"-60000ms >= -60000ms"
]
},
{
"Risk": "MODERATE",
"Signature": "Enables debug privileges",
"Signature Sources": [
"",
"Debug"
]
},
{
"Risk": "MODERATE",
"Signature": "Sample sleeps for a long time (installer files shows these property).",
"Signature Sources": [
""
]
}
],
"Stealth": [
{
"Risk": "LOW",
"Signature": "Disables application error messages",
"Signature Sources": [
"",
"NOOPENFILEERRORBOX",
"NOOPENFILEERRORBOX",
"NOOPENFILEERRORBOX",
"NOOPENFILEERRORBOX"
]
},
{
"Risk": "MODERATE",
"Signature": "Very long cmdline option found",
"Signature Sources": [
"",
"C:\\Windows\\SysWOW64\\logman.exe logman  create trace autosession\\IntelNetwfw02 -p  0xffffffff 255 -f bincirc -max 250 -o C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\IntelNetwfw02_WIN_7_64BIT-PC_11-01-2017_0825.etl",
"C:\\Windows\\SysWOW64\\logman.exe logman  create trace autosession\\bcrmwlan -p {CEA4623F-AA31-4286-B3A5-797EF8A75C17} 0xffffffff 255 -f bincirc -max 250 -o C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\BCRMwlan_WIN_7_64BIT-PC_11-01-2",
"C:\\Windows\\SysWOW64\\logman.exe logman  create trace autosession\\mwls97w8arm -p {BFA91C93-9E18-497C-971B-490D06089E97} 0x1 255 -f bincirc -max 250 -o C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\Marvell_WIN_7_64BIT-PC_11-01-2017_0",
"C:\\Windows\\SysWOW64\\logman.exe logman  create trace autosession\\qcwlan -p {BB6F5B93-635C-47BE-816F-E895E77064A8} 0xffff 18 -f bincirc -max 250 -o C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\QCwlan_WIN_7_64BIT-PC_11-01-2017_0825.",
"C:\\Windows\\SysWOW64\\logman.exe logman  start bcrmwlan -p {CEA4623F-AA31-4286-B3A5-797EF8A75C17} 0xffffffff 255 -f bincirc -max 150 -o C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\BCRMwlan_WIN_7_64BIT-PC_11-01-2017_0825.etl -ets",
"C:\\Windows\\SysWOW64\\logman.exe logman  start mwls97w8arm -p {BFA91C93-9E18-497C-971B-490D06089E97} 0x1 255 -f bincirc -max 150 -o C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\Marvell_WIN_7_64BIT-PC_11-01-2017_0825.etl -ets",
"C:\\Windows\\SysWOW64\\logman.exe logman  start qcwlan -p {BB6F5B93-635C-47BE-816F-E895E77064A8} 0xffff 18 -f bincirc -max 150 -o C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\QCwlan_WIN_7_64BIT-PC_11-01-2017_0825.etl -ets",
"C:\\Windows\\SysWOW64\\netsh.exe netsh  trace sta wireless_dbg provider={21ba7b61-05f8-41f1-9048-c09493dcfe38} 0xff globallevel=0xff persistent=yes trace=C:\\Users\\win_7_64bit\\Desktop\\WlanTraces\\WIN_7_64BIT-PC-11-01-2017_0825\\wlan_WIN_7_64BIT-PC_11-01-2017_08"
]
}
],
"Persistence": [
{
"Risk": "MODERATE",
"Signature": "Creates or modifies Windows services",
"Signature Sources": [
"",
"HKEY_LOCAL_MACHINE\\SYSTEM\\ControlSet001\\services\\IKEEXT\\Parameters"
]
},
{
"Risk": "HIGH",
"Signature": "Modifies security policies related information",
"Signature Sources": [
"",
"HKEY_LOCAL_MACHINE\\SYSTEM\\ControlSet001\\Control\\Lsa\\Kerberos\\Parameters KerbDebugLevel"
]
},
{
"Risk": "HIGH",
"Signature": "Uses sc.exe to modify the status of services",
"Signature Sources": [
"",
"C:\\Windows\\SysWOW64\\sc.exe "
]
}
]
}
}

## Contents
- **API Developer & Reference Guide**
  - [Getting Started](/zia/getting-started-zia-api)
  - [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client)
  - [Understanding Rate Limiting](/zia/understanding-rate-limiting)
  - [API Response Codes and Error Messages](/zia/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [3rd-Party App Governance API](/zia/3rd-party-app-governance-api)
    - [Sandbox Submission API](/zia/sandbox-submission-api)
    - [Activation](/zia/activation)
    - [Admin Audit Logs](/zia/admin-audit-logs)
    - [Admin & Role Management](/zia/admin-role-management)
    - [Advanced Settings](/zia/advanced-settings)
    - [Advanced Threat Protection Policy](/zia/advanced-threat-protection-policy)
    - [Alerts](/zia/alerts)
    - [API Authentication](/zia/api-authentication)
    - [Authentication Settings](/zia/authentication-settings)
    - [Bandwidth Control & Classes](/zia/bandwidth-control-classes)
    - [Browser Control Policy](/zia/browser-control-policy)
    - [Browser Isolation](/zia/browser-isolation)
    - [Cloud Applications](/zia/cloud-applications)
    - [Cloud App Control Policy](/zia/cloud-app-control-policy)
    - [Cloud Nanolog Streaming Service (NSS)](/zia/cloud-nanolog-streaming-service-nss)
    - [Data Loss Prevention](/zia/data-loss-prevention)
    - [Device Groups](/zia/device-groups)
    - [DNS Control Policy](/zia/dns-control-policy)
    - [End User Notifications](/zia/end-user-notifications)
    - [Event Logs](/zia/event-logs)
    - [File Type Control Policy](/zia/file-type-control-policy)
    - [Firewall Policies](/zia/firewall-policies)
    - [Forwarding Control Policy](/zia/forwarding-control-policy)
    - [FTP Control Policy](/zia/ftp-control-policy)
    - [Intermediate CA Certificates](/zia/intermediate-ca-certificates)
    - [IoT Report](/zia/iot-report)
    - [IPS Control Policy](/zia/ips-control-policy)
    - [Location Management](/zia/location-management)
    - [Malware Protection Policy](/zia/malware-protection-policy)
    - [Mobile Malware Protection Policy](/zia/mobile-malware-protection-policy)
    - [NAT Control Policy](/zia/nat-control-policy)
    - [Organization Details](/zia/organization-details)
    - [PAC Files](/zia/pac-files)
    - [Policy Export](/zia/policy-export)
    - [Remote Assistance Support](/zia/remote-assistance-support)
    - [Rule Labels](/zia/rule-labels)
    - [SaaS Security API](/zia/saas-security-api)
    - [Sandbox Policy & Settings](/zia/sandbox-policy-settings)
    - [Sandbox Report](/zia/sandbox-report)
    - [Security Policy Settings](/zia/security-policy-settings)
    - [Service Edges](/zia/service-edges)
    - [Shadow IT Report](/zia/shadow-it-report-api)
    - [SSL Inspection Policy](/zia/ssl-inspection-policy)
    - [System Audit Report](/zia/system-audit-report)
    - [Time Intervals](/zia/time-intervals)
    - [Traffic Capture Policy](/zia/traffic-capture-policy)
    - [Traffic Forwarding](/zia/traffic-forwarding-0)
    - [URL Categories](/zia/url-categories)
    - [URL Filtering Policy](/zia/url-filtering-policy)
    - [URL & Cloud App Control Policy Settings](/zia/url-cloud-app-control-policy-settings)
    - [User Authentication Settings](/zia/user-authentication-settings)
    - [User Management](/zia/user-management)
    - [Workload Groups](/zia/workload-groups)
    - [API Rate Limit Summary](/zia/api-rate-limit-summary)
  - **Working with APIs**
    - [Generating Admin Audit Logs Using API ](/zia/generating-admin-audit-logs-using-api)
    - [Managing Admins and Roles Using API ](/zia/managing-admins-and-roles-using-api)
    - [Managing Intermediate CA Certificates Using API](/zia/managing-intermediate-ca-certificates-using-api)
    - [Managing Locations Using API](/zia/managing-locations-using-api)
    - [Obtaining Sandbox Reports Using API](/zia/obtaining-sandbox-reports-using-api)
    - [SD-WAN Integrations Using API](/zia/sd-wan-integrations-using-api)
    - [Configuring VPN Credentials for IPSec Tunnels Using API](/zia/configuring-vpn-credentials-ipsec-tunnels-using-api)
    - [Managing URL Allowlist and Denylist Using API](/zia/managing-url-allowlist-and-denylist-using-api)
    - [Configuring URL Categories Using API](/zia/configuring-url-categories-using-api)
    - [Managing Users Using API](/zia/managing-users-using-api)