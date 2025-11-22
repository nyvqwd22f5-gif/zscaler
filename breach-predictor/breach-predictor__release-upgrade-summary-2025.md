# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/breach-predictor/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for Breach Predictor.

**Clouds:** zscalerbp.net
The following service updates were deployed to zscalerbp.net on

## June 30, 2025
### Feature Available
#### Integration with SIEM Applications
Breach Predictor lets you send event data to security information and event management (SIEM) applications (e.g., CrowdStrike Next-Gen SIEM and Splunk) so that you can take direct action on threats with a holistic view of your organization's threat landscape.
You can integrate your SIEM applications on the Integration page in the Breach Predictor Portal (Profile > Integration).
[See image.](#siem-integration-tiles-06.25-rn)
To learn more, see [Integrating Applications with Zscaler Breach Predictor](/breach-predictor/integrating-applications-zscaler-breach-predictor).
[]![The SIEM Tiles on the Integration Page in Zscaler Breach Predictor](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Integrations_SIEM-06.25-RN.png)

### Feature Available
#### User Threat Profile Page
The Breach Predictor User Threat Profile page (Breach Predictor Portal > Users) gives you an overview of how threats are affecting users across your organization, broken down by MITRE ATT&CK  stage, department, threat type, and geography.
The Overview tab uses charts and graphics to give you a high-level look at how threats are affecting groups of users within your organization:
[See image.](#users-page-overview-06.25-rn)
The Users List tab lets you see information about how threats are affecting specific users in your organization, and gives you the ability to see details about each threat and user:
[See image.](#users-page-users-list-06.25-rn)
To learn more, see [About Users](/breach-predictor/about-users).
[]![The Overview Tab on the User Threat Profile Page in Zscaler Breach Predictor](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Users_Overview-Tab-06.25-RN.png)
[]![The Users List Tab on the User Threat Profile Page in Zscaler Breach Predictor](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Users_Users-List-Tab-06.25-RN.png)

### Feature Available
#### Various Updates to the Breach Predictor Portal
The Breach Predictor Portal contains extensive updates that improve the overall look, feel, and usability, including new charts, graphs, and filtering options, as well as updated data visibility.
To learn more, see [Using Zscaler Breach Predictor](/breach-predictor/using-zscaler-breach-predictor).

### Feature in Limited Availability
#### AI Assist Dashboard
To learn more about getting access to this feature, contact your Zscaler Account team.
The Breach Predictor AI Assist dashboard uses AI and machine learning analysis to provide a dynamic view of the threats that are affecting or could affect your organization. You can open the AI Assist dashboard from any screen in Breach Predictor:
[See image.](#ai-assist-button-06.25-rn)
On the splash page, you see customized recommendations based on Breach Predictor's exhaustive analysis of threat data for your organization:
[See image.](#ai-assist-greeting-06.25-rn)
Breach Predictor's agentic approach to threat monitoring gives your organization constant visibility across multiple areas, including detection, context, triage, response, and third-party integrations. At the top of the AI Assist dashboard, you can see the Breach AI Agents that are monitoring your organization's data:
[See image.](#breach-ai-agents-06.25-rn)
The AI Assist dashboard also provides dynamic prompts to give you more information about the data on a particular page, or you can enter your own questions to drill down further:
[See image.](#ai-agent-prompts-06.25-rn)
To learn more, see [Using the AI Assist Dashboard](/breach-predictor/using-ai-assist-dashboard).
[]![The AI Assist Button in Zscaler Breach Predictor](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-AI-Assist-Button-25.06-RN.png)
[]![The Splash Page of the AI Assist Dashboard in Zscaler Breach Predictor](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-AI-Assist-Dashboard-Main-Page-25.06-RN.png)
[]![The Breach AI Agents Bar in Zscaler Breach Predictor](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Breach-AI-Agents-Bar-25.06-RN.png)
[]![The prompts available on the Zscaler Breach Predictor AI Assist Dashboard](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-AI-Assist-Dashboard-Prompts-25.06-RN.png)

## May 01, 2025
### Feature in Limited Availability
#### Improved Integration with Log Data
To help you more easily identify which logs produce the threat information you see in the Zscaler Breach Predictor Portal, the Zscaler service includes company logos as part of the threat data on the Findings page (Breach Predictor Portal > Findings) and the Events page (Breach Predictor Portal > Events).
On the Findings page, on the Attack Path tab, you can see logos alongside certain observed MITRE ATT&CK  techniques. In the following example, the smashbrowser threat family is shown to have achieved the Drive-by Compromise technique. In this case, Zscaler logs identified the threat, and CrowdStrike logs provided data about the endpoints that the threat affected.
[See image.](#ZBP-Attack-Page-logos-0425-RN)
On the Events tab on the Findings page and on the Events page, you can click an individual event to see which log data identified the threat.
[See image.](#ZBP-Events-0425-RN)
To learn more, see [About Findings](/breach-predictor/about-findings), [Analyzing Findings](/breach-predictor/analyzing-findings), [About Events](/breach-predictor/about-events), and [Analyzing Events](/breach-predictor/analyzing-events).
[]![The Attack Path tab in the Breach Predictor Portal](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Findings-Smashbrowser-0425-RN.png)
[]![Event information in the Breach Predictor Portal](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Events-CrowdStrike-0425-RN.png)

### Feature in Limited Availability
#### Improvements to Policy Recommendations
In addition to existing policies (i.e., Sandbox and URL Filtering), the Zscaler service analyzes your File Type Control and SSL Inspection policies when making policy recommendations based on threat information in the Zscaler Breach Predictor Portal. After you click the name of a threat on the Findings page (Breach Predictor Portal > Findings), you can click Update Policy on the Threat page to see the policy updates that Breach Predictor recommends based on its threat analysis.
[See image.](#ZBP-Update-Policy-Button-0425-RN)
In the Recommendation panel, you can view the policy recommendations based on the threat analysis.
[See image.](#ZBP-Recommendation-Panel-0425-RN)
You can click Create Ticket to open the Create New Ticket from policy recommendation panel to specify the details of a Support ticket to make policy updates. Breach Predictor automatically populates the policy update information it's recommending, and you can specify other details (e.g., a name for the ticket, the assignee for the ticket, etc.).
[See image.](#ZBP-Create-New-Ticket-Panel-0425-RN)
To learn more, see [About Findings](/breach-predictor/about-findings), [Analyzing Findings](/breach-predictor/analyzing-findings), and [Requesting Updates in Zscaler Breach Predictor](/breach-predictor/requesting-updates-zscaler-breach-predictor).
[]![The Update Policy option in the Zscaler Breach Predictor Portal](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Threat-Page-Update-Policy-Button-RN.png)
[]![The Recommendation panel in the Zscaler Breach Predictor Portal](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-RecommendationPanel-RN.png)
[]![The Create New Ticket panel in the Zscaler Breach Predictor Portal](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-JiraTickets_CreateNewTicketPanel-RN.png)

## February 03, 2025
### Feature in Limited Availability
#### Updates to Zscaler Breach Predictor
To learn more about getting access to Zscaler Breach Predictor for your organization, contact your Zscaler Account team.
Policy Recommendations
Breach Predictor includes policy recommendations based on its analysis of your organization's risk of a security breach from every identified threat family. The recommendations allow you to preemptively remediate threats and vulnerabilities before they become incidents. You can find policy recommendations on the Findings page (Breach Predictor Portal > Findings) by clicking the name of a threat family, then clicking Update Policy.
[See image.](#zbp-policy-update-rn)
To learn more, see [About Findings](/breach-predictor/about-findings).
A Unified UI with Attack Path, Users, and Events to Enhance Threat Visibility
In addition to the analysis of individual threats available on the Findings page (Breach Predictor Portal > Findings), you can access the Events page (Breach Predictor Portal > Events) to see context around attack path, users, and events all in one place.
[See image.](#zbp-events-page-rn)
To learn more, see [About Events](/breach-predictor/about-events).
Endpoint Data Ingestion and Enrichment
In addition to Zscaler Internet Access (ZIA) and Zscaler Sandbox logs, Breach Predictor includes endpoint data from CrowdStrike logs as part of its data analysis to further enhance its ability to preemptively eliminate attack paths and lower your organization's overall threat risk.
To request enhancements for additional third-party endpoint data integrations, contact your Zscaler Account team.
To learn more, see [What Is Zscaler Breach Predictor?](/breach-predictor/what-zscaler-breach-predictor)
Enhancements Throughout the Breach Predictor Portal
The Breach Predictor Portal contains extensive updates that improve the overall look, feel, and usability of the product, including an updated Dashboard page (Breach Predictor Portal > Dashboard) with allowed policies over time and Breach Predictor trends. The entire Breach Predictor Portal has been updated to provide new charts and graphs, new filtering options, and updated data visibility.
To learn more, see [Using Zscaler Breach Predictor](/breach-predictor/using-zscaler-breach-predictor).
Ability to Create Tickets for Policy Updates and Product Improvements
As part of Breach Predictor's new policy recommendation functionality, you can create Request (Jira) tickets from the Breach Predictor Portal so that Zscaler Support can make the necessary updates. Additionally, you can create Support (ServiceNow) tickets to report problems and suggest improvements to Breach Predictor. The tickets created for your organization appear on the Tickets page (Breach Predictor Portal > Tickets).
[See image.](#zbp-jira-ticket-rn)
To learn more, see [Requesting Updates in Zscaler Breach Predictor](/breach-predictor/requesting-updates-zscaler-breach-predictor) and [Integrating Applications with Zscaler Breach Predictor](/breach-predictor/integrating-applications-zscaler-breach-predictor).
[]![Updating a policy](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Policy-Recommendation-RN.png)
[]![Creating a Jira ticket](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Create-Jira-Tickets-RN.png)
[]![Viewing the Events page](/sites/default/files/downloads/breach-predictor/release-notes/release-upgrade-summary-2025/ZBP-Events-Page-RN.png)
