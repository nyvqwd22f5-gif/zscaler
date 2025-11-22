# Adding a Change Detection to the AD Change Detection Object Safelist
Source: https://help.zscaler.com/itdr/adding-change-detection-ad-change-detection-object-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531800.pdf

If you enable change detection for your Active Directory (AD) domain, any changes detected in the first and subsequent scan results are recorded and compared, and the data is categorized as Good, Bad, or Info on the [Change Detection dashboard](/itdr/about-entra-id-change-detection-dashboard). You can review these changes to confirm that they are not a risk and mark them as safe by moving them to the object safelist.
The safelist option is not supported for [custom change detections](/itdr/about-active-directory-custom-change-detection-dashboard).
To add a change detection in an AD domain to the object safelist:
- Go to **ITDR** > **Dashboard **>** Entra ID** **Change Detection > Default**.
-
Select an AD domain from the **Result for** drop-down menu.
[See image.](#change-detection-select-ad-domain)
The change detection data for the AD domain appears.
-
Locate the change detection issue that you want to add to the safelist, and under **Actions**, click the **Add to Object Safelist **icon.
[See image.](#change-detection-add-issue-safelist)
-
In the **Add to Safelist** window, enter a reason for marking the change detection issue as safe and select an expiration date if needed.
[See image.](#change-detection-enter-reason)
-
Click **Save**.
The change is added to the safelist. You can view and manage it from the [AD Change Detection Object Safelist](/itdr/about-ad-change-detection-object-safelist).
[]![Selecting an AD domain to view change detection results](/downloads/itdr/safelists/active-directory-safelists/ad-change-detection-object-safelist/adding-change-detection-ad-change-detection-object-safelist/itdr-ad-change-detection-default-dashboard.png)
[]![Adding a change detection issue to safelist](/downloads/itdr/safelists/active-directory-safelists/ad-change-detection-object-safelist/adding-change-detection-ad-change-detection-object-safelist/itdr-ad-cd-icon-object_0.png)
[]![Entering a reason for adding a change detection issue to safelist](/downloads/itdr/safelists/entra-id-safelists/entra-id-change-detection-issue-safelist/adding-change-detection-issue-entra-id-change-detection-safelist/itdr-add-to-safelist-window.png)