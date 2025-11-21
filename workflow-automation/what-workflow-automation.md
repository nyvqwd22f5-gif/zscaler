# What Is Workflow Automation?
Source: https://help.zscaler.com/workflow-automation/what-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1417816.pdf

Zscaler provides a subscription to Data Loss Prevention (DLP) Incidents, Business Insights Events, and Zscaler Digital Experience (ZDX) Alerts integrated with Workflow Automation. ZDX and Business Insights integrations are automatically enabled when you subscribe to ZDX Advanced Plus and Business Insights, respectively. However, you should purchase a separate subscription to manage your DLP incidents. For more information, contact Zscaler Support.
Workflow Automation is an application that enables governance admins to automate the management and resolution of Data Protection incidents, Business Insights events, and ZDX alerts that occur in their organization. Workflow Automation integrates with:
- Zscaler Internet Access (ZIA) to capture the Data Protection incidents generated from the DLP policies defined in ZIA.
- ZDX to generate enriched tickets for different events that are triggered when the predefined threshold is reached for the alert rules defined in ZDX.
- Business Insights to manage the usage of the SaaS application licenses provisioned to end users.
The following sections provide more details on each Workflow Automation integration:
- [DLP Incidents](#dlp-incidents)
- [ZDX Alerts](#zdx-alerts)
- [Business Insights Events](#business-insights-events)
[]Workflow Automation integration with Business Insights allows admins to manage Business Insights events by reviewing unused application licenses, helping to optimize SaaS application usage within the organization. The Events and Event Details pages in the Workflow Automation Admin Portal display all the events along with the end user details for easy verification and remediation of those events.
This integration also provides the capability to group individual events into event groups and assign priorities to those event groups. Admins can configure workflows in Workflow Automation to notify the end user about the event regarding their unused application licenses, request for justification, and create a ticket in ServiceNow to deprovision the users based on their response.
By using all the event features provided in Workflow Automation, admins can streamline application license management allocated to the employees, leading to more granular and cost-effective management. These insights can assist admins with SaaS application deployment, compliance, and optimization of purchase or renewal of the application licenses.
To learn more about configuring Workflow Automation, see [Step-by-Step Configuration Guide for Workflow Automation for Events](/workflow-automation/step-step-configuration-guide-workflow-automation-events).
[]Workflow Automation provides a closed loop Incidents management where admins can review and remediate the Data Protection incidents that have occurred in their organization all in one location. The Incidents page lists all the Data Protection incidents along with the details for each of those incidents. The incident details include the metadata for the incident and the data that triggered the incident.
Workflow Automation provides the capability to group individual incidents into incident groups and assign priorities to those incident groups. These incident groups can then be assigned to different admins.
To assist with the review and remediation process of incidents on the Incidents page, Workflow Automation utilizes workflow management features. Admins can use the workflow management features to:
- Notify the end user involved in an incident requesting justification for the incident.
- Escalate the incident to an end user's manager or other approver requesting justification.
Workflow Automation also enables you to configure workflows that automatically perform different actions to manage and remediate DLP incidents.
By using all the DLP features provided in Workflow Automation, admins can dramatically reduce resolution time and obtain insights into where their security is at risk in their organization. These insights can assist them with security challenges such as deployment, compliance, and upgrades.
To learn more about configuring Workflow Automation for DLP Incidents, see [Step-by-Step Configuration Guide for Workflow Automation](/zia/step-step-configuration-guide-workflow-automation).
[]Workflow Automation enables you to configure workflows that automatically trigger tickets for ZDX alerts and send the alert details to admins to review and remediate the issue. An alert is triggered when certain events in your organization meet the alert rule criteria defined in the ZDX Admin Portal. Alert details primarily include information about issues with connected devices, applications, network performance, and ZDX Score.
The application also provides you with the capability to group alerts of the same entity and assign the related tickets to dedicated teams. The application can be used to configure integrations, workflows, and other related configurations to automatically generate tickets for the ZDX alerts when a predefined threshold is reached for different types of events.
By using all the ZDX alert features provided in Workflow Automation, admins can proactively monitor end user experience and productivity metrics that might fluctuate due to device and network issues that occur in the organization. This application also helps them to take the necessary steps to resolve and improve end user performance.
To learn more about configuring Workflow Automation, see [Step-by-Step Configuration Guide for Workflow Automation for ZDX Alerts](/workflow-automation/step-step-configuration-guide-workflow-automation-zdx)[.]
Key Benefits
The key benefits of using Workflow Automation are as follows:
- Protection of your security posture, optimization of application license usage, and improvement of user experience by proactively monitoring every DLP incident, Business Insights event, and ZDX alert, respectively, that occur in your organization.
- Reduction in resolution time by centralized management of all incidents, alerts, and events through automated workflows in one location.
- Establishment of clear lines of responsibility for managing various incidents, alerts, and events by priority.
- Automatic generation of enriched tickets for streamlined management of ZDX alerts to reduce device, application, and network issues.
- Automatic creation of tickets to manage Business Insights events to reduce spending on unwanted licenses.
- Assignment of the tickets to the dedicated teams to review in-depth details of incidents, alerts, and events, and take necessary action.