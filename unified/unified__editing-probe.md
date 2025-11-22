# Editing a Probe
Source: https://help.zscaler.com/unified/editing-probe
PDF: https://help.zscaler.com/pdf/com/en/1492846.pdf

After adding an application and configuring its probes, you can edit any probe details that are not preconfigured.
You cannot reconfigure preset probe configurations. To learn more about configuring probes, see [Configuring a Probe](/unified/configuring-probe).
To edit a probe:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration > Probes**.
- Click the **Edit **icon to edit your probe. Cards for disabled probes are shown entirely in gray.
The **Edit **window appears.
[See image.](#Icon_to_editprobe)
-
On the **Configure Probe** tab of the window:
-
For **General**:
- If editing a probe associated with a custom application, you can edit the **Name**,** Run Frequency**,** **and **Status**.
[See image.](#Edit-Custom-Probe)
- If editing a probe associated with a predefined application, you can only **Enable** or **Disable** the probe **Status**.
[See image.](#Editing_PredefinedApplication)
- For **Probing Criteria**, edit the **User Groups**, **Users**, **Locations**, **Location Groups**, **Departments**, and **Devices**. The maximum number of Zscaler locations cannot exceed 100 locations.
- For **Exclusion Criteria**, edit the **User Groups**, **Users**, **Locations**, **Location Groups**, **Departments**, and **Devices**.
- Click **Next**.
[See image.](#MonCriteria)
-
After a probe is saved, you cannot edit the **Probe Name** and **Application Name**. On the **Additional Parameters** tab:
- If editing a Cloud Path probe associated with a predefined application, you can edit some fields, depending on the probe type:
- If editing a Web probe associated with a predefined application, you can edit the **Destination URL** if a tenant name is required.
- If editing a Cloud Path probe associated with a predefined application, you can edit the** Packet Count**,** Interval**,** **and **Timeout**,** **as well as the **Tenant ID **for the probe URL if the predefined application specified a tenant when onboarded. You can also select or deselect the setting to **Force Reverse Cloud Path in Trusted Network**.
[See image.](#Editing-probe-TR-predefined)
-
If editing a probe associated with a custom application, you can edit most fields, depending on the probe type:
- For Cloud Path probes, you can edit the **Protocol**,** Packet Count**, **TCP Port**, **UDP Port**,** Interval**,** Timeout**, **Cloud Path Host**, and change the setting for **Force Reverse Cloud Path in Trusted Network**. If you edit a Cloud Path probe and choose to follow a Web probe, the TCP Port is automatically updated to the standard TCP Port for HTTP Traffic, 443, and you cannot manually change the TCP Port number.
[See image.](#Editing-probe-TR-custom)
- For Web probes, you can edit the **Destination URL**,** Request Header**,** HTTP Response Status Codes**,** Number of Attempts**,** Timeout (seconds)**,** Follow Redirect**, and **Maximum Redirects**.
[See image.](#EditCustomAppWebProbe1)
- Click **Next**.
- Confirm your settings on the **Review** tab. Click **Save**.
Save and activate your changes. Zscaler recommends waiting at least 30 minutes after editing probe settings to begin seeing changes in the dashboard.
Deleting a Probe
You can delete probes associated with custom applications. However, you cannot delete probes associated with predefined applications.
To delete a probe associated with a custom application:
- Go to **Policies **> **Digital Experience Monitoring** > **Configuration > Probes**.
- Click the **Delete** icon to delete your probe.
[See image.](#icon-to-delete)
[]![Click edit icon to edit probe](/downloads/zdx/configuration/probes/editing-probe/zdx-probe-no-delete.png)
[]![Editing a probe for a predefined application](/downloads/zdx/configuration/probes/editing-probe/zdx-edit-probe-for-predefined3.png)
[]![Probing and Exclusion Criteria](/downloads/zdx/configuration/probes/editing-probe/zdx-edit-probe-criteria3.png)
[]![Edit Cloud Path probe fields for predefined applications](/downloads/zdx/configuration/probes/editing-probe/zdx-edit-probe-for-predefined-cp-checkbox3.png)
[]![Edit probe fields for custom application](/downloads/zdx/configuration/probes/editing-probe/zdx-edit-probe-for-custom3.png)
[]![Edit Cloud Path probe fields for custom application](/downloads/zdx/configuration/probes/editing-probe/zdx-edit-probe-for-custom-cp-checkbox3.png)
[]![Editing additional web parameters for a custom application](/downloads/zdx/configuration/probes/editing-probe/zdx-edit-probe-for-custom-web3.png)
[]![Example of Delete icon to delete a custom probe](/downloads/zdx/configuration/probes/editing-probe/zdx-edit-probe-delete3.png)