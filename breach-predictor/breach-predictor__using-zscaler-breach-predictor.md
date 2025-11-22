# Using Zscaler Breach Predictor
Source: https://help.zscaler.com/breach-predictor/using-zscaler-breach-predictor
PDF: https://help.zscaler.com/pdf/com/en/1500446.pdf

[]This guide takes you through the basic high-level steps for how to use Zscaler Breach Predictor and provides links to more information. Because Breach Predictor uses data from other Zscaler tools, you should familiarize yourself with how Zscaler Internet Access (ZIA) and Zscaler Sandbox work so that you can better understand the log data that Breach Predictor uses to identify threats to your organization. Additionally, as a major part of its predictive intelligence, Breach Predictor relies on the MITRE ATT&CK  framework to give you a clear picture of your overall security posture. Zscaler recommends reading the following articles before you begin using Breach Predictor:
- [Understanding the ZIA Cloud Architecture](/zia/understanding-zscaler-cloud-architecture)
- [About Sandbox](/zia/about-sandbox)
- [Integrating with CrowdStrike](/zia/integrating-crowdstrike)
- [MITRE ATT&CK  Overview](https://attack.mitre.org/)
To use Zscaler Breach Predictor, complete the following steps:
- [Step 1: Ensure Completion of Prerequisite Tasks](#prerequisites)
- [Step 2: Assess the Security Threats to Your Organization](#assess-threats-to-org)
- [Step 3: Use Breach Predictor Findings to Remediate with Policy Recommendations](#remediate-issues)
[]Before using Breach Predictor, ensure that you've completed prerequisite tasks and that you can log in to the Breach Predictor Portal. To learn more, see [Accessing and Navigating Zscaler Breach Predictor](/breach-predictor/accessing-and-navigating-zscaler-breach-predictor).
[]Breach Predictor uses easy-to-understand charts and tables to give you visibility into vast amounts of threat data across your organization. As you navigate the Breach Predictor Portal, you can use the interconnected data points to easily switch from macro to micro views of the data (e.g., clicking a threat family name on the **Dashboard** page takes you to the **Events** page with information about that particular threat family). You can use the following basic workflow to assess your threat risk:
- [Evaluate Your Overall Breach Probability Score and Prioritized Recommendations](#eval-overall-score)
- [Determine How Far Attacks Have Progressed](#determine-position-on-matrix)
- [Examine Data from Users at Risk](#users-at-risk)
- [Determine the Attack Path for Malware Families Present in Your Organization](#determine-attack-path)
- [Use ThreatLabz Research to Assess the Overall Threat Landscape](#assess-threat-landscape)
To learn more, see [Accessing and Navigating Zscaler Breach Predictor](/breach-predictor/accessing-and-navigating-zscaler-breach-predictor).
[]After you've examined the Breach Predictor data for your organization, you might need to remediate policies (e.g., File Type Control, SSL Inspection, URL Filtering, etc.). As you plan for remediation, you should always work from right to left in the MITRE ATT&CK  matrix. As a threat moves further to the right in the matrix, your organization is at a higher risk of a data breach. Use the policy recommendations provided by Breach Predictor to log Jira tickets for policy updates.
To learn more, see [Requesting Updates in Zscaler Breach Predictor](/breach-predictor/requesting-updates-zscaler-breach-predictor) and [Evaluating a Security Issue with Breach Predictor](/breach-predictor/evaluating-security-issue-breach-predictor).
[]On the **Dashboard** page, use the Overall Breach Probability score for an instant determination of the overall likelihood of a breach in your environment. Additionally, Breach Predictor provides a list of the highest-value policy updates based on imminent threats to your organization.
[]On the **Dashboard **page, use the various charts and tables to assess your organization’s placement within the MITRE ATT&CK  framework during the period you specify.
To learn more, see [Analyzing the Dashboard](/breach-predictor/analyzing-dashboard).
[]On the **Findings** page, you can see information about the malware families affecting your organization, as well as information about each user affected by each family. On the **Users** page, you can see the overall user information by department, threat type, and region. You can also drill down to see data for each user.
[]Also on the **Findings** page, use attack-path data to help you interpret what your threat placement means, and to determine whether a threat has already achieved a particular technique or whether its movement to that technique is probable or just possible.
[]On the **Threat Landscape** page, view cutting-edge data from [Zscaler ThreatLabz](https://threatlabz.zscaler.com/) about the biggest current security threats affecting customers across the globe.