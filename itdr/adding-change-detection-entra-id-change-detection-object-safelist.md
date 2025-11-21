# Adding a Change Detection to the Entra ID Change Detection Object Safelist
Source: https://help.zscaler.com/itdr/adding-change-detection-entra-id-change-detection-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531797.pdf

After you [connect an Entra ID](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) tenant for a [scan](/itdr/triggering-demand-scan-entra-id), any changes detected in the first and subsequent scan results are recorded and compared, and the data is categorized as Good, Bad, or Info on the [Entra ID Change Detection dashboard](/itdr/about-entra-id-change-detection-dashboard). You can review these changes to confirm that they are not a risk and mark them as safe by moving them to the object safelist if the changes are associated with a `principal_id`.
The safelist option is not supported for [custom change detections](/itdr/about-entra-id-custom-change-detection-dashboard).
To add a change detection in an Entra ID tenant to the object safelist:
- Go to **ITDR** > **Dashboard **>** Entra ID** **Change Detection > Default**.
-
Select an Entra ID tenant from the **Result for** drop-down menu.
The change detection data for the Entra ID tenant appears.
-
Locate the change detection issue that you want to add to the safelist, and under **Actions**, click the **Add to Object Safelist **icon.
[See image.](#change-detection-add-issue-safelist)
-
In the **Add to Safelist** window, enter a reason for marking the change detection issue as safe and select an expiration date if needed.
The option to add an item to change detection object safelist is available only if a `principal_id` is associated with the change.
[See image.](#change-detection-enter-reason)
-
Click **Save**.
The change is added to the safelist. You can view and manage it from the [Entra ID Change Detection Object Safelist](/itdr/about-entra-id-change-detection-object-safelist).
[]![Adding a change detection issue to safelist](/downloads/itdr/safelists/entra-id-safelists/entra-id-change-detection-object-safelist/adding-change-detection-entra-id-change-detection-object-safelist/itdr-entraid-changedetection-safelist.png)
[]![Entering a reason for adding a change detection issue to safelist](/downloads/itdr/safelists/entra-id-safelists/entra-id-change-detection-issue-safelist/adding-change-detection-issue-entra-id-change-detection-safelist/itdr-add-to-safelist-window.png)