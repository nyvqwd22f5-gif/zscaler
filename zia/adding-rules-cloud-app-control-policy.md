# Adding Rules to the Cloud App Control Policy
Source: https://help.zscaler.com/zia/adding-rules-cloud-app-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1399401.pdf

[Click to watch a video about Cloud App Control Policy, including how to add rules to the Cloud App Control policy.](https://fast.wistia.net/embed/iframe/8fzke0bo9y)
You can create rules to control access to specific cloud applications. Cloud apps are organized into [categories](/zia/cloud-app-categories) to facilitate defining rules for similar applications.
Additionally, you can define a daily quota by bandwidth or time. When users browse these sites after their quota has been reached, the Zscaler service displays a message that explains that the content cannot be viewed because they exceeded their daily quota.
Policy Execution
The Cloud App Control rules consist of a series of logical operators between their criteria. The rules are triggered based on the result of the following logical operations between the criteria:
[Cloud Applications (`OR`) Cloud Application Risk Profile] (`AND`) [Users (`OR`) Groups (`OR`) Departments] (`AND`) [Location Groups (`OR`) Locations] (`AND`) Time (`AND`) [Device Groups (`OR`) Devices] (`AND`) Device Trust Level (`AND`) User Agent (`AND`) User Risk Profile.
Adding a Cloud App Control Rule
To add a rule, you can go to **Policy **>** URL & Cloud App Control** and choose a category.
[See image.](#Image)
Click on a cloud application category below to learn more about creating rules for the category.
- [AI & ML Applications](/zia/adding-ai-ml-applications-rule-cloud-app-control)
- [Collaboration & Online Meetings](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control)
- [Consumer](/zia/adding-consumer-rule-cloud-app-control)
- [Custom Applications](/zia/adding-custom-applications-rule-cloud-app-control)
- [DNS Over HTTPS Services](/zia/adding-dns-over-https-services-rule-cloud-app-control)
- [File Sharing](/zia/adding-file-sharing-rule-cloud-app-control)
- [Finance](/zia/adding-finance-rule-cloud-app-control)
- [Health Care](/zia/adding-health-care-rule-cloud-app-control)
- [Hosting Providers](/zia/adding-hosting-providers-rule-cloud-app-control)
- [Human Resources](/zia/adding-human-resources-rule-cloud-app-control)
- [Instant Messaging](/zia/adding-instant-messaging-rule-cloud-app-control)
- [IT Services](/zia/adding-it-services-rule-cloud-app-control)
- [Legal](/zia/adding-legal-rule-cloud-app-control)
- [Productivity & CRM Tools](/zia/adding-productivity-crm-tools-rule-cloud-app-control)
- [Sales & Marketing](/zia/adding-sales-marketing-rule-cloud-app-control)
- [Social Networking](/zia/adding-social-networking-rule-cloud-app-control)
- [Streaming Media](/zia/adding-streaming-media-rule-cloud-app-control)
- [System & Development](/zia/adding-system-development-rule-cloud-app-control)
- [Webmail](/zia/adding-webmail-rule-cloud-app-control)
The cloud app control policy rules can also be applied to IoT devices from a [location](/zia/configuring-locations) or a [sublocation](/zia/configuring-sublocations) that has the Enforce IoT Policy Control option enabled. You can apply the rules to IoT devices that are identified and classified (e.g., Printers, Sensors, etc.) by the ZscalerAI/ML under the IoT group in the Device Groups criterion.
Zscaler provides the Allow Unauthenticated Traffic for IoT Classifications predefined rules for the preceding cloud application categories. You can enable these rules to temporarily allow unauthenticated traffic that could be blocked by other rules, so that the Zscaler AI/ML can classify devices. These rules are disabled by default and cannot be deleted. You can modify the Rule Order, Rule Status, Rule Label, and Description for these rules and cannot edit other attributes.
For information on the order in which the service enforces all policies, including this policy, see [About Policy Enforcement](/zia/about-policy-enforcement).
[]![The list of cloud app category names](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/cloud-apps/configuring-cloud-app-policies/how-do-i-add-rules-cloud-app-control-policy/zia-cloud-app-names.png)