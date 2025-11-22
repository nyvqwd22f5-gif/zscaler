# Updating the App Finding Status
Source: https://help.zscaler.com/unified/updating-app-finding-status
PDF: https://help.zscaler.com/pdf/com/en/1516106.pdf

Findings indicate security or posture issues identified and associated with an app or a user. Each finding has a short background, recommendation, MITRE mappings, and a severity level that impacts the app risk score. You can set the status of an app finding to one of the following:
- **Unattended**: The finding has yet to be dismissed or resolved. This is the default status of any new finding.
- **Dismissed**: The finding has been dismissed.
- **Resolved**: The recommended action is taken on the app and the finding has been resolved.
You can view and update the app finding status on the [App Panel Overview tab](/unified/about-app-panel#app-panel-overview).
To update the app finding status:
-
Select an app.
The App Panel opens.
- On the **Overview** tab, go to the finding for which you want to update the status.
-
From the drop-down menu next to the finding, select the appropriate status for the finding.
[See image.](#Finding-Drop-Down)
The **Update Finding Status** window appears.
-
(Optional) Enter the reason for changing the app's finding status, and click **Save**.
[See image.](#Update-Finding-Status-Window)
The finding status is updated successfully, and the app risk score is recalculated and updated. After the status is updated, the finding is removed from **Unattended **list and added to **Resolved** or **Dismissed** list on the App Panel **Overview** tab.
The update of the app finding status is recorded as an activity on the** **[Activities tab](/unified/about-app-panel#app-panel-activities) and the audit log.
You can revert the finding to its default status by setting the status back to **Unattended**.
[]![Screenshot of App Finding Drop Down](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/updating-app-finding-status/AppFinding_DropDown.png)
[]![Screenshot of Update Finding Status Window](/downloads/zia/policies/data-loss-prevention/apptotal/using-apptotal/updating-app-finding-status/Update_Finding_Window.png)