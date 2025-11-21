# Accessing & Interacting with the Insights Overview Dashboard
Source: https://help.zscaler.com/easm/accessing-interacting-insights-overview-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1503526.pdf

The Insights Overview dashboard has a collection of interactive widgets that present information on risk findings based on various parameters, such as their risk level, exposure, trend, type, distribution across geographic locations, certificate expiration, etc. using appropriate graphical visualizations. This dashboard provides a consolidated view of the risk findings and lookalike domains for your organization, highlighting the most critical and sensitive findings to enable you to identify them easily and take necessary action. In addition to interacting with the widgets to visualize the data in the desired representation, you can click on individual data points to examine them in depth.
Accessing the Dashboard
To access the Insights Overview dashboard, go to Dashboard > Insights Overview Dashboard in the EASM Admin Portal. The information consolidated on the dashboard corresponds to your organization selected on the top-right corner. You can use this drop-down menu to select the organization for which you want to view the dashboard. You can also see the timestamp when the current data displayed on the dashboard has been updated.
Interacting with Dashboard Widgets
The Insights Overview dashboard includes the following widgets:
- [Distribution of Findings by Risk Level](#distribution-of-findings-by-risk-level)
- [Findings Over Time by Risk Level](#findings-over-time-by-risk-level)
- [Findings Percentage by Category](#findings-percentage-by-category)
- [Top 5 Lookalike Domains by Exposure](#top5-lookalike-domains-by-exposure)
- [Top 5 Exposed VPN Appliances](#top5-exposed-vpn-appliances)
- [Top Locations by Findings](#top-locations-by-findings)
- [Top 5 Findings by Risk Level](#top5-findings-by-risk-level)
- [Exposed Sensitive Services](#exposed-sensitive-services:)
- [SSL/TLS Certificate Expiration](#ssl-tls-certificate-expiration)
- [Domain Registration Expiration](#domain-registration-expiration)
[]This widget provides information on how risk findings are distributed across risk levels such as low, medium, high, and critical. The categorization of findings based on risk levels enables you to efficiently handle risk remediation by prioritizing the findings based on their criticality and allocating appropriate resources. It also helps you quickly assess the overall level of risk exposure based on the volume of findings across risk levels. This widget includes a single stacked bar chart that uses color coding to indicate the volume of findings in each risk level and a numerical representation of the data with a breakdown of the count of findings in each risk level. You can also view the number of findings present in each risk level by hovering over the respective color-coded bar in the stacked bar graph.
You can click the number of findings in each risk level to get a filtered, tabulated view of the corresponding findings on the [Findings page](/easm/about-findings), where you can drill down on each finding for detailed information.
[See image.](#distribution-findings-by-risk-level-image)
[]This widget provides information about the trends of risk findings over a specific period of time using a line graph that plots the number of findings against specific timelines. You can customize the information shown by this graph using the following options:
- Select the time frame for which the trend is shown using the time filter on the top-right corner of the widget from last 7 days, last 30 days, last 90 days, and last 180 days.
- Select a risk level using the checkbox at the bottom to view the trend of the findings assigned with that specific risk level. You can select multiple risk levels simultaneously to view the corresponding trends together.
When customizing the graph for a time frame greater than the last 7 days, you can view the findings count for specific days by hovering over the line to the specific day.
[See image.](#findings-over-time-risk-level-image)
[]This widget provides a donut chart representing the percentage of risk findings that are grouped within different categories:
- **Exposure**: Shows the percentage of business-critical services, such as SSH, FTP, Telnet, and VPN services, MySQL data stores, revealing hostnames, etc.
- **Misconfiguration**: Shows the percentage of outdated SSL/TLS versions, SSL/TLS certificate expirations, domain registration expiration, usage of self-signed certificates, and absence of common security headers in HTTP requests including but not limited to HTTP Strict Transport Security (HSTS), X-XSS-Protection, Set-Cookie, Cross-Origin-Opener-Policy (COOP), Permissions-Policy, etc.
- **Vulnerability**: Shows the percentage of vulnerabilities that are part of the Common Vulnerabilities and Exposures (CVE) database.
You can hover over a specific area to view the number of risk findings grouped within the corresponding category. Furthermore, you can click on a specific area of the chart to get a filtered, tabulated view of the corresponding risk findings on the [Findings page](/easm/about-findings), where you can drill down on each finding for detailed information.
[See image.](#findings-percentage-by-category-image)
[]This widget provides the list of the top 5 exposed VPN appliances linked to your organization with the highest risk scores. The data is presented in a tabular form and the following information is available for each VPN appliance:
- **Name**: The name of the risk finding.
- **Version**: The version number associated with the identified VPN application.
- **CVE**: The CVE IDs of any publicly known vulnerabilities that are identified in the appliance.
- **Known Exploits**: A Boolean value that indicates if the vulnerability identified in the appliance is recognized in the [Known Exploited Vulnerabilities (KEV) Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) maintained by the [CISA](https://www.cisa.gov/).
- **Impacted Asset**: The name of the asset in which the finding was discovered.
- **Risk Score**: A risk score computed for the finding based on multiple vectors such as threat severity, likelihood, and impact using a combination of open industry standard risk scoring systems; public, governmental, and threat intelligence sources on vulnerability risk computation; and Zscaler's proprietary computation method.
You can click a specific VPN appliance finding in the table to go to the corresponding entry on the [Findings page](/easm/about-findings), where you can click the entry to view more detailed information about the finding. You can also click the **View All VPN Appliances** button on the top-right corner of the widget to get a filtered view of all VPN appliances on the [Findings page](/easm/about-findings).
[See image.](#top-5-exposed-vpn-image)
[]This widget provides a worldwide proportional symbols map that plots the geographical regions or countries with the number of risk findings detected as part of your attack surface. The size of each circle visually represents the number of risk findings in each region relative to others; larger circles indicate more findings compared to regions represented by smaller circles.
You can view the exact number of findings in a specific region by hovering over or clicking the region or the country on the map. In addition, the list of countries where the findings are located along with the number of findings for each country is shown on the left pane of the widget.
[See image.](#top-5-locations-image)
[]This widget provides the list of top 5 findings with the highest risk levels. The data is presented in a tabular form and the following information is available for each finding:
- **Name**: The name of the risk finding.
- **Impacted Asset**: The name of the asset in which the finding was discovered.
-
**Risk Level**: The risk level assigned to the finding is based on the risk score generated for the finding.
[Mapping Between Risk Level and Risk Score](#table-risk-level-score-mapping)
You can also click the **View All Findings** button on the top-right corner of the widget to go to the [Findings page](/easm/about-findings), where you can drill down on each finding for detailed information.
[See image.](#top-5-findings-by-risk-level-image)
[]
| Risk Level | Risk Score Range |
| ---------- | ---------------- |
| Low | 1–39 |
| Medium | 40–69 |
| High | 70–89 |
| Critical | 90–100 |
[]This widget provides information about specific internet-exposed, business-critical services and the risk findings associated with these services using a bar chart. Examples of sensitive services include SSH, FTP, Telnet, VNC, TFTP (UDP), SNMP (UDP), databases such as MySQL, MongoDB and Redis, and other services such as Elasticsearch. This bar graph shows the sensitive services plotted against the number of risk findings identified in each of the services.
You can hover over each bar to view the number of risk findings identified in a service. You can click a bar chart to get a filtered view of the risk findings for that specific service on the [Findings page](/easm/about-findings), where you can drill down on each finding for detailed information. Alternatively, you can click the **View All Exposed Services** button on the top-right corner of the widget to get a filtered view of all exposed services on the [Findings page](/easm/about-findings).
[See image.](#exposed-sensitive-services-image)
[]This widget provides information about SSL/TLS certificates detected in the assets attributed to your organization that are already expired or are nearing expiration. The certificates are categorized based on their expiration status and this widget provides a count breakdown for the following:
- Certificates that are already expired
- Certificates expiring in the next 30 days
- Certificates with a validity period longer than the next 30 days
You can click each of the counts to get a filtered, tabulated view of the corresponding certificates on the [Findings page](/easm/about-findings), where you can drill down on each certificate for detailed information.
[See image.](#ssl-tls-certificate-expiration-image)
[]This widget provides information about the domains that are attributed to your organization, categorized based on their expiration status. This widget provides a count breakdown for the following:
- Domains that are already expired
- Domains expiring in the next 30 days
- Domains with a validity period longer than the next 30 days
- Domains for which the validity period is unknown
You can click each of the counts to get a filtered, tabulated view of the corresponding domains on the [Findings page](/easm/about-findings), where you can drill down on each domain for detailed information.
[See image.](#domain-expiration-image)
[]This widget provides the list of top 5 lookalike domains linked to the legitimate domains of your organization based on their exposure score. The data is presented in a tabular form and the following information is available for each finding:
- **Original Domain**: The legitimate domain linked to your organization for which a lookalike domain has been identified.
- **Lookalike Domain**: The lookalike domain identified based on your original domain linked to your organization.
- **Risk Category**: The category assigned to the lookalike domain from Verified Phishing, Registered Lookalike, and Preventative Lookalike.
- **Exposure Score**: The risk score computed for the lookalike domain.
You can click the View **All Lookalike Domains** button in the top-right corner of the widget to go to the [Lookalike Domains page](/easm/about-lookalike-domains), where you can drill down on each entry for detailed information.
[See image.](#top-5-lookalike-domains-image)
[]![A widget providing information on how risk findings are distributed across risk levels in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-distribution-findings-by-risk-level.gif)
[]![A widget providing information about risk finding trends over time in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-findings-over-time-risk-level.gif)
[]![A donut chart widget representing the percentage of risk findings within categories in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-findings-percentage-by-category.gif)
[]![A widget providing the list of top 5 lookalike domains in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-top-5-lookalike-domains.gif)
[]![A widget providing the list of the top 5 exposed VPN appliances in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-top-5-exposed-vpn.gif)
[]![A widget using a map that plots the geographical regions or countries with the number of risk findings detected in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-top-5-locations.gif)
[]![A widget providing the list of top 5 findings with the highest risk levels in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-top-5-findings-by-risk-level.gif)
[]![A widget providing information about specific internet-exposed, business-critical services in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-exposed-sensitve-services.gif)
[]![A widget providing information about SSL/TLS certificates detected in the assets attributed to your organization in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-ssl-tls-certifcate-expiration.gif)
[]![A widget providing information about the domains that are attributed to your organization in EASM's Insights Overview dashboard](/downloads/easm/dashboards/accessing-interacting-insights-overview-dashboard/EASM-domain-regsitration-expiration.gif)