# Accessing AppProtection Diagnostics
Source: https://help.zscaler.com/unified/accessing-appprotection-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1496456.pdf

You can view and filter AppProtection data for past AppProtection events.
To view diagnostics for AppProtection data:
- Go to **Logs **> **Insights** > **Diagnostics**.
- Under **Log Type**, choose **AppProtection**.
By default, the detailed AppProtection profile and policy information for all AppProtection events are displayed for events that occurred in the last 24 hours. You can do the following:
- Click the **Calendar **drop-down menu to select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days.
- Click the **Time Zone** icon to change the time zone.
- Click the **Settings **icon to configure the [diagnostics settings](#settings).
Zscaler retains logs for rolling periods of at least 14 days during your subscription term. You can also view your logs or stream logs in real time using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service). The data in the dashboard might be more recent than the data presented within Diagnostics for the same time range.
[See image.](#SeeImage)
Viewing Logs
Log activity is automatically displayed after selecting the AppProtection log type.
By default, the table displays the **Total** number of AppProtection transactions. You can change this by choosing one of the following filters:
- **Total Transactions**: The total number of transactions.
- **Security Profile Violations**: The number of transactions with security profile violations.
- **No Violations**: The number of transactions with no security profile violations.
[See image.](#SeeImage2)
[]Configuring Settings
To configure settings for diagnostics pages in the ZPA Admin Portal:
- Go to **Logs** > **Insights** > **Diagnostics**.
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
Filtering AppProtection Diagnostics
On the AppProtection Diagnostics page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter User Status for real-time events, use [Live Logs](/unified/about-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu. To learn more, see [AppProtection Filters](#WebInspectionFilters) below.
- Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains **operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
![Filtering the AppProtection Diagnostics](/downloads/zpa/dashboard-diagnostics/about-web-inspection-diagnostics/zpa-web-inspection-diagnostics-filters.png)
- To apply more filters, click **Add Filters** again or click the **Apply Filter **icon (![Filter icon](/downloads/zpa/dashboard-diagnostics/about-web-inspection-diagnostics/zpa-inspection-diagnostics-filter-icon.png)
) within the table.
- To remove an added filter, click the **Close** icon and then click **Apply**.
- To remove all filters, click **Clear All**.
You can also click the **Copy **icon to save the filter query details. If you or another admin accesses **Diagnostics**, you can paste the query into the field by clicking the **Clipboard** icon.
[See image.](#SeeImage3)
[]AppProtection Filters
You can add the following filters:
- **API Discovery**: See logs for API Discovery. You can set the API Request and API Discovery filters within it to **True** or **False**.
- **API Request**: See logs by the API request.
- **API Style**: See logs based on the API style format. You can set the API Request and API Discovery filters within it to **True** or **False**.
- **App Connector: Name**: See logs by a specific App Connector you’ve configured.
- **Application: Domain**: See logs by an application that resolves to a specific domain.
- **Application: Segment Name**: See logs by a specific application segment you’ve configured.
- **Connection: Connection ID**: See requests by the ID associated with the application request.
- **AppProtection Control: Action**: See logs by the AppProtection control violation action (i.e., Allow, Block, or Redirect).
- **AppProtection Control: Category**: See logs by the list of categories in the WebSocket Custom Controls, HTTP Custom Controls, WebSocket Predefined Controls, ThreatLabZ Predefined Controls, and OWASP Predefined Controls.
- **AppProtection Control: Name**: See logs by the AppProtection control violation number and name (e.g., by ControlNumber:ControlName).
- **AppProtection Control: Severity**: See logs by the AppProtection control violation severity rating (i.e., Critical, High, Medium, & Low).
- **AppProtection Profile: Name**: See logs by the AppProtection profile violation name.
- **AuthN Type**: See logs by a particular authorization type.
- **Machine Tunnel**: See requests from Machine Tunnel users.
- **Path**: See logs for a particular endpoint path.
- **Policy: AppProtection Policy Name**: See logs by the name of one or more specific AppProtection policies.
- **Request Method**: See logs by the API method (i.e., GET, POST, etc.).
- **Sensitive Information**: See logs for specific types of sensitive information:
- **AWS-ACCESS-KEY**: Access key for AWS
- **CREDIT-CARD**: Credit card number
- **GCP-API-KEY**: API key for Google Cloud database
- **CPF**: Brazilian CPF number
- **FACEBOOK-ACCESS-TOKEN**: Access token for Facebook
- **SSN**: Social Security number
- **Source IP**: See logs by the source IP address.
- **User Agent**: See logs by the profile of the user machine, operating system version, and web browser.
- **Username**: See logs by the user.
If you are using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service), be aware that the ZPA LSS Client user represents the LSS service, not an actual user. By default, Diagnostic information for the ZPA LSS Client is captured but not displayed. You must explicitly select this user from the User field in order to display its log information. Each log receiver is displayed as an application, to reflect the data coming in from the service. To learn more, including how to stop the LSS service from streaming ZPA LSS Client logs, see [Configuring a Log Receiver](/unified/configuring-log-receiver).
The table displays the following data for transactions. You can expand each row to see more details or click the **Expand/Collapse **icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- [Transaction](#Transaction)
- [AppProtection Control](#InspectionControl)
- [AppProtection Profile](#InspectionProfile)
- [User](#User)
- [Policy](#Policy)
- []**Transaction Start Time**: The time the transaction started.
- **Transaction End Time**: The time the transaction ended.
- **Exchange ID**: The ID associated with the exchange.
- **Request Method**: The method of HTTP request in the transaction.
- **Certificate Name**: The name associated with the certificate.
- **Certificate ID**: The ID associated with the certificate.
- **Connection ID**: The ID associated with the transaction request. Click the **Copy** icon to copy this to your clipboard.
- **App Connector Name**: The name of the App Connector in the transaction request.
- **App Connector ID**: The internal ID (created by Private Applications) of the App Connector in the transaction request. Click the **Copy** icon to copy this ID to your clipboard.
- **Connection Status Log**: View, download, and copy the raw JSON for the request:
- Click the **View** icon to view details about the connection status log in JSON format.
- Click the **Download** icon to download this JSON file.
- Click the **Copy** icon to copy the raw JSON text for the request to your clipboard.
- **Processing Times**: The time to complete the transaction request listed in milliseconds.
- **Request Header**: The time to send the HTTP request header.
- **Request Body**: The time to send the HTTP request body.
- **Response Header**: The time to receive the HTTP response header.
- **Response Body**: The time to receive the HTTP response body.
- []**Control Name**: The name of the AppProtection control violation.
- **Control Action**: The action of the AppProtection control violation (i.e., Allow, Block, or Redirect).
- **Control ID**: The ID of the AppProtection control violation.
- **Control Severity**: The severity of the AppProtection control violation (i.e., Critical, High, Medium, & Low).
- **Control Category**: The category of the AppProtection control violation (i.e., OWASP Predefined Controls or Custom Controls).
- **Execution Flow**: The execution of multiple AppProtection control violations within a profile. AppProtection control violations are listed in chronological order and displayed by number, name, action, severity, and category.
If access is blocked by control 200005, go to the [AppProtection Profile](/unified/about-appprotection-profiles) page and [edit the specific AppProtection profile](/unified/editing-appprotection-profiles). Click** Next** on each tab without editing anything, then click **Save**. This specific control violation is then prevented. Repeat this process for the rest of your AppProtection profiles to avoid this same control violation.
- []**AppProtection Profile Name**: The name of the AppProtection profile. Click the name to edit the AppProtection profile.
- **AppProtection Profile ID**: The ID of the AppProtection profile. Click the **Copy** icon to copy this ID to your clipboard.
- **SSL Inspected**: Displays whether the AppProtection profile was SSL inspected or not.
- **Response Code**: The HTTP response code to the web request.
- []**Username**: The name of the user who initiated the transaction.
- **IP (Source)**: The source IP address of the machine that initiated the transaction.
- **User Agent**: The profile of the user machine, operating system version, and web browser that initiated the transaction.
- **User Metadata**: The metadata of the user who requested the application:
- **IdP Name**: The name of the IdP as configured in the Admin Portal.
- **IdP ID**: The ID associated with the IdP. You can click the **Copy** icon to copy the ID to your clipboard.
- **SAML Attributes**: View, download, and copy the SAML attributes for the user:
- Click the **View Log** icon to display the SAML Attributes for the user within the Admin Portal.
- Click the **Download **icon to download the SAML attributes statement for the user to a text (.txt) file.
- Click the **Copy** icon to copy the SAML attribute statement for the user to your clipboard.
- **SCIM Users**: The name of the user as identified by the IdP.
- **SCIM Groups**: The name of the group as identified by the IdP.
- **Hostname**: The hostname of the user's device.
- **Platform**: The platform on the user's device.
- **Zscaler App Trusted Networks**: The names of the trusted networks accessible by the user's device.
- **Posture Profiles Verified**: If Zscaler Client Connector verified the user's device against the criteria specified in the posture profile, then a list of verified posture profiles are displayed for this field. **Unavailable** means that there are no posture profiles to display.
- **Posture Profiles Unverified**: If Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile, then a list of unverified posture profiles are displayed for this field. **Unavailable** means that there are no posture profiles to display.
- []**AppProtection Policy Name**: The name of the AppProtection policy configured. Click the name to edit the AppProtection policy.
- **AppProtection Policy ID**: The ID of the AppProtection policy configured. You can click the **Copy** icon to copy the ID to your clipboard.
- **Application Segment**: The name of the application segment in the transaction request. Click the name to [edit the application segment](/unified/editing-defined-application-segments). Click the **Configuration Graph** icon to view a flowchart of components connected to the application segment.
- **Application ID**: The ID of the application in the transaction request. You can click the **Copy** icon to copy this ID to your clipboard.
- **Application Domain**: The domain of the application in the transaction request.
Within the table, you can click the **Apply Filter **icon next to certain field names in order to drill down further into the data. The filter query section within the page updates automatically to include the proper filter for the field name you selected and the applicable Boolean operator configuration for that field.
[]![AppProtection Diagnostics log type](/downloads/zpa/dashboard-diagnostics/about-web-inspection-diagnostics/Log%20Type%20highlight.png)
[]![Viewing AppProtection Diagnostics Logs](/downloads/zpa/dashboard-diagnostics/about-web-inspection-diagnostics/Totaltrans%20highlight.png)
[]![Using AppProtection Diagnostics Filter Tools](/downloads/zpa/dashboard-diagnostics/about-web-inspection-diagnostics/zpa-web-inspection-diagnostics-filter-tools.png)