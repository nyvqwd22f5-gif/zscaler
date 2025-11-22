# Accessing API Protection Diagnostics
Source: https://help.zscaler.com/unified/accessing-api-protection-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1505496.pdf

You can view and filter API Protection data for API application access transactions.
Accessing API Protection Diagnostics
To view diagnostics for API Protection data:
- Go to **Logs **> **Insights** > **Diagnostics**.
- Under **Log Type**, choose **API Protection**.
By default, the detailed AppProtection control, AppProtection profile, and policy information are displayed that occurred in the last 24 hours. To change the time range, click the **Calendar** menu and select a preset range or specify a custom start and end date. If you use a **Custom Range**, the start date must be within the last 14 days. To change the time zone, click the current **Time Zone** button.
Click the refresh icon (![refresh%20icon.jpg](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/accessing-api-protection-diagnostics/refresh%20icon.jpg)
) to reflect the most current information on the diagnostics page.
[See image.](#logtype)
Viewing Logs
Log activity is automatically displayed after selecting the API Protection log type.
By default, the table displays the total number of API Protection transactions. You can change this by choosing one of the following filters:
- **Total Transactions**: The total number of API application access transactions.
- **Security Profile Violations**: The number of API application access transactions with security profile violations.
- **No Violations**: The number of API application access transactions with no security profile violations.
[See image.](#logs)
Filtering API Diagnostics
On the API Protection Diagnostics page, you can apply filters or drill down further into the log data using the Query Builder. By default, no filters are applied. If you want to view and filter User Status for real-time events, use [Live Logs](/unified/about-live-logs).
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu. To learn more, see AppProtection Filters below.
- Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Not Equals**, **Starts With**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains** operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
- Click **Apply**.
[See image.](#filters)
- To apply more filters, click **Add Filters** again or click the **Filter **icon (![Filter icon](/downloads/zpa/dashboard-diagnostics/about-web-inspection-diagnostics/zpa-inspection-diagnostics-filter-icon.png)
) within the table.
- To remove an added filter, click the **Close** icon and then click **Apply**.
- To remove all filters, click **Clear All**.
You can also click the **Copy** icon to save the filter query details. If you or another admin accesses **Diagnostics**, you can paste the query into the field by clicking the** Clipboard** icon.
[See image.](#copy)
API Protection Filters
You can add the following filters:
- **App Connector: Name**: See logs by a specific App Connector you’ve configured.
- **Application: Domain**: See logs by an application that resolves to a specific domain.
- **Application: Segment Name**: See logs by a specific application segment you’ve configured.
- **AppProtection Control: Action**: See logs by the API Protection control violation action (i.e., Allow, Block, or Redirect).
- **AppProtection Control: Category**: See logs by the list of categories (API Protection Controls, WebSocket Custom Controls, HTTP Custom Controls, WebSocket Predefined Controls, ThreatLabZ Predefined Controls, and OWASP Predefined Controls).
- **AppProtection Control: Name**: See logs by the API Protection control violation number and name (e.g., by ControlNumber:ControlName).
- **AppProtection Control: Severity**: See logs by the API Protection control violation severity rating (i.e., Critical, High, Medium, & Low).
- **AppProtection Profile: Name**: See logs by the API Protection profile violation name.
- **Connection: Connection ID**: See requests by the ID associated with the application request.
- **Contains Credit Card**: See logs by transactions that have detected credit card information. Zscaler doesn't store or display the credit card information details, only the transaction category is tracked.
- **Contains SSN**: See logs by transactions that have detected social security number information. Zscaler doesn't store or display the social security number itself or any other secure information details, only the transaction category is tracked.
- **Path**: See logs for a particular endpoint path.
- **Policy: AppProtection Policy Name**: See logs by the name of one or more specific AppProtection policies.
- **Request Method**: See logs by the API method (i.e., GET, POST, etc.).
- **Response Code**: See logs by the HTTP or HTTPS response code (error or success).
- **Source IP**: See logs by the source IP address.
- **URL**: See logs by the URL endpoint query parameters.
- **User Agent**: See logs by the profile of the user machine, operating system version, and web browser.
- **Username**: See logs by the user.
The table displays the following data for transactions. You can expand each row to see more details or click the **Expand**/**Collapse** icon to expand or collapse all rows within the table. By default, the table displays 20 transactions. You can scroll to load more transactions.
- [Transaction](#transaction)
- [AppProtection Control](#appcontrol)
- [AppProtection Profile](#appprofile)
- [User](#user)
- [Policy](#policy)
- []**Transaction Start Time**: The time the transaction started.
- **Transaction End Time**: The time the transaction ended.
- **Exchange ID**: The ID associated with the exchange.
- **Request Method**: The method of HTTP request in the transaction.
- **Certificate Name**: The name associated with the certificate.
- **Certificate ID**: The ID associated with the certificate.
- **Connection ID**: The ID associated with the transaction request. Click the **Copy** icon to copy this to your clipboard.
- **App Connector Name**: The name of the App Connector in the transaction request.
- **App Connector ID**: The internal ID of the App Connector in the transaction request. Click the **Copy** icon to copy this ID to your clipboard.
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
- **Control ID**: The ID of the AppProtection control violation.
- **Control Action**: The action of the AppProtection control violation (i.e., Allow, Block, or Redirect).
- **Control Severity**: The severity of the AppProtection control violation (i.e., Critical, High, Medium, & Low).
- **Control Category**: The category of the AppProtection control violation (i.e., OWASP Predefined Controls or Custom Controls).
- []**App Protection Profile Name**: The name of the AppProtection profile. Click the name to edit the AppProtection profile.
- **App Protection Profile ID**: The ID of the AppProtection profile. Click the **Copy** icon to copy this ID to your clipboard.
- **SSL Inspected**: Displays whether the AppProtection profile was SSL inspected or not.
- **Response Code**: The HTTP response code to the web request.
- []**Username**: The name of the user who initiated the transaction.
- **IP (Source)**: The source IP address of the machine that initiated the transaction.
- **Location**: The location of the Private Applications Public Service Edge or Private Service Edge used to connect the application to the user.
- **User Agent**: The profile of the user machine, operating system version, and web browser that initiated the transaction.
-
**User Metadata: **The metadata of the user who requested the application.
- **IdP Name**: The name of the IdP as configured in the Admin Portal.
- **IdP ID**: The ID associated with the IdP. You can click the **Copy** icon to copy the ID to your clipboard.
- **SAML Attributes **or** Session Attributes**: View, download, and copy the SAML attributes for the user:
- Click the **View Log** icon to display the SAML Attributes for the user within the Admin Portal.
- Click the **Download** icon to download the SAML attributes statement for the user to a text (.txt) file.
- Click the **Copy **icon to copy the SAML attribute statement for the user to your clipboard.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SAML Attributes** field is replaced with **Session Attributes**. The user attributes are populated from the ZIdentity Admin Portal and are used for defining various sign-on policies. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
- **SCIM Users** or **ZIdentity Users**: The user that is provisioned for SCIM.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SCIM Users** field is replaced with **ZIdentity Users**. The ZIdentity users are populated from the ZIdentity Admin Portal. To learn more, see [About Users](/zslogin/about-users) and [What Is ZIdentity?](/zslogin/what-zslogin)
- **SCIM Groups** or **User Groups**: The group that is provisioned for SCIM.
If you are subscribed to ZIdentity and have this feature enabled for your tenant, the **SCIM Groups** field is replaced with **User Groups**. The groups are populated from the ZIdentity Admin Portal. To learn more, see [About User Groups](/zslogin/about-user-groups) and [What Is ZIdentity?](/zslogin/what-zslogin)
- **Hostname**: The hostname of the user's device.
- **Platform**: The platform on the user's device.
- **Zscaler App Trusted Networks**: The names of the trusted networks accessible by the user's device.
- **Posture Profiles Verified**: If Zscaler Client Connector verified the user's device against the criteria specified in the posture profile, then a list of verified posture profiles are displayed for this field. If it displays **Unavailable**, there are no posture profiles to display.
- **Posture Profiles Unverified**: If Zscaler Client Connector was unable to verify the user's device against the criteria specified in the posture profile, then a list of unverified posture profiles are displayed for this field. If it displays **Unavailable**, there are no posture profiles to display.
- []**App Protection Policy Name**: The name of the AppProtection policy configured. Click the name to edit the AppProtection policy.
- **App Protection Policy ID**: The ID of the AppProtection policy configured. You can click the **Copy** icon to copy the ID to your clipboard.
- **Application Segment**: The name of the application segment in the transaction request. Click the name to [edit the application segment](/unified/editing-defined-application-segments). Click the **Configuration Graph** icon to view a flowchart of components connected to the application segment.
- **Application ID**: The ID of the application in the transaction request. You can click the **Copy** icon to copy this ID to your clipboard.
- **Application Domain**: The ID of the application in the transaction request. You can click the **Copy** icon to copy this ID to your clipboard.
Within the table, you can click the **Filter** icon next to certain field names in order to drill down further into the data. The filter query section within the page updates automatically to include the proper filter for the field name you selected and the applicable Boolean operator configuration for that field.
[See image.](#table)
[]![Time range and refresh icon for the API Protection Diagnostics page](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/accessing-api-protection-diagnostics/top%20area.jpg)
[]![Log totals for the API Protection diagnostics page](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/accessing-api-protection-diagnostics/logs.jpg)
[]![Filters for the API Protection Logs table on the API Protection diagnostics page](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/accessing-api-protection-diagnostics/Filter.png)
[]![The Copy and Clipboard icons on the API Protection Diagnostics page ](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/about-user-activity-diagnostics/copy%20and%20clipboard.jpg)
[]![Expanded view of the API Protection diagnostics table on the API Protection diagnostics page](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/accessing-api-protection-diagnostics/Updated%20expanded%20table%20view.jpg)