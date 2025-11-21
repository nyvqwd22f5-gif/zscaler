# Sharing and Managing Snapshots
Source: https://help.zscaler.com/unified/sharing-digital-experience-monitoring-snapshots
PDF: https://help.zscaler.com/pdf/com/en/1494581.pdf

The Digital Experience Monitoring Snapshot feature captures the current state of a UI page, and provides a URL that admins can share with Digital Experience Monitoring users or other admins for view-only access. The Snapshot enables users without portal login access to view a subset of Digital Experience Monitoring features while bypassing the login authentication process.
Prerequisites
To create and share Snapshots, ensure:
- Your Digital Experience Monitoring subscription level supports Snapshot sharing. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#analytics).
- Your admin role is configured to share Snapshots. To learn more, see [Adding Digital Experience Monitoring Roles](/unified/adding-digital-experience-monitoring-roles).
Sharing a Snapshot
You can create and share a Snapshot by clicking **Share** **Snapshot **in the upper-right corner of the following pages:
- [User details](/unified/evaluating-user-details)
- [Applications Overview](/unified/monitoring-applications-overview)
- [Application details](/unified/monitoring-applications-overview#indivapp)
- [Alert details](/unified/evaluating-individual-alert-details)
- [Diagnostics details](/unified/viewing-diagnostics-session-results)
- [Incident details](/unified/monitoring-incidents-dashboard)
For the user details page, the **Share Snapshot **link is enabled only when an application has been selected, and only for the selected device.
![Share Snapshot link on user details page](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ZDXSnapshot-ShareSnapshot-UserDetails.png)
- Click **Share Snapshot**.
The **Share ZDX Snapshot **window appears.
- Enter a **Name** for the Snapshot.
- Select a time range from the **Valid for** drop-down menu, based on increments from **2 Hours** to **90 Days**. This time range represents the duration in which the Snapshot can be shared.
-
Enable or disable **Obfuscate Data**. If you enable the setting, select the data types from the **Obfuscation **drop-down menu to be hidden from the recipient. The availability of these data types corresponds to the recipient's privileges in viewing the Snapshot.
[See image.](#snap-obfuscate)
- Click **Next **to generate the Snapshot.
-
Click **Copy URL** to copy the generated URL and share with trusted recipients.
Make sure you only share Snapshots with trusted recipients to avoid inadvertent disclosure of data.
[See image.](#snap-share-url)
- (Optional) Click **Manage Snapshots **to view an accrued list of Snapshots.
Managing Snapshots
Go to **Analytics** > **Digital Experience Monitoring** > **Reporting **> **ZDX Snapshots** to view a history of Snapshots from an accrued list of generated URLs. You have the option to copy or delete any of the Snapshots.
- **Name**: The unique name of a generated Snapshot.
- **Created on**: The date and time when the Snapshot was created.
- **Valid until**: The end date and time when access to the Snapshot expires. The Snapshot is no longer valid after expiration, and a message confirms the URL is not found if you attempt to share it.
- **Status**: The current state of the Snapshot (Expired, Active).
- **URL**: The generated URL for sharing the Snapshot.
- **View Count**: The number of times the Snapshot URL has been generated.
- **Actions**: Copy the Snapshot URL or Delete the Snapshot.
![Manage ZDX Snapshots](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ShareZDXSnapshot-ManageZDXSnapshotWindow.png)
Viewing Snapshots
Users can identify a Snapshot by the green icon located in the upper-left corner of the page:
![ZDX Snapshot icon and page from user's viewpoint](/downloads/zdx/analytics/users/sharing-zdx-snapshots/zdx-snapshot-view2.png)
A Snapshot has only limited user interaction within the page, depending on what data is obfuscated and what details are shared. For example, user interaction for the following features is disabled by default when viewing a snapshot of the user details page:
- Time range filter
- Drop-down filters
- Device selection
- Applications other than the application already selected
- Data points for root cause analysis other than the data point already selected
- Web Probe Metrics
- Cloud Path
[]
![Obfuscate ZDX Snapshot data](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ShareZDXSnapshot-ShareZDXSnapshotWindow.png)
[]
![Copy the ZDX Snapshot URL](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ShareZDXSnapshot-ShareZDXSnapshotURLWindow.png)