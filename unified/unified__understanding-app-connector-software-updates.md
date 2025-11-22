# Understanding App Connector Software Updates
Source: https://help.zscaler.com/unified/understanding-app-connector-software-updates
PDF: https://help.zscaler.com/pdf/com/en/1496221.pdf

When creating App Connector groups, you can specify a day and time where the App Connector software is updated to the latest version. When a new software version is available, an App Connector in the group is chosen at random to update. While updating, the App Connector restarts and becomes temporarily unavailable. Any new application access is redirected to the other App Connectors in the App Connector group.
The update occurs within a 4-hour window and starts at the specified time for the App Connector group. After an App Connector has successfully updated, another eligible App Connector in the group is chosen and updated. This continues until the 4-hour window expires or all the App Connectors in the group have updated successfully. If a software update is unsuccessful, the update process is retried in every periodic software update until all App Connectors are upgraded.
Starting in App Connector version 24.650.4 and later, a version check and automated upgrade is performed during an initial connection. To learn more, see [Zscaler Trust](https://trust.zscaler.com/private.zscaler.com/security-advisories).
If the App Connectors for your internal applications are using software that is not functioning as expected, Zscaler Support might update software for these App Connectors prior to the next periodic software update. Zscaler Support informs your organization's Private Applications administrators in advance if there is a need for an immediate software update.
To learn more, see [Scheduling Periodic Software Updates for an App Connector Group](/unified/scheduling-periodic-software-updates-app-connector-group) and [Manually Updating App Connector Software](/unified/manually-updating-app-connector-software). For information on locally updating operating system software or software packages via a deployed App Connector console, see [Managing Deployed App Connectors](/unified/managing-deployed-app-connectors).
[]About the App Connector Update Status
On the App Connectors page (Infrastructure > Private Access > Components > App Connectors), you can see the update status of each App Connector in the Update Status column. There are three types of statuses:
- [Scheduled](#scheduled)
- [Success](#success)
- [Failure](#failure)
About App Connector Host Operating System Management
App Connectors are licensed so that Zscaler can periodically update their software. However, updates to the host OS is the organization's responsibility, not Zscaler's. The App Connector software is designed to be compatible with updates to the host OS. Zscaler recommends updating the host OS whenever you determine it is necessary. To learn more, see [Managing Deployed App Connectors](/unified/managing-deployed-app-connectors#Updating) and [Operating System Security](/unified/app-connector-deployment-prerequisites#SecurityAndFirewallReqs).
[]If an App Connector successfully updates to the latest version, its **Update Status** displays **Success**.
When you hover over the **Success** status, it displays the **Scheduled Version**, which is the scheduled software version that the App Connector updated to.
![Success status with Scheduled Version displayed](/downloads/zpa/documentation-knowledgebase/connectors/about-connector-periodic-software-update/about-connector-periodic-software-update/zpa-connector-successstatus.png)
[]If an App Connector is scheduled to update to the latest version, its **Update Status** displays **Scheduled**.
When you hover over the **Scheduled** status, it displays the following information:
- **Scheduled Version**: Displays the scheduled software version that the App Connector updates to.
- **Upgrade Window**: Displays the 4-hour window during which the App Connector updates.
![Scheduled status with Scheduled Version and Upgrade Window displayed](/downloads/zpa/documentation-knowledgebase/connectors/about-connector-periodic-software-update/about-connector-periodic-software-update/zpa-connector-scheduledstatus.png)
When the App Connector is scheduled for an update, you can't change the periodic software update time for that particular App Connector.
If an App Connector is scheduled for an update, you can also manually update the App Connector before the scheduled time. To learn more, see [Manually Updating App Connector Software](/unified/manually-updating-app-connector-software).
[]If an App Connector fails to update to the latest version, its **Update Status** displays **Failure**. When you hover over the **Failure** status, it displays the **Scheduled Version**, which is the scheduled software version that the App Connector failed to update to. If a software update is unsuccessful, the update process is retried in every periodic software update until all App Connectors are upgraded.
![Failure status with Scheduled Version displayed](/downloads/zpa/documentation-knowledgebase/connectors/about-connector-periodic-software-update/about-connector-periodic-software-update/zpa-connector-failedstatus.png)
Zscaler recommends that you restart the App Connector virtual machine (VM) to recover it from the failure state.