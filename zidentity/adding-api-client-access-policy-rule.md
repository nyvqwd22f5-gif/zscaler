# Adding API Client Access Policy Rule
Source: https://help.zscaler.com/zidentity/adding-api-client-access-policy-rule
PDF: https://help.zscaler.com/pdf/com/en/1531919.pdf

You can add an API client access policy rule by defining the API resources that API clients can access within a set time frame. An API client can be assigned to only one policy rule at a time.
ZIdentity administrators assigned with Full permission to access the API clients and API resources modules can configure an API client access policy rule. To learn more, see [Admin Roles and Permissions](/zidentity/admin-roles-and-permissions).
To add an API client access policy rule:
- Go to **Policy **>** API Client Access Policy.**
- On the **API Client Access Policy** page, click the **Policy Rule.**
-
On the **Add Policy Rule **page**,** use the query builder to define the policy rule:
- **Criteria (if)**: Define the criteria:
-
Select **Any **from the drop-down menu to apply either **Time **or **Resources **criteria or select **All **to apply both (**Time **and **Resources**) criteria.
This option appears only if both the repeating behavior in the **Time **criteria and the resources scope in the **Resources **criteria are selected.
- **Time**:
- Select the repeating behavior for the rule.
- Select a start date and time. The rule is valid from this date and time.
- Select an end date and time. The rule ends on this date and time.
- Select the time zone in which the rule should be valid.
-
**Resources**:
- Select the API resources that determine the permissions (scope) the API client has to access the API resources of each Zscaler service. To learn more, see [Viewing API Resources](/zidentity/viewing-api-resources).
Click the **Delete **icon to reset the expression, if required.
- **Expression**: The expression appears as you build the query.
- **Rule Action (then)**: Apply the required action (**Allow **or **Block**) to the policy rule you defined in the previous step.
[See image.](#define-criteria)
- Click **Next**.
-
On the **Assign API Clients** page, select the list of API clients to which this policy rule must be applied.
[See image.](#assign-api)
- Click **Next**.
-
On the **Summary **tab:
- Review the information.
- Enter the name of the rule.
[See image.](#summary)
- Click **Save **to create the API client access policy rule.
[]![Define criteria for the policy using the query builder.](/downloads/zidentity/integration/oneapi-authentication/adding-api-client-access-policy-rule/Define-criteria.png)
[]![Select the API clients to assign to the policy rule on Assign API Clients page.](/downloads/zidentity/integration/oneapi-authentication/adding-api-client-access-policy-rule/Assign-API.png)
[]
![Review the API Client Access Policy rule information on the Summary page.](/downloads/zidentity/integration/oneapi-authentication/adding-api-client-access-policy-rule/Summary.png)