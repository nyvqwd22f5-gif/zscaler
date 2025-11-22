# Configuring a Location Template
Source: https://help.zscaler.com/cloud-branch-connector/configuring-location-template
PDF: https://help.zscaler.com/pdf/com/en/1420606.pdf

Within the Zscaler Cloud & Branch Connector Admin Portal, you can create location templates. The selected attributes in the template are applied to a [location](/cloud-branch-connector/about-locations). To learn more, see [About Location Templates](/cloud-branch-connector/about-location-templates).
To configure a location template:
- Go to **Administration** > **Location Templates**.
- Select **Add Location Template**.
The **Add Location Template** window appears.
[See image.](#image-addlctntmplte)
- In the **Add Location Template** window, enter a name for the location template in the **Name** field. This field is mandatory.
- Enter a prefix for the location template in the **Template Prefix** field. All locations created using this location template contain this prefix. This field is optional.
-
In the **Gateway Options** section:
- **Enable XFF Forwarding**: Enable this setting if you want the Zscaler service to use the X-Forwarded-For (XFF) headers that your on-premises proxy server inserts in outbound HTTP requests.
- **Enforce Authentication**: Enable this setting to require users from this location to authenticate to the service.
- **Enable Caution**: Enable this setting to display an end user notification for unauthenticated traffic. If you do not enable this setting, the action is treated as an allow policy.
- **Enable AUP**: Enable this setting to display an Acceptable Use Policy (AUP) for unauthenticated traffic and require users to accept it. If you enable this setting, the **Custom AUP Frequency (Days)** field appears. Enter in days how frequently the AUP is displayed to users.
- **Enforce Firewall Control**: Enable this setting to enable the service's firewall controls. If you enable this setting, the **Enable IPS Control** setting appears. Select this setting to enable Intrusion Prevention System (IPS) controls for the location template. To enable IPS controls, you must be subscribed to the advanced firewall SKU.
- **Enforce Bandwidth Control**: Enable this setting to enter the maximum bandwidth limits for Download (Mbps) and Upload (Mbps).
- (Optional) In the **Description** section, enter a description of the location template.
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]![Add Location Template window to add a location template in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-connector/administration/location-management/configuring-location-template/Add%20Location%20Template%20Brnch.jpg)