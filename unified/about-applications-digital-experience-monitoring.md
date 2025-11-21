# About Applications for Digital Experience Monitoring
Source: https://help.zscaler.com/unified/about-applications-digital-experience-monitoring
PDF: https://help.zscaler.com/pdf/com/en/1492676.pdf

The Applications page provides an overview of the configured applications. The Zscaler service provides predefined applications, or you can configure a customized application. Each application is designed to have corresponding probes associated with it.
The Applications page provides the following benefits and enables you to:
- Configure or add applications by creating web probes and cloud path probes for insight.
- Configure tenants access for applications.
- Manage the top private applications from Private Applications based on port usage.
You can configure two types of applications in the Admin Portal:
- Predefined Application: SaaS applications provided by the Admin Portal for you to configure for your organization. There are predefined paths for each application. Zscaler recommends that you configure these paths to a SaaS tenant for your organization for applications that require a tenant ID. To view the list of predefined applications, see [Predefined Applications for Digital Experience Monitoring](/unified/predefined-applications-digital-experience-monitoring).
- Custom Application: Customizable SaaS or web applications that you can create and onboard in the Admin Portal for your organization.
By default, all predefined applications have web and cloud path preconfigured probes and are automatically enabled when onboarded.
If you create a custom application, you must create a Web probe to enable it. Most applications have at least one Web probe and one Cloud Path probe to monitor the application's front door. Network applications are the exception, since they require only a single Cloud Path probe for monitoring. To learn more, see [Monitoring the Applications Overview](/unified/monitoring-applications-overview).
For Microsoft Teams, in addition to the application front door for monitoring the Teams client connectivity and call signaling (teams.microsoft.com), an additional cloud path is created to monitor the Teams Transport Relay service which handles media communication (world.tr.teams.microsoft.com).
Although a Web probe must be onboarded for most predefined or custom applications to be enabled, Network applications require only a single Cloud Path probe.
To view the probes for an application:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration **> **Applications**.
- Under the **Predefined Applications** or **Custom Applications** sections, expand an **Application **row within the table.
All probes that have been configured for the application are displayed, along with their current **Status**. To learn more, see [About Probes](/unified/about-probes).
The **Status **for predefined applications that are not yet fully activated appears as **Pending Onboard** in the Predefined Applications list.
About the Applications Page
On the Applications page, you can do the following:
- [Add a new custom application](/unified/adding-custom-application).
- [Configure a predefined application](/unified/configuring-predefined-application).
- [Add a new probe](/unified/configuring-probe).
- [Edit an application](/unified/editing-application).
- Expand Unified Communication or Web Applications.
- Delete a custom application. You cannot delete a predefined application.
- [Manage Top Private Apps.](/unified/managing-top-private-applications)
- [View and manage probes for applications you have configured](/unified/about-probes).
![Applications Overview](/downloads/zdx/configuration/applications/about-applications/zdx-applications-overview-callouts5.png)