# About Microsegmentation Policies
Source: https://help.zscaler.com/zpa/about-microsegmentation-policies
PDF: https://help.zscaler.com/pdf/com/en/1531962.pdf

Admins can create Layer 3 and Layer 4 Microsegmentation enforcement policies to protect east-west traffic in both cloud and data center environments. By anchoring the policy with a [resource group](/zpa/about-resource-groups), a rule is built around that with other dynamic criteria to enforce either allowing or blocking certain traffic.
The Resource Policy page provides the following benefits and enables you to:
- View the list of configured policies for your organization.
- View policy hit status.
- Configure new policy rules.
- Filter policies based on rule data.
After you've configured Microsegmentation policies, they appear on the Resource Policy page. To learn more, see [Configuring Microsegmentation Policies](/zpa/configuring-microsegmentation-policies).
About the Resource Policy Page
On the Resource Policy page (Microsegmentation > Policy > Resource Policy), you can do the following:
- Refresh the Resource Policy page to reflect the most current information.
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Show or hide filter options.
- Filter the table information by **Name**, **Rule Action**,** Scope**, **Source**, **Destination**, or** Rule ID**. By default, no filters are applied.
- Add a [new policy rule](/zpa/configuring-microsegmentation-policies).
- A view of the [policy settings](/zpa/enabling-microsegmentation-policy-settings) statuses.
- View a list of all policies that are configured for your organization. For each policy rule, you can see:
- **Priority**: The ranking of which policy rule should be applied first.
- **Name**: The name of each policy rule.
- **Source**: The source location for the policy rule.
- **Destination**: The destination location for the policy rule.
- **Protocol**: The protocols added to the policy rule.
- **Scope**: The AppZone the policy rule should affect.
- **Rule Action**: The command for the policy rule to apply.
- **Last Hit**: The last time the policy rule was triggered.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Click a policy name to expand the sideview of its details.
[See image.](#side-view-details)
- [Edit](/zpa/editing-microsegmentation-policy) the policy rule.
- [Delete](/zpa/deleting-microsegmentation-policy) the policy rule.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Policy Map](/zpa/viewing-microsegmentation-policy-map) page to view, monitor, and analyze configured policy rules.
- Go to the [Settings](/zpa/enabling-microsegmentation-policy-settings) page to view and manage options for policy enforcement access and the default policy rule.
![About-Resource-Policy_page_2.png](/downloads/zpa/microsegmentation/policy/about-microsegmentation-policies/About-Resource-Policy_page_2.png)
[]![The sideview details page expanded in the Resource Policy page. ](/downloads/zpa/microsegmentation/policy/about-microsegmentation-policies/policy-rule-sideview-expanded.png)