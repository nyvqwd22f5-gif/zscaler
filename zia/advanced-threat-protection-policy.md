# Advanced Threat Protection Policy
Source: https://help.zscaler.com/zia/advanced-threat-protection-policy

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /cyberThreatProtection/advancedThreatSettings`

Retrieves the advanced threat configuration settings in the ZIA Admin Portal

**Tags:** Advanced Threat Protection Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedThreatConfig |

## `PUT /cyberThreatProtection/advancedThreatSettings`

Updates the advanced threat configuration settings. To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy).

**Tags:** Advanced Threat Protection Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | AdvancedThreatConfig | No | ATP policy configuration |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | AdvancedThreatConfig |

## `GET /cyberThreatProtection/maliciousUrls`

Retrieves the malicious URLs added to the denylist in the Advanced Threat Protection (ATP) policy

**Tags:** Advanced Threat Protection Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | MaliciousUrls |

## `PUT /cyberThreatProtection/maliciousUrls`

Updates the malicious URLs added to the denylist in ATP policy. To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy).

**Tags:** Advanced Threat Protection Policy
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | MaliciousUrls | No | ATP policy configuration |
| action | query | string | No | Indicates whether to include or exclude the specified URLs from the list |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | MaliciousUrls |

## `GET /cyberThreatProtection/securityExceptions`

Retrieves information about the security exceptions configured for the ATP policy

**Tags:** Advanced Threat Protection Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SecurityExceptions |

## `PUT /cyberThreatProtection/securityExceptions`

Updates security exceptions for the ATP policy.To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy).

**Tags:** Advanced Threat Protection Policy
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | SecurityExceptions |

## Models
### AdvancedThreatConfig
ATP policy settings
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| activeXBlocked | boolean | No | A Boolean value specifying whether sites are allowed or blocked from accessing vulnerable ActiveX controls that are known to have been exploited. |
| activeXCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for ActiveX controls |
| adSpywareSitesBlocked | boolean | No | A Boolean value specifying whether to allow or block websites known to contain adware or spyware that displays malicious advertisements that can collect users' information without their knowledge |
| adSpywareSitesCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for adware and spyware sites |
| alertForUnknownOrSuspiciousC2Traffic | boolean | No | A Boolean value specifying whether to send alerts upon detecting unknown or suspicious C2 traffic |
| anonymizerBlocked | boolean | No | A Boolean value specifying whether to allow or block applications and methods used to obscure the destination and the content accessed by the user, therefore blocking traffic to anonymizing web proxies. |
| anonymizerCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for anonymizers |
| bitTorrentBlocked | boolean | No | A Boolean value specifying whether to allow or block the usage of BitTorrent, a popular P2P file sharing application that supports content download with encryption. |
| bitTorrentCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for BitTorrent |
| blockCountriesCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for blocked countries |
| blockedCountries | array[string] | No | A Boolean value specifying whether to allow or block requests to websites located in specific countries based on the ISO3166 mapping of countries to their IP address space |
| browserExploitsBlocked | boolean | No | A Boolean value specifying whether known web browser vulnerabilities prone to exploitation are allowed or blocked. |
| browserExploitsCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for browser exploits |
| cmdCtlServerBlocked | boolean | No | A Boolean value specifying whether connections to known Command & Control (C2) Servers are allowed or blocked |
| cmdCtlServerCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for connections to known C2 servers |
| cmdCtlTrafficBlocked | boolean | No | A Boolean value specifying whether botnets are allowed or blocked from sending or receiving commands to unknown servers |
| cmdCtlTrafficCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for botnets |
| cookieStealingBlocked | boolean | No | A Boolean value specifying whether to allow or block third-party websites that gather cookie information, which can be used to personally identify users, track internet activity, or steal a user's session or sensitive information. |
| cookieStealingPCAPEnabled | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for cookie stealing |
| cryptoMiningBlocked | boolean | No | A Boolean value specifying whether to allow or block cryptocurrency mining network traffic and scripts, which can negatively impact endpoint device performance and potentially lead to a misuse of company resources. |
| cryptoMiningCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for cryptomining |
| dgaDomainsBlocked | boolean | No | A Boolean value specifying whether to allow or block domains that are suspected to be generated using domain generation algorithms (DGA) |
| dgaDomainsCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for DGA domains |
| fileFormatVunerabilitesBlocked | boolean | No | A Boolean value specifying whether known file format vulnerabilities and suspicious or malicious content in Microsoft Office or PDF documents are allowed or blocked |
| fileFormatVunerabilitesCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for file format vulnerabilities |
| googleTalkBlocked | boolean | No | A Boolean value specifying whether to allow or block access to Google Hangouts, a popular P2P VoIP application. |
| googleTalkCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for Google Hangouts |
| ircTunnellingBlocked | boolean | No | A Boolean value specifying whether to allow or block IRC traffic being tunneled over HTTP and HTTPS |
| ircTunnellingCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for IRC tunnels |
| knownPhishingSitesBlocked | boolean | No | A Boolean value specifying whether known phishing sites are allowed or blocked |
| knownPhishingSitesCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for known phishing sites |
| maliciousUrlsCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for malicious URLs |
| malwareSitesBlocked | boolean | No | A Boolean value specifying whether known malicious sites and content are allowed or blocked |
| malwareSitesCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for malicious sites |
| potentialMaliciousRequestsBlocked | boolean | No | A Boolean value specifying whether to allow or block this type of cross-site scripting (XSS) |
| potentialMaliciousRequestsCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for (XSS) attacks |
| riskTolerance | integer (int32) | No | The Page Risk tolerance index set between 0 and 100 (100 being the highest risk). Users are blocked from accessing web pages with higher Page Risk than the specified value. |
| riskToleranceCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for suspicious web pages |
| sshTunnellingBlocked | boolean | No | A Boolean value specifying whether to allow or block SSH traffic being tunneled over HTTP and HTTPS |
| sshTunnellingCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for SSH tunnels |
| suspectAdwareSpywareSitesBlocked | boolean | No | A Boolean value specifying whether to allow or block any detections of communication and callback traffic associated with spyware agents and data transmission |
| suspectAdwareSpywareSitesCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for suspected adware and spyware sites |
| suspectedPhishingSitesBlocked | boolean | No | A Boolean value specifying whether to allow or block suspected phishing sites identified through heuristic detection. The Zscaler service can inspect the content of a website for indications that it might be a phishing site. |
| suspectedPhishingSitesCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for suspected phishing sites |
| torBlocked | boolean | No | A Boolean value specifying whether to allow or block the usage of Tor, a popular P2P anonymizer protocol with support for encryption. |
| torCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for Tor |
| webspamBlocked | boolean | No | A Boolean value specifying whether to allow or block web pages that pretend to contain useful information, to get higher ranking in search engine results or drive traffic to phishing, adware, or spyware distribution sites. |
| webspamCapture | boolean | No | A Boolean value specifying whether packet capture (PCAP) is enabled or not for web spam |

### MaliciousUrls
Denylist URLs for ATP policy
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| maliciousUrls | array[string] | Yes | List of malicious URLs that are blocked by the ATP policy |

### SecurityExceptions
Security exceptions for ATP policy
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| bypassUrls | array[string] | Yes | Allowlist URLs that are not inspected by the ATP policy |
