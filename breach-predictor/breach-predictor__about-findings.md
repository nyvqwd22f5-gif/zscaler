# About Findings
Source: https://help.zscaler.com/breach-predictor/about-findings
PDF: https://help.zscaler.com/pdf/com/en/1518456.pdf

Breach Predictor Findings provide a high-level overview of all threat families affecting your organization, while also allowing you to drill down to get specific information about each threat family. The basic idea with Breach Predictor Findings is to quickly determine where each threat family sits on the MITRE ATT&CK  matrix, and then to use attack-path data to help you interpret what your threat placement means. As a result, you can determine whether a threat has already achieved a particular technique, or whether Breach Predictor is predicting its advancement. Some events are identified as "possible," meaning that they might have happened but were not captured as part of Breach Predictor's threat detection. Focusing on the attack path also lets you see how a particular threat is affecting groups of users at each stage of the MITRE ATT&CK  matrix (i.e., that groups of users have been exposed at a particular URL).
Breach Predictor uses its Findings to make specific policy update recommendations. In the Threat section, you can create Jira tickets so that Zscaler Support can make policy updates to remediate the threats affecting your organization.
To learn more, see [Analyzing Findings](/breach-predictor/analyzing-findings) and [Requesting Updates in Zscaler Breach Predictor](/breach-predictor/requesting-updates-zscaler-breach-predictor).
Findings provide the following benefits and enable you to:
- See a high-level overview of all malware threat families affecting your organization.
- See specific information about each threat family, including attack path, affected users, and associated events.
- Create Jira tickets to make policy updates based on Breach Predictor recommendations.
About the Findings Page
The Findings page (Breach Predictor Portal > Findings) contains the following sub-pages:
- [MITRE ATT&CK  Mapping Page](#matrix-overview)
- [Threat Page](#threat-page)
[]On the MITRE ATT&CK  Mapping page, you can do the following:
- Filter by attack stage (e.g., **Discover Attack**, **Compromise**, **Lateral Movement**, and **Data Loss**).
- Specify the time frame for the data on the page.
- Search for malware families or users in your organization to filter the results in the table.
- View a list of all malware families affecting your organization and quickly determine where each threat sits on the MITRE ATT&CK  matrix. For malware families, you can see:
- **Threat**: The name of the malware family. You can sort this column.
- **Severity Score**: The threat score (0 to 10) assigned to each malware family by Zscaler ThreatLabz. The higher the score, the more damage a malware family can cause to your organization. You can sort this column.
- **Stage and technique**: The matrix is organized by threat stage (e.g., **Discover Attack**, **Compromise**, etc.) and by MITRE ATT&CK  technique (e.g., **Reconnaissance**, **Resource Development**, etc.). The threat for a data breach increases as a malware family moves further to the right on the matrix. To learn more, see [What Is Zscaler Breach Predictor?](/breach-predictor/what-zscaler-breach-predictor)
![The MITRE ATT&CK  Matrix in Zscaler Breach Predictor](/downloads/breach-predictor/25.01/ZBP-Findings_MITRE-ATTACK-Mapping.png)
[]When you click the name of a malware family on the MITRE ATT&CK  Mapping page, the Threat page for the malware family opens. The Threat page contains the following tabs:
- [Attack path](#attack-path-tab)
- [Users](#users-tab)
- [Events](#events-tab)
[]On the Attack path tab, you can do the following:
- Select a different threat family from the drop-down menu.
- Specify the time frame for the data on the page.
- See high-level information about the selected threat family.
- See high-level information about the policy recommendation for the threat.
- Click **Update Policy** to see specific Breach Predictor recommendations for policy updates, and [create a Jira ticket](/breach-predictor/requesting-updates-zscaler-breach-predictor) to update the policy.
- Go to the **Users** tab to see data about users affected by the threat.
- Go to the **Events** tab to see all events related to the threat.
- See a generative AI summary of the malware family, including information about its lateral movement in your organization, recommendations for remediation, and information about any related threats.
- View the attack path data for the malware family. For the attack path, you can see:
- How the malware family has moved or is expected to move through your organization. The chart is organized by threat stage (e.g., **Discover Attack**, **Compromise**, etc.) and by MITRE ATT&CK  technique (e.g., **Reconnaissance**, **Resource Development**, etc.). The threat for a data breach increases as a malware family moves further to the right on the matrix. Use the **Event key** to determine the status of the threat's advancement to a particular technique (e.g., **Observed**, **Possible**, or **Predicted**).
- You can click **Observed** events to see specific information (e.g., which URLs exposed users to the threat).
![The Attack Path Tab in Zscaler Breach Predictor](/downloads/breach-predictor/25.04/ZBP-Findings_Attack-Path-Tab.png)
[]On the Users tab, you can do the following:
- Go to the **Attack path** tab to see where the threat has moved and is expected to move.
- Go to the **Events** tab to see all events related to the threat.
- Search for users in your organization to filter the list of users.
- View the MITRE ATT&CK  data for the users affected by the malware family. For users, you can see:
- **User Impacted**: The list of users affected by the selected malware family, including the total number of users affected. Select a user from the list to view all events for the malware family associated with that user. You can sort this column.
- **Stage and technique**: The matrix is organized by threat stage (e.g., **Discover Attack**, **Compromise**, etc.) and by MITRE ATT&CK  technique (e.g., **Reconnaissance**, **Resource Development**, etc.). The threat for a data breach increases as a malware family moves further to the right on the matrix. To learn more, see [What Is Zscaler Breach Predictor?](/breach-predictor/what-zscaler-breach-predictor)
![The Users Tab in Zscaler Breach Predictor](/downloads/breach-predictor/25.01/ZBP-Findings_Users-Tab.png)
[]The data presented on the Events tab is nearly identical to the data presented on the Events page. The primary difference between the two is that the Events tab focuses on a single threat, whereas the Events page lets you look at data across multiple threats. The Events tab also provides more information about why Breach Predictor is recommending particular policy updates.
To learn more, see [About Events](/breach-predictor/about-events).