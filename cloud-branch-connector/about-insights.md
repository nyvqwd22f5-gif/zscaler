# About Insights
Source: https://help.zscaler.com/zia/about-insights
PDF: https://help.zscaler.com/pdf/com/en/1401021.pdf

[Watch a video about Insights & Dashboards.](https://fast.wistia.net/embed/iframe/hn1697gbbr)
The Insights page is where you can view and define traffic information that you want to view when analyzing traffic through charts. To learn more about how to analyze your traffic on the Insights pages, see [Analyzing Traffic Using Insights](/zia/analyzing-traffic-using-insights).
The Insights pages provide the following benefits and enable you to:
- View insights for each transaction processed by Zscaler on any chart type of your choice.
- Quickly drill down on insights with the help of multiple filters and operators available.
You can view insights for the following:
- Web
- Mobile
- Firewall
- DNS
- Tunnel
- [Threat](/zia/about-threat-insights) (different from the other Insights pages)
- [SaaS Security](/zia/saas-security-insights)
- Endpoint Data Loss Prevention (DLP)
- Email DLP
- Extranet
Zscaler Support can view Tunnel Insights even if [remote assistance](/zia/about-remote-assistance) is disabled.
About the Insights Pages
To view Insights, go to **Analytics** and choose the Insights page you want to view.
- Clear all filters.
- Click to show or hide the left pane.
- Print the entire sequence of charts in the history bar.
- Choose a predefined time frame or select **Custom** to use the calendar and time menus to define your own time frame. In **Custom**, the end date can be up to 92 days after start date. Selecting multiple days results in seeing the sum of bytes/transactions per day in whichever chart type you select.
- Define data types. To view Insights data types for specific categories, see the articles listed in #7.
- For certain data types, you can choose to view the top 5, 10, 25, 50 or 100 items. For example, you can view the top 5 or 100 domains that were visited by your users. This option is available in bar charts and tables only.
- In trend and pie charts, you'll only see the top 5 items. The **Other** category refers to the rest of the data types not in the top 5.
- View the chart and interactively drill down for more information.
- Narrow down the data scope by applying filters. Each data type has its own set of filters. See the articles listed in #7.
- To get more information about a specific item in a chart, hover and click it, and then choose a data type.
- View logs for a specific item in the chart. Hover and click it, and then choose **View Logs**.
- Select a chart type.
- View the data as **Units**, **Metrics** (in Tunnel Insights only), and **Time** (for Domain and URL Host only).
- Define filters. Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. To view Insights filters for specific traffic types, see the following articles:
- [Web Data Types and Filters](/zia/web-data-types-and-filters)
- [Mobile Data Types and Filters](/zia/mobile-data-types-and-filters)
- [Firewall Data Types and Filters](/zia/firewall-data-types-and-filters)
- [DNS Data Types and Filters](/zia/dns-data-types-and-filters)
- [Tunnel Data Types and Filters](/zia/tunnel-data-types-and-filters)
- [Endpoint DLP Data Types and Filters](/zia/endpoint-dlp-data-types-and-filters)
- [Email DLP Data Types and Filters](/zia/email-dlp-data-types-and-filters)
- [Extranet Data Types and Filters](/zia/extranet-data-types-and-filters)
There are certain filter combinations that won't appear together in Insights, but appear together in Insights Logs. For example, the** Department** and **Location** filters don't appear together in Insights, but appear together in Insights Logs when applied.
- Always click **Apply Filters** to activate your changes.
- View your workflow in the history bar.
As you work with your data, the History bar records the workflow. Each time you make a change to the chart (e.g., add a filter or change the chart type), the portal adds the previous version to the history bar. You can then click any chart in the history bar to see it again. If you view an earlier version and change it, all subsequent versions are automatically deleted. This enables an administrator to review the various stages of the investigation and change direction for the analysis upon review, if necessary. The history bar can retain up to 50 versions of the chart. If there are more than 50 versions, the portal deletes the oldest versions as new ones are added. The chart icons are numbered, so you can track how many versions you have. You can delete charts from your workflow.
- View the weblog time, which appears at the bottom of every window. The Nanolog servers collect the logs of all users worldwide, and then consolidates and correlates them. The weblog time displays the date and time of the logs that are being processed by the Nanolog servers.
- Go to the [Insights Logs page](/zia/about-insights-logs).
![The Web Insights page with different labeled parts](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/about-insights/ZIA-6.1-Web-Insights_2.png)