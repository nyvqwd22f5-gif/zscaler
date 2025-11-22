# ServiceNow Webhook Configuration Guide
Source: https://help.zscaler.com/risk360/servicenow-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1483281.pdf

This guide provides information on configuring webhooks using ServiceNow for alerts in Risk360. This article provides a sample configuration that can be built on per user requirements. The following ServiceNow webhook sample configuration uses a ServiceNow developer configuration.
To configure webhook using ServiceNow:
- Create a ServiceNow developer account at [https://developer.servicenow.com/](https://developer.servicenow.com/).
-
Create a developer instance.
[See image.](#servicenow-admin-page)
This instance automatically hibernates, so you must wake it every 24 hours. Also, the instance is reclaimed if you don’t use it for 10 days.
- In the **Filter Navigator **search window on the left sidebar, enter `rest`.
- Under **Scripted Web Services**, click **Scripted REST APIs**.
-
Click **New** at the top of the page to create a new resource.
[See image.](#create-new)
-
Enter the API name and click **Submit**.
The API appears on the page.
- Click the API name to open it.
-
At the bottom of the page, under the **Resources **tab, select **New**.
[See image.](#select-new)
- Based on the authentication type you want to configure the webhook, choose one of the following methods:
- [Basic Authentication](#basic-auth-flow)
- [Token authentication](#token-auth-flow)
- In the Risk360 Admin Portal, go to **Alerts** > **Webhooks** > **Add Webhooks**.
- Complete the following fields:
- **Name**: Enter the name of the webhook.
- **Status**: Select **Enabled** or **Disabled** for the webhook.
- **URL**: Enter the ServiceNow developer instance hostname concatenated with the API name from the Scripted REST APIs page in the ServiceNow instance (e.g., `https://dev91028.service-now.com/api/516508/alertsincident`).
- **Authentication Type**: Select the authentication type for the webhook from Basic or Token.
- [Basic](#Basic)
- [Token](#Bearer)
-
Click **Save**.
The webhook is successfully configured. Whenever an alert is triggered, a webhook notification is sent, thereby creating an entry in the ServiceNow Incident table.
To view the webhook notification:
- Go to the ServiceNow instance.
- Enter `incidents` in the **Filter Navigator **search box on the left side of the page.
-
Click **Incidents**.
The Incidents page appears, showing the list of incidents (alerts). Click an incident to view more details about the alert.
[![ServiceNow Developer Instance](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_SNow_instance.png)
][]
[![Create a new ServiceNow API](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_SNow_CreateNew.png)
][]
[![Select to fill in the API name ](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_Snow_SelectNew.png)
][]
- []Enter your preferred name and select **POST** as the http method.
- Check the authentication box.
-
Paste the following script in the Script field and click **Submit**.
- [Script for Basic authentication](#Basicscript)
[See image.](#paste-script)
To use basic authentication for your webhook, you must create a non-admin user on ServiceNow so that admin credentials need not be shared.
- Enter `Users` in the **Filter Navigator** search box on the left side of the page.
- Select **Users** under **Users and Groups**.
- Click **New** on the top bar to open a new user page.
-
Enter the username and password for this user.
[See image.](#non-admin-user)
[]
- Enter your preferred name and select **POST** as the http method.
- Disable the authentication box.
- Paste the script under **Token Authentication** in the Script field and click **Submit**.
- [Script for Token authentication](#Tokenscript)
-
Edit the token in your script to the one used for the webhook configuration in the [Risk360 Admin Portal](#token-step).
The resource is populated on the **Scripted REST Service** page.
[](function process( /*RESTAPIRequest*/ request, /*RESTAPIResponse*/ response) {
// implement resource here
var reqData = request.body.dataString;
var jData = new global.JSON().decode(reqData);
var alertId = jData.alertId;
var ruleName = jData.ruleName;
if (ruleName.equalsIgnoreCase("test")) {
// test webhook
return;
}
var alertstatus = jData.status;
var url = '[code]<a href="' + jData.url + '" target="_blank">View alert in Risk360</a>[/code]';
var startTime = jData.startTime;
var endTime = jData.endTime;
var state;
if (alertstatus == "STARTED" || alertstatus == "ONGOING")
state = 2; // in progress
else if (alertstatus == "ENDED_ON_RULE_DEL" || alertstatus == "ENDED_ON_RULE_MODIFY")
state = 8; // cancelled
else
state = 6; // resolved
var impact = 1;
if (jData.severity == "High" || jData.severity == "Critical")
impact = 1;
else if (jData.severity == "Medium")
impact = 2;
else if (jData.severity == "Low")
impact = 3;
var gdt = new GlideDateTime();
var criteria = jData.criteriaString;
//based on type of alert cause
var orgAlertCauses = [];
var categoryAlertCauses = [];
var factorgroupAlertCauses = [];
var factorAlertCauses = [];
// Manually iterate through the alert causes and categorize them
for (var i = 0; i < jData.alert_causes.length; i++) {
var cause = jData.alert_causes[i];
if (cause.type === "Org") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
orgAlertCauses.push({
id: cause.id,
status: status
});
} else if (cause.type === "Category") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
categoryAlertCauses.push({
id: cause.id,
status: status
});
} else if (cause.type === "FactorGroup") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
factorgroupAlertCauses.push({
id: cause.id,
status: status
});
} else if (cause.type === "Factor") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
factorAlertCauses.push({
id: cause.id,
status: status
});
}
}
// Initialize a string to hold the output
var output = "";
var numbering = 1;
// Build the output string dynamically for "Org" type
if (orgAlertCauses.length > 0) {
output += numbering + ". Organization Level Change\n";
for (var j = 0; j < orgAlertCauses.length; j++) {
output += "\t. " + orgAlertCauses[j].id + " (" + orgAlertCauses[j].status + ")\n";
}
numbering++;
}
// Build the output string dynamically for "Category" type
if (categoryAlertCauses.length > 0) {
output += "\n" + numbering + ". Category Level Change\n";
for (var k = 0; k < categoryAlertCauses.length; k++) {
output += "\t. " + categoryAlertCauses[k].id + " (" + categoryAlertCauses[k].status + ")\n";
}
numbering++;
}
if (factorgroupAlertCauses.length > 0) {
output += "\n" + numbering + ". Factor Group Level Change\n";
for (var l = 0; l < factorgroupAlertCauses.length; l++) {
output += "\t. " + factorgroupAlertCauses[l].id + " (" + factorgroupAlertCauses[l].status + ")\n";
}
numbering++;
}
if (factorAlertCauses.length > 0) {
output += "\n" + numbering + ". Factor Level Change\n";
for (var m = 0; m < factorAlertCauses.length; m++) {
output += "\t. " + factorAlertCauses[m].id + " (" + factorAlertCauses[m].status + ")\n";
}
}
if (jData.custom_msg == undefined || jData.custom_msg === null) {
jData.custom_msg = "";
}
var desc = "";
desc = "Rule Name: " + ruleName + "\n\nCriteria: \n" + criteria + "\n\nAlert Cause:\n" + output + "\nCustom Message:\n" + jData.custom_msg;
var gr = new GlideRecord('incident');
gr.addQuery('short_description', 'CONTAINS', alertId);
gr.query();
if (gr.next()) {
gr.state = state;
gr.impact = impact;
if (state == 6) {
gr.close_code = "Alert resolved";
} else if (state == 8) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
var sd = gr.short_description;
gr.short_description = "Risk360 Alert " + alertId;
gr.description = desc;
gr.work_notes = url;
gdt.setValue(startTime * 1000);
gr.work_start = gdt.getDisplayValue();
if (alertstatus == "STARTED" || alertstatus == "ONGOING") {
gr.work_end = "";
} else {
gdt.setValue(endTime * 1000);
gr.work_end = gdt.getDisplayValue();
}
//gr.caller_id = e9f176e2db54101087f7478239961941;
gr.update();
} else {
gr.newRecord();
if (state == 2) // in progress
state = 1; // new
gr.state = state;
gr.impact = impact;
if (state == 6) {
gr.close_code = "Alert resolved";
} else if (state == 8) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
gr.short_description = "Risk360 Alert " + alertId;
gr.description = desc;
gr.work_notes = url;
gdt.setValue(startTime * 1000);
gr.work_start = gdt.getDisplayValue();
if (alertstatus == "STARTED" || alertstatus == "ONGOING") {
gr.work_end = "";
} else {
gdt.setValue(endTime * 1000);
gr.work_end = gdt.getDisplayValue();
}
//gr.caller_id = e9f176e2db54101087f7478239961941;
var result = gr.insert();
}
})(request, response);
[](function process(/*RESTAPIRequest*/ request, /*RESTAPIResponse*/ response) {
// implement resource here
var headers = request.headers;
var authHeader = request.getHeader('authorization');
var token = authHeader.split(" ");
if (token[1] != gs.getProperty("risk.360.token"))
response.setError(new sn_ws_err.BadRequestError('Bad token'));
var reqData = request.body.dataString;
var jData = new global.JSON().decode(reqData);
var alertId = jData.alertId;
var ruleName = jData.ruleName;
if (ruleName.equalsIgnoreCase("test")) {
// test webhook
return;
}
var alertstatus = jData.status;
var url = '[code]<a href="' + jData.url + '" target="_blank">View alert in Risk360</a>[/code]';
var startTime = jData.startTime;
var endTime = jData.endTime;
var state;
if (alertstatus == "STARTED" || alertstatus == "ONGOING")
state = 2; // in progress
else if (alertstatus == "ENDED_ON_RULE_DEL" || alertstatus == "ENDED_ON_RULE_MODIFY")
state = 8; // cancelled
else
state = 6; // resolved
var impact = 1;
if (jData.severity == "High" || jData.severity == "Critical")
impact = 1;
else if (jData.severity == "Medium")
impact = 2;
else if (jData.severity == "Low")
impact = 3;
var gdt = new GlideDateTime();
var criteria = jData.criteriaString;
//based on type of alert cause
var orgAlertCauses = [];
var categoryAlertCauses = [];
var factorgroupAlertCauses = [];
var factorAlertCauses = [];
// Manually iterate through the alert causes and categorize them
for (var i = 0; i < jData.alert_causes.length; i++) {
var cause = jData.alert_causes[i];
if (cause.type === "Org") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
orgAlertCauses.push({
id: cause.id,
status: status
});
} else if (cause.type === "Category") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
categoryAlertCauses.push({
id: cause.id,
status: status
});
} else if (cause.type === "FactorGroup") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
factorgroupAlertCauses.push({
id: cause.id,
status: status
});
} else if (cause.type === "Factor") {
var status;
if (cause.prev < 0)
prev = 0;
if (cause.cur > cause.prev) {
status = "Increase";
} else if (cause.cur < cause.prev) {
status = "Decrease";
} else {
status = "No Change";
}
factorAlertCauses.push({
id: cause.id,
status: status
});
}
}
// Initialize a string to hold the output
var output = "";
var numbering = 1;
// Build the output string dynamically for "Org" type
if (orgAlertCauses.length > 0) {
output += numbering + ". Organization Level Change\n";
for (var j = 0; j < orgAlertCauses.length; j++) {
output += "\t. " + orgAlertCauses[j].id + " (" + orgAlertCauses[j].status + ")\n";
}
numbering++;
}
// Build the output string dynamically for "Category" type
if (categoryAlertCauses.length > 0) {
output += "\n" + numbering + ". Category Level Change\n";
for (var k = 0; k < categoryAlertCauses.length; k++) {
output += "\t. " + categoryAlertCauses[k].id + " (" + categoryAlertCauses[k].status + ")\n";
}
numbering++;
}
if (factorgroupAlertCauses.length > 0) {
output += "\n" + numbering + ". Factor Group Level Change\n";
for (var l = 0; l < factorgroupAlertCauses.length; l++) {
output += "\t. " + factorgroupAlertCauses[l].id + " (" + factorgroupAlertCauses[l].status + ")\n";
}
numbering++;
}
if (factorAlertCauses.length > 0) {
output += "\n" + numbering + ". Factor Level Change\n";
for (var m = 0; m < factorAlertCauses.length; m++) {
output += "\t. " + factorAlertCauses[m].id + " (" + factorAlertCauses[m].status + ")\n";
}
}
if (jData.custom_msg == undefined || jData.custom_msg === null) {
jData.custom_msg = "";
}
var desc = "";
desc = "Rule Name: " + ruleName + "\n\nCriteria: \n" + criteria + "\n\nAlert Cause:\n" + output + "\nCustom Message:\n" + jData.custom_msg;
var gr = new GlideRecord('incident');
gr.addQuery('short_description', 'CONTAINS', alertId);
gr.query();
if (gr.next()) {
gr.state = state;
gr.impact = impact;
if (state == 6) {
gr.close_code = "Alert resolved";
} else if (state == 8) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
var sd = gr.short_description;
gr.short_description = "Risk360 Alert " + alertId;
gr.description = desc;
gr.work_notes = url;
gdt.setValue(startTime * 1000);
gr.work_start = gdt.getDisplayValue();
if (alertstatus == "STARTED" || alertstatus == "ONGOING") {
gr.work_end = "";
} else {
gdt.setValue(endTime * 1000);
gr.work_end = gdt.getDisplayValue();
}
//gr.caller_id = e9f176e2db54101087f7478239961941;
gr.update();
} else {
gr.newRecord();
if (state == 2) // in progress
state = 1; // new
gr.state = state;
gr.impact = impact;
if (state == 6) {
gr.close_code = "Alert resolved";
} else if (state == 8) {
gr.close_code = "Rule deleted or modified";
}
gr.close_notes = " ";
gr.short_description = "Risk360 Alert " + alertId;
gr.description = desc;
gr.work_notes = url;
gdt.setValue(startTime * 1000);
gr.work_start = gdt.getDisplayValue();
if (alertstatus == "STARTED" || alertstatus == "ONGOING") {
gr.work_end = "";
} else {
gdt.setValue(endTime * 1000);
gr.work_end = gdt.getDisplayValue();
}
//gr.caller_id = e9f176e2db54101087f7478239961941;
var result = gr.insert();
}
})(request, response);
[![Basic Authentication in ServiceNow](/downloads/zdx/alerts/webhook-configuration-guide-servicenow/ZDX_Snow_Basic.png?1615525745)
][]
[![Create a Non-Admin User ](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-servicenow/ZDX_SNow_NonAdminUSer.png)
][]
[]
[]
Enter the **Username **and** Password** for the user in ServiceNow.
[]
[]Enter the same bearer token used in the script. A bearer token is a unique alphanumeric string used for authentication.