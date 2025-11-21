# Understanding Entity Types
Source: https://help.zscaler.com/uvm/entity-types
PDF: https://help.zscaler.com/pdf/com/en/1527811.pdf

An entity is a distinct object or resource with defined attributes used to organize information. In security operations, entities like vulnerabilities, assets, and findings structure the data essential for identifying risks and managing exposures. These entities create relationships that drive effective prioritization and streamlined remediation, empowering teams to reduce organizational risk efficiently. Below is a breakdown of the core entities in the SecOps platform.
Global Vulnerability
A global vulnerability represents a publicly disclosed security vulnerability documented by the National Vulnerability Database (NVD) and assigned a unique CVE identifier (e.g., CVE-2023-32360). These vulnerabilities are enriched with additional context such as:
- Reference tags for cross-verification.
- CVSS scores for severity assessment.
- Details on affected Common Platform Enumerations (CPEs) and associated Common Weakness Enumerations (CWEs).
A global vulnerability can be exist on multiple assets and components across your environment. Each occurrence of the vulnerability is treated as a unique Finding, linked back to the original global vulnerability entity for centralized tracking and contextual analysis.
Finding
A finding is a specific instance of a vulnerability or misconfiguration detected on a particular component of an asset. For example: CVE-2024-30068 could represent a vulnerability affecting Windows 10 on a workstation.
Asset
An asset refers to any organizational-owned resource that may carry risk due to potential vulnerabilities or misconfigurations. Assets represent the core targets for security monitoring and remediation efforts and can include:
- Servers (e.g., Production or Cloud Instances).
- Endpoints (e.g., Workstations, Laptops).
- Code Repositories (e.g., GitHub repositories).
- Containers (e.g., Docker images).
- Images (e.g., Virtual Machine templates).
Component
A Component is the specific part of an asset that introduces a vulnerability or misconfiguration to the environment. Components often require remediation or patching and can be classified as:
- Software (e.g., Adobe Acrobat, Google Chrome).
- Packages (e.g., Python libraries, Java dependencies).
- Operating Systems (e.g., Windows 10, Linux).
Ticket
A ticket acts as the operational entity for tracking, grouping, and initiating the remediation process for vulnerabilities and misconfigurations. It provides a structured mechanism for collaboration across teams and integration with case management platforms (e.g., JIRA, ServiceNow). Tickets typically aggregate findings based on configurable grouping rules tailored to your organization's needs. For example:
- Findings with the same component name across assets can be grouped together.
- Findings tied to similar asset types (e.g., all endpoints running Adobe Acrobat vulnerabilities) can be consolidated into a single ticket.
Tickets serve as actionable work items assigned to relevant teams. For instance, a ticket may represent multiple vulnerabilities (e.g., various CVEs affecting Adobe Acrobat) that can be remediated collectively by updating the software to its latest version.