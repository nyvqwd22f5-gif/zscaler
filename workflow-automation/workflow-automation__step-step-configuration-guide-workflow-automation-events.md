# Step-by-Step Configuration Guide for Workflow Automation for Events
Source: https://help.zscaler.com/workflow-automation/step-step-configuration-guide-workflow-automation-events
PDF: https://help.zscaler.com/pdf/com/en/1500331.pdf

Business Insights integration with Workflow Automation is automatically enabled if you are subscribed to Business Insights. If you have subscriptions to various integrated applications of Workflow Automation such as Data Loss Prevention (DLP) and Zscaler Digital Experience (ZDX), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. Select Business Insights to configure and manage your organization's SaaS application events.
This guide takes you through the configuration steps you need to complete to begin using Workflow Automation for your organization. Because Workflow Automation integrates with Business Insights, you need to set up and configure Business Insights applications before you configure Workflow Automation. To learn more, see the [What Is Zscaler Business Insights?](/business-insights/what-zscaler-business-insights)
Before you begin configuring Workflow Automation, Zscaler recommend reading the following articles:
- [What Is Workflow Automation?](/zia/what-zscaler-workflow-automation)
- [Accessing and Navigating the Workflow Automation Admin Portal for Events](/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-events)
- [Managing Events](/workflow-automation/managing-events)
- [Understanding Workflows for Events](/workflow-automation/understanding-workflows-events)
Prerequisites
Ensure that you have the appropriate permissions to access Workflow Automation Admin Portal from the Business Insights Admin Portal. If you don't have permission, contact an admin with full access to provide you with the necessary permission. To learn more, see [Adding Admins in Business Insights](/business-insights/adding-admins-business-insights).
Configuring Workflow Automation for Events
To configure Workflow Automation for events, complete the following steps:
- [Step 1: Provision Your Admins in Business Insights to Access Workflow Automation](#Step1-Provision-Admins)
- [Step 2: Integrate Workflow Automation with a Ticketing Integration Application](#ticketing-application-integration-step)
- [Step 3: Configure Event Groups in Workflow Automation](#Event-Groups)
- [Step 4: Configure Event Group Priorities in Workflow Automation](#Event-Group-Priorities)
- [Step 5: Configure and Map Notification and Survey Templates in Workflow Automation](#Step8-Configure-Templates)
- [Step 6: Configure Workflows in Workflow Automation](#step10-configure-workflows)
[]To manage events in Workflow Automation, admins need to be provisioned in Business Insights with a role that has the **Workflow Access** permission configured.
To provision administrators as applicable, see:
- [About Administrators in Business Insights](/business-insights/about-administrators-business-insights)
- [Adding Admins in Business Insights](/business-insights/adding-admins-business-insights)
After the admins in your organization are provisioned for Workflow Automation, they can access the Workflow Automation Admin Portal. To access the Workflow Automation Admin Portal, go to **Administration** > **Workflow Automation** in the Business Insights Admin Portal. You are redirected to the Workflow Automation Admin Portal.
[See image.](#Navigation-to-Workflow-Automation)
[]Admins can create and associate the ServiceNow ticketing integration application for managing Business Insights events. To create and associate a ticket with an event, you must integrate Workflow Automation with ServiceNow.
To integrate Workflow Automation with ServiceNow, see:
- [Adding Integrations for Events](/workflow-automation/adding-integrations-events)
- [Managing ServiceNow Integration for Events](/workflow-automation/managing-servicenow-integration-events)
[]To assist with the management of events that appear on the Events page in the Workflow Automation Admin Portal, admins can add and map event groups. Admins with workflow access to Workflow Automation can map event groups to the different properties.
To configure event groups, see:
- [Managing Event Groups](/workflow-automation/managing-event-groups)
- [Managing Event Group Mappings](/workflow-automation/managing-event-group-mappings)
[]Admins can prioritize the Business Insights events that appear on the Events page on the Workflow Automation Admin Portal by assigning a priority to the different event groups that are associated with the events.
To configure event group priorities, see [Managing Priorities for Events](/workflow-automation/managing-priorities-events).
[]Admins can configure automated workflows to notify the end user related to the event and ask for justification for the event. The email sent to the end user uses a notification template and a survey template that is created in the Workflow Automation Admin Portal. Workflow Automation provides default notification templates and survey templates, but admins can configure custom notification or survey templates as necessary.
To configure and map notification and survey templates, see:
- [Managing Notification Templates for Events](/workflow-automation/managing-notification-templates-events)
- [Managing Survey Templates for Events](/workflow-automation/managing-survey-templates-events)
- [Managing Template Mappings for Events](/workflow-automation/managing-template-mappings-events)
[]Admins can configure workflows to assist them with creating tickets and assigning them to dedicated teams for managing events. Workflows are automatically triggered by those event types that match the mapped criteria for the workflows. Workflows can contain one or more actions to be performed against an event and do not require user intervention.
To configure and map workflows, see:
- [Managing Workflow Templates for Events](/workflow-automation/managing-workflow-templates-events)
- [Managing Workflows for Events](/workflow-automation/managing-workflows-events)
- [Managing Workflow Mappings for Events](/workflow-automation/managing-workflow-mappings-events)
[]![Navigation to Workflow Automation](/downloads/workflow-automation/business-insights/getting-started/step-step-configuration-guide-workflow-automation-events/WA-BI-step-by-step-admin-portal.png)