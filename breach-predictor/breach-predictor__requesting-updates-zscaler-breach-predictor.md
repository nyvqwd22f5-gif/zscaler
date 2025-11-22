# Requesting Updates in Zscaler Breach Predictor
Source: https://help.zscaler.com/breach-predictor/requesting-updates-zscaler-breach-predictor
PDF: https://help.zscaler.com/pdf/com/en/1518501.pdf

You can create two types of tickets in Breach Predictor: Request tickets and Support tickets. Request tickets are based on Breach Predictor policy update recommendations and are created from the [Findings page](/breach-predictor/about-findings). Breach Predictor uses its extensive threat information to analyze your existing policies (i.e., File Type Control, SSL Inspection, URL Filtering, etc.) and suggests policy updates based on that analysis. Breach Predictor automatically populates the ticket request with specific information about the threat family involved, its placement on the MITRE ATT&CK  matrix, and the policies that require updates.
Support tickets cover updates that don't involve policy changes (i.e., suggestions or problems with the software). You can create a request for a Support ticket directly from the Support tab on the Tickets page, and Zscaler Support uses the information you provide to create a ServiceNow ticket as needed.
Ticket creation in Breach Predictor requires that you [integrate Breach Predictor with Jira and ServiceNow](/breach-predictor/integrating-applications-zscaler-breach-predictor). After integration, you can access instances of Jira and ServiceNow where you can see more specific details about each ticket. The Breach Predictor Tickets page provides high-level details about each ticket, with a link that opens your instance of Jira or ServiceNow in a separate browser tab.
- [Creating a Request Ticket for a Policy Update](#create-request-ticket)
- [Submitting Information for a Support Ticket](#submit-support-ticket)
You can view any Request or Support tickets that have been opened for your organization on the [Tickets page](/breach-predictor/about-tickets).
[]
- Go to **Breach Predictor Portal** > **Findings**.
- On the **Findings** page, on the **MITRE ATT&CK  Mapping** page, click the name of a threat family.
[See image.](#click-threat-name)
The **Threat** page opens.
- On the **Threat** page, click **Update Policy**.
[See image.](#click-update-policy)
The **Recommendation** panel opens.
- In the **Recommendation** panel, review the policy recommendations, then click **Create Ticket**.
[See image.](#click-create-jira-ticket)
The **Create New Ticket from policy recommendation** panel opens.
- In the **Create New Ticket from policy recommendation** panel, review the policy recommendations, select the policies to update, provide a name and details for the ticket, then click **Create**.
[See image.](#create-new-ticket)
- In the **Confirm Update** window, click **Confirm**.
[See image.](#click-confirm)
The ticket is created and you can track its progress on the **Request** tab on the **Tickets** page.
[]![A Threat Name in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-JiraTickets_ClickThreatName.png)
[]![The Update Policy Option in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-JiraTickets_UpdatePolicyButton.png)
[]![Creating a Jira Ticket in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-JiraTickets_RecommendationPanel.png)
[]![Policy Recommendation Details in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-JiraTickets_CreateNewTicketPanel.png)
[]![The Confirm Option for a Support Ticket in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-JiraTickets_ConfirmUpdate.png)
[]
- Go to **Breach Predictor Portal** > **Tickets**.
- On the **Tickets** page, on the **Support** tab, click **Create**.
[See image.](#click-create-support)
The **Create New Ticket** panel opens.
- In the **Create New Ticket** panel, in the **Describe your issue** field, enter information about the update you're requesting.
[See image.](#enter-ticket-description)
- Click **Submit**.
The ticket information appears in the table. A Zscaler Support team member will follow up with more information and a ticket number if a ticket is created.
[]![Creating a Support Ticket in Zscaler Breach Predictor](/downloads/breach-predictor/25.01/ZBP-JiraTickets_SupportCreate.png)
[]![The Describe Your Issue Field for a Support Ticket in Zscaler Breach Predictor](/downloads/breach-predictor/25.01/ZBP-JiraTickets_SupportDescription.png)