# ServiceNow Webhook Configuration Guide for Developers
Source: https://help.zscaler.com/zdx/servicenow-webhook-configuration-guide-developers
PDF: https://help.zscaler.com/pdf/com/en/1367296.pdf

This guide provides information on configuring webhooks using ServiceNow for alerts in ZDX. This article provides a sample configuration that you can build upon per user requirements. The ServiceNow webhook sample configuration here uses a ServiceNow developer configuration.
Creating a ServiceNow Developer Account
You must create a ServiceNow Developer Account to configure instances where you can enter Scripted REST APIs.
- Create a ServiceNow developer account at [https://developer.servicenow.com/](https://developer.servicenow.com/).
-
Create a developer instance.
[See image.](#SNowImage)
This instance automatically hibernates, so you should wake it every 24 hours. Also, if you don’t use it for 10 days, it is reclaimed.
- In the **Filter Navigator **search bar on the left-side navigation menu, enter `rest`.
- Go to **Scripted Web Services** > **Scripted REST APIs**.
-
Click **New **to create a new resource.
[See image.](#CreateNew)
- Enter the API name and click **Submit**.
- Search by the API name for the newly created Scripted REST API to access its resource page.
-
[]On the bottom tabs of the same page, under **Resources**, select **New**.
[See image.](#SelectNew)
-
On the **Scripted Rest Resource** page, create an authentication based on your needs.
[See image.](#img_servicenow_resourcepage)
- [Basic](#BasicAuthentication)
- [Token](#TokenAuthentication)
- [OAuth](#OAuth)
If you are using OAuth for authentication, you must create an OAuth 2.0 API endpoint in ServiceNow. To learn more, see [ServiceNow Webhook Configuration Guide](/zdx/servicenow-webhook-configuration-guide).
Creating a Webhook in the ZDX Admin Portal
To create a webhook in the ZDX Admin Portal:
-
Go to **Administration** > **Integrations** > **Webhooks** > **Add New Webhook**.
- In the **Add New Webhook** window:
- **Name**: Enter a name for the webhook.
- **Status**: Select **Enabled** to enable the webhook.
-
**URL**: Enter the ServiceNow developer instance hostname and concatenate it with the API name from the Scripted REST service page.
For example: `https://dev91028.service-now.com/api/516508/alertsincident`
-
**Authentication Type**: Select **Basic**, **Token**, or **OAuth** based on your authentication from the previous step.
- For **Basic**, enter the credentials from when the user was created.
- For **Token**, enter the same token as you are using in your script.
- For **OAuth**, enter the required fields from your OAuth 2.0 API endpoint that you created in ServiceNow.
To learn more, see [ServiceNow Webhook Configuration Guide.](/zdx/servicenow-webhook-configuration-guide)
- Click **Test Webhook** to verify that it functions correctly.
- To view the webhook notification on ServiceNow:
- In the **Filter Navigator** search bar in the left-side navigation menu, enter `incidents`.
-
Go to **Service Desk** > **Incidents**.
You see a list of incidents, and you can double-click any to view individual incident details.
The webhook output is also viewable here for integration with other third-party providers.
[See image.](#Webhookoutput)
-
Click **Save** in the **Add New Webhook** window and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[See image.](#WebhookURL)
Now, when your alert triggers and sends a webhook notification, an entry is created in the ServiceNow Incident list.
[]
To use basic authentication for your webhook, you must create a non-admin user on ServiceNow so that admin credentials are shared.
- **Name**: Enter your preferred name.
- **HTTP method**: Select **POST**.
- Select the **Active** checkbox.
- Copy and paste the following script into the Script box.
- [Script for Basic authentication](#Basicscript)
- On the **Security** tab, select the following checkboxes:
- **Requires authentication**
- **Requires ACL authorization**
-
Click **Submit**.
[See image.](#BasicAuth)
- In the **Filter Navigator** search bar in the left-side navigation menu, enter `users`.
- Go to **Users and Groups** > **Users** > **New**.
- Enter a User ID and password for this user.
-
Click **Submit**.
[See image.](#NonAdminUser)
[]
- **Name**: Enter your preferred name.
- **HTTP method**: Select **POST**.
- Deselect the **Requires authentication** checkbox.
-
Copy and paste the following script into the **Script** box.
Remember to edit the token in your script (`12345679` in the following script) to the one your webhook in ZDX is using.
- [Script for Token authentication](#Tokenscript)
- Click **Submit**.
Your resource populates on the **Scripted REST Service** page.
[]
After creating the OAuth 2.0 API endpoint in ServiceNow, enter the following on the **Scripted Rest Resource** page:
- **Name**: Enter your preferred name.
- **HTTP method**: Select **POST**.
- Deselect the **Requires authentication** checkbox.
-
Copy and paste the following script into the **Script** box.
Since the token is not applicable, you can leave it as `12345679`.
- [Script for Oauth authentication](#Oauthscript)
- Click **Submit**.
Your resource populates on the **Scripted REST Service** page.
[]
(function process(/*RESTAPIRequest*/ request, /*RESTAPIResponse*/ response) {
var reqData = request.body.dataString;
var jData = new global.JSON().decode(reqData);
var alertId = jData.alertId;
var ruleName = jData.ruleName;
if ( ruleName.equalsIgnoreCase("test") ) {
// test webhook
return;
}
var status = jData.status;
var zdxurl = jData.zdxUrl;
var startTime = jData.startTime;
var endTime = jData.endTime;
var state;
if ( status == "STARTED")
state = 2; // in progress
else if ( status == "ENDED_ON_RULE_DEL" || status == "ENDED_ON_RULE_MODIFY")
state = 8; // cancelled
else
state = 6; // resolved
var impact = 1;
if ( jData.severity == "High" )
impact = 1;
else if ( jData.severity == "Medium" )
impact = 2;
else if ( jData.severity == "Low" )
impact = 3;
var gdt = new GlideDateTime();
var gr = new GlideRecord('incident');
gr.addQuery('short_description', 'CONTAINS 1', alertId);
gr.query();
if ( jData.alertType == "Incident") {
impacted = jData.geolocationCount + " Geolocations\n" + jData.impactedDeviceCount + " Devices\n" + jData.impactedUserCount + " Users\n";
context = jData.context;
epicenter = context;
} else if ( jData.alertType == "ZProbe") {
impacted = "Zscaler Hosted Locations: " + jData.zscaler_hosted_locations + "\n";
} else {
impacted = jData.geolocationCount + " Geolocations\n" + jData.deptCount + " Departments\n" + jData.osverCount + " OS Versions\n" + jData.impactedDeviceCount + " Devices\n";
}
var criteria = jData.criteria;
var condOp = criteria.op;
var conditions = criteria.conditions;
var text = "";
for (i = 0; i < conditions.length; i++) {
if ( i != 0)
text += condOp + " ";
text += conditions[i].conditionString;
if ( conditions[i].isHit)
text += "*";
if (conditions[i].stats ) {
text += ", min: " + conditions[i].stats.min + ", max: "  + conditions[i].stats.max + ", avg: "  + conditions[i].stats.avg;
}
text += "\n";
}
var desc = "";
if ( jData.alertType == "Incident") {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered" + "\n\nEpicenter: " + epicenter.attribute + ", " + epicenter.epicenter;
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered" + "\n\nEpicenter: " + epicenter.attribute + ", " + epicenter.epicenter;
} else if ( jData.alertType == "ZProbe") {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered";
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered";
} else {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered";
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered";
}
var category = "ZDX Alerts";
if (gr.next()) {
gr.state = state;
gr.impact = impact;
if ( state == 6 ) {
gr.close_code = "Alert resolved";
} else if ( state == 8 ) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
var sd = gr.short_description;
if ( jData.alertType == "ZProbe") {
gr.short_description = "ZDX Alert " + alertId + " " + jData.zscaler_hosted_locations + " impacted";
} else {
gr.short_description = "ZDX Alert " + alertId + " " + jData.impactedDeviceCount + " devices impacted";
}
gr.description = desc;
gr.u_linked_incident = zdxurl;
gr.u_alert_details = reqData;
gdt.setValue(startTime*1000);
gr.work_start = gdt.getDisplayValue();
if ( status == "STARTED") {
gr.work_end = "";
} else {
gdt.setValue(endTime*1000);
gr.work_end = gdt.getDisplayValue();
}
//gr.caller_id = e9f176e2db54101087f7478239961941;
gr.update();
}
else {
gr.newRecord();
if ( state == 2 ) // in progress
state = 1; // new
gr.state = state;
gr.impact = impact;
gr.category = category;
if ( state == 6 ) {
gr.close_code = "Alert resolved";
} else if ( state == 8 ) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
if ( jData.alertType == "ZProbe") {
gr.short_description = "ZDX Alert " + alertId + " " + jData.zscaler_hosted_locations + " impacted";
} else {
gr.short_description = "ZDX Alert " + alertId + " " + jData.impactedDeviceCount + " devices impacted";
}
gr.description = desc;
gr.u_linked_incident = zdxurl;
gr.u_alert_details = reqData;
gdt.setValue(startTime*1000);
gr.work_start = gdt.getDisplayValue();
if ( status == "STARTED") {
gr.work_end = "";
} else {
gdt.setValue(endTime*1000);
gr.work_end = gdt.getDisplayValue();
}
//gr.caller_id = e9f176e2db54101087f7478239961941;
var result = gr.insert();
}
})(request, response);
[]
(function process(/*RESTAPIRequest*/ request, /*RESTAPIResponse*/ response) {
var headers = request.headers;
var authHeader = request.getHeader('authorization');
var token = authHeader.split(" ");
if (token[1] != "12345679")
response.setError(new sn_ws_err.BadRequestError('Bad token'));
var reqData = request.body.dataString;
var jData = new global.JSON().decode(reqData);
var alertId = jData.alertId;
var ruleName = jData.ruleName;
if ( ruleName.equalsIgnoreCase("test") ) {
// test webhook
return;
}
var status = jData.status;
var zdxurl = jData.zdxUrl;
var startTime = jData.startTime;
var endTime = jData.endTime;
var state;
if ( status == "STARTED")
state = 2; // in progress
else if ( status == "ENDED_ON_RULE_DEL" || status == "ENDED_ON_RULE_MODIFY")
state = 8; // cancelled
else
state = 6; // resolved
var impact = 1;
if ( jData.severity == "High" )
impact = 1;
else if ( jData.severity == "Medium" )
impact = 2;
else if ( jData.severity == "Low" )
impact = 3;
var gdt = new GlideDateTime();
var gr = new GlideRecord('incident');
gr.addQuery('short_description', 'CONTAINS 1', alertId);
gr.query();
if ( jData.alertType == "Incident") {
impacted = jData.geolocationCount + " Geolocations\n" + jData.impactedDeviceCount + " Devices\n" + jData.impactedUserCount + " Users\n";
context = jData.context;
epicenter = context;
} else if ( jData.alertType == "ZProbe") {
impacted = "Zscaler Hosted Locations: " + jData.zscaler_hosted_locations + "\n";
} else {
impacted = jData.geolocationCount + " Geolocations\n" + jData.deptCount + " Departments\n" + jData.osverCount + " OS Versions\n" + jData.impactedDeviceCount + " Devices\n";
}
var criteria = jData.criteria;
var condOp = criteria.op;
var conditions = criteria.conditions;
var text = "";
for (i = 0; i < conditions.length; i++) {
if ( i != 0)
text += condOp + " ";
text += conditions[i].conditionString;
if ( conditions[i].isHit)
text += "*";
if (conditions[i].stats ) {
text += ", min: " + conditions[i].stats.min + ", max: "  + conditions[i].stats.max + ", avg: "  + conditions[i].stats.avg;
}
text += "\n";
}
var desc = "";
if ( jData.alertType == "Incident") {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered" + "\n\nEpicenter: " + epicenter.attribute + ", " + epicenter.epicenter;
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered" + "\n\nEpicenter: " + epicenter.attribute + ", " + epicenter.epicenter;
} else if ( jData.alertType == "ZProbe") {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered";
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered";
} else {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered";
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered";
}
var category = "ZDX Alerts";
if (gr.next()) {
gr.state = state;
gr.impact = impact;
if ( state == 6 ) {
gr.close_code = "Alert resolved";
} else if ( state == 8 ) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
var sd = gr.short_description;
if ( jData.alertType == "ZProbe") {
gr.short_description = "ZDX Alert " + alertId + " " + jData.zscaler_hosted_locations + " impacted";
} else {
gr.short_description = "ZDX Alert " + alertId + " " + jData.impactedDeviceCount + " devices impacted";
}
gr.description = desc;
gr.u_linked_incident = zdxurl;
gr.u_alert_details = reqData;
gdt.setValue(startTime*1000);
gr.work_start = gdt.getDisplayValue();
if ( status == "STARTED") {
gr.work_end = "";
} else {
gdt.setValue(endTime*1000);
gr.work_end = gdt.getDisplayValue();
}
gr.update();
}
else {
gr.newRecord();
if ( state == 2 ) // in progress
state = 1; // new
gr.state = state;
gr.impact = impact;
gr.category = category;
if ( state == 6 ) {
gr.close_code = "Alert resolved";
} else if ( state == 8 ) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
if ( jData.alertType == "ZProbe") {
gr.short_description = "ZDX Alert " + alertId + " " + jData.zscaler_hosted_locations + " impacted";
} else {
gr.short_description = "ZDX Alert " + alertId + " " + jData.impactedDeviceCount + " devices impacted";
}
gr.description = desc;
gr.u_linked_incident = zdxurl;
gr.u_alert_details = reqData;
gdt.setValue(startTime*1000);
gr.work_start = gdt.getDisplayValue();
if ( status == "STARTED") {
gr.work_end = "";
} else {
gdt.setValue(endTime*1000);
gr.work_end = gdt.getDisplayValue();
}
var result = gr.insert();
}
})(request, response);
[]
(function process(/*RESTAPIRequest*/ request, /*RESTAPIResponse*/ response) {
var headers = request.headers;
var authHeader = request.getHeader('authorization');
var token = authHeader.split(" ");
if (token[1] != "12345679")
response.setError(new sn_ws_err.BadRequestError('Bad token'));
var reqData = request.body.dataString;
var jData = new global.JSON().decode(reqData);
var alertId = jData.alertId;
var ruleName = jData.ruleName;
if ( ruleName.equalsIgnoreCase("test") ) {
// test webhook
return;
}
var status = jData.status;
var zdxurl = jData.zdxUrl;
var startTime = jData.startTime;
var endTime = jData.endTime;
var state;
if ( status == "STARTED")
state = 2; // in progress
else if ( status == "ENDED_ON_RULE_DEL" || status == "ENDED_ON_RULE_MODIFY")
state = 8; // cancelled
else
state = 6; // resolved
var impact = 1;
if ( jData.severity == "High" )
impact = 1;
else if ( jData.severity == "Medium" )
impact = 2;
else if ( jData.severity == "Low" )
impact = 3;
var gdt = new GlideDateTime();
var gr = new GlideRecord('incident');
gr.addQuery('short_description', 'CONTAINS 1', alertId);
gr.query();
if ( jData.alertType == "Incident") {
impacted = jData.geolocationCount + " Geolocations\n" + jData.impactedDeviceCount + " Devices\n" + jData.impactedUserCount + " Users\n";
context = jData.context;
epicenter = context;
} else if ( jData.alertType == "ZProbe") {
impacted = "Zscaler Hosted Locations: " + jData.zscaler_hosted_locations + "\n";
} else {
impacted = jData.geolocationCount + " Geolocations\n" + jData.deptCount + " Departments\n" + jData.osverCount + " OS Versions\n" + jData.impactedDeviceCount + " Devices\n";
}
var criteria = jData.criteria;
var condOp = criteria.op;
var conditions = criteria.conditions;
var text = "";
for (i = 0; i < conditions.length; i++) {
if ( i != 0)
text += condOp + " ";
text += conditions[i].conditionString;
if ( conditions[i].isHit)
text += "*";
if (conditions[i].stats ) {
text += ", min: " + conditions[i].stats.min + ", max: "  + conditions[i].stats.max + ", avg: "  + conditions[i].stats.avg;
}
text += "\n";
}
var desc = "";
if ( jData.alertType == "Incident") {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered" + "\n\nEpicenter: " + epicenter.attribute + ", " + epicenter.epicenter;
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered" + "\n\nEpicenter: " + epicenter.attribute + ", " + epicenter.epicenter;
} else if ( jData.alertType == "ZProbe") {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered";
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered";
} else {
if ( status == "STARTED" )
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\nImpacted: \n\n" + impacted + "\n\n * - Condition triggered";
else
desc = "Rule Name: " + ruleName + "\n\nAlert criteria triggers: \n\n" + text + "\n\n * - Condition triggered";
}
var category = "ZDX Alerts";
if (gr.next()) {
gr.state = state;
gr.impact = impact;
if ( state == 6 ) {
gr.close_code = "Alert resolved";
} else if ( state == 8 ) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
var sd = gr.short_description;
if ( jData.alertType == "ZProbe") {
gr.short_description = "ZDX Alert " + alertId + " " + jData.zscaler_hosted_locations + " impacted";
} else {
gr.short_description = "ZDX Alert " + alertId + " " + jData.impactedDeviceCount + " devices impacted";
}
gr.description = desc;
gr.u_linked_incident = zdxurl;
gr.u_alert_details = reqData;
gdt.setValue(startTime*1000);
gr.work_start = gdt.getDisplayValue();
if ( status == "STARTED") {
gr.work_end = "";
} else {
gdt.setValue(endTime*1000);
gr.work_end = gdt.getDisplayValue();
}
gr.update();
}
else {
gr.newRecord();
if ( state == 2 ) // in progress
state = 1; // new
gr.state = state;
gr.impact = impact;
gr.category = category;
if ( state == 6 ) {
gr.close_code = "Alert resolved";
} else if ( state == 8 ) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
if ( jData.alertType == "ZProbe") {
gr.short_description = "ZDX Alert " + alertId + " " + jData.zscaler_hosted_locations + " impacted";
} else {
gr.short_description = "ZDX Alert " + alertId + " " + jData.impactedDeviceCount + " devices impacted";
}
gr.description = desc;
gr.u_linked_incident = zdxurl;
gr.u_alert_details = reqData;
gdt.setValue(startTime*1000);
gr.work_start = gdt.getDisplayValue();
if ( status == "STARTED") {
gr.work_end = "";
} else {
gdt.setValue(endTime*1000);
gr.work_end = gdt.getDisplayValue();
}
var result = gr.insert();
}
})(request, response);
[][![ServiceNow Developer Instance](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_SNow_instance.png)
]
[][![Create a new ServiceNow API](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_SNow_CreateNew.png)
]
[][![Select to fill in the API name ](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_Snow_SelectNew.png)
]
[][![Basic Authentication in ServiceNow](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_Snow_Basic.png?1615525745)
]
[][![Create a Non-Admin User ](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-servicenow/ZDX_SNow_NonAdminUSer.png)
]
[][![Adding the webhook URL ](/downloads/zdx/alerts/configuring-webhooks/ZDX-ConfiguringWebhook-Add-Window.png)
]
[][![Webhook JSON Format ](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_Webhook_output.png)
]
[]
![Scripted API Resource Page](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ServiceNow-Developer-ScriptedRESTResourcePage.png)