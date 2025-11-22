# Understanding the ThreatLabz Source
Source: https://help.zscaler.com/uvm/understanding-threatlabz-source
PDF: https://help.zscaler.com/pdf/com/en/1527651.pdf

ThreatLabz is a research organization within Zscaler that focuses on identifying and analyzing emerging threats, vulnerabilities, and attack techniques. As part of their effort, the ThreatLabz team maintains a database of CVEs with information on* *how they're mitigated by different Zscaler products. The ThreatLabz source retrieves this data, which is then correlated with your deduplicated asset records and Zscaler product coverage. This information is used to calculate contextualized risk scores based on the level of protection provided by your Zscaler products.
The ThreatLabz source is provisioned in every new account created within the platform. To access the ThreatLabz source, go to Configure > Sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#configure-sources-threatlabz)
ThreatLabz and the Zscaler Client Connector Source
The ThreatLabz source retrieves data on which CVEs are mitigated by which Zscaler products, including Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA). The Zscaler Client Connector Devices source retrieves data on assets in your organization, including which Zscaler products are installed on which assets. By cross-referencing ThreatLabz data with Zscaler Client Connector data, you can determine which of your Zscaler tools are protecting against specific CVEs in your security environment. This insight can be used as a mitigating risk factor to inform finding scoring. To learn more, see [Configuring the Zscaler Client Connector Devices Connector](/uvm/configuring-zscaler-client-connector-devices-connector) and [Configuring the ZIA Devices and Users Connector](/uvm/configuring-zia-devices-and-users-connector).
Finding Is Mitigated Field
The Finding Is Mitigated field is populated based on the overlap between data from the two sources, returning TRUE when a match is found (i.e., when a CVE found on your asset is mitigated by a Zscaler tool installed on it) or FALSE otherwise. The [unification](/uvm/what-data-unification) rule checks if any of the products that can mitigate the vulnerability (as reported by the ThreatLabz source) are actually installed on the asset where the vulnerability was detected (as reported by the Zscaler Client Connector Devices source). If the product is installed on the asset, it sets the Finding Is Mitigated field to TRUE. Otherwise, it sets the value to FALSE. To learn more, see [Configuring Field Unification](/uvm/configuring-field-unification).
[See image.](#finding-is-mitigated-unification)
Score Settings
The Finding Is Mitigated field is used score settings for UVM findings to create the CVE Mitigated By factor, which refines your risk assessment and scoring practices. You can adjust this setting to align with your organization's specific requirements. To learn more, see [Configuring Severity Score Formulas](/uvm/configuring-severity-score-formulas).
[See image.](#cve-mitigated-by-factor)
Use Case Example
Consider the following example of a CVE finding:
- The ThreatLabz source reports that CVE-2017-3044 is mitigated by ZIA (i.e., the value of the Vulnerability Mitigation Products field is ZIA).
- The Zscaler Client Connector Devices source reports that Asset A has ZIA installed and contains the CVE-2017-3044 finding (i.e., the Asset Mitigation Products field value is ZIA).
- CVE-2017-3044 is mitigated by the ZIA tool and Asset A has ZIA installed on it.
These points indicate an overlap between the vulnerability mitigation products (i.e., ZIA) and the asset mitigation products (i.e., ZIA). This sets the Finding Is Mitigated field on Asset A for CVE-2017-3044 to TRUE, indicating that the vulnerability is no longer a significant threat to the asset. This information is then used to reduce the severity score of the finding.
[]![56f803b6-b9a4-4edd-9927-042925aadef3.png](/downloads/uvm/configure/sources/threatlabz/56f803b6-b9a4-4edd-9927-042925aadef3.png)
[]![1f2ab50e-9ad4-41a4-af1f-95e796e67b4b.png](/downloads/uvm/configure/sources/threatlabz/1f2ab50e-9ad4-41a4-af1f-95e796e67b4b.png)
[]![12ff52a0-0896-48fe-857b-5ae5ef21a6c7.png](/downloads/uvm/configure/sources/threatlabz/12ff52a0-0896-48fe-857b-5ae5ef21a6c7.png)