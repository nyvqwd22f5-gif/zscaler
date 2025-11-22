# Understanding Zscaler Hosted Monitoring
Source: https://help.zscaler.com/unified/understanding-zscaler-hosted-monitoring
PDF: https://help.zscaler.com/pdf/com/en/1509581.pdf

Zscaler Hosted Monitoring operates from within the Zscaler cloud infrastructure as a multi-tenant service. The service allows you to logically group Web and Cloud Path probes into independent collections to set up your own tests for monitoring performance. As an extension to Digital Experience Monitoring probes for predefined and custom applications, Zscaler Hosted Probes monitor the performance of a specific service or application directly from a Zscaler data center to an endpoint destination.
To access Zscaler Hosted Monitoring, make sure you've configured Zscaler Hosted Probes and met the feature prerequisites. To learn more, see [Configuring Zscaler Hosted Probes](/unified/configuring-zscaler-hosted-probes).
To access Zscaler Hosted Monitoring:
- Go to **Analytics **> **Digital Experience Mangagement** > **Reporting **> **Zscaler Hosted Monitoring**.
- Select a probe from a collection in the left-side navigation.
- Select the **Zscaler Hosted Locations** from the drop-down menu to specify the Zscaler data centers from where the probe is run. All locations are selected by default.
- Click **Apply**. The applicable probe charts are displayed for either a Web probe or Cloud Path probe.
[See image.](#select-filter-and-probes)
Setting a Time Range
Depending on the probe you've selected, charts are displayed by default for Availability and Page Fetch Time for Web probes, and End-to-End Latency for Cloud Path probes. The default time range for the initial chart on the page is the previous 30 days. Each subsequent chart reflects the time range and metrics reflected by the [time range widget](#Using_the_Time_Range_Widget).
[]Using the Time Range Widget
You can customize the time range to capture a subset of metrics. As you move, expand, or shorten the widget's time range, the identical time range is reflected within the chart for Page Fetch Time (Web probe) or End-to-End Latency (Cloud Path probe):
- Select one side of the widget to expand or shorten a specific time range.
- Select the middle of the widget to move it to a specific time range.
The minimum time range for the widget is 2 hours, and the maximum time range is 48 hours. The default time range of the widget is 24 hours.
[See image.](#time-range-widget)
Monitoring Web Probe Metrics
For Web probes, **Availability **and **Page Fetch Time** metrics are automatically displayed.
Metrics for Availability
The **Availability **chart provides the following metrics:
- **Month To Date (MTD)**: The average availability from the first day of the month to the current date, along with a percentage increase or decrease from the previous month.
- **Past 30 Days**: The average availability within the past 30 days, along with a percentage increase or decrease from the prior 30 days.
- **Time range from widget**: The average availability within your designated time range, along with a percentage increase or decrease from the prior 30 days.
[See image.](#web-availability)
Metrics for Page Fetch Time
The **Page Fetch Time **chart provides the following metrics and actions:
- Click any data point to view metrics for the hosted locations.
- Select the drop-down menu to incrementally add Web probe metrics and charts to Page Fetch Time. To learn more about Web probe metrics, see [About Probes](/unified/about-probes) and [Evaluating User Details](/unified/evaluating-user-details).
- Click the chart format icon to switch views between a line chart and a scatter chart. Each data point within a scatter chart represents an individual probe run.
[See image.](#web-pft)
Key Metrics
To view granular metrics for the Web probe:
- Click the chart format icon to ensure the scatter chart is displayed for Page Fetch Time.
- Hover over a data point to view metrics for the hosted location.
- Click **View Details**.
[See image.](#select-web-view-details)
The following key metrics are provided in milliseconds on the probe details page:
- **Redirect Time**: The time measurement of traffic redirects.
- **DNS**: The resolution time for the DNS name.
- **TCP**: The time measurement of the Transmission Control Protocol.
- **SSL Handshake**: The communication time to the device.
- **Server Response Time**: The Time to First Byte (TTFB).
- **Page Fetch Time**: The time it takes the application to load a page for the user.
[See image.](#granular-web-probe-details-page)
Request sizes are delineated for Download, Header, and the HTTP Request in milliseconds. A percentage increase or decrease accompanies each metric, based on an hourly average.
Server redirect information is also provided per URL:
- **URL**: The redirected URL.
- **Response Code**: The HTTP informational or success code.
- **Timing Information**: The distribution of individual key metrics for each URL, in milliseconds.
Monitoring Cloud Path Probe Metrics
For Cloud Path probes, **End-to-End Latency** metrics are automatically displayed.
Metrics for End-to-End Latency
The **End-to-End Latency **chart provides the following metrics and actions:
- Click any data point to view metrics for the hosted locations.
- Select the drop-down menu to incrementally add Cloud Path probe metrics and charts to End-to-End Latency. To learn more about Cloud Path probe metrics, see [About Probes](/unified/about-probes) and [Evaluating the Cloud Path](/unified/evaluating-cloud-path).
- Click the chart format icon to switch views between a line chart and a scatter chart. Each data point within a scatter chart represents an individual probe run.
[See image.](#cp-ee-latency-actions)
Key Metrics
To view granular metrics for the Cloud Path probe:
- Click the chart format icon to ensure the scatter chart is displayed for End-to-End Latency.
- Hover over a data point to view metrics for the hosted location.
- Click **View Details**.
[See image.](#select-cp-view-details)
The following key metrics are provided on the probe details page:
- **End-to-End Latency**: The time to send a data packet from source to destination, including hops between legs in the Cloud Path.
- **Packet Loss**: When data packets that travel across a network fail to reach their destination.
- **Jitter**: The variance in time delay between data packets over a network.
[See image.](#granular-cp-probe-details-page)
Cloud Path Visualization
A Cloud Path representation is provided for the specified Cloud Path probe. This visualization consolidates all hosted locations into one image. Hover over any leg in the path to view route details.
[See image.](#cp-visualization-hop-view)
To learn more about the visualization of data traffic, see [Evaluating the Cloud Path](/unified/evaluating-cloud-path).
[]![Select filter locations and probe](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-locations-filter.png)
[]![Time range widget](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-time-widget.png)
[]![Web probe availability chart](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-web-availability.png)
[]![Example of Page Fetch Time chart](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-web-pft2.png)
[]![Link to view granular details of Web probe](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-web-pft-view-details.png)
[]![Web probe granular details page](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-granular-details-page.png)
[]![Example of End-to-End Latency chart](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-cp-ee-latency-actions.png)
[]![Link to view granular details of Cloud Path probe](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-cp-latency-view-details.png)
[]![Cloud Path probe granular details page](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-cp-granular-details-page.png)
[]![Cloud Path Hop View](/downloads/zdx/analytics/understanding-zscaler-hosted-monitoring/zdx-zprobe-monitoring-cp-visualization.png)