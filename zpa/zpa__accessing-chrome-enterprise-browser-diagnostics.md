# Accessing Chrome Enterprise Browser Diagnostics
Source: https://help.zscaler.com/zpa/accessing-chrome-enterprise-browser-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1530732.pdf

You can view and filter managed Chrome Enterprise Browser policy log data and trend data for past events.
Accessing Chrome Enterprise Browser Diagnostics
To view diagnostics for user activity:
- Go to **Analytics **> **Diagnostics**.
- Under **Log Type**, choose **Chrome Enterprise Browser**.
By default, the detailed activity for all Chrome Enterprise browsers is displayed for events that occurred in the last 24 hours. You can do the following:
- Click the **Calendar **drop-down** **menu to select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days.
- Click the **Time Zone** icon to change the time zone.
- Click the **Settings** icon to configure the [diagnostics settings](#settings).
Zscaler retains logs for rolling periods of at least 14 days during the Subscription Term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/zpa/about-log-streaming). Data in the [dashboard](/zpa/dashboard-diagnostics) might be more recent than the data presented within Diagnostics.
[See image.](#img-timerange)
Viewing Logs
Log activity is automatically displayed after selecting the Chrome Enterprise Browser log type.
By default, the table displays the total number of Chrome Enterprise browser requests made by users. You can change this by choosing one of the following filters:
- **Errors**: The total number of Chrome Enterprise browser errors.
- **Successful**: The total number of successful Chrome Enterprise browser requests.
- **Info**: The total number of application connections that terminated because the user or App Connector abruptly ended the TLS session (e.g., user laptop enters sleep mode which ends the TLS session) or the application's connection gracefully timed out.
[See image.](#img-logtotals)
[]Configuring Settings
To configure settings for diagnostics pages in the ZPA Admin Portal:
- Go to **Analytics** > **Diagnostics**.
- Click the **Settings** icon (![Settings icon within the diagnostics pages](/downloads/tech-pubs-drafts/configuring-diagnostics-settings-doc-60060/zpa-diagnostics-settings-icon.png)
).
The **Settings** drawer appears.
-
In the **Settings** drawer, select the default filter operator (i.e., **Equals** or **Contains**) from the** **drop-down menu. The **Default Filter Operator** is set to **Equals** by default.
[See image.](#settingsDrawer)
-
Click **Save** to apply your changes.
The selected filter operator is saved for future sessions.
[]![Settings drawer in the diagnostics pages](/downloads/tech-pubs-drafts/configuring-diagnostics-settings-doc-60060/zpa-diagnostics-settings-drawer.png)
Filtering Chrome Enterprise Browser Logs
On the Chrome Enterprise Browser page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied.
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu:
- [View the query builder filters.](#filters)
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Filtering the Chrome Enterprise Browser diagnostics page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/accessing-chrome-enterprise-browser-diagnostics/zpa-chrome-enterprise-browser-diagnostics-filters.png)
To apply more filters, click **Add Filters** again or click on the **Filter **icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon, and then click **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy** icon to save the filter query details. If you or another ZPA admin access **Diagnostics**, you can paste the query into the field by clicking the **Clipboard **icon.
[See image.](#QueryBuilder_CopyPaste)
[]The table displays the following data for application requests:
- [Timestamp](#time)
- [Browser Version](#browserVersion)
- [Operating System](#operatingSystem)
- [Safe Browsing Protection Level](#safeBrowsingProtectionLevel)
To learn more, refer to the [Chrome Verified Access API documentation](https://developers.google.com/chrome/verified-access/reference/rest/v2/challenge/verify#response-body).
[See image.](#chromeDiagnosticsDataTable)
You can expand each row to see more details or click the **Expand All **or **Collapse** **All** to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
[]![Using the Time Range for the Chrome page Enterprise Browser Diagnostics](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/accessing-chrome-enterprise-browser-diagnostics/zpa-chrome-enterprise-browser-diagnostics-time-range.png)
[]![Viewing the Totals for the Chrome Enterprise Browser Diagnostics page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/accessing-chrome-enterprise-browser-diagnostics/zpa-chrome-enterprise-browser-diagnostics-totals.png)
- []**Browser Version**: The version of the Chrome Enterprise browser.
- **Cookie Domain ID**: The cookie domain ID.
- **CrowdStrike Agent**: The CrowdStrike Agent software. This can be **Enabled** or **Disabled**.
- **Disk Encryption**: The disk encryption type (i.e., **Unspecified Disk Encryption**, **Unknown Disk Encryption**, **Disabled Disk Encryption**, or **Encrypted Disk Encryption**).
- **Operating System**: The host operating system (i.e., **Unspecified Operating System**, **ChromeOS**, **ChromiumOS**, **Windows**, **macOS**, **Linux**).
- **Safe Browsing Protection Level**: The Safe Browsing protection level (i.e., **Unspecified Safe Browsing Protection Level**, **Inactive Safe Browsing Protection Level**, **Standard Safe Browsing Protection Level**, or **Enhanced Safe Browsing Protection Level**).
- **Screen Lock Secured**: The screen lock security types (i.e., **Unspecified Secured Screen Lock**, **Unknown Secured Screen Lock**, **Enabled Screen Lock**, or **Disabled Screen Lock**).
- **Secure Boot Mode**: The Secure Boot mode (i.e., **Unspecified Secure Boot Mode**, **Unknown Secure Boot Mode**, **Enable Secure Boot Mode**, or **Disable Secure Boot Mode**).
To learn more, refer to the [Chrome Verified Access API documentation](https://developers.google.com/chrome/verified-access/reference/rest/v2/challenge/verify#response-body).
The Timestamp** **column sorts requests by the connection date and start time in descending order. You can click the **Arrow** icon to sort the requests in ascending order. The time displayed is based on the time you choose for [your account setting](/zpa/accessing-and-navigating-zpa-admin-portal) in the ZPA Admin Portal.
- []**OS Version**: The host operating system version.
- **Trigger**: The trigger for the Chrome Enterprise browser.
- **Display Name**: The display name of the machine using the Chrome Enterprise browser.
- **OS Firewall**: Indicates if the operating system firewall is enabled or disabled.
- **Cookie Domain ID**: The cookie domain ID. You can click the **Copy **icon to copy the ID to your clipboard, or click the **Filter **icon to filter the logs in the table by the specified cookie domain ID.
The Browser Version column sorts requests by the browser version in descending order. You can click the **Arrow** icon to sort the requests in ascending order, or you can click the **Filter **icon to filter the logs in the table by the specified browser version.
- []**Device Enrollment Domain**: The device enrollment domain for the browser version.
- **Password Protection Warning Trigger**: Indicates if the Password Protection Warning feature is enabled or disabled.
- **MAC Addresses**: The unique identifier of the Media Access Control (MAC) address for the browser version. You can click the **Copy **icon to copy the ID to your clipboard.
- **Serial Number**: The serial number for the browser version. You can click the **Copy **icon to copy the ID to your clipboard.
- **System DNS Servers**: The system DNS servers for the browser version.
The Operating System** **column sorts requests by the operating system in descending order. You can click the **Arrow **icon to sort the requests in ascending order, or you can click the click the **Filter **icon to filter the logs in the table by the specified operating system.
- []**Device Model**: The device model of the operating system (e.g., VMware7).
- **Device Manufacturer**: The device manufacturer of the operating system (e.g., VMWare, Inc.).
- **Key Trust Level**: The key trust level of the operating system (e.g., Chrome Browser OS Key).
- **CrowdStrike Agent**: Indicates if the CrowdStrike Agend software is enabled or disabled.
The Safe Browsing Protection Level column sorts requests by the Safe Browsing protection level in descending order. You can click the **Arrow** icon to sort the requests in ascending order, or you can click the **Filter **icon to filter the logs in the table by the specified browser version.
- []**Screen Lock Secured**: The screen lock security types (i.e., **Unspecified Secured Screen Lock**, **Unknown Secured Screen Lock**, **Enabled Screen Lock**, or **Disabled Screen Lock**).
- **Secure Boot Mode**: The Secure Boot mode (i.e., **Unspecified Secure Boot Mode**, **Unknown Secure Boot Mode**, **Enable Secure Boot Mode**, or **Disable Secure Boot Mode**).
- **Disk Encryption**: The disk encryption type (i.e., **Unspecified Disk Encryption**, **Unknown Disk Encryption**, **Disabled Disk Encryption**, or **Encrypted Disk Encryption**).
- **Device Affiliation IDs**: The device affiliation ID.
- **Device Enrollment Domain**: The device enrollment domain that the device is enrolled to.
[]![Using the Query Builder](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/accessing-chrome-enterprise-browser-diagnostics/zpa-chrome-enterprise-browser-diagnostics-query-builder.png)
[]![Viewing the data table in the Chrome Enterprise Browser diagnostics](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/accessing-chrome-enterprise-browser-diagnostics/zpa-chrome-enterprise-browser-diagnostics-data-table.png)