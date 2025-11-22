# Sharing ZDX Snapshots
Source: https://help.zscaler.com/zdx/sharing-zdx-snapshots
PDF: https://help.zscaler.com/pdf/com/en/1462931.pdf

The Zscaler Digital Experience (ZDX) Snapshot feature captures the current state of a UI page, and provides a URL that admins can share with ZDX users or other admins for view-only access. ZDX Snapshot enables users without ZDX Admin Portal login access to view a subset of ZDX features while bypassing the login authentication process.
Prerequisites
To create and share ZDX Snapshots, ensure:
- Your ZDX subscription level supports ZDX Snapshot sharing. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- Your admin role is configured to share ZDX Snapshots. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Sharing Your ZDX Snapshot
You can create and share a ZDX Snapshot by clicking **Share** **Snapshot **in the upper-right corner of the following pages:
- [User details](/zdx/evaluating-user-details)
- [Applications Overview](/zdx/monitoring-applications-overview)
- [Application details](/zdx/monitoring-applications-overview#indivapp)
- [Alert details](/zdx/evaluating-individual-alert-details)
- [Diagnostics details](/zdx/viewing-diagnostics-session-results)
- [Incident details](/zdx/monitoring-incidents-dashboard)
For the user details page, the **Share Snapshot **link is enabled only when an application has been selected, and only for the selected device.
![Share Snapshot link on user details page](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ZDXSnapshot-ShareSnapshot-UserDetails.png)
- Click **Share Snapshot**.
The **Share ZDX Snapshot **window appears.
- Enter a **Name** for the ZDX Snapshot.
- Select a time range from the **Valid For** drop-down menu, based on increments from **2 Hours** to **90 Days**. This time range represents the duration in which you can share the ZDX Snapshot.
-
Enable or disable **Obfuscate Data**. If you enable the setting, select the data types from the **Obfuscation **drop-down menu to be hidden from the recipient. The availability of these data types corresponds to the recipient's privileges in viewing the ZDX Snapshot.
[See image.](#snap-obfuscate)
- Click **Next **to generate the ZDX Snapshot.
-
Click **Copy URL** to copy the generated URL and share with trusted recipients.
Make sure you only share ZDX Snapshots with trusted recipients to avoid inadvertent disclosure of data.
[See image.](#snap-share-url)
- (Optional) Click **Manage ZDX Snapshots **to view an accrued list of ZDX Snapshots.
Managing ZDX Snapshots
Go to **Analytics** > **ZDX Snapshots** to view a history of ZDX Snapshots from an accrued list of generated URLs. You have the option to copy or delete any of the ZDX Snapshots.
- **Name**: The unique name of a generated ZDX Snapshot.
- **Created On**: The date and time when the ZDX Snapshot was created.
- **Valid Until**: The end date and time when access to the ZDX Snapshot expires. The ZDX Snapshot is no longer valid after expiration, and a message confirms the URL is not found if you attempt to share it.
- **Status**: The current state of the ZDX Snapshot (Expired, Active).
- **URL**: The generated URL for sharing the ZDX Snapshot.
- **Views**: The number of times the ZDX Snapshot URL has been generated.
- **Actions**: Copy the ZDX Snapshot URL or Delete the ZDX Snapshot.
![Manage ZDX Snapshots](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ShareZDXSnapshot-ManageZDXSnapshotWindow.png)
Viewing ZDX Snapshots
Users can identify a ZDX Snapshot by the green icon located in the upper-left corner of the page:
![ZDX Snapshot icon and page from user's viewpoint](/downloads/zdx/analytics/users/sharing-zdx-snapshots/zdx-snapshot-view2.png)
A ZDX Snapshot has only limited user interaction within the page, depending on what data is obfuscated and what details are shared. For example, user interaction for the following features is disabled by default when viewing a snapshot of the user details page:
- Time range filter
- Drop-down menu filters
- Device selection
- Applications other than the application already selected
- Data points for root cause analysis other than the data point already selected
- Web Probe Metrics
- Cloud Path
[]
![Obfuscate ZDX Snapshot data](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ShareZDXSnapshot-ShareZDXSnapshotWindow.png)
[]
![Copy the ZDX Snapshot URL](/downloads/zdx/analytics/users/sharing-zdx-snapshots/ShareZDXSnapshot-ShareZDXSnapshotURLWindow.png)