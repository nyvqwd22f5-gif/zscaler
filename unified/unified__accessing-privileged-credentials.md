# Accessing Privileged Credentials
Source: https://help.zscaler.com/unified/accessing-privileged-credentials
PDF: https://help.zscaler.com/pdf/com/en/1530958.pdf

You can view and filter data for privileged credentials that were created to provide access to Privileged Remote Access (PRA) Portals. To view privileged credential data, go to Logs > Insights > Privileged Remote Access > Credentials.
Credentials Tools
The Credentials page displays the following information and functionality:
- **Time Range Filter**: View privileged credential data over a period between 1 hour and 365 days. To change the time range, click the **Calendar** menu and select a preset range or select **Custom Range**. If you use **Custom Range**, the start date must be within the last 365 days. The end date automatically sets to the system's current time. To change the time zone, click the current **Time Zone** button. This filter applies to all widgets on the Credentials page. By default, the detailed activity for all privileged credentials that occurred in the last 24 hours.
- **Refresh Icon**: Refresh the dashboard to reflect the most current information.
![Credentials tools on the Credentials page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/privileged-remote-access-monitoring/accessing-privileged-credentials/unified-logs-insights-privileged-credentials-tools.png)
Viewing Credentials
By default, the table displays the total credentials created in the Admin Portal. You can change this by choosing one of the following filters:
- **SSH**: The total number of used privileged credentials that are SSH enabled.
- **RDP**: The total number of used privileged credentials that are RDP enabled.
- **VNC**: The total number of used privileged credentials that are VNC enabled.
- **RealVNC**: The total number of used privileged credentials that are RealVNC enabled.
![Credentials total widgets displayed on the Credentials page in the Admin Porta](/downloads/zpa/dashboard-diagnostics/privileged-remote-access-monitoring/accessing-privileged-credentials/unified-logs-insights-privileged-credentials-widgets.png)
Filtering Credentials
You can apply filters or drill down further into the privileged credential data using the Query Builder. By default, no filters are applied.
- **Credential Pool**: See requests for a particular privileged credential pool.
- **Policy**: See requests for a particular privileged credential policy rule.
To configure filters using the Query Builder:
- Click **Add Filters** and select a filter from the drop-down menu. The ampersand (&) character cannot be used in the **Add Filters** field.
- Select an operator from the drop-down menu (e.g., **Contains**). The operators available are determined by the filter you are configuring.
Filters using the Contains operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., 137; 138; 139). When configuring multiple text entries and using the Less Than operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the Greater Than operator, the results show transactions starting from the smallest entry provided.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
![Adding filters to the Credentials table on the Credentials page within the Admin Portal](/downloads/zpa/dashboard-diagnostics/privileged-remote-access-monitoring/accessing-privileged-credentials/unified-logs-insights-privileged-credentials-filter.png)
- Click **Apply**.
To apply more filters, click **Add Filters** again. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field. The ampersand (&) character cannot be used in the **Add Filters** field.
To remove an added filter, click the** Close** icon then click **Apply**. To remove all filters, click **Clear All**.
The table displays the following data for privileged credentials:
- **Credential Pool**: The name of the privileged credential pool. When you click on a privileged credential pool you can see the following information for privileged credentials currently being used:
- **Credential**: The name of the privileged credential.
- **Console**: The privileged console associated with the privileged credential.
- **Portal**: The privileged portal assigned to the privileged credential.
- **Protocol**: The protocol assigned to the privileged credential.
- **Username**: The username used to log in to the privileged credential.
- **Policy**: The name of the privileged credentials policy assigned to the privileged credential pool.
- **Used Credentials**: The amount of privileged credentials that are currently being used from that privileged credential pool.
- **Total Credentials**: The total amount of privileged credentials within that privileged credential pool.
![Credentials table on the Credentials page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/privileged-remote-access-monitoring/accessing-privileged-credentials/unified-logs-insights-privileged-credentials-table.png)