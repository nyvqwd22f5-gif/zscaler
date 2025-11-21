# Viewing Risk Factors
Source: https://help.zscaler.com/unified/viewing-risk-factors
PDF: https://help.zscaler.com/pdf/com/en/1526551.pdf

The Factors page (Analytics > Risk360 > Factors) shows the list of contributing factors that are affecting your organization's risk score. The Risk360 service quantifies each factor according to its risk weight, which then adds to your overall organization risk score and also maps these factors to various renowned risk and security frameworks like MITRE, NIST, etc.
Contributing Factors to Organizational Risk Score
From the top right of the page, you can select how you want to view the page. Based on your selection, the page updates to the following views:
- [Attack-Based](#attack-stage)
- [Entity-Based](#entity)
[]The attack view shows the factors in a single list.
In this view, you can:
- Export the factors contributing to your organization's risk score into a CSV file. The downloaded file shows all the factors contributing to your organization's risk score, irrespective of any filter selected at the time of the download.
- Switch to the entity-based view (**Tree View**).
- View the category-based risk score for your organization.
- Search for a factor.
- View a list of all the contributing factors to your organization's risk score. For each factor, you can see:
- **Factor Name**: The name of the contributing factor affecting the risk score.
- **Category**: The category the factor falls under.
- **Your Score**: The score for the contributing factor. The total score for a factor depends on its severity (0 being a healthy score).
- **Last 30 Days**: The graph showing the last 30-day score trend for that factor.
- **Entities**: The entities affected by the factor.
- **Licensed?**: Whether you are subscribed to the required feature to implement the recommended action (**Y** for Yes and **N** for No).
-
**Recommended Actions**: The recommended action proposed to attain a healthy risk score.
Click on any of the columns (except Licensed?, Include, and Entities) to view more information about the factor in the drawer view:
- [Drawer](#category-drawer)
-
Disable this option to remove the factor from risk score computation by providing an explanation. By default, this option is enabled for all factors. You can exclude a factor if you have a compensating control over the factor or any other reason. Compensating controls are supplementary security measures that are implemented to protect against identified risks or threats (e.g., multi-factor authentication, firewalls, antivirus software). The changes made by the admin are captured in the [audit logs](/unified/about-risk360-audit-logs) with the username and reason provided for the change.
[See image.](#factor-overrirde-reason)
![Contributing Factors to Organizational Risk Score](/downloads/unified/analytics/unified-dashboards/risk/viewing-contributing-factors-organizational-risk-score/Experience-Center-Factors-page..png)
[]The drawer consists of the following tabs:
Details
On the Details tab, you can view the following information:
- The name of the factor.
- **Severity**: The severity of the factor.
- **Recommended Actions**: The recommended action proposed to attain a healthy risk score.
- **Description**: Detailed information about the factor, useful help article links, and a link that redirects you to the Zscaler service's admin portal that is responsible for the factor, if available.
- **Related Recommendation Cards**: The related discovered problems and their recommendations.
Each problem or factor affecting your organization's risk is visualized in the form of Cards on the Insights Page.
![The Drawer view for the factors in the Risk360 Portal](/downloads/tech-pubs-drafts/risk360-draft-articles/about-factors-draft-0/Risk360-Factors-page-drawer_0.png)
Compliance
On the Compliance tab, you can view a list of recognized cybersecurity frameworks and their control IDs mapped to the factor. Click on the control ID; you're redirected to the framework's website where the control IDs are explained in detail.
![Compliance tab in the Factors tab](/downloads/risk360/dashboard-analytics/analyzing-risk-nist-csf/Risk360-factor-compliance-tab.png)
[]The entity-based view shows the factors listed within their category.
In this view, you can:
- Export the factors contributing to your organization's risk score into a CSV file. The downloaded file shows all the factors contributing to your organization's risk score, irrespective of any filter selected at the time of the download.
- Switch to the attack-based view (**List View**).
- Filter factors for specific entities by clicking the entity tiles. To deselect an entity, click on it again.
- View the contributing factors to your organization's risk score. For each factor, you can see:
- **Factor Name**: The name of the contributing factor affecting the risk score.
- **Recommended Actions**: The recommended action proposed to attain a healthy risk score.
- **Licensed?**: Whether you are subscribed to the required feature to implement the recommended action (**Y** for Yes and **N** for No).
- **Your Score**: The score for the contributing factor. The total score for a factor depends on its severity (0 being a healthy score).
- **Last 30 Days**: The graph shows the last 30-day score trend for the factor.
-
**Include**: Whether the factor is enabled for risk score computation.
Click on any of the columns (except Licensed? and Include) to view more information about the factor in the drawer view:
- [Drawer](#entity-drawer)
-
Disable this option to remove the factor from risk score computation by providing an explanation. By default, this option is enabled for all factors. You can exclude a factor if you have a compensating control over the factor or any other reason. Compensating controls are supplementary security measures that are implemented to protect against identified risks or threats (e.g., multi-factor authentication, firewalls, antivirus software). The changes made by the admin are captured in the [audit logs](/unified/about-risk360-audit-logs) with the username and reason provided for the change.
[See image.](#factore-override-reason-2)
- Show or hide the factors for a specific category.
![Factors Page: Category View](/downloads/risk360/dashboard-analytics/about-factors/Risk360-Factors-page-Tree-View.png)
[]
The drawer consists of the following tabs:
Details
On the Details tab, you can view the following information:
- The name of the factor.
- **Severity**: The severity of the factor.
- **Recommended Actions**: The recommended action proposed to attain a healthy risk score.
- **Description**: Detailed information about the factor, useful help article links, and a link that redirects you to the Zscaler service's admin portal that is responsible for the factor, if available.
- **Related Recommendation Cards**: The related discovered problems and their recommendations.
![The Drawer view for the factors in the Risk360 Portal](/downloads/tech-pubs-drafts/risk360-draft-articles/about-factors-draft-0/Risk360-Factors-page-drawer.png)
Compliance
On the Compliance tab, you can view a list of recognized cybersecurity frameworks and their control IDs mapped to the factor. Click on the control ID; you're redirected to the framework's website where the control IDs are explained in detail.
![Compliance tab in the drawer](/downloads/risk360/dashboard-analytics/analyzing-risk-nist-csf/Risk360-factor-compliance-tab.png)
[]![Factor Override Note WIndow](/downloads/risk360/dashboard-analytics/about-factors/Risk360-Factor-Override-Explanation.png)
[]![Factor Override Note WIndow](/downloads/risk360/dashboard-analytics/about-factors/Risk360-Factor-Override-Explanation.png)