# Configuring a Cellular Quota with Zscaler Client Connector for Android
Source: https://help.zscaler.com/zscaler-client-connector/configuring-cellular-quota-zscaler-client-connector-android
PDF: https://help.zscaler.com/pdf/com/en/1340926.pdf

Zscaler ended support of bandwidth quota control for Zscaler Client Connector version 1.5.3 and later for Android.
For Android devices, you can define a monthly quota to ensure that cellular bandwidth is used for business applications only. The cellular quota is defined in [App Profiles](/zscaler-client-connector/configuring-zscaler-app-profiles).
The quota affects cellular data only. It does not affect Wi-Fi. You must allowlist your business applications to exempt them from the quota.
Before the quota is exceeded, users can use cellular data for both personal and business apps. Once the quota is met, users can only access cellular data for corporate apps (i.e., apps placed on the allowlist). Personal apps are not allowed to access the cellular data network, but they can still be used on Wi-Fi.
To configure the monthly cellular quota for Android devices:
- In the Zscaler Client Connector Portal, go to **App Profiles**.
- Select **Android**.
- Click **Add Android Policy** or edit an existing Android policy by clicking the **Edit **icon.
- Click the **Cellular Quota** tab.
- Click **Enable Quota on Cellular Network**.
- Configure the following options:
- **Enforce Quota Only For Roaming Users**: Select whether to enforce the quota only when users are roaming.
- **Monthly Billing Day**: Select a day of the month from the drop-down menu. This day is when the cellular quota is reset every month (e.g., if you select 1, the cellular quota is reset on January 1st, February 1st, March 1st, etc.).
- **Quota (MB)**: Specify the quota in MB. Enter a value from 1 to 10,000.
- **Wi-Fi SSID**: (Optional) Enter the SSID of your internal local-area network (WLAN) if you want to test and simulate data usage for that specific SSID.
- **Block Notification Message**: (Optional) Type in or paste text for the notification that appears when the quota is exceeded. You can enter HTML tags and images, as long as the image files are accessible from the internet.
- (Optional) Under **Android Applications on Allowlist**:
-
Add the apps’ identifiers, separated by commas, to exclude apps from the quota calculation. To find the app identifier, go to Google Play and navigate to the app’s details page. The identifier is listed after the `id `parameter in the details page’s URL.
For example, the URL for Zscaler Client Connector’s Google Play detail page is `https://play.google.com/store/apps/details?``id=zscaler.com.zscaler`
The identifier for Zscaler Client Connector is `zscaler.com.zscaler.`
- Click **Find Applications**.
- In the **Edit Applications List **window:
- View the applications under **Apps** **on Allowlist **list.
- Click the **Delete** icon for an application to remove it from **Apps on Allowlist**.
- Select applications from the **Preloaded Apps** list to add them back to **Apps on Allowlist**.
- Click **Save**.
The saved applications appear in the **Android Applications** on **Allowlist **section.
- Click **Save**.