# Understanding Asset Discovery
Source: https://help.zscaler.com/easm/understanding-asset-discovery
PDF: https://help.zscaler.com/pdf/com/en/1503541.pdf

In the modern digital landscape, organizations deal with increasingly complex external attack surfaces, driven by their expanding online presence. As organizations expand digitally, their attack surfaces grow, introducing new potential vulnerabilities. Unknown or unmonitored assets are particularly dangerous because they might not be regularly updated or secured, leaving them exposed to attacks. This expansion includes assets resulting from mergers and acquisitions or third-party services that were once used but have since been forgotten.
Asset discovery, a core function of EASM, helps organizations identify, inventory, and continuously monitor their internet-facing assets. This capability provides critical visibility into risks and potential vulnerabilities. Asset discovery involves identifying and inventorying all internet-facing assets an organization owns or manages. These assets include domains, hosts, web pages, certificates, ASNs, IP addresses, and IP blocks exposed to the public internet. In EASM, asset discovery provides organizations with a clear view of their external attack surface by mapping out these assets and any risks associated with them. The discovery process ensures that even unknown, unmanaged, or forgotten assets—often referred to as "shadow IT"—are identified and brought under security management.
Effective asset discovery enables organizations to:
- **Gain Visibility**: Establish a complete inventory of all internet-facing assets, which is critical for managing external threats.
- **Identify Risks**: Proactively uncover and address risks from both known and unknown assets.
- **Prioritize Remediation**: Prioritize actions to mitigate vulnerabilities, based on the risks associated with each asset.
- **Monitor Changes**: Continuously track changes in the asset inventory, allowing security teams to respond quickly to new risks.
To learn more about the use cases of EASM, see [What is Zscaler EASM?](/easm/what-zscaler-easm)
How Asset Discovery Works in EASM
EASM's asset discovery process starts with the use of seeds. A seed is a legitimate asset provided by the organization, such as a known domain, IP address, or IP block, which serves as the starting point for discovery. EASM then uses this seed to begin mapping the organization’s external attack surface through a recursive process.
Seeds are part of the discovery profile and EASM allows you to create distinct discovery profiles for different business entities (e.g., parent companies, subsidiaries), allowing organizations to have granular control over how they manage their attack surface.
The following sections outline the key steps in EASM's asset discovery and monitoring process:
- **Seed-based Scanning**: EASM starts by scanning the seed, mapping its direct connections and discovering related assets.
- **Discovery Chain**: When the first level of assets connected to the seed is found, EASM recursively scans subsequent levels of connections, ultimately building a comprehensive map of the organization's attack surface.
- **Risk Evaluation**: After assets are discovered, EASM evaluates each asset against a set of risk parameters. This includes identifying known vulnerabilities, misconfigurations, and exposed sensitive services. Risks are continuously monitored as part of the asset inventory to provide real-time updates on the organization's external exposure.
- **Automated Monitoring**: After the discovery process is complete, EASM continues to monitor the organization's external attack surface through periodic scans. This ensures that any new risks are detected promptly and that any changes to existing assets are tracked.
To learn how to set up asset discovery in EASM, see [Step-by-Step Configuration Guide for EASM](/easm/step-step-configuration-guide-easm).