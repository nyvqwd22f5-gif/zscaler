# Creating Outegrations
Source: https://help.zscaler.com/uvm/creating-outegrations
PDF: https://help.zscaler.com/pdf/com/en/1530646.pdf

The Zscaler Security Operations (SecOps) platform allows you to set up outbound integrations (i.e., outegrations) with external systems, such as work management tools (e.g., [Jira](/uvm/configuring-jira-outegration), [ServiceNow](/uvm/configuring-servicenow-outegration)), alert systems (e.g., Slack, email), automation tools, and storage solutions. For information on managing existing outegrations, see [Managing Outegrations](/uvm/managing-outegrations).
To create an outegration:
-
Go to **Configure** > **Outegrations**.
A list of all existing outegrations appears.
- Click** Create**.
-
Select an outegration from the available tiles. You can also search for an outegration in the search field.
The outegration setup wizard appears.
- In the outegration setup wizard, configure the setup in the following steps:
- **Connect**: Enter the outegration details. Depending on the outegration type, this step includes selecting an [authentication](/uvm/configuring-authentications) method to communicate with the external system.
- **Settings**: Configure the outegration settings. All outegrations require selecting an entity to create the outegration from. Some types might include additional settings (e.g., work management outegrations allow you to configure the Create Ticket button).
- **Mapping**: Configure the outegration mapping to define how data is exchanged and synchronized between the two systems.
-
Click **Finish** to save the outegration.
Your new outegration appears on the Outegrations page.