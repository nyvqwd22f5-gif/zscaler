# Adding a Change Detection Issue to the Safelist
Source: https://help.zscaler.com/itdr/adding-change-detection-issue-safelist
PDF: https://help.zscaler.com/pdf/com/en/1531648.pdf

After you [configure an Active Directory (AD) domain for a scan](/itdr/scanning-active-directory) and enable change detection, any changes detected in the first and subsequent scan results are recorded and compared, and the data is categorized as Good, Bad, or Info on the [Change Detection](/itdr/about-change-detection) dashboard. You can review these change detection issues to confirm that it is not a risk and mark them as safe. For example, if you mark the Privileged Accounts issue as safe, then all issues related to Privileged Accounts are removed from the Change Detection page for the selected AD domain.
The safelist option is not supported for [custom change detections](/itdr/about-active-directory-custom-change-detection-dashboard).
To add a change detection issue to the safelist:
- Go to **ITDR** > **Dashboard **> **Change Detection > Default**.
-
Select an AD domain from the **Result for** drop-down menu.
[See image.](#deception-change-detection-select-ad-domain)
The change detection data for the AD domain appears.
-
Under **Actions**, click the **Shield** icon to add the selected change detection issue to the safelist.
[See image.](#deception-change-detection-add-issue-safelist)
-
In the **Add to Safelist** window, enter a reason for marking the change detection issue safe and set an expiration date if needed.
[See image.](#deception-change-detection-enter-reason)
-
Click **Save**.
The change detection issue is added to the safelist. You can [view and manage](/itdr/viewing-and-managing-change-detection-safelist) it on the Change Detection Safelist page.
[]![Selecting an AD domain to view change detection results](/downloads/itdr/safelists/active-directory-safelists/ad-change-detection-issue-safelist/adding-change-detection-issue-safelist/itdr-ad-change-detection-default-dashboard.png)
[]![Adding a change detection issue to safelist](/downloads/itdr/safelists/active-directory-safelists/ad-change-detection-issue-safelist/adding-change-detection-issue-safelist/itdr-ad-add-to-object-safelist-icon.png)
[]![Entering a reason for adding a change detection issue to safelist](/downloads/itdr/safelists/active-directory-safelists/ad-change-detection-issue-safelist/itdr-add-to-safelist-window.png)