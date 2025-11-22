# Managing Templates
Source: https://help.zscaler.com/zdx/managing-templates
PDF: https://help.zscaler.com/pdf/com/en/1499921.pdf

[Watch a video about Templates in ZDX.](https://fast.wistia.net/embed/iframe/t4mafl179c)
On the Templates page, you can manage and configure templates by adding, editing, copying, or deleting a Zscaler Hosted probe. You can use the template to create an alert rule with prefilled criteria. To learn more, see [Configuring a Zscaler Hosted Probe](/zdx/configuring-zscaler-hosted-probes).
Prerequisites
Before you manage templates, ensure that:
- Your admin role supports Alerts and Configuration. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
- Your subscription level supports Hosted Monitoring. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
Managing Templates
To manage your templates (Alerts > Templates), you can perform the following actions:
- [Add a new template.](#Add)
- [Edit a template.](#Edit)
- [Copy a template.](#Copy)
- [Delete a template.](#Delete)
Predefined Templates
To start creating alert rules for Zscaler Hosted probes, there are a number of predefined templates ready for use.
You cannot delete or edit predefined templates.
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Predefined Template | Severity | Probe Type | Criteria |
| ------------------- | -------- | ---------- | -------- |
| Warning Availability | High | Web | **Availability** < 100%**Occurs** 2 **times in **60 **minutes****Across any **1 **Zscaler Hosted Locations** |
| Critical Page Fetch Time | High | Web | **Page Fetch Time** > 1000 ms**Occurs** 3 **times in **15 **minutes****Across any **2 **Zscaler Hosted Locations** |
| Warning Page Fetch Time | Medium | Web | **Page Fetch Time** > 1000 ms**Occurs** 3 **times in **15 **minutes****Across any **1 **Zscaler Hosted Locations** |
| Probe Failure | High | Web | **Availability** = 0%**Occurs** 3 **times in 15** **minutes****Across any **1 **Zscaler Hosted Locations** |
| Critical Latency | High | Cloud Path | **Latency **> 5 ms**Occurs** 3 **times in 15** **minutes****Across any **2 **Zscaler Hosted Locations** |
| Warning Latency | Medium | Cloud Path | **Latency **> 5 ms**Occurs** 3 **times in 15** **minutes****Across any **1 **Zscaler Hosted Locations** |
[]To add a new template:
- Click **New Template**.
-
In the** Add New Template** drawer, enter the required information:
- **Name**: Enter a name to identify the template.
- **Severity**: Select **High**, **Medium**, or **Low **for severity, depending on the impact of this event on users.
- **Probe Type**: Select **Cloud Path** or **Web** for the probe type.
- **Criteria**: Select your criteria for the template. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[See image.](#addNewTemplate)
- Click **Save**.
[]To edit a template:
- Click the **Edit** icon.
-
In the **Edit Template **drawer, you can edit:
- **Name**: Enter a name to identify the template.
- **Severity**: Select **High**, **Medium**, or **Low **for severity, depending on the impact of this event on users.
- **Probe Type**: Select **Cloud Path** or **Web** for the probe type.
- **Criteria**: Select your criteria for the template. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[See image.](#editTemplate)
- Click **Save**.
[]To copy a template:
- Click the **Copy** icon.
-
In the **Add New Template** drawer, enter the following:
- **Name**: Enter a name to identify the template.
- **Severity**: Select **High**, **Medium**, or **Low **for severity, depending on the impact of this event on users.
- **Probe Type**: Select **Cloud Path** or **Web** for the probe type.
- **Criteria**: Select your criteria for the template. To learn more, see [Configuring an Alert Rule](/zdx/configuring-alert-rule).
[See image.](#copyTemplate)
- Click **Save**.
[]To delete a template:
- Click the **Delete** icon.
- In the **Delete** window, review the deletion request for the specified template.
- Click **Delete** to confirm deletion.
[See image.](#deleteTemplate)
[]
![Add New Template](/downloads/zdx/alerts/managing-templates/ZDX-Add-New-Template-1.png)
[]
![Edit Template](/downloads/zdx/alerts/managing-templates/ZDX-Edit-Template-1.png)
[]
![Copy Template](/downloads/zdx/alerts/managing-templates/ZDX-Templates-Copy-Template-1.png)
[]
![Confirm Deleting Template](/downloads/zdx/alerts/managing-templates/ZDX-Templates-Delete.png)