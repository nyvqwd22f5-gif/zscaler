# Viewing the Exposed Endpoint Credential Risk Reduction Roadmap
Source: https://help.zscaler.com/itdr/viewing-exposed-endpoint-credential-risk-reduction-roadmap
PDF: https://help.zscaler.com/pdf/com/en/1531849.pdf

The Risk Reduction Roadmap provides a proactive security approach to improve the security posture of your endpoints. It enables you to view the current risk severity of your endpoints and allows you to systematically lower the severity by providing an actionable remediation roadmap. You can leverage this roadmap to remediate issues and improve the security posture of your endpoints.
ITDR categorizes risk severity into 4 levels: Critical, High, Medium, or Low. Issues with critical severity need immediate attention.
The interactive slider in the Risk Reduction Roadmap on the [Endpoint Credential Exposure dashboard](/itdr/about-endpoint-credential-exposure-dashboard) allows you to view the current risk severity of your endpoints and set a target severity level. For example, if the current risk is Critical, you can adjust the slider to set a goal to lower it to High. After the target is set, ITDR automatically analyzes security issues, prioritizes them based on severity, and provides a clear remediation plan. Each identified risk shows the total number of affected objects (identities with exposed endpoint credentials) and actionable remediation links. You can click the links to view the details to remediate issues and achieve the targeted risk severity for the endpoints.
To view the risk remediation roadmap:
- Go to **ITDR** > **Dashboard** > **Endpoint Credential Exposure**.
-
Select a date from the **As of Date** calendar to view the total number of exposed credential issues on that scan date.
[See image.](#itdr-credex-risk-reduction-roadmap-select-date)
-
In the **Risk Reduction Roadmap** section, adjust the slider to a lower severity level. For example, if your current tenant risk is **Critical**, adjust the slider to **High**.
[See image.](#itdr-credex-risk-reduction-adjust-slider)
ITDR automatically analyzes issues, prioritizes them based on severity, and lists the total number of objects with actionable remediation links.
[See image.](#itdr-credex-view-risk-reduc-roadmap)
-
Select an issue and click **View Remediation**.
The [Detailed Findings](/itdr/viewing-exposed-endpoint-credential-detailed-findings-and-recommendations-details) page opens with the remediation details.
[See image.](#itdr-credex-view-remediation-details)
- Remediate all the issues listed in the roadmap to achieve the target risk severity for your endpoints.
[]![Select a date](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-endpoint-credential-risk-reduction-roadmap/itdr-credex-risk-reduction-scan-date.png)
[]![Adjust the slider to lower the severity](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-endpoint-credential-risk-reduction-roadmap/itdr-about-endpoint-credential-exposure-adjust-slider-2.png)
[]![View remediation details](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-endpoint-credential-risk-reduction-roadmap/itdr-about-endpoint-credential-exposure-remediation-roadmap.png)
[]![Remediation details](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-endpoint-credential-risk-reduction-roadmap/itdr-about-endpoint-credential-exposure-detailed-findings.png)