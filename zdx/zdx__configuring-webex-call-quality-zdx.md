# Configuring Webex Call Quality for ZDX
Source: https://help.zscaler.com/zdx/configuring-webex-call-quality-zdx
PDF: https://help.zscaler.com/pdf/com/en/1443551.pdf

You can configure Webex Call Quality to monitor audio calls or meetings among two or more users. Call Quality can help you pinpoint issues that are unique to a device or the network by working in parallel with its Cloud Path probe. To learn more, see [Understanding Webex Call Quality for ZDX](/zdx/understanding-webex-call-quality-zdx).
Prerequisites
Before onboarding a Webex Call Quality tenant, ensure:
- You're running the required versions of Zscaler Client Connector and ZDX Module to configure a ZDX Autosense probe. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility#ZDXAutosenseZoom).
- Your ZDX subscription level supports ZDX Autosense. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- You enable the Windows Filtering Platform (WFP) driver installation setting for ZDX Autosense in the Zscaler Client Connector Portal. To learn more, see [Configuring Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles).
- You enable the setting to collect device hostname information in the Zscaler Client Connector Portal. To learn more, see [Configuring Zscaler Client Connector to Collect Hostnames](/client-connector/configuring-zscaler-client-connector-collect-hostnames).
Adding a Tenant
In the left-side navigation of the ZDX Admin Portal:
- Go to **Configuration > Applications**.
[See image.](#predefined-apps)
- Under **Webex Call Quality** in the** **Predefined Applications list, click **Add New Tenant**.
[See image.](#add-tenant)
- In the **Add New Webex Call Quality Tenant** window, enter the tenant name and configure the **Status** to **Enable**.
[See image.](#tenant-modal)
- In the Monitoring Criteria section, use the filters to gather Call Quality metrics for selected ZDX users. Meetings are monitored only for these users. Selections among the filters are cumulative, whereas selections within a single filter are not cumulative. For example, if you select DevTest and Service Admin in the User Groups filter, and then select Engineering and IT in the Departments filter, you can then identify users who belong to the DevTest or Service Admin user group *and *the Engineering or IT department.
Meetings are monitored and displayed only for your selected ZDX users in Monitoring Criteria.
[See image.](#monitor-criteria)
- In the Authentication section, click **Webex Authentication**.
You must authenticate with Webex before you can save the new tenant. You must also reauthenticate whenever you update the Monitoring Criteria settings.
- Enter your Webex credentials to sign in.
[See image.](#ms-credentials)
- Accept the requested permissions from Webex.
[See image.](#ms-permission)
- Return to the **Add New Webex Call Quality Tenant** window and click **Save**.
- (Optional) From the Predefined Applications list, select the Webex Call Quality tenant name. Click **Validate **within the dialog window to verify your Webex setup was successful.
[See image.](#validate-button)
Adding a Probe
To manually add a new probe for Webex Call Quality:
- Go to **Configuration > Applications**.
- Under **Webex Call Quality** in the** **Predefined Applications list, click **Add New Probe**.
[See image.](#add-webex-probe)
- In the **Add New Probe** window, enter a probe name, and select your probe type as either **Cloud Path **or **Autosense Cloud Path**. Then click **Next**:
[See image.](#add-webex-probe-popup)
- [Adding the Cloud Path Type](#cp-probe-type)
- [Adding the Autosense Cloud Path Probe Type](#acp-probe-type)
[]To add the Cloud Path Probe Type:
- Verify or configure the fields under **Probing Criteria** and **Exclusion Criteria**. To learn more, see [Configuring a Probe](/zdx/configuring-probe).
- Click **Next**.
- On the **Additional Parameters** tab, specify the **Cloud Path Host**, such as `zscaler.webex.com`. This field is for a fully qualified domain name.
[See image.](#webex-additional-params)
- Click **Next**.
- On the **Review **tab, confirm your configuration, and click **Submit**.
[]To add the Autosense Cloud Path Probe Type, which automatically detects the destination IP address:
A WFP driver installation is required within the Zscaler Client Connector Portal. To learn more, see [Configuring Zscaler Client Connector Profiles](/client-connector/configuring-zscaler-client-connector-profiles).
[See image.](#cp-host-auto-caution-webex)
- Verify or configure the fields under **Probing Criteria** and **Exclusion Criteria**. To learn more, see [Configuring a Probe](/zdx/configuring-probe).
- Click **Next**.
- On the **Additional Parameters** tab, verify the **Cloud Path Host** was automatically discovered via ZDX Autosense.
[See image.](#cp-host-auto-webex)
- Click **Next**.
- On the **Review **tab, confirm your configuration, and click **Submit**.
Disabling the Tenant
To disable the Webex Call Quality tenant:
- Go to **Configuration > Applications**.
- Under **Webex Call Quality** in the** **Predefined Applications list, click the **Edit **icon for the tenant or select the tenant name in the table.
- In the dialog window, configure the **Status** to **Disable**.
- Click **Save**.
Deleting the Tenant
To delete the Webex Call Quality tenant:
- Go to **Configuration > Applications**.
- Under **Webex Call Quality** in the** **Predefined Applications list, click the **Delete **icon for the tenant.
- In the dialog window, confirm you want to delete the tenant.
[]![Webex Call Quality in Predefined Applications](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-cqm-predefined-apps.png)
[]![Add New Tenant link is shown under Webex Call Quality app](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-add-tenant-link.png)
[]![Modal to add Webex Call Quality tenant](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-add-tenant-modal2.png)
[]![Modal to select monitoring criteria](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-select-monitoring-criteria2.png)
[]![Webex sign-in screens](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-credentials.png)
[]![Screen to accept Webex permissions](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-permissions2.png)
[]![Button to validate Webex authentication](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-validate-button.png)
[]![Link to Add New Probe for Webex](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-webex-add-probe-link.png)
[]![Select Probe Type](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-autosense-webex-probe-type.png)
[]![Enter Cloud Path Host on Additional Parameters tab](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-autosense-webex-cp-host.png)
[]![Caution shown when adding a ZDX Autosense Probe Type](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-autosense-webex-cp-host-auto-caution.png)
[]![Autosense Cloud Path Host](/downloads/zdx/configuration/applications/configuring-webex-call-quality-zdx/zdx-autosense-webex-cp-host-discovered.png)