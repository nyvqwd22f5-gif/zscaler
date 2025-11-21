# PagerDuty Webhook Configuration Guide
Source: https://help.zscaler.com/zdx/pagerduty-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1376326.pdf

This guide provides information on using PagerDuty for configuring webhooks for alerts in ZDX. These instructions provide a sample configuration that you can use based on user requirements.
- Create a PagerDuty account at `www.pagerduty.com`.
- On your PagerDuty account page:
-
Click **Developer Mode**.
[See image.](#PagerdutyDevMode)
-
Click **Create New App**.
[See image.](#CreateNew)
-
On the **Build App** window:
- **AppName**: Enter a name for the application.
- **Description**: Enter a description.
- **Category**: Select **Error Tracking**.
- **We would like to help you publish a public app for all PagerDuty users. Do you intend to publish the app for all PagerDuty users and the app ecosystem?**: Select **No, I am not interested**.
Click **Save**.
[See image.](#BuildApp)
-
When the **Configure App** page appears, go to **Events Integration** > **Manage**.
[See image.](#ManageEvent)
-
Select **Yes** for **Event Integration** and enter the event transformation script.
[See image.](#TransformEvent)
- [Script for Event Transformation](#BasicScript)
-
[]**Copy** the Events API Endpoint address as the URL to use when configuring a webhook in the ZDX Admin Portal.
[See image.](#EventIntegration)
- Click **Save**.
- [Configure a webhook in the ZDX Admin Portal.](/zdx/configuring-webhooks)
-
Go to **Administration** > **Integrations** > **Webhooks** > **Add New Webhook**.
- In the **Add New Webhook** window:
- **Name**: Enter the name of the webhook for PagerDuty.
- **Status**: Select **Enabled**.
- **URL**: Enter the URL you copied from the previous step.
- **Authentication Type**: Select **Token**.
- **Bearer Token**: PagerDuty does not generate a bearer token. To meet webhook configuration requirements, enter any text for the bearer token (e.g., `1234`).
- (Optional) Click **Test Webhook** to confirm the webhook configuration works.
-
Verify the incident within PagerDuty if an alert is raised from the Test Webhook.
[See image.](#ZDXAlert_PagerDuty)
- Click **Save** in the **Add New Webhook** window.
[]
[![Access Developer Mode for Pager Duty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/pageduty1.png)
]
[]
[![Create Application in PagerDuty](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_Pagerduty_createnew.png)
]
[]
[![Manage Events in PagerDuty](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_ManageEvents.png)
]
[]
[![Build an App in PagerDuty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_BuildanApp.png)
]
[]
[![Event Transformation Script for PagerDuty](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_ScriptforPagerDuty.png)
]
[]
[![Events Integration in PagerDuty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_EventsInteg_PagerDuty.png)
]
[]
[![ZDX Alerts in PagerDuty ](/downloads/zdx/alerts/webhook-configuration-guide-pagerduty/ZDX_Alert_PagerDuty.png)
]
[]
export function transform(PD) {
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