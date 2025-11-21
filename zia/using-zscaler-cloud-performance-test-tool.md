# Using the Zscaler Cloud Performance Test Tool
Source: https://help.zscaler.com/zia/using-zscaler-cloud-performance-test-tool
PDF: https://help.zscaler.com/pdf/com/en/1402306.pdf

The Zscaler Cloud Performance Test is a browser-based tool for collecting performance troubleshooting information for end users when connecting to the internet through the ZIA cloud service. This tool runs several performance tests, such as download or upload bandwidth, between the browser and the [ZIA Public Service Edge](/zia/about-zscaler-enforcement-nodes) or [ZIA Private Service Edge](/zia/about-service-edge) to which the traffic is forwarded.
Zscaler recommends you use our proprietary Cloud Performance Test tool powered by [Zscaler Digital Experience (ZDX) ](/zdx/what-is-zscaler-digital-experience)over third-party speed test tools, such as Speedtest.net because these tools introduce additional latency and variables that make it difficult to troubleshoot issues.
Accessing and Running the Zscaler Cloud Performance Test Tool
Ensure that you are authenticated to ZIA to access this tool. If you are not authenticated (i.e., working remotely with Zscaler Client Connector enabled), you are prompted to enter your user ID and password.
To access and run the Zscaler Cloud Performance Test tool:
The Zscaler Cloud Performance Test tool is hosted only on HTTP and not on HTTPS.
-
Open your browser and enter [http://speedtest.zscaler.com](http://speedtest.zscaler.com) in the address bar.
You are automatically redirected to your ZIA Public Service Edge or ZIA Private Service Edge instance, which acts as the server for the speed test tool. This tool displays the following information:
- [User Details](#user-details)
- [Data Center Details](#data-center)
- [Geolocation Map](#geolocation-map)
-
Click **Start Speed Test**.
The tool calculates the performance parameters and displays the results. To learn more, see [Viewing and Downloading the Results](#viewing-downloading-results).
[See image.](#zscaler-cloud-performance-test-tool)
[]You can view the following information about the data center:
- **Data Center Name**: The name of the data center.
- **Location**: The physical location of the data center.
- **Proxy Hostname**: The name of the proxy server.
- **IP**: The IP address of the data center.
- **Cloud Name**: The name of your Zscaler cloud.
[]You can view the following information about the user:
- **User Name**: The name of the user.
- **Location**: The physical location of the user.
- **IP**: The IP address of the user.
[]The geolocation map displays the geographic location of the user and the connected data center. You can zoom in and out of the map to view regions of interest. You can also view your traffic forwarding method at the bottom of this map.
[]Viewing and Downloading the Results
The tool calculates and displays the following results after you initiate the speed test:
- **HTTP Ping**: Displays the average HTTP round-trip time observed in the application layer between the browser and the test server hosted on the ZIA Public Service Edge or ZIA Private Service Edge. The average time is calculated based on multiple subsequent small HTTP requests. It is measured in milliseconds.
- **HTTP Jitter**: Displays the variation across the HTTP ping measurements. A lower jitter value indicates that the network connectivity is more consistent. It is measured in milliseconds.
- **Download Bandwidth**: Displays the average bandwidth value between your device and the ZIA Public Service Edge or ZIA Private Service Edge based on multiple simultaneous large file downloads from a Zscaler-hosted HTTP test server, excluding outliers. You can hover over the graph to view the average, maximum, and minimum download bandwidth in a particular instance. It is measured in Mbps.
- **Upload Bandwidth**: Displays average bandwidth value between your device and the ZIA Public Service Edge or ZIA Private Service Edge based on multiple simultaneous large file uploads to a Zscaler-hosted HTTP test server, excluding outliers. You can hover over the graph to view the average, maximum, and minimum upload bandwidth in a particular instance. It is measured in Mbps.
-
**Cloud Path (Probe: Zscaler Service Edge to Client)**: Displays the **ICMP Traceroute Latency** in milliseconds and a summarized ZDX path calculated based on a *reverse* ICMP traceroute initiated from the ZIA Public Service Edge or ZIA Private Service Edge to your device. To learn more, see [What Is Zscaler Digital Experience?](/zdx/what-is-zscaler-digital-experience)
You can use the following views to analyze the Cloud Path from the user's device to the destination:
-
**Hop View**: Click the magnifying glass icon to expand the path. Hover over different sections of the path to see details such as latency and packet loss.
[See image.](#hop-view-image)
-
**Command Line View**: Click this tab to view further details about the Cloud Path, including the hop direction, packet loss in percentage, number of failed and total packets, and latency metrics.
[See image.](#command-line-view-image)
- **Download Results**: Click **Download Results** to download your speed test results as a CSV file.
- **More Diagnostics**: Click **More Diagnostics** to view additional details of your internet performance. To learn more, see [Viewing Additional Diagnostics](#more-client-connector-diagnostics).
[See image.](#results-image)
[]**Viewing Additional Diagnostics**
You can view additional information about your internet's performance by clicking the **More Diagnostics** option under the Results section. The resulting information differs depending on the Zscaler Client Connector Zscaler Tunnel (Z-Tunnel) you are using.
Irrespective of the Z-Tunnel version, clicking **More Diagnostics** displays the Cloud Path with a change in direction, which is calculated using a *forward* ICMP traceroute.
- [Z-Tunnel 1.0](#z-tunnel1.0)
- [Z-Tunnel 2.0](#z-tunnel2.0)
[]When you click **More Diagnostics**, and if you are connected via Z-Tunnel 1.0, you can view the following information:
-
**Cloud Path (Probe: Client to Zscaler Service Edge)**: Displays the **ICMP Traceroute Latency** in milliseconds and a summarized path calculated based on the *forward* ICMP traceroute initiated from your device to the ZIA Public Service Edge or ZIA Private Service Edge.
The **Hop View** and **Command Line View** tabs also display a *forward* ICMP traceroute Cloud Path with details such as latency and packet loss, latency metrics, etc.
[See image.](#cloud-path-ztunnel1.0)
[]When you click **More Diagnostics**, and if you are connected via Z-Tunnel 2.0, the **More Client Connector Diagnostics** section appears.
The **More Client Connector Diagnostics** section displays the following information:
- **File Download Speed**: Displays the Z-Tunnel and direct download speed between your device and the Zscaler data center. The speed is calculated based on a single large file download from a Zscaler-hosted HTTP test server.
- **UDP Throttling**: Displays the speed throttling information such as latency, jitter, packet loss percentage, etc.
-
**Cloud Path (Probe: Client to Zscaler Service Edge)**: Displays the **ICMP Traceroute Latency** in milliseconds and a summarized path calculated based on the *forward* ICMP traceroute initiated from your device to the ZIA Public Service Edge or ZIA Private Service Edge.
The **Hop View** and **Command Line View** tabs also display a *forward* ICMP traceroute Cloud Path with details such as latency and packet loss, latency metrics, etc.
[See image.](#cloud-path-ztunnel2.0)
You can view the date and time of the last test executed at the bottom of the page.
[]![Screenshot of the Zscaler Cloud Performance Test tool with details about data center, user and geolocation map](/downloads/zia/troubleshooting/using-zscaler-cloud-performance-test-tool/ZIA-zscaler-cloud-performance-test-tool-details.png)
[![Screenshot of the Results in the Zscaler Cloud Performance Test tool](/downloads/zia/troubleshooting/using-zscaler-cloud-performance-test-tool/zia-zscaler-cloud-performance-tool-results-more-diagnostics-option.png)
][]
[![Screenshot of Hop View in Zscaler Cloud Performance Test](/downloads/zia/troubleshooting/using-zscaler-cloud-performance-test-tool/ZIA-zscaler-cloud-performance-test-tool-hop-view-0.png)
][]
[![Screenshot of the Command Line View in the Zscaler Cloud Performance Test tool](/downloads/zia/troubleshooting/using-zscaler-cloud-performance-test-tool/ZIA-zscaler-cloud-performance-test-tool-command-line-view.png?1646325883)
][]
![Screenshot of the changes in cloud path, hop view, command line view with forward ICMP throttling for Z-Tunnel 1.0](/downloads/zia/troubleshooting/using-zscaler-cloud-performance-test-tool/zia-zscaler-cloud-performance-tool-ztunnel1.0-more-diagnostics.png)
[]
![Screenshot of the changes in cloud path, hop view, command line view with forward ICMP throttling for Z-Tunnel 2.0](/downloads/zia/troubleshooting/using-zscaler-cloud-performance-test-tool/zia-zscaler-cloud-performance-tool-ztunnel2.0-more-diagnostics.png)
[]