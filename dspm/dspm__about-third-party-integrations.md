# About Third-Party Integrations
Source: https://help.zscaler.com/dspm/about-third-party-integrations
PDF: https://help.zscaler.com/pdf/com/en/1474786.pdf

Security Information and Event Management (SIEM) is a solution to detect and address security threats and vulnerabilities. Data from security systems, network devices, servers, domain controllers, etc., is aggregated and analyzed to identify threats or anomalies, enabling security teams to investigate and address these issues.
You can integrate DSPM with the following third-party tools:
- Cloud storage services: [Amazon simple storage service (Amazon S3)](/dspm/integrating-amazon-s3), [Azure Blob Storage](/dspm/integrating-azure-blob-storage), and [Amazon Security Lake](/dspm/integrating-amazon-security-lake)
- ITSM tools:[ Jira](/dspm/integrating-jira) and [ServiceNow](/dspm/integrating-servicenow)
- ChatOps tools: [Slack](/dspm/integrating-slack)
Third-party integration includes the following benefits and enables you to:
- Have increased visibility into the security posture of your data.
- Reduce the number of false positive alerts and focus on real threats.
- Audit security incidents and take immediate action to remediate issues.
About the Integrations Page
On the Integrations page (Administration > Integrations), you can view the integrations for:
- [Cloud Storage](#ds-cloudstorage)
- [ITSM](#ds-itsm)
- [ChatOps Tools](#ds-slack)
![The Integrations page](/downloads/dspm/third-party-integrations/about-third-party-integrations/ds-integ-page.png)
- [][Add a cloud storage integration](/dspm/integrating-dspm-cloud-storage-services).
- View the list of cloud storage integrations. For each integration, you can see:
- **Cloud Storage**: The name of the cloud storage service (Amazon S3 Bucket or Azure Blob Storage).
- **Integration Name**: The integration name.
- **Log Type**: The type of data log that is sent to the storage service.
- **Last Sent**: The date and time when the data was last sent to the storage service.
- **Status**: The outcome (Success, Failed, Paused, or Pending) of the previous data transfer. For failed status, hover over the label to see the reason for failure.
-
**Data Transfer**: The state (Enabled or Disabled) of data transfer.
By default, the data transfer is enabled. If you want to pause the transfer without deleting the integration, click the toggle to disable the data transfer. If any data transfer is in progress, the activity is completed and then the data transfer is disabled.
- Sort the column data.
- Enable or disable the data transfer.
- Edit a cloud storage integration.
- Delete a cloud storage integration.
![View the cloud storage integrations](/downloads/dspm/third-party-integrations/about-third-party-integrations/ds-cs-tab.png)
- [][Add an ITSM integration](/dspm/integrating-dspm-itsm-tools).
- View the list of ITSM integrations. For each ITSM integration, you can see:
- **IT Service**: The name of the service (Jira or ServiceNow).
- **Integration Name**: The integration name.
- **Hostname**: The host name for the service.
- **Log Type**: The type of data log that is sent to the IT service.
- **Last Sent**: The date and time when the data was last sent to the IT service.
- **Status**: The outcome (Success, Failed, Paused, or Pending) of the previous data transfer. For failed status, hover over the label to see the reason for failure.
- **Data Transfer**: The state (Enabled or Disabled) of data transfer.
- Sort the column data.
- Enable or disable the data transfer.
- Edit an ITSM integration.
- Delete an ITSM integration.
![View the ITSM integrations](/downloads/dspm/third-party-integrations/about-third-party-integrations/ds-itsm-tab.png)
- [][Add a Slack integration](/dspm/integrating-slack).
- View the list of Slack integrations. For each integration, you can see:
- **Service**: The name of the service (Slack).
- **Integration Name**: The integration name.
- **Channels**: The number of channels that are added for sending notifications.
- **Last Sent**: The date and time when the data was last sent to the Slack channels.
- **Status**: The outcome (Success, Failed, Paused, or Pending) of the previous data transfer. For failed status, hover over the label to see the reason for failure.
- **Data Transfer**: The state (Enabled or Disabled) of data transfer.
- Sort the column data.
- Enable or disable the data transfer.
- Edit a Slack integration.
- Delete a Slack integration.
![View the ChatOps integrations](/downloads/dspm/third-party-integrations/about-third-party-integrations/ds-chatops-tab.png)