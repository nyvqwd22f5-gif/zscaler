# About Third-Party Integrations
Source: https://help.zscaler.com/zpc/about-third-party-integrations
PDF: https://help.zscaler.com/pdf/com/en/1403366.pdf

Security Information and Event Management (SIEM) solutions collect security data from security systems, network devices, servers, domain controllers, etc. The tools store, aggregate and apply analytics to that data to discover trends, detect threats, anomalies, enabling the security team to investigate these threats and any alerts from all of their security tools in one place.
You can integrate ZPC with the following third-party tools:
- SIEM and ITSM tools for data analysis, incident management, and remediation.
- Cloud storage services such as Amazon simple storage service (Amazon S3) and send the system audit logs and alert notifications to an S3 bucket for further evaluation.
- ChatOps tools like Slack and send notifications to specific Slack channels.
Third-party integration includes the following benefits and enables you to:
- Have increased visibility into the security posture of your cloud infrastructure, identify potential threats, and take immediate action.
- Reduce the number of false positive alerts and focus on real threats.
- Integrate the SIEM solutions with other tools or services, such as Amazon S3, Azure Blob Storage, etc. for storage, auditing, or further evaluation.
About the Integrations Page
On the Integrations page (Administration > Integrations), you can view the integrations for:
- [Cloud Storage](#cloud)
- [ITSM](#itsm)
- [ChatOps Tools](#slack)
![The Integrations page](/downloads/zpc/third-party-integrations/about-third-party-integrations/zpc-integ-page.png)
- []View the list of cloud storage integrations. For each integration, you can see:
- **Cloud Storage**: The name of the cloud storage service (Amazon S3 Bucket or Azure Blob Storage).
- **Integration Name**: The integration name.
- **Log Type**: The type of data log (Alert or Audit Logs) that is sent to the storage service.
- **Last Sent**: The date and time when the data was last sent to the storage service.
- **Status**: The outcome (Success, Failed, Paused, or Pending) of the previous data transfer.
- **Data Transfer**: The state (Enabled or Disabled) of data transfer.
By default, the data transfer is enabled. If you want to pause the transfer without deleting the integration, select the toggle to disable the data transfer. If any data transfer is in progress, the activity is completed and then the data transfer is disabled.
- [Add a cloud storage integration](/zpc/adding-cloud-storage-integrations).
- [Edit a cloud storage integration](/zpc/editing-or-deleting-cloud-storage-integration).
- [Delete a cloud storage integration](/zpc/editing-or-deleting-cloud-storage-integration).
![Cloud storage integrations](/downloads/zpc/third-party-integrations/about-third-party-integrations/zpc-integ-cloudstoragesection.png)
- []View the list of ITSM integrations. For each ITSM integration, you can see:
- **IT Service**: The name of the service (Jira or ServiceNow).
- **Integration Name**: The integration name.
- **Hostname**: The host name for the service.
- **Log Type**: The type of data log (Alert or Audit Logs) that is sent to the IT service.
- **Last Sent**: The date and time when the data was last sent to the IT service.
- **Status**: The outcome (Success, Failed, Paused, or Pending) of the previous data transfer.
- **Data Transfer**: The state (Enabled or Disabled) of data transfer.
- [Add an ITSM integration](/zpc/integrating-servicenow).
- Sort the column data.
- Enable or disable the data transfer.
- [Edit an ITSM integration](/zpc/editing-or-deleting-itsm-integration).
- [Delete an ITSM integration](/zpc/editing-or-deleting-itsm-integration).
![ITSM integrations](/downloads/zpc/third-party-integrations/about-third-party-integrations/zpc-integ-itsmsection.png)
- []View the list of Slack integrations. For each integration, you can see:
- **Service**: The name of the service (Slack).
- **Integration Name**: The integration name.
- **Channels**: The number of channels that are added for sending notifications.
- **Last Sent**: The date and time when the data was last sent to the Slack channels.
- **Status**: The outcome (Success, Failed, Paused, or Pending) of the previous data transfer.
- **Data Transfer**: The state (Enabled or Disabled) of data transfer.
- [Add a Slack integration](/zpc/integrating-zpc-slack).
- Sort the column data.
- Enable or disable the data transfer.
- [Edit a Slack integration](/zpc/editing-or-deleting-slack-integrations).
- [Delete a Slack integration](/zpc/editing-or-deleting-slack-integrations).
![Slack integrations](/downloads/zpc/third-party-integrations/about-third-party-integrations/zpc-integ-chatopssection.png)