# Bandwidth Control Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/bandwidth-control-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417461.pdf

This guide describes the benefits of using Bandwidth Control and the steps necessary for configuring Zscaler Internet Access (ZIA) to add Bandwidth Control to your security posture.
Bandwidth Control allows you to preserve access to your business-critical applications regardless of your internet pipe consumption by adding more restrictive rules around activities such as social media and streaming media.
To learn more, see [About Bandwidth Control](/zia/about-bandwidth-control).
Value of Deploying Bandwidth Control
Using Bandwidth Control provides the following benefits:
- Limits the impact of streaming media, file sharing, and social media on business apps.
- Identifies bandwidth constraints before they impede the user experience.
- Aligns policies for all users to business needs, with granular rules by application class, location, and time.
Deployment Phase
The deployment phase includes initially setting up and integrating Zscaler solutions into an existing network infrastructure. During the deployment phase, configure ZIA Bandwidth Control to meet the needs of your infrastructure. The following sections discuss steps to deploy ZIA Bandwidth Control.
Prerequisites
For Bandwidth Control deployment, verify and complete the following prerequisites:
- One of the following ZIA subscriptions is required:
- ZIA Business Edition and later
- Bandwidth Control Add-On
- Determine the available bandwidth for each location where you plan to add Bandwidth Control. For example, for an organization deploying Bandwidth Control at a head office and two branch offices:
- Headquarters: 1 Gbps
- Bangalore office: 250 Mbps
- Mumbai office: 150 Mbps
- Determine the maximum bandwidth requirement for any [sub-locations](/zia/about-sub-locations) at each [location](/zia/about-locations). Using the previous example:
- HR team (configured as a sub-location called HR in the ZIA Admin Portal) at the headquarters: 250 Mbps
- Support team (configured as a sub-location called Support in the ZIA Admin Portal) at the headquarters: 500 Mbps
- Guest Wi-Fi (configured as a sub-location called Guest Wifi in the ZIA Admin Portal) at the Bangalore office: 40 Mbps
- Marketing team (configured as a sub-location called Marketing in the ZIA Admin Portal) at the Mumbai office: 150 Mbps
- Determine a list of productivity apps or categories (e.g., Outlook, OneDrive, SuccessFactors, etc.) that need an allocated minimum guaranteed bandwidth.
- Determine a list of non-productivity apps or categories (e.g., streaming, social networking, new sites, etc.) that have a defined bandwidth cap.
- (Optional) Consider whether you need to enforce bandwidth rules 24 hours per day, during peak working hours, or for some other specific period using [Time Intervals](/zia/about-time-intervals).
- For an example, see [Bandwidth Control Policy Example](/zia/bandwidth-control-policy-example).
Considerations
Review the following considerations:
- About five to seven percent of TCP traffic is overhead (e.g., packet headers). The Zscaler service does not include overhead in its bandwidth calculations. It only includes the application traffic that is proxied to Zscaler. Therefore, the best practice for computing a location's bandwidth is as follows:
- Actual bandwidth should be set at 10 to 15 percent less than the measured traffic to account for the protocol overhead when setting the upload and download bandwidth in the ZIA Admin Portal.
- For example, if the actual bandwidth of a location is 100 Mbps, set the location bandwidth in ZIA Admin Portal to 85 Mbps (100 minus 15 percent).
- Determine the times of day to apply the Bandwidth Control policies. Define the time settings using the [Time Intervals](/zia/defining-time-intervals) option.
- For example, you can apply a Bandwidth Control policy limitation for streaming media apps during business hours (9:00 AM to 5:00 PM) and leave the bandwidth for these apps unrestricted at all other times.
- While creating [bandwidth classes](/zia/about-bandwidth-classes), consider using [cloud applications](/zia/about-cloud-app-categories) (if available).
- On a sub-location where [Enforce Bandwidth Control is disabled](/zia/configuring-bandwidth-control-policy), it uses the shared bandwidth at any given time.
- On a sub-location with [Enforce Bandwidth Control set to Override](/zia/configuring-bandwidth-control-policy), the defined bandwidth is dedicated to that sub-location. It can't be used by any other sub-location, regardless if there is any traffic or not on the sub-location.
For example, given the following configuration:
| Location Name in ZIA | Bandwidth Control Configuration | Actual Throughput | Configured Throughput(Actual - 15%) |
| -------------------- | ------------------------------- | ----------------- | ----------------------------------- |
| HQ | Enabled | 100 Mbps Up/Down | 85 Mbps Up/Down |
| Sub-location_1 | Override | 35 Mbps Up/Down | N/A |
| Sub-location_2 | Disabled | N/A | N/A |
| Other | Use Location Bandwidth | N/A | N/A |
-
At any given time, HQ only uses up to the max shared bandwidth (i.e., 85 minus 35 equals 50 Mbps of total shared bandwidth).
-
Since the Bandwidth Control option on Other is set to Use Location Bandwidth, the behavior is the same (i.e., Other only uses up to the maximum shared bandwidth of 50 Mbps).
-
With Bandwidth Control set to Disabled, no Bandwidth Control policies and functionalities are applied. Bandwidth Control policies are applied if Bandwidth Control is set to Use Location Bandwidth.
-
Sub-location_1 has a dedicated 35 Mbps of bandwidth. That bandwidth can’t be used by any other sub-location regardless if the sub-location has traffic.
Deployment Steps
The following steps explain how to deploy Bandwidth Control:
- Enable Bandwidth Control on the [location](/zia/configuring-bandwidth-control-policy#A) and [sub-location](/zia/configuring-bandwidth-control-policy#B).
- Configure [bandwidth classes](/zia/about-bandwidth-classes).
- Configure [Bandwidth Control policy](/zia/adding-rules-bandwidth-control-policy).
- [Bandwidth Control Policy Example](/zia/bandwidth-control-policy-example) shows a Bandwidth Control configuration example.
Operations Phase
This section describes common practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune ZIA Bandwidth Control during the operations phase to meet your infrastructure needs.
Prerequisites
For Bandwidth Control operation, complete the following prerequisites:
- When your organization introduces a new productivity or business-related app, and a Bandwidth Control policy is necessary for this app:
- Evaluate the criticality of this new application to your business.
- [Create bandwidth classes](/zia/about-bandwidth-classes) for this app and configure the minimum bandwidth policy. That way, during bandwidth contention, the app is guaranteed its needed bandwidth.
- During a Zscaler Quarterly Operations Review (or internal audit), if a non-productivity app is overusing the office bandwidth:
- Evaluate how much bandwidth this app uses.
- [Create a bandwidth class](/zia/about-bandwidth-classes) for the app and then configure a maximum bandwidth policy. This restricts the bandwidth available to the app.
- Regularly review the [Bandwidth Control dashboard](/zia/about-dashboards#bandwidth-control). If the bandwidth usage of any app swings, adjust the Bandwidth Control policies accordingly.
- (Optional) Create a [custom dashboard](/zia/creating-copying-report) for bandwidth usage as per your organization's requirements.
Common Troubleshooting Items
The following list describes common issues related to Bandwidth Control operation:
- Bandwidth Control is not applied per expectations:
- Check where the user is (in the office or remote) as Bandwidth Control policies aren’t enforced for remote users.
- Check if [Enforce Bandwidth Control](/zia/configuring-bandwidth-control-policy) is enabled for that location or sub-location.
- Check the [Web Insight Logs](/zia/about-insights-logs) for that transaction, and check if the correct Bandwidth Control policy is getting enforced:
- If not, check the URL against that transaction, and revisit the matching Bandwidth Control rule.
- Add the URL in the correct [bandwidth class](/zia/about-bandwidth-classes).
- Open a ticket with Zscaler Support for further analysis.
- A productivity app, already bandwidth-controlled, is having performance issues during peak production hours:
- Visit the [Bandwidth Control dashboard](/zia/about-dashboards#bandwidth-control) and check for the top bandwidth classes.
If the impacted bandwidth class is the top bandwidth user, and there is a performance issue, consider [increasing the policy’s minimum bandwidth percentage](/zia/adding-rules-bandwidth-control-policy).
Consider increasing the minimum bandwidth five percent and test for performance. If there is no change, increase minimum bandwidth another five percent and test again. Repeat this process until performance is acceptable.
- If your impacted bandwidth class is not the top bandwidth user, then consider [reducing the minimum bandwidth percentage](/zia/adding-rules-bandwidth-control-policy) of the top bandwidth user to balance it with the impacted Bandwidth Control policy.
- Increasing or decreasing the values too much has implications on other apps used by your organization. Therefore, test thoroughly before changing the percentage.
- A non-productivity app, already bandwidth-controlled, is still using the highest bandwidth.
- Consider [reducing the maximum bandwidth percentage](/zia/adding-rules-bandwidth-control-policy) for this Bandwidth Control policy.
- Consider blocking this app during business hours by implementing Zscaler’s [Cloud App Control](/zia/about-cloud-app-control) or [URL Filtering](/zia/about-url-filtering) policies.
Deployment Checklist
Zscaler recommends downloading the [Bandwidth Control Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/bandwidth-control-deployment-and-operations-guide/Bandwidth-Control-Deployment-Operations-Checklist.pdf) to help plan and implement ZIA Bandwidth Control: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/bandwidth-control-deployment-and-operations-guide/Bandwidth-Control-Deployment-Operations-Checklist.pdf)
Additional Information
For more SaaS Security information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).