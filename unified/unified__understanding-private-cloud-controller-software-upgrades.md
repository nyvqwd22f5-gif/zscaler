# Understanding Private Cloud Controller Software Upgrades
Source: https://help.zscaler.com/unified/understanding-private-cloud-controller-software-upgrades
PDF: https://help.zscaler.com/pdf/com/en/1528711.pdf

When creating Private Cloud Controller groups, you can specify a day and time when the Private Cloud Controller software is updated to the latest version. When a new software version is available, a Private Cloud Controller in the group is chosen at random to update. While updating, the Private Cloud Controller restarts and becomes temporarily unavailable. Any new application access is redirected to the other Private Cloud Controllers in the Private Cloud Controller group.
The update occurs within a 4-hour window and starts at the specified time for the Private Cloud Controller group. After a Private Cloud Controller is successfully updated, another eligible Private Cloud Controller in the group is chosen and updated. This continues until the 4-hour window expires or all the Private Cloud Controllers in the group have updated successfully. If a software update is unsuccessful, the update process is retried in every periodic software update until all Private Cloud Controllers are upgraded.
If the Private Cloud Controllers for your internal applications are using software that is not functioning as expected, Zscaler Support might update software for these Private Cloud Controllers prior to the next periodic software update. Zscaler Support informs your organization's administrators in advance if there is a need for an immediate software update.
To learn more, see [Scheduling Periodic Software Updates for a Private Cloud Controller Group](/unified/scheduling-periodic-software-updates-private-cloud-controller-group) and [Manually Updating Private Cloud Controller Software](/unified/manually-updating-private-cloud-controller-software).
[]About the Private Cloud Controller Upgrade Status
On the Private Cloud Controllers page, you can see the update status of each Private Cloud Controller in the **Upgrade Status** column. There are three types of statuses:
- [Scheduled](#scheduled)
- [Success](#success)
- [Failure](#failure)
About Private Cloud Controller Host Operating System Management
Private Cloud Controllers are licensed so that Zscaler can periodically update their software. However, updates to the host OS are the organization's responsibility, not Zscaler's. The Private Cloud Controller software is designed to be compatible with updates to the host OS. Zscaler recommends updating the host OS whenever you determine it is necessary.
[]If a Private Cloud Controller successfully updates to the latest version, its **Update Status** displays **Success**.
When you hover over the **Success** status, it displays the **Scheduled Version**, which is the scheduled software version that the Private Cloud Controller updated to.
![Success status with Scheduled Version displayed](/downloads/zpa/documentation-knowledgebase/connectors/about-connector-periodic-software-update/about-connector-periodic-software-update/zpa-connector-successstatus.png)
[]If a Private Cloud Controller is scheduled to update to the latest version, its **Update Status** displays **Scheduled**.
When you hover over the **Scheduled** status, it displays the following information:
- **Scheduled Version**: Displays the scheduled software version that the Private Cloud Controller updates to.
- **Upgrade Window**: Displays the 4-hour window during which the Private Cloud Controller updates.
![Scheduled status with Scheduled Version and Upgrade Window displayed](/downloads/zpa/documentation-knowledgebase/connectors/about-connector-periodic-software-update/about-connector-periodic-software-update/zpa-connector-scheduledstatus.png)
When the Private Cloud Controller is scheduled for an update, you can't change the periodic software update time for that particular Private Cloud Controller.
If a Private Cloud Controller is scheduled for an update, you can also manually update the Private Cloud Controller before the scheduled time. To learn more, see [Manually Updating Private Cloud Controller Software](/unified/manually-updating-private-cloud-controller-software).
[]If a Private Cloud Controller fails to update to the latest version, its **Update Status** displays **Failure**. When you hover over the **Failure** status, it displays the **Scheduled Version**, which is the scheduled software version that the Private Cloud Controller failed to update to. If a software update is unsuccessful, the update process is retried in every periodic software update until all Private Cloud Controllers are upgraded.
![Failure status with Scheduled Version displayed](/downloads/zpa/documentation-knowledgebase/connectors/about-connector-periodic-software-update/about-connector-periodic-software-update/zpa-connector-failedstatus.png)
Zscaler recommends that you restart the Private Cloud Controller virtual machine (VM) to recover it from the failure state.