# Configuring the ServiceNow Outegration Webhook
Source: https://help.zscaler.com/uvm/configuring-servicenow-outegration-webhook
PDF: https://help.zscaler.com/pdf/com/en/1528051.pdf

The ServiceNow outegration webhook enables automatic syncing of ServiceNow ticket updates such as Status or SLA changes to their corresponding SecOps tickets, reducing the need for manual changes. This step is required when configuring the ServiceNow to SecOps ticket mapping to keep the tickets in the two systems in sync. To learn more, see [Configuring the ServiceNow Outegration](/uvm/configuring-servicenow-outegration).
[See image.](#snow-ticket-step)
Prerequisite
To set up the ServiceNow webhook, you need Zscaler API token credentials (i.e., Client ID and Client Secret) and your account ID. To obtain these, submit a support ticket in the SecOps platform requesting the necessary credentials.
Configuring the ServiceNow Webhook
To set up your ServiceNow webhook:
-
In the ServiceNow console, go to **Activity Subscription **>** Business Rules**.
[See image.](#snow-business-rules)
-
Click **New**.
The **Business Rule** page appears.
- On the **Business Rule** page:
- **Name**: Enter a name** **for the business rule.
- **Table**: From the drop-down menu, select one of the following ServiceNow tables to trigger the platform on update:
- For the **Incidents** table, select **Incident [incident]**.
- For the **Requests** table, select **Requested Item [sc_req_item]**.
- For the **Exceptions** table, select **Policy Exception [sn_compliance_policy_exception]**.
- For any other table, select the relevant table name based on your use case.
-
Select the **Advanced** checkbox.
[See image.](#name-table-advanced)
-
On the **When to run **tab:
- From the **When** drop-down menu, select **after**.
- Select the **Update** and **Delete** checkboxes.
[See image.](#when-to-run-tab)
-
On the **Advanced **tab, copy and paste the following script:
- [See script.](#snow-webhook-script)
Make the following changes to the script:
- In the `getAvalorJWT()` function, replace the `<Client ID>`** **and** **`<Client Secret>` variables that appear in red.
-
In the `sendWebhookRequest()` function, replace the `<Account ID>` variable that appears in red.
You can find your Account ID in your platform URL, or contact Zscaler Support for assistance.
- Click **Submit**.
After your webhook is set up, configured triggers for field updates in your ServiceNow outegration mapping automatically sync changes made to ServiceNow tickets with their corresponding SecOps tickets.
[]![09668695-899a-4463-93f3-fda0c6b5a3f1.png](/downloads/uvm/configure/outegrations/servicenow-outegration-webhook/09668695-899a-4463-93f3-fda0c6b5a3f1.png)
[]**![d464eb49-b175-45d4-accf-4db240e2f6d8.png](/downloads/uvm/configure/outegrations/servicenow-outegration-webhook/d464eb49-b175-45d4-accf-4db240e2f6d8.png)
**
[]**![d0aa2a75-cfc7-4619-969f-a48ee6972f7d.png](/downloads/uvm/configure/outegrations/servicenow-outegration-webhook/d0aa2a75-cfc7-4619-969f-a48ee6972f7d.png)
**
[]![a37664de-91a7-41b2-b6dd-6c52c1006f74.png](/downloads/uvm/configure/outegrations/servicenow-outegration-webhook/a37664de-91a7-41b2-b6dd-6c52c1006f74.png)
[]function getAvalorJWT(){
var url='https://auth.us01.app.avalor.io/oauth2/token';
var restMessage = new sn_ws.RESTMessageV2();
restMessage.setEndpoint(url);
restMessage.setHttpMethod('POST');
restMessage.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
restMessage.setRequestHeader('Accept', 'application/json');
var payload = "grant_type=client_credentials&client_id=`<Client ID>`&client_secret=`<Client Secret>`";
restMessage.setRequestBody(payload);
var response = restMessage.execute();
var responseBody = response.getBody();
var statusCode = response.getStatusCode();
if (statusCode !== 200) {
gs.error('Failed to get access. Status code: ' + statusCode + ', Response body: ' + responseBody);
}
var jsonResponse = JSON.parse(responseBody);
return jsonResponse.access_token;
}
function sendWebhookRequest(sysId, displayKey, changedFields, isDeleted) {
var jwt = getAvalorJWT();
var url = 'https://webhook.avalor.io/integration/inbound/`<Account ID>`/servicenow';
var restMessage = new sn_ws.RESTMessageV2();
var payload = {};
payload.sysId = sysId;
payload.displayKey = displayKey;
payload.changedFields = changedFields;
payload.isDeleted = isDeleted;
restMessage.setEndpoint(url);
restMessage.setHttpMethod('POST');
restMessage.setRequestHeader('Content-Type', 'application/json');
restMessage.setRequestHeader('Authorization', 'Bearer ' + jwt);
restMessage.setRequestBody(JSON.stringify(payload));
var response = restMessage.execute();
var responseBody = response.getBody();
var statusCode = response.getStatusCode();
if (statusCode !== 200) {
gs.error('Failed to send webhook request. Status code: ' + statusCode + ', Response body: ' + responseBody);
}
}
(function executeRule(current, previous /*null when async*/ ) {
if (current.operation() === 'delete') {
sendWebhookRequest(current.sys_id.getDisplayValue(), current.number.getDisplayValue(), {}, true);
}
if (current.operation() === 'update') {
var changedFields = {};
var fieldNames = current.getFields().toArray().map(function(field) {
return field.getName();
});
fieldNames.forEach(function(fieldName) {
if (current.getValue(fieldName) != previous.getValue(fieldName)) {
changedFields[fieldName] = current.getDisplayValue(fieldName);
}
});
sendWebhookRequest(current.getValue('sys_id'), current.getValue('number'), changedFields, false);
}
})(current, previous);