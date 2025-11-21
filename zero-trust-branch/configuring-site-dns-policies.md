# Configuring Site DNS Policies
Source: https://help.zscaler.com/zero-trust-branch/configuring-site-dns-policies
PDF: https://help.zscaler.com/pdf/com/en/1531196.pdf

You can configure a site to manage DNS queries with the DNS policy engine. Zscaler provides several preconfigured DNS gateways, or you can create custom domain and DNS gateway objects as described in [Managing Objects](/zero-trust-branch/managing-objects).
To learn more about site DNS policies, see [What Are Site DNS Policies?](/zero-trust-branch/what-site-dns-policies)
To configure a site for DNS policies:
- Go to **Deployment > Sites**.
-
In the** Site Name** column, click the name of the site that you want to configure for DNS routing.
[See image.](#view-site)
-
On the site details page, click the **DNS Policies **tab.
[See image.](#site-details)
- To add a new DNS policy:
-
On the **DNS Policies** tab, click **Configure**, then click **Add Policy**. The **Add Policy** panel appears.
[See image.](#add-dns-policy)
-
In the **Add Policy** panel, enter the following information:
- **Name**: Enter a name for this policy.
- **Source**: Select the source from which you want to route queries.
- **Domain Name**: Select the domain object for the domain you want to match. To learn more about creating custom domain objects, see [Managing Objects](/zero-trust-branch/managing-objects).
- **Action**: Select the routing action for this policy:
- **Reject**: Reject queries that match this policy. When you select this action, in the **Error Code** field, choose the error you want to return.
- **Redirect**: Redirect queries that match this policy. When you select this action, DNS queries that match this policy are forwarded to the DNS gateway you select in the **DNS Gateways** field. To learn more about creating custom DNS objects, see [Managing Objects](/zero-trust-branch/managing-objects).
- **Override**: Override queries that match this policy. When you select this action, the IP address that you enter in the **Override IP** field is returned as the response.
- **Skip**: Disable this policy.
- **Description**: Enter a detailed description of this DNS policy.
[See image.](#add-policy-panel)
- Click **Add **to create the new policy.
-
(Optional) You can reorder the policies by clicking **Reorder**, dragging the policies into the order you want, and clicking **Save Policy Order**.
DNS policies are processed based on first match. When a DNS query is matched to a query, subsequent policies are not evaluated.
[See image.](#reorder)
-
To verify that the policies are working as expected, click the **Console **tab and view the last few entries of the DNS policy log using the `tail` command (e.g., `tail -n 20 /etc/airgap/dns_proxy/policy_logs/dns_policy.log`).
[See image.](#console)
[]![Accessing details for a site on the Sites page](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-site-dns-policies/add-site-dns.png)
[]![Accessing the DNS Policies tab on the site details page](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-site-dns-policies/dns-policies.png)
[]![Reordering DNS Policies tab on the site details page](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-site-dns-policies/reorder-policies.gif)
[]![Viewing the DNS Policies tab for a Site](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-site-dns-policies/add-dns-policy.gif)
[]![Adding a DNS Policy for a Site](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-site-dns-policies/add-policy-panel.png)
[]![Console tab on the Sites page](/downloads/zero-trust-branch/administration/deployment-configuration/configuring-site-dns-policies/site-dns-console.png)