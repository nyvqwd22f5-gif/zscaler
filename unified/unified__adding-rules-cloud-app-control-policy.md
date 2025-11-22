# Adding Rules to the Cloud App Control Policy
Source: https://help.zscaler.com/unified/adding-rules-cloud-app-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1494666.pdf

You can create rules to control access to specific cloud applications. Cloud apps are organized into [categories](/unified/understanding-cloud-app-categories) to facilitate defining rules for similar applications.
Additionally, you can define a daily quota by bandwidth or time. When users browse to these sites after their quota has been reached, the Zscaler service displays a message that explains that the content cannot be viewed because they exceeded their daily quota.
To add a rule, you can go to **Policies **>** Access Control > Internet & SaaS > Policies** and choose a category.
[See image.](#Image)
Click on a cloud application category below to learn more about creating rules for the category.
- [AI & ML Applications](/unified/adding-ai-ml-applications-rule-cloud-app-control)
- [Collaboration & Online Meetings](/unified/adding-collaboration-online-meetings-rule-cloud-app-control)
- [Consumer](/unified/adding-consumer-rule-cloud-app-control)
- [Custom Applications](/unified/adding-custom-applications-rule-cloud-app-control)
- [DNS Over HTTPS Services](/unified/adding-dns-over-https-services-rule-cloud-app-control)
- [File Sharing](/unified/adding-file-sharing-rule-cloud-app-control)
- [Finance](/unified/adding-finance-rule-cloud-app-control)
- [Health Care](/unified/adding-health-care-rule-cloud-app-control)
- [Hosting Providers](/unified/adding-hosting-providers-rule-cloud-app-control)
- [Human Resources](/unified/adding-human-resources-rule-cloud-app-control)
- [Instant Messaging](/unified/adding-instant-messaging-rule-cloud-app-control)
- [IT Services](/unified/adding-it-services-rule-cloud-app-control)
- [Legal](/unified/adding-legal-rule-cloud-app-control)
- [Productivity & CRM Tools](/unified/adding-productivity-crm-tools-rule-cloud-app-control)
- [Sales & Marketing](/unified/adding-sales-marketing-rule-cloud-app-control)
- [Social Networking](/unified/adding-social-networking-rule-cloud-app-control)
- [Streaming Media](/unified/adding-streaming-media-rule-cloud-app-control)
- [System & Development](/unified/adding-system-development-rule-cloud-app-control)
- [Webmail](/unified/adding-webmail-rule-cloud-app-control)
The cloud app control policy rules can also be applied to IoT devices from a [location](/unified/configuring-locations) or a [sub-location](/unified/configuring-sub-locations) that has the Enforce IoT Policy Control option enabled. You can apply the rules to IoT devices that are identified and classified (e.g., Printers, Sensors, etc.) by the Zscaler AI/ML under the IoT group in the Device Groups criterion.
Zscaler provides the Allow Unauthenticated Traffic for IoT Classifications predefined rules for the preceding cloud application categories. You can enable these rules to temporarily allow unauthenticated traffic that could be blocked by other rules, so that the Zscaler AI/ML can classify devices. These rules are disabled by default and cannot be deleted. You can modify the Rule Order, Rule Status, Rule Label, and Description for these rules and cannot edit other attributes.
For information on the order in which the service enforces all policies, including this policy, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).
[]![Cloud App Category Names](/downloads/unified/policies/internet-saas/access-control/cloud-apps/cloud-app-control-policies/adding-rules-cloud-app-control-policy/Unified-Cloud-App-Names.png)