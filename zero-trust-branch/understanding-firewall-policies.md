# Understanding Firewall Policies
Source: https://help.zscaler.com/zero-trust-branch/understanding-firewall-policies
PDF: https://help.zscaler.com/pdf/com/en/1532548.pdf

Zero Trust Branch allows you to create firewall policies to isolate and control communication between various network environments. Built on Zscaler's Zero Trust framework, these policies ensure that no connection is trusted by default, effectively preventing lateral movement and minimizing attack surfaces.
Zero Trust Branch provides a comprehensive set of capabilities to secure and manage network communications:
- **Granular Isolation**: Segment and control traffic between zones, sites, or network segments.
- **Zero Trust Enforcement**: Authenticate and authorize every connection before granting access.
- **Threat Containment**: Restrict lateral movement, minimizing the blast radius in the event of a breach.
- **Object-Based Policy Building**: Define source and destination criteria using reusable network, service, and group objects.
You can create firewall policies at different levels:
- **Global**: Policies that apply to all sites.
- **Template**: Policies that apply to all sites that share a specific template.
-
**Site**: Policies that apply only to an individual site.
When a new site is created, Zero Trust Branch automatically generates** **system (default) policies** **for the site. These policies are editable but cannot be reordered.
Policy Evaluation
Firewall policies are evaluated in the following sequence:
- **Site policies**: Checked first. If a match is found, the policy is applied and evaluation stops.
- **Template policies**: Evaluated if no site-level policy matches. If a match is found, the policy is applied and evaluation stops.
- **Global policies**: Evaluated if no template-level policy matches. If a match is found, the policy is applied and evaluation stops.
- **System (default) policies**: Applied only if no match is found at the site, template, and global levels.
With Zero Trust Branch firewall policies, security teams can standardize enforcement, maintain flexibility for site-specific needs, and align with zero trust principles—all while simplifying branch network security management.
To learn more, see [Configuring Firewall Policies](/zero-trust-branch/configuring-firewall-policies) and [Managing Firewall Policies](/zero-trust-branch/managing-firewall-policies).