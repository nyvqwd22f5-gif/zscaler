# Adding a Change Detection Issue to the Entra ID Change Detection Safelist
Source: https://help.zscaler.com/itdr/adding-change-detection-issue-entra-id-change-detection-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531769.pdf

After you [connect an Entra ID](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) tenant for a [scan](/itdr/triggering-demand-scan-entra-id), any changes detected in the first and subsequent scan results are recorded and compared, and the data is categorized as Good, Bad, or Info on the [Entra ID Change Detection](/itdr/about-entra-id-change-detection-dashboard) page. You can review these change detection issues to confirm that they are not a risk and mark them as safe. For example, if you mark the Privileged Accounts issue as safe, then all issues related to Privileged Accounts are removed from the [Entra ID Change Detection](/itdr/about-entra-id-change-detection-safelist) page for the selected Entra ID tenant.
The safelist option is not supported for [custom change detections](/itdr/about-entra-id-custom-change-detection-dashboard).
To add a change detection issue in an Entra ID tenant to the safelist:
- Go to **ITDR** > **Dashboard **>** Entra ID** **Change Detection > Default**.
-
Select an Entra ID tenant from the **Result for** drop-down menu.
[See image.](#change-detection-select-ad-domain)
The change detection data for the Entra ID tenant appears.
-
Under **Actions**, click the **Shield** icon to add the selected change detection issue to the safelist.
[See image.](#change-detection-add-issue-safelist)
-
In the **Add to Safelist** window, enter a reason for marking the change detection issue as safe and select an expiration date if needed.
[See image.](#change-detection-enter-reason)
-
Click **Save**.
The change detection issue is added to the safelist. You can view and manage it from the [Entra ID Change Detection Safelist](/itdr/about-entra-id-change-detection-safelist).
[]![The Result for drop-down menu to select an Entra ID tenant.](/downloads/itdr/safelists/entra-id-safelists/entra-id-change-detection-issue-safelist/adding-change-detection-issue-entra-id-change-detection-safelist/itdr-custom-result-dropdown.png)
[]![Adding a change detection issue to the safelist](/downloads/itdr/safelists/entra-id-safelists/entra-id-change-detection-issue-safelist/adding-change-detection-issue-entra-id-change-detection-safelist/itdr-entraID-shield-icon.png)
[]![Entering a reason for adding a change detection issue to the safelist](/downloads/itdr/safelists/entra-id-safelists/entra-id-change-detection-issue-safelist/adding-change-detection-issue-entra-id-change-detection-safelist/itdr-add-to-safelist-window.png)