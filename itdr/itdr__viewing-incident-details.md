# Viewing Incident Details
Source: https://help.zscaler.com/itdr/viewing-incident-details
PDF: https://help.zscaler.com/pdf/com/en/1531877.pdf

Zscaler ITDR seamlessly integrates with ServiceNow to track and assess the posture and change issues in the Zscaler ITDR Admin Portal. The list of incidents created in the ITDR Admin Portal is available on the ServiceNow page.
You must [configure ServiceNow with ITDR](https://help.zscaler.com/itdr/v4_29/configuring-itdr-servicenow) to view the incidents.
The ServiceNow page displays the list of incidents including additional information, such as incident number, short description, the impact of the issue, urgency, status of the issue in both the ITDR Admin Portal and ServiceNow portal, etc. You can further investigate the incident and take the necessary action.
On the ServiceNow page (ITDR > ServiceNow), you can view the following:
- **Incident Number**: The incident ID in the ServiceNow portal. Click the number to go to the ServiceNow portal to open the incident.
- **Short Description**: A short description of the issue.
- **Impact**: The impact (**High**, **Medium**, or **Low**) of the issue in the ITDR Admin Portal. You can filter the column to view incidents of a specific impact.
- **Urgency**: The urgency (**High**, **Medium**, or **Low**) of the issue in the ServiceNow portal. You can filter the column to view incidents of a specific urgency.
- **Status**: The status (**Open **or **Resolved**) of the issue in the ITDR Admin Portal. You can filter the column to view incidents of a specific status.
- **Incident State**: The state (**New**, **In Progress**, **On Hold**, **Resolved**, **Closed**, or **Cancelled**) of the incident in the ServiceNow portal. You can filter the column to view incidents of a specific state.
- **Incident Type**: The incident type (**AD**, **Entra**, or **Credential Exposure**). You can filter the column to view incidents for a specific type.
- **Domain**: The domain on which the incident is created. You can filter the column to view incidents for a specific domain.
- **Issue Name**: The name of the issue.
- **Description**: The description of the issue.
- **Last Work Note**: The last note that was updated in the ServiceNow portal.
- **Created At**: The date and timestamp for when the incident was created.
- **Last Updated**: The date and timestamp for when the incident was last updated.
![The ServiceNow page with the list of incidents created in the ITDR Admin Portal.](/downloads/itdr/third-party-integrations/viewing-incident-details/itdr-ServiceNow-tab-incidentlist.jpg)