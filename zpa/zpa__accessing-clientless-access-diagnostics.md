# Accessing Clientless Access Diagnostics
Source: https://help.zscaler.com/zpa/accessing-clientless-access-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1485616.pdf

You can view and filter Clientless Access data for past browser session events.
Accessing Clientless Access Diagnostics
To view diagnostics for clientless access:
- Go to **Analytics **> **Diagnostics**.
- Under **Log Type**, choose **Clientless Access**.
By default, the detailed activity for all clientless access is displayed for events that occurred in the last 24 hours. You can do the following:
- Click the **Calendar **drop-down menu to select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days.
- Click the **Time Zone** icon to change the time zone.
- Click the **Settings** icon to configure the [diagnostics settings](#settings).
Zscaler retains logs for rolling periods of at least 14 days during your subscription term. To learn more, see [Customer Logs and Data](/customer-logs-fair-use/zpa-customer-logs-and-data). You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/zpa/about-log-streaming). Data in the [dashboard](/zpa/dashboard-diagnostics) might be more recent than the data presented within Diagnostics for the same time range.
![Clientless Access Time Range](/downloads/zpa/dashboard-diagnostics/about-clientless-access-diagnostics/Log%20type.png)
Viewing Logs
Log activity is automatically displayed after selecting the Clientless Access log type.
By default, the table displays the **Total** number of clientless access requests made by monitored users. You can change this by choosing one of the following filters:
- **Requests with Fingerprints**: The total number of clientless access requests with fingerprints.
- **Requests with Fingerprints Changed**: The total number of clientless access requests with fingerprints that have changed over the specified time range.
![Clientless Access Total and Requests with Fingerprints](/downloads/zpa/dashboard-diagnostics/about-clientless-access-diagnostics/Table%20options.png)
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
Filtering Clientless Access Logs
On the Clientless Access page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied.
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu:
[View query builder filters:](#filters)
- Select an operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains** operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Adding filters to the Clientless Access Diagnostics page](/downloads/zpa/dashboard-diagnostics/about-clientless-access-diagnostics/Filter.png)
To apply more filters, click **Add Filters** again or click on the **Apply Filter **icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon then **Apply**. To remove all filters, click **Clear All**.
You can also click the **Copy** icon to save the filter query details. If you or another ZPA admin access **Diagnostics**, you can paste the query into the field by clicking the **Clipboard **icon.
![Copy and Clipboard icons in the filter section of the Clientless Access Diagnostics page](/downloads/zpa/dashboard-diagnostics/about-clientless-access-diagnostics/Copy%20clipboard%20icons.png)
The table displays the following data for Browser Protection requests:
- [Request](#Request)
- [User](#User)
- [Fingerprint](#Fingerprint)
- [Policy](#Policy)
[See image.](#clientlessaccess)
You can expand each row to see more details or click the Expand/Collapse icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- []**Application**: **Domain**: See requests for a specific application. Enter the FQDN or IP address of the application.
- **Application**: **Segment Name**: See requests by application segment name as configured in the ZPA Admin Portal.
- **Browser**: See requests for a specific browser. Enter the browser name.
- **Browser Fingerprint**: **Changed After Login**: See requests for a specific browser fingerprint that was changed after the monitored user logged in.
- **Browser Fingerprint**: **On Login**: See requests for a specific browser fingerprint that was changed when the user logged in.
- **Browser Fingerprint**: **Present**: See requests for a specific browser fingerprint that are currently present.
- **Browser Protection Policy**: **Name**: See requests that triggered a specific browser protection policy.
- **Browser Protection Profile**: **Name**: See requests for a specific browser protection profile name. Enter the browser protection profile name.
- **Connection**: **Connection ID**: See requests by the connection ID.
- **Domain ID**: See requests by the domain ID.
- **Operating System**: See requests by the operating system.
- **Session ID**: See requests by one-user login sessions. This filter shows all fingerprints captured for a given session. All fingerprints should be the same for all domains accessed by the user in the same session. If there is a change, it means attributes for the fingerprint have changed for the user (i.e., location, screen resolution, etc.).
- **User Agent**: See requests by the profile of the user machine, operating system version, and web browser.
- **User Email**: See requests by the email address of the monitored user.
[]The **Request** column sorts Browser Protection requests by the connection date and start time in descending order.
- **Transaction Start Time**: The date and time the transaction started.
- **Transaction End Time**: The date and time the transaction ended.
- **Request Method**: The method in which the browser request was made.
- **Connection ID**: The ID associated with the browser request. Click the **Copy** icon to copy the ID to your clipboard.
- **Clientless Log**: View, download, and copy the raw JSON for the request:
- Click the **View Log** icon to display the **Raw JSON** for the request within the ZPA Admin Portal.
- Click the **Download** icon to download the raw JSON for the request to a text (.txt) file.
- Click the **Copy icon** to copy the raw JSON text for the request to your clipboard.
- **Exporter Name**: The name of the exporter used for the request.
- []**User**: The email address of the user who requested the browser.
- **IP (Source)**: The IP address of the user's device.
- **Location**: The city and country the user is connecting from. If ZPA is unable to determine the user's location, then the private IP address is shown.
- **User Agent**: The profile of the user machine, operating system version, and web browser that initiated the transaction.
- **User Metadata**: The metadata of the user who requested the browser:
- **IDP Name**: The name of the IdP as configured in the ZPA Admin Portal.
- **IDP ID**: The ID associated with the IdP. Click the **Copy** icon to copy the ID to your clipboard.
- **SAML Attributes**: View, download, and copy the SAML attributes for the user:
- Click the **View Log** icon to display the SAML Attributes for the user within the ZPA Admin Portal.
- Click the **Download **icon to download the SAML attributes statement for the user to a text (.txt) file.
- Click the **Copy** icon to copy the SAML attribute statement for the user to your clipboard.
- **SCIM Users**: The name of the user as identified by the IdP.
- **SCIM Groups**: The name of the group as identified by the IdP.
- **Hostname**: The hostname of the user's device.
- **Platform**: The platform on the user's device.
- **Client Connector Trusted Networks**: The names of the trusted networks accessible by the user's device.
- **Posture Profiles Verified**: If Zscaler Client Connector verified the user's device against the criteria specified in the posture profile, then TBD is displayed for this field.
- []**Fingerprint Generated**: How the fingerprint was generated.
- **Browser Name**: The name of the browser that the user accessed for the request.
- **Operating System**: The operating system that was used for the request.
- **Mobile Device**: If a mobile device was used for the request, it shows as **True**. If a mobile device was not used for the request it shows as **False**.
- **Location**: The latitude and longitude of the fingerprint's location.
- **JA3**: The JA3 fingerprint. This field only shows if you selected the JA3 hash when [configuring Browser Protection Profiles](/zpa/configuring-browser-protection-profiles).
You might see different results based on the machine and browser you are using.
- []**Browser Protection Policy Name**: The name of the Browser Protection policy configured. Click the name to edit the AppProtection policy.
- **Browser Protection Policy ID**: The ID of the Browser Protection policy configured. Click the **Copy** icon to copy the ID to your clipboard.
- **Browser Protection Profile Name**: The name of the Browser Protection profile. Click the name to edit the Browser Protection profile.
- **Browser Protection Profile ID**: The ID of the Browser Protection profile. Click the **Copy** icon to copy this ID to your clipboard.
- **Application Segment**: The application segment name as configured in the ZPA Admin Portal. Click on the name to open the [Edit Application Segment window](/zpa/editing-application-segments), which includes the defined application.
- **Application ID**: The ID associated with the application. Click the **Copy **icon to copy the ID to your clipboard.
- **Application Domain**: The domain of the application in the transaction request.
- **User Portal**: The name, ID, and domain of the application segment. Click the **Copy** icon to copy the ID to your clipboard. When you select User Portal criteria, this field replaces the **Application Segment**, **Application ID**, and **Application Domain** fields.
[]![Clientless Access Diagnostics page within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/accessing-clientless-access-diagnostics/Clientless%20Access%20Diagnostics.png)