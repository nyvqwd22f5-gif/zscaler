# Configuring Zoom Call Quality for Digital Experience Monitoring
Source: https://help.zscaler.com/unified/configuring-zoom-call-quality-zdx
PDF: https://help.zscaler.com/pdf/com/en/1492786.pdf

You can configure Zoom Call Quality to monitor calls among two or more users. Call Quality can help you pinpoint issues that are unique to a device or the network by working in parallel with its Cloud Path probe. To learn more, see [Understanding Zoom Call Quality for Digital Experience Monitoring](/unified/understanding-zoom-call-quality-digital-experience-monitoring).
When onboarding a Zoom Call Quality tenant for the first time, an Autosense Cloud Path probe is automatically generated that detects the destination IP address.
Prerequisites
Before onboarding a Zoom Call Quality tenant, ensure:
- You're running the required versions of Zscaler Client Connector and ZDX Module to configure an Autosense probe.
- Your Digital Experience Monitoring subscription level supports Autosense. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#applications-probes).
- You enable the Windows Filtering Platform (WFP) driver installation setting for Autosense in Zscaler Client Connector settings in the Admin Portal. To learn more, see [Configuring Zscaler Client Connector Profiles](/unified/configuring-zscaler-client-connector-app-profiles).
- You enable the setting to collect device hostname information in Zscaler Client Connector settings in the Admin Portal. To learn more, see [Configuring Zscaler Client Connector to Collect Hostnames](/unified/configuring-zscaler-client-connector-collect-hostnames).
Adding a Tenant
In the Admin Portal:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration > Applications**.
[See image.](#predefined-apps)
-
Under **Zoom Call Quality** in the** **Predefined Applications list, click **Authenticate**.
[See image.](#authenticate-link)
-
Sign in with your email and password, and then click **Authorize **to accept the Zoom permissions. A Zoom API tenant is created under **Zoom Call Quality** on the Applications page. You can either onboard the Zoom API tenant or onboard a Zoom Quality of Service Subscription (QSS) tenant for Zoom's data streaming service.
[See image.](#zoom-credentials)
- To onboard the Zoom API tenant:
- Click **Zoom CQM Tenant**. You can rename the tenant.
-
Ensure the **Status **is configured to **Enable**.
[See image.](#add-zoom-tenant)
- To onboard a Zoom QSS tenant instead of the Zoom API tenant:
- Delete the Zoom API tenant.
- Select **Add Tenant**.
- Select **Zoom QSS** to name and configure the QSS tenant.
- Ensure the **Status **is configured to **Enable**.
You can onboard either a Zoom API tenant or a Zoom QSS tenant. You cannot onboard both at one time.
[See image.](#add-qss-tenant)
- In the Monitoring Criteria section, use the filters to gather Call Quality metrics for selected Digital Experience Monitoring users. Meetings are monitored only for these users. Selections among the filters are cumulative, whereas selections within a single filter are not cumulative. For example, if you select DevTest and Service Admin in the User Groups filter, and then select Engineering and IT in the Departments filter, you can then identify users who belong to the DevTest or Service Admin user group *and *the Engineering or IT department.
Meetings are monitored and displayed only for your selected Digital Experience Monitoring users in Monitoring Criteria. You must reauthenticate with Zoom after you configure or update the Monitoring Criteria settings.
[See image.](#select-filters)
- (Optional) Click **Validate **to verify your setup with Zoom was successful.
[See image.](#validate-button)
- Click **Save**.
Adding a Probe
To manually add a new probe for Zoom Call Quality:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration > Applications**.
- Under **Zoom Call Quality** in the** **Predefined Applications list, click **Add Probe**.
[See image.](#add-probe)
- In the **Add Probe** window, enter a probe name, and select your probe type as either **Cloud Path **or **Autosense Cloud Path**. Then click **Next**:
[See image.](#add-probe-popup)
- [Adding the Cloud Path Probe Type](#cp-probe-type)
- [Adding the Autosense Cloud Path Probe Type](#acp-probe-type)
[]To add the Cloud Path Probe Type:
- Verify or configure the fields under **Probing Criteria** and **Exclusion Criteria**. To learn more, see [Configuring a Probe](/unified/configuring-probe).
- Click **Next**.
- On the **Additional Parameters** tab, specify the **Cloud Path Host**, such as `zscaler.zoom.us`. This field is for a fully qualified domain name.
[See image.](#additional-parameters)
- Click **Next**.
- On the **Review **tab, confirm your configuration, and click **Submit**.
[]To add the Autosense Cloud Path Probe Type:
A WFP driver installation is required within the Admin Portal Zscaler Client Connector settings. To learn more, see [Configuring Zscaler Client Connector](/unified/configuring-zscaler-client-connector-app-profiles) [Profiles](/client-connector/configuring-zscaler-client-connector-profiles).
[See image.](#cp-host-auto-caution)
- Verify or configure the fields under **Probing Criteria** and **Exclusion Criteria**. To learn more, see [Configuring a Probe](/unified/configuring-probe).
- Click **Next**.
- On the **Additional Parameters** tab, verify the **Cloud Path Host** was automatically discovered via Autosense.
[See image.](#cp-host-auto)
- Click **Next**.
- On the **Review **tab, confirm your configuration, and click **Submit**.
Disabling the Tenant
To disable the Zoom Call Quality tenant:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration > Applications**.
- Under **Zoom Call Quality** in the** **Predefined Applications list, click the **Edit **icon for the tenant or select the tenant name in the table.
- In the dialog window, configure the **Status** to **Disable**.
- Click **Save**.
Deleting the Tenant
To delete the Zoom Call Quality tenant:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration > Applications**.
- Under **Zoom Call Quality** in the** **Predefined Applications list, click the **Delete **icon for the tenant.
- In the dialog window, confirm you want to delete the tenant.
[]![Zoom Call Quality shown in Predefined Applications](/downloads/zdx/configuration/applications/configuring-zoom-call-quality-zdx/zdx-config-begin-zoom-qss3.png)
[]![Link to Authenticate Zoom Call Quality](/downloads/zdx/analytics/configuring-zoom-call-quality-zdx/zdx-zoom-cqm-authenticate2.png)
[]![Enter Zoom credentials to sign in](/downloads/zdx/analytics/configuring-zoom-call-quality-zdx/zdx-zoom-cqm-enter-credentials.png)
[]![Pop-up window to edit Zoom Call Quality tenant](/downloads/zdx/configuration/applications/configuring-zoom-call-quality-zdx/zdx-zoom-cqm-edit-tenant5.png)
[]![Selecting Zoom QSS to add a QSS tenant](/downloads/zdx/configuration/applications/configuring-zoom-call-quality-zdx/zdx-select-zoom-qss3.png)
[]![Select monitoring criteria](/downloads/zdx/configuration/applications/configuring-zoom-call-quality-zdx/zdx-zoom-cqm-monitoring-filter5.png)
[]![Validate Zoom authentication](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-zoom-call-quality-zdx-draft-b/zdx-zoom-cqm-validate.png)
[]![Link to Add New Probe](/downloads/zdx/analytics/configuring-zoom-call-quality-zdx/zoom-cqm-add-new-probe2.png)
[]![Pop-up window to Add New Probe](/downloads/tech-pubs-drafts/zdx-draft-articles/configuring-zoom-call-quality-zdx-draft-autosense-doc-47559/zdx-autosense-probe-type.png)
[]![Enter Cloud Path Host on Additional Parameters tab](/downloads/zdx/configuration/applications/configuring-zoom-call-quality-zdx/zdx-autosense-cp-host3.png)
[]![Autosense Cloud Path Host](/downloads/zdx/configuration/applications/configuring-zoom-call-quality-zdx/zdx-autosense-cp-host-auto4.png)
[]![Caution shown when adding a ZDX Autosense Probe Type](/downloads/zdx/configuration/applications/configuring-zoom-call-quality-zdx/zdx-autosense-cp-host-auto-caution.png)