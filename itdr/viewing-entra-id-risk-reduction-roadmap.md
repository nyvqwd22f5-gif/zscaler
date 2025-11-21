# Viewing the Entra ID Risk Reduction Roadmap
Source: https://help.zscaler.com/itdr/viewing-entra-id-risk-reduction-roadmap
PDF: https://help.zscaler.com/pdf/com/en/1531848.pdf

The Risk Reduction Roadmap provides a proactive security approach to improve the security posture of your Entra ID tenant. It enables you to view the current risk severity of your tenant and allows you to systematically lower the severity by providing an actionable remediation roadmap. You can leverage this roadmap to remediate issues and improve the security posture of your Entra ID tenant.
Zscaler ITDR categorizes risk severity into 4 levels: Critical, High, Medium, or Low. Issues with critical severity need immediate attention.
The interactive slider in the Risk Reduction Roadmap on the [Entra ID Posture](/itdr/about-entra-id-posture-dashboard) dashboard allows you to view the current risk severity level and set a target severity level. For example, if the current risk is Critical, you can adjust the slider to set a goal to lower it to High. After the target is set, ITDR automatically analyzes security issues, prioritizes them based on severity, and provides an actionable remediation plan. Each identified risk shows the total number of affected objects (users, service principals, and configurations) and actionable remediation links. You can click the links to view remediation flowcharts or step-by-step instructions to remediate issues and achieve the targeted risk severity for the Entra ID tenant.
To view the risk remediation roadmap:
- Go to **ITDR** > **Dashboard** > **Entra ID Posture**.
-
On the **Entra ID Posture **dashboard:
- Select a tenant from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#entra-dashboard-result)
The scan result for the Entra ID tenant appears.
-
In the **Risk Reduction Roadmap** section, adjust the slider to a lower severity level. For example, if your current tenant risk is **Critical**, adjust the slider to **High**.
[See image.](#itdr-entra-id-risk-reduction-adjust-slider)
ITDR automatically analyzes issues, prioritizes them based on severity, and lists the total number of objects with actionable remediation links.
[See image.](#itdr-entra-id-view-risk-reduc-roadmap)
-
Select an issue and click **View Remediation**.
The [Detailed Findings and Recommendations](/itdr/viewing-entra-id-findings-recommendations) page opens with the remediation flowcharts or step-by-step remediation instructions.
[See image.](#itdr-entra-id-view-remediation-details)
- Remediate all the issues listed in the roadmap to achieve the target risk severity for your Entra ID tenant.
[]![Adjust the slider to set lower severity level](/downloads/itdr/dashboard/entra-id/viewing-entra-id-risk-reduction-roadmap/itdr-entra-id-risk-reduction-roadmap-set-target-severity-1.png)
[]![View remediation details](/downloads/itdr/dashboard/entra-id/viewing-entra-id-risk-reduction-roadmap/itdr-entra-id-risk-roadmap-issue-list-view-remediation-1.png)
[]![View remediation details](/downloads/itdr/dashboard/entra-id/viewing-entra-id-risk-reduction-roadmap/itdr-entra-id-risk-reduction-roadmap-remediation-details.png)
[]![The Entra ID Posture dashboard with annotation around Result for and scanned on options.](/downloads/itdr/dashboard/entra-id/viewing-entra-id-risk-reduction-roadmap/itdr-entra-id-post-scan-domain-date-without-options.png)