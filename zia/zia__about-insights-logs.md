# About Insights Logs
Source: https://help.zscaler.com/zia/about-insights-logs
PDF: https://help.zscaler.com/pdf/com/en/1400986.pdf

The Zscaler service performs global time-ordered log consolidation, with potential latency ranging from several seconds to a few minutes, so you can view every transaction that your users perform regardless of where they are in the world.
Logs are stored for 180 days in the Zscaler Nanolog servers. Zscaler also offers the [Nanolog Streaming Service](/zia/understanding-nanolog-streaming-service) (NSS), a virtual machine (VM) that can stream web traffic logs in real time from the Zscaler Nanolog to your security information and event management (SIEM) system, such as Splunk, enabling real-time alerting, correlation with the logs of your firewall and other devices, and long-term local log archival. Contact the Zscaler Account team or Zscaler Support for more information on subscribing to NSS.
The Insights Logs pages provide the following benefits and enable you to:
- View logs for each transaction processed by Zscaler.
- Quickly access the desired logs with the help of multiple filters and operators when troubleshooting.
Interactive reports support UTF-8 characters, enabling the display of special characters.
You can view logs for the following:
-
**Web**: View transactions initiated from any device (e.g., Windows, Mac, Mobile Devices, etc.). You can view the Page Risk Index score for each URL requested, the number of bytes sent and received, and more.
You can view the logs for messages that triggered the inline DLP rules in the Web Insights Logs for Webex.
- **Mobile**: View transactions initiated from the browsers of mobile devices only. The logs appear based on the device OS. You can view the Page Risk Index score for each URL requested, the number of bytes sent and received, and more.
- **Firewall**: View details such as the rule that was applied, the client and server details, and the network services and applications.
- **DNS**: View data, such as the DNS request and response details.
- **Tunnel**: View data about GRE and IPSec tunnels, such as their health, status, and authentication and encryption algorithms.
- [SaaS Security](/zia/saas-security-insights-logs): View every scan performed by the Zscaler SaaS Connector of the data based on your SaaS application tenant.
- **Endpoint DLP**: View activities specific to Endpoint Data Loss Prevention (DLP).
- **Email DLP Insights**: View insights into Email Data Loss Prevention (DLP).
- **Extranet**: View insights into extranets.
Zscaler Support can view Tunnel Insights even if [Remote Assistance](/zia/about-remote-assistance) is disabled.
About the Insights Logs Pages
On the Insights Logs pages** **(Analytics > choose the Insights page you want to view logs for** **> Logs), you can do the following:
- Clear all filters. You'll be directed back to the default Insights page.
- Click to show or hide the left pane.
- Choose a predefined time frame or select **Custom** to use the calendar and time menus to define your own time frame. In **Custom**, the end date can be up to 92 days after start date.
- View the transactions in a log table. You can search for specific entries wherever you see a magnifying glass on a column field name. You can also sort certain columns by ascending or descending order. To customize the column fields:
- Click the icon (#5) on the top right of the logs to list the available fields for display. Tick a box to add a column or clear it to remove a column. Alternatively, click **Select all** or **Deselect all** to display or remove all columns.
- Drag a column to another location.
- Resize a column by positioning the cursor on its border and dragging it to the desired width.
- Customize your log view by selecting or deselecting which column fields you want to see. To view Insights Logs column fields for specific categories, see the following articles:
- [Web Insights Logs: Columns](/zia/web-insights-logs-columns)
- [Mobile Insights Logs: Columns](/zia/mobile-insights-logs-columns)
- [Firewall Insights Logs: Columns](/zia/firewall-insights-logs-columns)
- [DNS Insights Logs: Columns](/zia/dns-insights-logs-columns)
- [Tunnel Insights Logs: Columns](/zia/tunnel-insights-logs-columns)
- [Endpoint DLP Insights Logs: Columns](/zia/endpoint-dlp-insights-logs-columns)
- [Email DLP Insights Logs: Columns](/zia/email-dlp-insights-logs-columns)
- [Extranet Insights Logs: Columns](/zia/extranet-insights-logs-columns)
- Apply filters to narrow down the list or to find transactions, such as those associated with a specific user or URL.
Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Also, certain filters support additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform string match, like **Threat Category** and others.
To view Insights Logs filters for specific traffic types, see the following articles:
- [Web Insights Logs: Filters](/zia/web-insights-logs-filters)
- [Mobile Insights Logs: Filters](/zia/mobile-insights-logs-filters)
- [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters)
- [DNS Insights Logs: Filters](/zia/dns-insights-logs-filters)
- [Tunnel Insights Logs: Filters](/zia/tunnel-insights-logs-filters)
- [Endpoint DLP Insights Logs: Filters](/zia/endpoint-dlp-insights-logs-filters)
- [Email DLP Insights Logs: Filters](/zia/email-dlp-insights-logs-filters)
- [Extranet Insights Logs: Filters](/zia/extranet-insights-logs-filters)
There are certain filter combinations that appear together in Insights Logs when applied, but won't appear together in Insights. For example, the **Department** and **Location** filters appear together in Insights Logs when applied, but won't appear together in Insights.
- You can either download the list of transactions as a CSV file or keep it displayed on your screen. When you download the list, the Zscaler service only exports visible columns. It exports up to 100K lines of data at a time. You can continue to use the service while the export is in progress. The limit for the number of times you can export is 20 requests/hour. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zia/ranges-limitations#Reporting).
For URL-based column values in the Logs display and CSV files, there is a character limit of 2,041 in the sub-URL string. For example, in www.zscaler.com/index.html, www.zscaler.com is the domain and /index.html is the sub-URL. If the sub-URL exceeds the 2,041 character limit, it is truncated. This does not affect the behavior or functionality of the URL.
- Choose the number of records that you want displayed on the page.
- Always click **Apply Filters** to activate your changes.
- View the weblog time, which appears at the bottom of every window. The Nanolog servers collect the logs of all users worldwide, and then consolidate and correlate them. The weblog time displays the date and time of the logs that are being processed by the Nanolog servers.
- Go to the [Insights page](/zia/about-insights).
![The Web Insights Logs page with different labeled parts](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/logs/about-insights-logs/web_insights_logs_page.png)