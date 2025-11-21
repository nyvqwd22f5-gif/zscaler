# Step-by-Step Configuration Guide for Workflow Automation for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/step-step-configuration-guide-workflow-automation-zdx
PDF: https://help.zscaler.com/pdf/com/en/1487436.pdf

Zscaler Digital Experience (ZDX) integration with Workflow Automation is automatically enabled if you are subscribed to ZDX Advanced Plus. If you have subscriptions to various integrated applications of Workflow Automation such as Data Loss Prevention (DLP), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. Select Zscaler Digital Experience (ZDX) to configure automated workflows for the ZDX alerts.
This guide takes you through the configuration steps you must complete to begin using Workflow Automation for your organization. Because Workflow Automation integrates with ZDX, you must configure the ZDX alert rules before you configure Workflow Automation.
Before you begin configuring Workflow Automation, Zscaler recommends reading the following articles:
- [What Is Workflow Automation?](/zia/what-zscaler-workflow-automation)
- [Accessing and Navigating the Workflow Automation Admin Portal for ZDX Alerts](/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-zdx)
- [Understanding Workflows for ZDX Alerts](/workflow-automation/understanding-workflows-workflow-automation-zdx)
Prerequisites
Before configuring Workflow Automation for ZDX alerts, ensure that:
- You have the appropriate permission for Alerts to access Workflow Automation from the ZDX Admin Portal. If you don't have permission, contact an admin with full access to provide you with the necessary permission. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
- Your subscription level supports Workflow Automation. To learn more, see [Ranges & Limitations for ZDX](/zdx/ranges-limitations).
Configuring Workflow Automation for ZDX Alerts
To configure Workflow Automation for ZDX alerts, complete the following steps:
- [Step 1: Provision Your Admins in ZDX Admin Portal to Access Workflow Automation](#provision-wa-zdx-step1)
- [Step 2: Integrate Workflow Automation with a Ticketing Integration Application](#ticket-intergration-zdx-step2)
- [Step 3: Configure Workflows in Workflow Automation](#managing-workflows-zdx-step3)
[]To manage ZDX alerts in Workflow Automation, admins must be provisioned in the ZDX Admin Portal with a role that has the Workflow Access permission configured. You can configure admins with full workflow access or restricted workflow access to the Workflow Automation Admin Portal.
To provision administrators as applicable, see:
- [About Administrators](/zdx/about-administrators)
- [Adding ZDX Admins](/zdx/adding-zdx-admins)
- [About ZDX Role-Based Administration](/zdx/about-zdx-role-based-administration)
- [Adding ZDX Roles](/zdx/adding-zdx-roles)
After the admins have been provisioned with the appropriate permissions, they must ensure that they can access the Workflow Automation Admin Portal. To access the Workflow Automation Admin Portal, go to **Administration** > **Workflow Automation **in the ZDX Admin Portal.
[See image.](#Navigation-WA-ZDX-protal)
[]Admins can create and associate the ServiceNow ticketing integration application for managing alerts. To create and associate a ticket with an alert, you must integrate Workflow Automation with ServiceNow.
To integrate Workflow Automation with ServiceNow, see [Managing ServiceNow Integration for ZDX Alerts](/workflow-automation/managing-servicenow-integration-zdx-alerts).
[]Admins can configure workflows to assist them with creating tickets and assigning them to dedicated teams for managing alerts. Workflows are automatically triggered by those alerts that match the mapped criteria for the workflows. Workflows can contain one or more actions to be performed against an alert and do not require user intervention.
To configure and map workflows, see:
- [Understanding Workflows for ZDX Alerts](/workflow-automation/understanding-workflows-workflow-automation-zdx)
- [Managing Workflow Templates for ZDX Alerts](/workflow-automation/managing-workflow-templates-zdx-alerts)
- [Managing Workflows for ZDX Alerts](/workflow-automation/managing-workflows-zdx-alerts)
- [Managing Workflow Mappings for ZDX Alerts](/workflow-automation/managing-workflow-mappings-zdx-alerts)
- [Managing Shared Configuration for ZDX Alerts](/workflow-automation/managing-shared-configuration-zdx)
![Navigating to the Workflow Automation Admin Portal from the ZDX Admin Portal](/downloads/zia/workflow-automation/getting-started/step-step-configuration-guide-workflow-automation/WA-navigation-ZDX.png)
[]