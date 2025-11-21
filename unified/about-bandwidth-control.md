# About Bandwidth Control
Source: https://help.zscaler.com/zia/about-bandwidth-control
PDF: https://help.zscaler.com/pdf/com/en/1398776.pdf

[Watch a video about Bandwidth Control including configuring the Bandwidth Control Policy.](https://fast.wistia.net/embed/iframe/z9h2f81rrs)
Bandwidth control allows you to preserve access to your business-critical applications regardless of your internet pipe consumption. This enables you to do things like adding more restrictive rules around social media and streaming media. For example, you can allocate a maximum of 10% of the bandwidth to the streaming media, social media, or file share bandwidth classes. When bandwidth is restricted, these classes are not guaranteed any bandwidth and are restricted to 10% of the bandwidth when it is available.
- [Bandwidth Control at Two Levels](#bw-2-levels)
- [How Bandwidth Control Works](#bw-works)
- [Best Practices for Bandwidth Control Policy](#best-practices)
- [Recommended Bandwidth Control Policy](#recommended-policy)
To see a sample policy for bandwidth management, see [Bandwidth Control Policy Example](/zia/bandwidth-control-policy-example).
To see how this policy fits into the overall order of policy enforcement, see [About Policy Enforcement](/zia/about-policy-enforcement).
You can go to the Bandwidth Control [dashboard](/zia/about-dashboards) to view your organization's bandwidth usage in real time. You can also go to **Analytics **>** Interactive Reports** to view the [standard reports](/zia/about-interactive-reports) for bandwidth control and to [create custom reports](/zia/creating-copying-report) as well.
About the Bandwidth Control Page
On the Bandwidth Control page (Policy > Bandwidth Control), you can:
- [Configure a bandwidth control policy rule](/zia/configuring-bandwidth-control-policy).
- View the recommended policy for bandwidth control.
[See image.](#recommended-policy-image)
- Select one of the following **View by** option to see the bandwidth control rules accordingly:
- **Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-bandwidth-control)
- **Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
[See image.](#rule-label-bandwidth-control)
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
- Search for a configured bandwidth control policy rule.
- View a list of all configured bandwidth control policy rules:
- **Rule Order:** The rule order number. Bandwidth control rules are evaluated in ascending numerical order and the default rule is evaluated last. You can sort this column.
- **Admin Rank: **The assigned [admin rank](/zia/about-admin-rank) for the rule. This is only visible if you have enabled admin ranking in the [Advanced Settings](/zia/about-advanced-settings#admin-ranking). You can sort this column.
- **Rule Name:** The name of the rule. You can sort this column.
- **Criteria:** The criteria of the rule (e.g., Bandwidth Classes, Protocols, etc.)
- **Action:** Displays the configured bandwidth control actions of the rule.
- **Label and Description**: The label and description of the policy rule, if available.
- [Modify the table and its columns](/zia/using-tables).
- [Edit the bandwidth control policy rule](/zia/editing-deleting-duplicating-items).
- [Duplicate the bandwidth control policy rule](/zia/editing-deleting-duplicating-items).
![Screenshot of the Zscaler Bandwidth Control page and tasks.](/downloads/zia/policies/bandwidth-control-classes/about-bandwidth-control/zia-bandwidth-control-policy-page.png)
[]Zscaler provides bandwidth control at two levels:
- At the first level, the Zscaler service provides bandwidth control by [location](/zia/about-locations). You can configure maximum upload and download bandwidth limits for each location in your organization. These limits apply to the traffic that is proxied to Zscaler for bandwidth control. Further, you can also control bandwidth management by [sublocation](/zia/understanding-sublocations). This provides admins with the versatility of configuring different policies for different sublocations. Different sublocations can use bandwidth from the location or, if desired, sublocations can have a specific bandwidth limit enforced. Enforcing limits is particularly useful for guest Wi-Fi networks.
The service applies bandwidth controls to traffic from known locations only (i.e., locations that are configured on the ZIA Admin Portal). The bandwidth control policy does not apply to remote users because their traffic does not come from a configured location and their source IP address has unknown upload and download bandwidth values.
- At the second level, for each location, you can configure bandwidth shaping rules based on bandwidth classes, such as VoIP or Web Conferencing, URL categories, or custom application classes that you define. The Zscaler bandwidth algorithm allows an application class full bandwidth utilization until there is contention for the bandwidth by a traffic class with a higher priority. When application classes compete for bandwidth, the service takes action based on the multiple bandwidth policies that you configured in the bandwidth control policy, as shown below:
![Diagram of how Zscaler service acts based on QoS controls configured in Bandwidth Control policy](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/bandwidth-management/bandwidth-management-guide/about-bandwidth-control/zia-bandwidth-control-policy-diagram.png)
You must configure upload and download bandwidth limits for your locations or sublocations to use the second level of bandwidth controls.
The Zscaler service rebalances the bandwidth in real time and buffers packets for application classes that hit the bandwidth quota limit during one-second intervals. This behavior ensures that business-critical applications run at full speed, with no deterioration in quality. The Zscaler service applies the policy to all HTTP and HTTPS traffic from the location. You do not need to enable SSL interception because it works at the TCP level. Bandwidth Control only applies to the TCP traffic for the following protocols:
- HTTP
- HTTPS
- HTTP Proxy
- SSL
- Native FTP
- DNS over HTTPS
- Tunnel SSL
[]First, you specify the maximum upload and download bandwidth limits for each location in your organization. About 5–7% of TCP traffic is overhead, such as packet headers. The Zscaler service does not include these in its bandwidth calculations. It only includes the application traffic.
Next, you [define your bandwidth classes](/zia/about-bandwidth-classes), specifying the URL categories and cloud applications to which the bandwidth class applies. You must configure the bandwidth classes before you can reference them in bandwidth control policy rules. To configure bandwidth classes, edit the predefined bandwidth classes or add new bandwidth classes, by grouping URL categories, cloud applications, or custom domain lists. You can then reference those bandwidth classes in your bandwidth control policy, a set of prioritized rules that tell the service how to allocate the bandwidth when contention occurs. Bandwidth is allocated based on the rule order. Therefore, bandwidth classes such as business-critical applications, O365, etc., that require priority bandwidth control should be placed at the top of the rule sets. Each rule defines a maximum and minimum bandwidth for the bandwidth classes in the rule along with other parameters, like location and time of day.
Based on the bandwidth policy, Zscaler distributes the bandwidth to each rule from top to bottom by looking at the minimum bandwidth first. Once completed, it passes through each rule a second time to allocate the remaining bandwidth and distribute it based on the maximum bandwidth configuration.
The maximum bandwidth specifies the maximum percentage of the total bandwidth that the configured bandwidth class can use at a given point in time, and the minimum bandwidth specifies the guaranteed minimum bandwidth percentage that is available for the bandwidth class.
The maximum bandwidth percentage is applied at all times. Because of this, traffic can only take up to the specified percentage of the location's bandwidth, whether there is any congestion. This is useful to users who wish to suppress, but not block, non-business traffic.
The minimum bandwidth percentage is only enforced when there is contention on a location's connection and when traffic from the specified bandwidth classes is present. This allows a bandwidth class for full bandwidth utilization until there is contention between the bandwidth by a traffic class with a higher priority. When bandwidth classes compete for bandwidth, the service allocates the guaranteed minimum bandwidth percentages to the bandwidth classes and allocates the remaining bandwidth according to the prioritized rules. Therefore, the total minimum bandwidth must be less than 100%.
[]The following are the best practices for setting up the bandwidth control policy for locations:
- You must specify the maximum upload and download bandwidth limits for each location in your organization. Ensure that you exclude UDP traffic sent to Zscaler and traffic not forwarded to Zscaler while specifying the limits.
- About 5–7% of TCP traffic is overhead, such as packet headers. The Zscaler service does not include these in its bandwidth calculations. It only includes the application traffic that is proxied to Zscaler. Therefore, computing a location's bandwidth is shown in the following equation:
- (Actual bandwidth) – (10–15% overhead) = Upload and Download bandwidth
Only 70–80% of the overall bandwidth per location is the ideal setting for upload and download limits.
The following are the best practices for setting up the bandwidth control policy for sublocations:
- If bandwidth control is disabled on the main location but enabled on a sublocation, then an admin has to manually enter the upload and download limits for the sublocation.
- Whenever the main location has bandwidth control enabled after a sublocation does, it needs to have upload and download limits added. The value of upload and download limits added to the main location must be greater than or equal to the total value of limits used for all the sublocations.
For example, say you first enable bandwidth control on the sublocation *San Jose* and set it to have a download limit of 15 Mbps and an upload limit of 80 Mbps. If you then enable bandwidth control on the main location, *California*, and San Jose is its only sublocation, then California's download and upload limits should be at least 15 Mbps and 80 Mbps respectively.
- If you manually set the bandwidth control on a sublocation to a number that is equal to the bandwidth of the main location, bandwidth control is disabled on all other sublocations.
[]Zscaler recommends that you configure the following bandwidth control policy:
- **Rule Order**: 1
- **Rule Status**: Enabled
- **Bandwidth Classes**: Any
- **Locations**: Any
- **Location Groups**: Any
- **Time**: Always
- **Min. Bandwidth**: 0%
- **Max. Bandwidth**: 100%
[]![Screenshot of Recommended Bandwidth Control Policy in the Bandwidth Control page](/downloads/zia/policies/bandwidth-control-classes/about-bandwidth-control/zia-recommended-policy-about-bandwidth-control.png)
[]![Screenshot of the Zscaler Bandwidth Control page with Rule Order view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/bandwidth-management/bandwidth-management-guide/about-bandwidth-control/ZIA-Bandwidth-Control-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of the Zscaler Bandwidth Control page with Rule Label view selected.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/bandwidth-management/bandwidth-management-guide/about-bandwidth-control/ZIA-Bandwidth-Control-Policy-Page-Viewby-Rule-Label.png)