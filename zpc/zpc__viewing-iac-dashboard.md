# Viewing the IaC Dashboard
Source: https://help.zscaler.com/zpc/viewing-iac-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1394191.pdf

The IaC Dashboard offers insight into your IaC deployment by integrating with your code repositories, continuous integration (CI) and continuous deployment/delivery (CD) tools, and integrated development environments (IDE). To learn more, see [About IaC Integrations](/zpc/about-iac-integrations).
Most dashboard widgets and icons are interactive. You can drill down to view the IaC Dashboard in more detail.
On the IaC Dashboard page (Dashboard > IaC), you can do the following:
- Filter the policy violations based on the time range.
- View **Policy Violations via Scan Plugin**. The policy violation count for all IaC scanner plugins across your CI/CD tools such as GitHub. Click the scan plugin to view the policy on the **Alerts **>** All Alerts List** tab. The policy is filtered based on the scan plugin selected.
- View **Top Policy Violations**. The policy violation count across all the CI/CD tools and version control systems for each policy. Click the policy violation to view the policy on the **Alerts** > **All Alerts List** tab. The policy is filtered based on the policy violation selected.
- View **Policy Violations via Cloud Type**. The Policy violation count for each cloud service provider and Kubernetes categorized by severity. Click the policy violation for any CSP to view the policy on the **Alerts** > **All Alerts List** tab. The policy is filtered based on the cloud selected.
![View the IaC Dashboard on ZPC](/downloads/zpc/dashboards/about-iac-dashboard/iac-dashboard.png)