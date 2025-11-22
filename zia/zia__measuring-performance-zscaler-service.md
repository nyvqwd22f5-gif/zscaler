# Measuring the Performance of the Zscaler Service
Source: https://help.zscaler.com/zia/measuring-performance-zscaler-service
PDF: https://help.zscaler.com/pdf/com/en/1400951.pdf

Common tools for network performance measurement, such as Speedtest and Iperf, can provide inaccurate results when using the Zscaler service. This is due to their test conditions and the methods they use to test network throughput. To obtain a more accurate measure of end-user performance, Zscaler recommends that you use the Zscaler Cloud Performance Test tool, one of your browser's network analysis tools, or Wireshark.
Issues with Common Measurement Tools
One issue with some measurement tools is the length of the test. For example, the length used for Speedtest is only 10 seconds. This has an impact as many internet service providers boost the available bandwidth for a short period of time or for a portion of a transaction. Since the type of file that can be uploaded or downloaded over 10 seconds usually falls within this boosting window, this can provide results that are much higher than the true average speed.
The Zscaler service uses data trickling to help avoid timeouts and this can also impact the results. With data trickling, Zscaler sends a small amount of data to the browser to keep the session open while the rest of the data is buffered for scanning. As soon as the Zscaler service has determined that the connection is allowed, the rest of the data in the buffer is released to the client. This can cause problems as Speedtest does not include the fastest 10% or the slowest 30% of data in their analysis. As a result, the buffer release will likely be treated as an outlier and not included in the results. So, the majority of the test is based on the trickle function which is not indicative of the true speed.
Another aspect of testing that can lead to misleading results is caching. While Speedtest has taken steps to address this concern, many services have not. Many types of services and software cache content that is known to be safe. If this content hasn't changed recently, it's delivered directly from the cache to the user. If this type of data is included, it gives results with much higher speeds than could be achieved without caching.
Iperf shares many of the same issues as Speedtest. In addition, it's highly susceptible to both server limitations and limitations on a single session.
Zscaler does not recommend using ping tests to measure the end-user performance because Zscaler implements ICMP deprioritization on its data centers (DCs).
Recommended Tools
Zscaler recommends using the following tools to obtain an accurate measure of end-user performance.
Zscaler Cloud Performance Test Tool
The Zscaler Cloud Performance Test tool collects performance troubleshooting information for end users when connecting to the internet through the Zscaler Internet Access (ZIA) cloud service. This tool runs several performance tests, such as download or upload bandwidth, between the browser and the [ZIA Public Service Edge](/zia/about-zscaler-enforcement-nodes) or [ZIA Private Service Edge](/zia/about-service-edge) to which the traffic is forwarded.
To learn more, see [Using the Zscaler Cloud Performance Test Tool.](/zia/using-zscaler-cloud-performance-test-tool)
Browser Developer Tools
Many web browsers also provide powerful network analysis tools that can help analyze your end user's experience.
To use developer tools, see the relevant product documentation:
- [Chrome documentation](https://developers.google.com/web/tools/chrome-devtools/network-performance/)
- [Edge documentation](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide/network)
- [Firefox documentation](https://developer.mozilla.org/en-US/docs/Tools/Network_Monitor)
- [Internet Explorer documentation](https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/samples/dn255004%28v%3dvs.85%29)
Wireshark
Wireshark is another highly useful tool for troubleshooting network performance issues. With an I/O graph, you can compare the performance of traffic that goes through Zscaler and traffic that goes directly to the internet. It also helps you to identify if you are hitting a bandwidth cap or if the throughput plateaus. To learn more, see [Wireshark's documentation](https://www.wireshark.org/docs/wsug_html_chunked/ChStatIOGraphs.html) on I/O graphs.
The Wireshark summary page also provides a good overview of download speed.
What Results to Expect
The Zscaler service inspects content on an individual user session basis. There should be no expectation of one user being able to fill the entire available network pipe the enterprise has available. This is both unrealistic and usually disallowed. As a result, having a 10 Gbps internet egress does not automatically allow a user to get 10 Gbps.
If their connection and traffic shaping allow, a user should expect to see enough bandwidth to easily conduct day-to-day business transactions and to support demanding enterprise applications such as voice and video conferencing.
Connection Speeds Required for Video Conferencing1
| **Video Codec** | **Resolution & Aspect Ratio** | **Maximum Video Payload Bitrate (Kbps)** | **Minimum Video Payload Bitrate (Kbps)** |
| --------------- | ----------------------------- | ---------------------------------------- | ---------------------------------------- |
| H.264 | 320x180 (16:9)
212x160 (4:3) | 250 | 15 |
| H.264/RTVideo | 424x240 (16:9)
320x240 (4:3) | 350 | 100 |
| H.264 | 480x270 (16:9)
424x320 (4:3) | 450 | 200 |
| H.264/RTVideo | 640x360 (16:9)
640x480 (4:3) | 800 | 300 |
| H.264 | 848x480 (16:9) | 1500 | 400 |
| H.264 | 960x540 (16:9) | 2000 | 500 |
| H.264/RTVideo | 1280x720 (16:9) | 2500 | 700 |
| H.264 | 1920x1080 (16:9) | 4000 | 1500 |
| H.264/RTVideo | 960x144 (20:3) | 500 | 15 |
| H.264 | 1280x192 (20:3) | 1000 | 250 |
| H.264 | 1920x288 (20:3) | 2000 | 500 |
As displayed above, a connection of 4 Mbps is capable of providing HD-quality video. Further, the following major video streaming and video conferencing companies all recommend 5 Mbps or more to use their products.
- [Amazon Video](https://www.primevideo.com/help/ref=atv_hp_nd_srchr?nodeId=GUX9FYHU5D8LC9EJ)
- [GoToMeeting](https://support.logmeininc.com/gotomeeting/help/system-requirements-for-attendees-g2m010003)
- [Hulu](https://help.hulu.com/en-us/network-recommendations)
- [Netflix](https://help.netflix.com/en/node/306)
- [Skype](https://support.skype.com/en/faq/FA1417/How-much-bandwidth-does-Skype-need)
- [YouTube](https://support.google.com/youtube/answer/3037019?hl=en&ref_topic=3014746&kbid=88468)
- [WebEx](https://collaborationhelp.cisco.com/article/en-us/WBX22158)
- [Zoom](https://support.zoom.us/hc/en-us/articles/201362023-System-Requirements-for-PC-Mac-and-Linux)
With this in mind, the Zscaler service is capable of providing users with an end-user experience that is free of disruption, even when they are using highly demanding applications.
Analyzing MTR Results
When analyzing your traffic, it's also important to be aware of how to interpret MTR results as packet loss doesn't necessarily indicate a connectivity problem. Consider the following example:
![Screenshot of traceroute showing healthy latency](/downloads/zia/documentation-knowledgebase/troubleshooting/troubleshooting-zscaler-issues/measuring-performance-zscaler-service/good-traceroute.png)
Here you can see that there is a gradual increase in latency as the traffic travels from source to destination, yet there is little to no packet loss. This is an example where there is no connectivity problem.
In contrast, consider the following traceroute:
![Screenshot of a My traceroute with unhealthy latency](/downloads/zia/documentation-knowledgebase/troubleshooting/troubleshooting-zscaler-issues/measuring-performance-zscaler-service/bad-traceroute.png)
In the last few hops, there is a noticeable spike in latency. Since the loss begins at the end of the trace and the end of the trace is the customer's gateway, this indicates that the problem is with the customer's ISP.
Potential Causes of Network Performance Issues
If after measuring your traffic you still feel you are having network performance issues, there could be multiple reasons that are not caused by the Zscaler service. One such reason is DNS traffic. DNS plays an important part in network performance. Although it primarily impacts traffic when using transparent traffic forwarding, it can also impact explicit traffic forwarding when you are using PAC files.
When using transparent traffic forwarding methods, the browser is not aware of a proxy being present in the transaction. Consequently, all websites that users access need to be resolved by the computer itself. This increases dependency on DNS.
While using [PAC files](/zia/what-pac-file), the pac.<cloudname>.net needs to be resolved, which requires DNS. In addition, if logic such as dnsResolve(host) or isInNet(host, "y.y.y.y", "x.x.x.x") is used, then every new domain that is accessed needs to be resolved. This also increases dependency on DNS.
When there is a high dependency on DNS, a delayed response from the DNS server negatively affects page loading times. One common reason for a delayed response is web pages that fetch content from multiple websites, not a single destination.
Performing NAT on your gateway device before forwarding traffic to the ZIA Public Service Edge can also impact performance. The device performing the NAT overload could potentially run out of source ports. This can result in performance issues, pages not loading, and broken applications.
1. Microsoft Product Documentation. 2015. Network bandwidth requirements for media traffic in Lync Server 2013. Available at: [https://docs.microsoft.com/en-us/lyncserver/lync-server-2013-network-bandwidth-requirements-for-media-traffic](https://docs.microsoft.com/en-us/lyncserver/lync-server-2013-network-bandwidth-requirements-for-media-traffic). [Accessed 28 November 2018].