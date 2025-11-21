# Working with Tags
Source: https://help.zscaler.com/zero-trust-branch/working-with-tags
PDF: https://help.zscaler.com/pdf/com/en/1509861.pdf

Tagging provides additional information about an asset, allowing you to create policies that are not based on IP addresses. Tagging helps with resource categorization, simplified policy management, granular access control, traffic flow analysis, and operational efficiency.
For example, consider a business requirement to only allow Windows 7/Server 2008 machines to access an old Network Attached Storage (NAS). With a traditional firewall, you could allocate static IP addresses to the Windows 7/Server 2008 machines and create policies based on those IP addresses. While this works in a small environment, it is not a scalable solution in an enterprise environment.
With Zero Trust Branch, you can create a tag called `microsoft windows kernel 6.1` and apply it to all Windows 7/Server 2008 machines. You can then create a policy based on this tag as the source. Any changes in IP addresses do not require the admin to adjust the policy. To learn more, see [Managing Segmentation Policies](/zero-trust-branch/managing-segmentation-policies).