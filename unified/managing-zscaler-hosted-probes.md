# Managing Zscaler Hosted Probes
Source: https://help.zscaler.com/zdx/managing-zscaler-hosted-probes
PDF: https://help.zscaler.com/pdf/com/en/1506026.pdf

Hosted Monitoring operates from within the Zscaler cloud infrastructure as a multitenant service. The service allows you to logically group Web and Cloud Path probes into independent collections to create your own tests to monitor performance. To learn about configuring Zscaler Hosted Probes and the required prerequisites for monitoring, see [Configuring Zscaler Hosted Probes](/zdx/configuring-zscaler-hosted-probes).
Managing a Collection
To view and manage configured probes within a collection, go to **Configuration **> **Zscaler Hosted Probes **and select a probe collection from the list of collections.
The page provides the following details and actions for the selected collection:
- **Collection Name**: Click the **Edit **icon to change the collection name.
- **Status**: Displayed as either Enabled or Disabled. Click the blue toggle to change the Status.
- **Collection Removal**: Click the **Delete** link to remove the probe collection.
- **Total**:** **The total number of active probes that are within the collection.
- **Probes**:** **The number of active Web probes and Cloud Path probes within the collection.
- **Add Probe**: Add a probe to the selected collection.
- **Filters**:** **The options to monitor a specific probe type or status.
- **Search**: Find a specific probe within the collection. Search for any character string that might be part of the probe name.
![Zscaler Hosted Probes collection details](/downloads/tech-pubs-drafts/zdx-draft-articles/managing-zscaler-hosted-probes-draft-doc-47869-0/zdx-zprobe-collection-details4.png)
The following information and actions are provided within the table for the selected collection:
- **Type**: Identified with an icon as either a Web probe or Cloud Path probe.
- **Name**: The configured probes within the selected collection. Click any probe name to view its specific settings.
- **Host**: The URL of the hosted location.
- **Status**: The probe is currently either **Enabled** or **Disabled**. If the probe is **Enabled**, then it is an active probe.
- **Protocol/Methods**: The method for Web probes or the protocol for Cloud Path probes.
- **Locations**: The number of Zscaler hosted locations from where the probe is run.
- **Alert Rules**: The number of alert templates associated with the probe.
- **Frequency**: The time interval for how often the probe is run.
- **Actions**: The option to edit or delete the probe, or to add or edit alert rules.
![Table of probes within a collection](/downloads/tech-pubs-drafts/zdx-draft-articles/configuring-zscaler-hosted-probes-alerts-doc-47869/zdx-zprobe-collection-table2.png)
You can manage the number of active probes with the following actions:
- [Enabling or disabling a collection.](#collectionStatus)
- [Adding or deleting a collection.](#deleteCollection)
- [Edit the probe or companion probe.](#editProbeStatus)
- [Add or delete a probe.](#deleteProbe)
[]
You can enable a collection for active use or disable a collection if you want to use it later and to manage the amount of active Zscaler Hosted probes.
- Go to **Configuration **> **Zscaler Hosted Probes**.
-
Toggle the blue toggle of the collection to **Enabled** or **Disabled**.
![Disable the Enabled toggle](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/ZDX-zscaler-hosted-collection-enabled.png)
- A confirmation window appears briefly to confirm that the collection was enabled or disabled and its configuration was saved.
When disabling a collection, you disable all probes within the collection.
[]
You can [create a collection](/zdx/configuring-zscaler-hosted-probes) to organize your Zscaler Hosted probes or delete a collection if it is no longer of use to you.
To delete a collection:
- Go to **Configuration **> **Zscaler Hosted Probes**.
- Click the **Collection Removal** icon to begin collection deletion. The **Delete Collection** window appears.
-
Confirm the deletion of the collection by clicking **Delete**.
![Confirm the deletion of the collection](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/ZDX-zscaler-hosted-collection-delete.png)
If you delete a collection, then all probes and associated companion probes are deleted.
[][]
After you add a probe to a collection, you can enable or disable any probe within a collection by clicking the **Edit** icon. You manage the status if there are other probes within a collection that you want to remain active, but you are selecting one to disable.
In the Edit Probe window, you can toggle the **Status** of the probe or companion probe.
![Enable or disable the probe](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/ZDX-zscaler-hosted-collection-probestatus.png)
When you disable a probe, then the companion probe is also disabled.
You cannot enable a companion probe while the parent probe is disabled.
When you enable the parent probe, the companion probe is not enabled immediately as you must enable its status in the **Edit Probe - Companion Probe** configuration.
[]
You can [add a probe](/zdx/configuring-zscaler-hosted-probes) and enable it to become an active probe to provide you with telemetry data.
You can delete a probe and its companion probe if they are no longer of use to you.
To delete a probe, click on the **Delete** icon, then you can confirm its deletion in the **Delete Probe** window.
![Confirm probe deletion](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/ZDX-zscaler-hosted-probe-delete.png)
If you delete a probe with a companion probe, then the companion probe is also deleted.
You cannot selectively delete a companion probe, but [you can disable it](#disableProbe) so that it does not count towards your active probes.
Managing Alert Rules
You can add or edit templates for alert rules directly from the probe collection table. Alert templates can be useful when reusing settings for alert rules. To learn more about the templates, see [About Templates](/zdx/about-templates) and [Managing Templates](/zdx/managing-templates). To add alert templates as an option when configuring Zscaler Hosted Probes, see [Configuring Zscaler Hosted Probes](/zdx/configuring-zscaler-hosted-probes).
Adding Alert Rules
Create an alert template or add a predefined alert template from the collection table:
- [Creating a Template.](#create-new-template)
- [Adding a Predefined Template.](#add-existing-template)
[]To create and add a new template for an alert rule:
- Locate a probe within the table to add the alert rule.
- Click the probe's **Alert **icon located on the right side of the table.
-
Click **Add**, and then click **Create New Template**.
[See image.](#create-alert-template)
- Configure the template details and criteria in the **Add New Template** window and click **Save**. To learn more, see [Managing Templates](/zdx/managing-templates).
- Select your new template from the drop-down menu. The alert criteria appears.
-
Under **Define Alert Action**, confirm whether the alert should be muted or unmuted. If you disable **Muted**, select your alert delivery method from the drop-down menu. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[See image.](#add-new-alert-template)
- Click **Save**.
[]To add a template with predefined criteria for an alert rule:
- Locate a probe within the table to add the alert rule.
- Click the probe's **Alert **icon located on the right side of the table.
-
Click **Add**, and then select a predefined template from the drop-down menu. The alert criteria appears.
[See image.](#add-exist-predef-template)
-
Under **Define Alert Action**, confirm whether the alert should be muted or unmuted. If you disable **Muted**, select your alert delivery method from the drop-down menu. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[See image.](#add-existing-alert-template)
- Click **Save**.
Editing Alert Rules
To edit an existing template from the collection table:
- Click the probe's **Alert **icon located on the right side of the table.
- If the probe has more than one alert rule, locate the template and update the alert criteria. To learn more about configuring templates, see [Managing Templates](/zdx/managing-templates).
-
Under **Define Alert Action**, confirm whether the alert should be muted or unmuted. If you disable **Muted**, select your alert delivery method from the drop-down menu. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[See image.](#edit-existing-template)
- Click **Save**.
To learn more about monitoring the probes, see [Understanding Hosted Monitoring](/zdx/understanding-zscaler-hosted-monitoring).
[]![Create new alert template](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/zdx-zprobe-add-alert-template.png)
[]![Add new alert template](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/zdx-zprobe-add-new-template.png)
[]![Add existing alert template](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/zdx-zprobe-add-existing-template.png)
[]![Add existing predefined template](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/zdx-zprobe-add-predefined-existing-template.png)
[]![Edit existing template](/downloads/zdx/configuration/probes/managing-zscaler-hosted-probes/zdx-zprobe-edit-existing-template.png)