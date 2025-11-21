# About the SaaS Dashboard
Source: https://help.zscaler.com/zia/about-saas-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1529895.pdf

When you access Zscaler [Advanced SaaS Security Posture Management (SSPM)](/zia/what-advanced-posture-management), the Software as a Service (SaaS) dashboard displays automatically. The dashboard contains 10 predefined widgets with information about the overall posture score, posture score over time, and top risky controls, accounts, and apps.
This feature is in limited availability. To access this feature, contact your Zscaler Account team.
The SaaS dashboard provides the following benefits and enables you to:
- View a high-level overview of the posture score across all apps, platforms, and user accounts.
- Understand whether the overall posture improved or declined over time.
- Identify the top risky controls, apps, and accounts that must be attended to immediately.
About the SaaS Dashboard Page
On the SaaS dashboard page, you can view the following predefined widgets:
- [1. Integrations](#Integrations)
- [2. Overall Posture Score](#Overall-Posture-Score)
- [3. Posture Score Breakdown](#Posture-Score-Breakdown)
- [4. Posture Score Over Time](#Posture-Score-Over-Time)
- [5. Controls by Risk Level](#Controls-by-Risk-Level)
- [6. Accounts by Risk Level](#Accounts-by-Risk-Level)
- [7. Apps by Risk Level](#Apps-by-Risk-Level)
- [8. Top Risky Controls](#Top-Risky-Controls)
- [9. Top Risky Accounts](#Top-Risky-Accounts)
- [10. Top Risky Apps](#Top-Risky-Apps)
![SaaS Dashboard showing all widgets](/downloads/tech-pubs-drafts/zia-draft-articles/about-saas-dashboard-draft-doc-58548/Saas_Dashboard_New.png)
[]The **Integrations** banner displays buttons for each currently configured integration, as well as an **All** button that is clicked by default, so the dashboard displays the status for all integrations. This banner appears on all pages in Advanced SSPM. You can filter the platforms by tenant or by label:
- **Filter by Tenant**: Click this button to filter the platforms by tenant.
-
To view the status for an individual integration (e.g., **Google Workspace**), click the button for that integration.
You can select multiple integration views simultaneously. To revert to seeing all integrations, click **All**.
- To add another integration, click **Connect**. To learn more, see [Connecting Your Platforms to 3rd-Party App Governance](/zia/connecting-your-platforms-3rd-party-app-governance).
- To select one or more tenants for a platform, click the arrow on the button for that platform, and select the desired tenants from the drop-down menu. When you select a platform, all the tenants for that platform are selected by default.
[See image.](#Tenants-Drop-Down-Menu)
When a single tenant or multiple tenants are onboarded, a **Pending** icon appears next to the tenants and the relevant platform to indicate that the tenants are still being processed. An **Error** icon appears next to the tenants and the relevant platform to indicate an error.
- **Filter by Label**: Click this button to filter the platforms by labels such as **Legacy**,** Staging**, and **Production**.
-
To view the status for an individual label (e.g.,** Production**), click the button for that label.
You can select multiple labels simultaneously. To revert to seeing all labels, click **All**.
- To select one or more tenants under a label, click the arrow on the button for that label, and select the desired tenants from the drop-down menu. You can also search for a tenant or add a new tenant.
[See image.](#Labels-Drop-Down-Menu)
- **Manage Labels**: You can add and manage labels for the tenants. To add a new label:
- Click **Manage Labels, **and then** **click** New Label.**
- Enter the label name, and select a color and the tenants for the label in the **Add New Label** window.
[See image.](#Add-New-Label-Window)
To edit or delete a label, click the **Edit **or** Delete **icon next to the label in the **Manage Labels** window.
[See image.](#Manage-Labels-Window)
You must have user or admin permissions to add or manage labels. To learn more, see [About Roles in 3rd-Party App Governance](/zia/about-roles-3rd-party-app-governance).
[]The **Overall Posture Score** widget displays an overview of the posture score across all apps, platforms, and user accounts. It displays the posture score out of 10 along with its rating.
[]The **Posture Score Breakdown** widget displays the breakdown of the posture score by risky apps, platforms, and accounts. The score breakdown represents negative contributions from the apps, platforms, and accounts to the overall score.
[]The** Posture Score Over Time** widget displays a graph showing the posture score over a period of time. You can use the filters to view the overall posture score or the posture score for platforms, user accounts, or apps over a specific time period.
[]The **Controls by Risk Level **widget displays the total number of controls and a breakdown of the controls by their risk level. It also displays the number of recently added or removed controls. Click any number to view further details on the [Posture page](/zia/about-posture).
[]The** Accounts by Risk Level **widget displays the total number of accounts and a breakdown of the accounts by their risk level. It also displays the number of recently added or removed accounts. Click any number to view further details on the [User Inventory](/zia/about-user-inventory).
[]The **Apps by Risk Level** widget displays the total number of apps and a breakdown of the apps by their risk level. It also displays the number of recently added or removed apps. Click any number to view further details on the [App Inventory](/zia/about-app-inventory).
[]The** Top Risky Controls** widget displays the list of controls with the highest severity levels. Click any control to open the [Control Panel](/zia/about-control-panel) and view further details. Click **Show More** to view further details on the **Posture** page.
[]The** Top Risky Accounts** widget displays the list of user accounts with the highest risk scores. Click any account to open the [User Panel](/zia/about-user-panel) and view further details. Click **Show More** to view further details on the **User Inventory**.
[]The** Top Risky Apps** widget displays the list of apps with the highest risk scores. Click any app to open the [App Panel ](/zia/about-app-panel)and view further details. Click **Show More** to view further details on the** App Inventory**.
[]![Integrations Banner showing Tenants Drop-Down Menu](/downloads/tech-pubs-drafts/zia-draft-articles/about-3rd-party-app-governance-dashboard-draft-doc-54149/Integrations_Banner_TenantList.png)
[]![Image]()
![Integrations Banner Labels Drop-Down Menu](/downloads/tech-pubs-drafts/zia-draft-articles/about-3rd-party-app-governance-dashboard-Draft-Doc58548/Labels_Drop_Down.png)
[]![Add New Label Window showing label details](/downloads/tech-pubs-drafts/zia-draft-articles/about-3rd-party-app-governance-dashboard-Draft-Doc58548/Add_New_Label_Window.png)
[]![Manage Labels Window showing the list of labels](/downloads/tech-pubs-drafts/zia-draft-articles/about-3rd-party-app-governance-dashboard-Draft-Doc58548/Manage_Labels.png)