# Configuring Acceptable Use Policy for Zscaler Client Connector
Source: https://help.zscaler.com/unified/configuring-acceptable-use-policy-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1491886.pdf

You can create an Acceptable Use Policy (AUP) that your users must accept before they can connect to the internet or access your organization's internal resources from devices protected by Zscaler Client Connector.
To configure an AUP:
- In the Admin Portal, go to **Policies > Common Configuration > Resources > Client Connector Notifications**.
- On the **Acceptable Use Policy (AUP) Settings** page:
- **Configure AUP Frequency**: Choose how often Zscaler Client Connector displays the AUP.
- Never
- After User Enrollment
- Daily
- Weekly
- Custom
- **Custom Days**: &amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;gt;
This field only appears if you select Custom as the AUP frequency. Enter any value from 1 to 180 days.
- **Configure AUP Message**: Enter or copy and paste your organization's AUP into the field. You can enter static HTML tags as well as images, as long as the image files are accessible from the internet.
- **Preview AUP Message**: Click to view the AUP as your users will see it.
![The Acceptable Usage Policy (AUP) Settings tab in the Zscaler Client Connector Portal](/downloads/client-connector/administration/zscaler-client-connector-notifications/configuring-acceptable-use-policy-zscaler-app/Client-Connector-Notifications-AUP-Settings.png)
- Click **Save**.
To learn more about other Zscaler Client Connector Notifications features, see [About Zscaler Client Connector Notifications](/unified/about-zscaler-client-connector-notifications).