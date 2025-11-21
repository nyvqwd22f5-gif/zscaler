# Viewing the Active Directory Risk Reduction Roadmap
Source: https://help.zscaler.com/itdr/viewing-active-directory-risk-reduction-roadmap
PDF: https://help.zscaler.com/pdf/com/en/1531847.pdf

The Risk Reduction Roadmap provides a proactive security approach to improve the security posture of your Active Directory (AD) domain. It enables you to view the current risk score of your AD domain and allows you to streamline efforts to reduce the current risk severity by providing an actionable remediation roadmap. You can leverage this roadmap to remediate issues and improve the security posture of your AD domain.
ITDR categorizes risk severity into 4 levels: Critical, High, Medium, or Low. Issues with critical severity need immediate attention.
The interactive slider in the Risk Reduction Roadmap on the [Active Directory Posture](/itdr/about-identity-posture-dashboard) dashboard allows you to view the current risk severity and set a target severity level. For example, if the current risk is Critical, you can adjust the slider to set a goal to lower it to High. After the target is set, ITDR automatically analyzes security issues, prioritizes them based on severity, and provides an actionable remediation plan. Each identified risk shows the total number of affected objects (users and computers) and actionable remediation links. You can click the links to view remediation flowcharts or step-by-step instructions to remediate issues and achieve the targeted risk severity for the AD domain.
To view the risk remediation roadmap:
- Go to **ITDR** > **Dashboard** > **Active Directory Posture**.
-
On the **Active Directory Posture** dashboard:
- Select an AD domain from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#itdr-ad-risk-reduction-ad-domain-timestamp)
The scan result for the AD domain appears.
-
In the **Risk Reduction Roadmap** section, adjust the slider to a lower severity level. For example, if your current AD domain risk is **Critical**, adjust the slider to **High**.
[See image.](#itdr-ad-risk-reduction-adjust-slider)
ITDR analyzes issues, prioritizes them based on severity, and lists the total number of objects with actionable remediation links. You can view the total number of issues that you need to remediate on priority to achieve the target risk severity level.
[See image.](#itdr-ad-view-risk-reduc-roadmap)
-
Select an issue and click **View Remediation**.
The [Detailed Findings and Recommendations](/itdr/viewing-issue-finding-recommendation-details) page opens with the remediation flowcharts or step-by-step remediation instructions.
[See image.](#itdr-ad-view-remediation-details)
- Remediate all the issues listed in the roadmap to achieve the target risk severity for your AD domain.
[]![Select an AD domain and scan timestamp](/downloads/itdr/dashboard/active-directory/viewing-active-directory-risk-reduction-roadmap/itdr-ad-post-scan-domain-date-without-options.png)
[]![Adjust the slider to a lower risk score](/downloads/itdr/dashboard/active-directory/viewing-active-directory-risk-reduction-roadmap/itdr-ad-risk-roadmap-slider-adjust-1.png)
[]![View remediation details](/downloads/itdr/dashboard/active-directory/viewing-active-directory-risk-reduction-roadmap/itdr-ad-risk-roadmap-issue-list-view-remediation-2.png)
[]![View remediation details](/downloads/itdr/dashboard/active-directory/viewing-active-directory-risk-reduction-roadmap/itdr-ad-risk-roadmap-remediation-details-1.png)