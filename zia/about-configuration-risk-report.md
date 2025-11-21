# About Configuration Risk Report
Source: https://help.zscaler.com/zia/about-configuration-risk-report
PDF: https://help.zscaler.com/pdf/com/en/1402426.pdf

Zscaler calculates the risk of a breach by evaluating your organization's policy configuration, traffic patterns, and feature capabilities against Zscaler's best practices. This helps improve your overall security posture to mitigate risk against all the encrypted, web, network, and file-based threats.
The Configuration Risk Report gives high-level visibility and insight into your organization’s policy structure to holistically evaluate and compare the posture against emerging cyber threats. This report gives situational awareness to discover any exposures to potential exploitation. The report shows whether any features are underutilized or not configured optimally and, in turn, recommends policy changes to give maximum value and protection.
The Configuration Risk Report provides the following benefits and enables you to:
- Analyze your organization's configuration-based risk score and the change over time to determine the effectiveness of various policy configurations.
- Gain in-depth visibility of your organization's risk from different threat categories, such as: web, file, network, and uninspected traffic to configure stronger policies as per the displayed recommendations.
- Understand risk score contribution at the category level and from individual factors within the categories.
About the Configuration Risk Report Page
In the Configuration Risk Report (Analytics > Configuration Risk Report), you can view the following sections:
- **Config****uration**** Risk Score**: This section displays the organization’s configuration risk score and further breaks down the score contributed from each of the following categories:
- [Web-Based Threats](#web-based)
- [File-Based Threats](#file-based)
- [Network-Based Threats](#network-based)
- [Uninspected Encrypted Traffic](#uninspected)
- []Advanced Threat Protection
- Malware Protection
- Advanced URL Filtering Settings
- URL Filtering
- Browser Control Settings
- Advanced Settings
- Mobile Malware Protection
- []Cloud Sandbox
- File Type Control
- []IPS Control Settings
- Firewall Traffic Analysis
- Firewall Filtering Rule
- IPS Traffic Analysis
- FTP Settings
- []SSL Inspected
- **Risk Trend**: The graph displays the configuration risk score trend. You can view data for the last 30 days, weekly, monthly, or quarterly. The default trend is displayed for the last 30 days. The risk scores are categorized in the following ranges to identify the level of risk:
- Low (0-29)
- Medium (30-59)
- High (60-79)
- Critical (80-100)
- **Risk Contribution Table**: Click on the threat category to display the risk contribution table for that category. The following columns appear in the table:
- **Contributing Factors**: The Zscaler feature that is analyzed for its configurations. Click on the drop-down arrow to view the settings that are affecting the risk score and the recommended configuration.
- **Threat Protection Status**: Displays the protection status based on the posture and feature utilization. One of the following statuses appears based on the risk contribution:
- Protected
- Moderately Protected
- Mildly Protected
- Not Protected
- **Risk Contribution**: The contribution to the configuration risk score as a result of optimum usage or underutilization of the Zscaler feature or its configuration.
The threat protection status and the risk contribution for each setting are computed independently, which means the same risk contribution value for two different settings may generate similar or different threat protection statuses.
-
**Action**: Click **Edit Policy**, and you are redirected to the corresponding policy configuration page to modify the policy as per the recommended settings.
![The Configuration Risk Report in the ZIA Admin Portal](/downloads/ZIA-6.2-cyber-risk-report_0_0.png)