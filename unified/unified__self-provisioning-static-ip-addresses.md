# Self-Provisioning of Static IP Addresses
Source: https://help.zscaler.com/unified/self-provisioning-static-ip-addresses
PDF: https://help.zscaler.com/pdf/com/en/1495261.pdf

You can self provision your static IP address to connect to the Zscaler service via the Admin Portal. To learn more, see [About Static IP](/unified/about-static-ip).
To configure the self-service static IP address from the Admin Portal:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Static IPs & GRE Tunnel**.
- Click **Add Static IP**. The** Add Static IP Configuration** wizard opens. If you edit an existing configuration, the **Edit Static IP Configuration** wizard opens.
- Under the **Source IP** tab:
- **Static IP Address**: &amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;gt;
Enter the static IP address that you want to provision with the Zscaler service. You cannot modify this field if you are editing an existing configuration.
- **Description**: &amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;gt;
(Optional) Enter additional information or note about the static IP address.
- **Managed By**: Select if the static IP address is managed by self or a specific Zscaler partner.
- Click **Next**.
- Under the **Region** tab:
- **Automatic**: Choose this option if you want to auto-discover the region and the coordinates based on the IP address.
- **Manual**: Choose this option to manually provide the co-ordinates or the region.
- **City**: Enter a region or search for the city you want to map the IP address to. Selecting a city from this field auto-fills the latitude and longitude information.
- **Latitude**: &amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;gt;
Enter the latitude of the region you want to map the static IP address to.
- **Longitude**: &amp;lt;!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--&amp;gt;
Enter the longitude of the region you want to map the static IP address to.
- Click **Next**.
- From the **Review** tab, review and edit your configurations if you want to change any of the values.
- Click **Save** and activate the change.