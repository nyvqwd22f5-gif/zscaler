# Isolation Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/cloud-browser-isolation-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417406.pdf

This guide describes the benefits of using Isolation and the steps necessary for configuring Zscaler Internet Access (ZIA) to add Isolation to your security posture.
Isolation isolates users from potentially harmful content on the internet by loading the accessed web page on a remote browser in a Zscaler data center and sending the rendered content as a stream of pixels to the user’s native browser.
This ensures that the HTML files, CSS files, JavaScript, and any other active content served by the accessed web page never reach the end user’s machine or the corporate network.
Isolation provides the following benefits:
- Zero-risk access to any destination by isolating the end user from potentially malicious content.
- Meets regulatory compliance requirements to isolate browser traffic.
To learn more, see [What Is Isolation](/isolation/what-is-isolation)?
Deployment Phase
The deployment phase initially sets up and integrates Zscaler solutions into an existing network infrastructure. During the deployment phase, you configure ZIA Isolation to meet the needs of your infrastructure. The following sections discuss steps to deploy ZIA Isolation.
Prerequisites
This feature requires:
A ZIA subscription and the Isolation add-on.
- Creating a URL Filtering Policy with the action Allow.
- Create a File Type Control Policy with the action Allow for Upload/Download.
- In addition, Isolation requires configuring the service URLs listed in the following table:
| Source | Destination URL | Port / Protocol | ZIA Configuration | Remarks |
| ------ | --------------- | --------------- | ----------------- | ------- |
| User Machine | .files.rbi.zscaler.com | 443/HTTPS | URL Filtering policy. Bypassed from isolation. Configure the appropriate file type control. | This wildcard domain shares the files between isolation and the user machine (upload and download). |
| User Machine | .isolation.zscaler.com | 443/HTTPS | SSL inspection is bypassed by default (Zscaler recommends this policy). | This wildcard domain connects to the isolation service. |
Deployment Steps
The following steps explain how to deploy ZIA Isolation:
- Create a [ZIA Isolation profile](https://help.zscaler.com/isolation/configuring-zia-isolation).
- Identify [criteria for enabling Isolation](/isolation/configuring-zia-isolation) (based on a risk or specific use case).
- Create [URL filtering rules](/zia/configuring-url-filtering-policy) for respective destinations with web traffic action *Isolate*.
Considerations
Review the following considerations:
- Latency is less than 100 ms for the optimal end user experience. Check through the [isolation browser menu](/isolation/accessing-network-diagnostics-isolation).
- Isolation only works with HTTP and HTTPS protocols in the web browser.
- The web traffic action *Isolate *is only available for known user agents. In a URL filtering rule, you cannot choose *Other *as the user agent criteria.
- SSL inspection for respective destinations is mandatory for redirecting HTTPS traffic to Isolation.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZIA Isolation during the Operations phase to meet your infrastructure needs.
Prerequisites
For Isolation operations, complete the following prerequisites:
- Create a standard operating procedure (SOP) for adding URL destinations to Isolation.
- Create an SOP for adding URL destinations to an isolation bypass.
- Create an SOP for collecting information to log a support case.
Common Troubleshooting Items
The following list describes common issues related to the Isolation operation:
- The HTTPS website fails to redirect to Isolation: Check if SSL inspection is enabled for the destination.
- The website fails to load or is only partially loading content: Check logs to see if any ZIA policy blocks content.
Deployment and Operations Checklist
Zscaler recommends downloading the [Isolation Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/cloud-browser-isolation-deployment-and-operations-guide/Isolation-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA Isolation: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/cloud-browser-isolation-deployment-and-operations-guide/Isolation-Deployment-Operations-Checklist.pdf)
Additional Information
For more Isolation information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com).