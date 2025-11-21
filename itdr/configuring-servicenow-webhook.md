# Configuring a ServiceNow Webhook
Source: https://help.zscaler.com/itdr/configuring-servicenow-webhook
PDF: https://help.zscaler.com/pdf/com/en/1531878.pdf

A webhook facilitates the integration of Zscaler ITDR with ServiceNow. With this integration, tickets are automatically created in ServiceNow to track and assess posture and change issues. You can configure webhooks to track actions on these tickets when specific events occur, such as updating, deleting, etc.
This article provides information on creating a business rule in ServiceNow that triggers a webhook based on defined criteria, such as when a new ticket is created, or when the status of an existing ticket changes, etc.
To create a business rule:
-
Sign in to the ServiceNow portal and go to **System Definition** > **Business Rules**.
[See image.](#business-rule)
-
On the **Business Rules** page, click **New**.
[See image.](#new-business-rule)
-
On the **Business Rule New Record** page:
- **Name**: Enter a unique name.
- **Table**: Select **Incident [incident]** from the drop-down menu.
- Select the **Advanced** checkbox.
[See image.](#newrecord)
-
On the **When to Run** tab, select the conditions for which the business rule must run.
[See image.](#whnetoruntab)
-
Copy the following script. On the **Advanced **tab, paste the script in the **Script **field to invoke the REST message:
`(function executeRule(current, previous /*null when async*/ ) {
// Only trigger webhook if these incident properties are updated
if (current.short_description.changes() || current.description.changes() || current.work_notes.changes() || current.state.changes() || current.impact.changes() | current.urgency.changes()) {
// Create a RESTMessageV2 object
var restMessage = new sn_ws.RESTMessageV2();
// Set the endpoint URL
restMessage.setEndpoint('URL');
// Set the HTTP method to POST
restMessage.setHttpMethod('POST');
// Set the HTTP header for Content-Type to application/json
restMessage.setRequestHeader('Content-Type', 'application/json');
// Set the API key
restMessage.setRequestHeader('x-service-now-auth', 'API Key');
// Prepare the JSON payload
var jsonPayload = JSON.stringify({
incident_number: current.number.getValue(),
short_description: current.short_description.getValue(),
description: current.description.getValue(),
work_notes: current.work_notes.getValue(),
state: current.state.getValue(),
impact: current.impact.getValue(),
urgency: current.urgency.getValue(),
updated_by: current.sys_updated_by.getValue(),
updated_on: current.sys_updated_on.getValue(),
});
// Set the JSON payload as request body
restMessage.setRequestBody(jsonPayload);
// Execute REST call
var response = restMessage.execute();
var httpResponseStatus = response.getStatusCode();
var responseBody = response.getBody(); // Get the response body
var responseHeaders = response.getAllHeaders(); // Get the response headers
gs.info('Webhook triggered: HTTP Status ' + httpResponseStatus);
gs.info('Response Body: ' + responseBody);
}
})(current, previous);`
[See image.](#advanced-tab)
-
Update the endpoint URL and API key in lines 8 and 17 of the script:
- `restMessage.setEndpoint('URL');` - Copy and paste the **Webhook URL** from the [Configurations ](/itdr/about-configurations)page.
- `restMessage.setRequestHeader('x-service-now-auth', 'API KEY');` - Copy and paste the **Webhook API Key** from the [Configurations](/itdr/about-configurations) page.
[See image](#url-api-key-update)
- Click **Save**.
- Click **Submit**.
[]
![The list of options under System Definition with annotation around Business rules.](/downloads/itdr/third-party-integrations/configuring-servicenow-webhook/servicenow-business-rules.png)
[]
![The ServiceNow portal with Business rules page and annotations around New.](/downloads/itdr/third-party-integrations/configuring-servicenow-webhook/servicenow-create-new-business-rule.png)
![Image]()
[]![Business Rule New record page with the required fields updated.](/downloads/itdr/third-party-integrations/configuring-servicenow-webhook/servicenow-new-record.png)
[]![The When to run tab with annotation around the filter conditions.](/downloads/itdr/third-party-integrations/configuring-servicenow-webhook/servicenow-when-to-run-tab.png)
[]![The Advanced tab with the script and endpoint URL and API key blurred.](/downloads/itdr/third-party-integrations/configuring-servicenow-webhook/advanced-tab-script.png)
[]
![The Advanced tab with the script and endpoint URL, API key blurred.](/downloads/itdr/third-party-integrations/configuring-servicenow-webhook/script-update.png)