# Understanding the EASM API
Source: https://help.zscaler.com/easm/understanding-easm-api
PDF: https://help.zscaler.com/pdf/com/en/1532904.pdf

To enable the EASM API for your organization, contact the Zscaler Account team.
The EASM API gives you programmatic access to manage the following EASM features:
- [Organizations](#organizations)
- [Findings](#findings)
- [Lookalike Domains](#lookalike-domains)
Zscaler provides secured access to the EASM API via [Zscaler OneAPI](/oneapi/understanding-oneapi), a unified programming interface for all Zscaler services specialized for platform automation. OneAPI uses a common endpoint that encompasses all Zscaler resources and secures API authorization with OAuth 2.0. API client identity registration and management are combined in Zscaler's unified identity service, [ZIdentity](/zidentity/what-zidentity).
Prior to using the API, Zscaler recommends reviewing [Getting Started](/oneapi/getting-started) with OneAPI for information regarding prerequisites, authentication, and making API calls. For detailed information on all available API calls, endpoints, and parameters, see the [Reference Guide](/easm/easm-api/api-developer-reference-guide/reference-guide). Zscaler can make periodic updates to the query and response parameters that the EASM API uses.
All endpoints within the EASM API are subject to a rate limit of 1,000 calls per second, per tenant. To learn more about HTTP error and status codes, see [API Response Codes and Error Messages](/easm/api-response-codes-and-error-messages). If you encounter any issues with the EASM API, contact Zscaler Support.
[]Organizations API resources allow you to retrieve all organizations configured for a tenant in the EASM Admin Portal. To learn more, see:
- [Reference Guide > Organizations](/easm/organizations)
- [Creating and Managing Organizations](/easm/creating-managing-organizations)
[]Findings API resources allow you to retrieve the findings identified for an organization's internet-facing assets after the initial scanning and discovery processes. The assets are investigated for various risk parameters, such as undetected vulnerabilities, misconfigurations, and compliance violations, and these detections are populated as findings in the EASM Admin Portal. Using these API resources, you can retrieve the list of findings, detailed information about individual findings, and evidence details and scan output for each finding. To learn more, see:
- [Reference Guide > Findings](/easm/findings)
- [About Findings](/easm/about-findings)
- [Understanding Finding Details](/easm/understanding-finding-details)
[]Lookalike Domains API resources allow you to retrieve fraudulent or fake domains that threat actors intentionally create to mimic the legitimate domains associated with your organization and deceive users for malicious activities. To learn more, see:
- [Reference Guide > Lookalike Domains](/easm/lookalike-domains)
- [About Lookalike Domains](/easm/about-lookalike-domains)
- [Understanding Lookalike Domain Details](/easm/understanding-lookalike-domain-details)

## Contents
- **API Developer & Reference Guide**
  - [API Response Codes and Error Messages](/easm/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [Organizations](/easm/organizations)
    - [Findings](/easm/findings)
    - [Lookalike Domains](/easm/lookalike-domains)