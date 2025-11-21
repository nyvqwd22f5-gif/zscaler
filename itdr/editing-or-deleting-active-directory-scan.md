# Editing or Deleting an Active Directory Scan
Source: https://help.zscaler.com/itdr/editing-or-deleting-active-directory-scan
PDF: https://help.zscaler.com/pdf/com/en/1531623.pdf

You can edit or delete an [Active Directory (AD) scan](/itdr/scanning-active-directory) that you configured.
Editing a Scan
To edit a scan:
- Go to **ITDR **> **Manage** > **Active Directory Posture**.
-
Locate the AD domain for which you want to modify the scan, and click the **Edit **icon.
[See image.](#deception-ad-scan-edit-icon)
-
In the **Scan Agents Details** window, modify the fields as necessary.
[See image.](#deception-ad-scan-modify-details)
If an endpoint agent has not checked in for more than 7 days, it is removed from the scan and its **Current State** status is set to **Error**.
[See image.](#scanagentsdetails)
- Click **Submit**.
Deleting a Scan
To delete a scan:
- Go to **ITDR **> **Manage** > **Active Directory Posture**.
-
Locate the AD domain for which you want to delete the scan, and click the **Delete **icon.
[See image.](#deception-ad-scan-delete-icon)
-
In the confirmation window, click **OK**.
After you delete a scan, all the identity vulnerability results pertaining to that AD domain on the [Active Directory Posture](/itdr/about-active-directory-posture-dashboard) dashboard are deleted.
[]![Edit an AD scan](/downloads/itdr/itdr/active-directory-posture-scan/editing-or-deleting-scan/itdr-ad-posture-edit-icon.png)
[]![Edit AD scan details](/downloads/itdr/itdr/active-directory-posture-scan/editing-or-deleting-scan/itdr-ad-edit-scan-details-2.png)
[]![Delete an AD scan](/downloads/itdr/itdr/active-directory-posture-scan/editing-or-deleting-scan/itdr-ad-posture-delete-icon.png)
![The Active Directory Posture tab listing the scans configured.](/downloads/itdr/itdr/active-directory-posture-scan/editing-or-deleting-active-directory-scan/itdr-error.png)
[]