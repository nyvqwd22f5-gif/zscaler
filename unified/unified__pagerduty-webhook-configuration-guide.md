# PagerDuty Webhook Configuration Guide
Source: https://help.zscaler.com/unified/pagerduty-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1491951.pdf

This guide provides information on using PagerDuty for configuring webhooks for alerts in Digital Experience Monitoring. The instructions here provide a sample configuration that can be used to build on per user requirements.
- Create a PagerDuty account at [www.pagerduty.com](www.pagerduty.com).
- On your PagerDuty account page, click **Developer Mode**.
[See image.](#PagerdutyDevMode)
- Click **Create New App**.
[See image.](#CreateNew)
- The **Build App** page opens.
- On the **Build App** page, enter an **AppName** and **Description**. Choose the **Category** as **Error Tracking** and fill in other details.
[See image.](#BuildApp)
- Click **Save**.
- The **Configure App** page opens.
- Under **Events Integration**, click **Manage**.
[See image.](#ManageEvent)
- Choose **Yes** for **Event Integration** and enter the event transformation script.
[See image.](#TransformEvent)
- [Script for Event Transformation](#Basicscript)
- Copy the Events API Endpoint address as the URL to send webhooks to in the Admin Portal. No token is used, so you can select Token authentication on Digital Experience Monitoring and enter any string. Then, click **Save** on the **Pager Duty Events Integration** page.
[See image.](#EventIntegration)
- Once an alert is raised from Digital Experience Monitoring, an incident will be raised in PagerDuty.
[See image.](#ZDXAlert_PagerDuty)
[]![Access Developer Mode for Pager Duty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/pageduty1.png)
[]![Create Application in PagerDuty](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_Pagerduty_createnew.png)
[]![Manage Events in PagerDuty](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_ManageEvents.png)
[]![Build an App in PagerDuty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_BuildanApp.png)
[]![Event Transformation Script for PagerDuty](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_ScriptforPagerDuty.png)
[]![Events Integration in PagerDuty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_EventsInteg_PagerDuty.png)
[]![ZDX Alerts in PagerDuty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_Alert_PagerDuty.png)
[]export function transform(PD) {
// Sample Event Transformation
let body = PD.inputRequest.body;
let zdxLinkURL = body.zdxUrl;
let emitEv = true;
let ruleName = body.ruleName;
if (ruleName.toLowerCase() == "test")
emitEv = false;
let payloadCount = "\n\n";
if ( body.status == "STARTED" ) {
payloadCount += "Affected: \nGeolocations: " +
body.geolocationCount + "\nDepartments: " +
body.deptCount + "\nImpacted Devices: " +
body.impactedDeviceCount + "\nOS Versions: " +
body.osverCount
}
let normalized_event = {
event_action: PD.Trigger,
// optionally include a key to prevent creating duplicate
// incidents when the same event is sent more than once
// dedup_key: body.event_key,
payload: {
summary: `Rule: ${body.ruleName}, Severity: ${body.severity} ${body.status}`,
source: 'ZDX',
severity: PD.Critical,
custom_details: `AlertId: ${body.alertId}\nRule Name: ${body.ruleName}\nSeverity: ${body.severity}\nCriteria: ${body.criteriaString}\nLink: ${zdxLinkURL} ${payloadCount}`
},
dedup_key: "",
// optionally display links or images on web and mobile
links: [{
"href": zdxLinkURL,
"text": "Alert Details"
}],
};
if ( emitEv)
PD.emitEventsV2([normalized_event]);
}