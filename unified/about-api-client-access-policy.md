# About the API Client Access Policy
Source: https://help.zscaler.com/zidentity/about-api-client-access-policy
PDF: https://help.zscaler.com/pdf/com/en/1499386.pdf

The API client access policies determine the API client's access to specific API resources within set time frames. Administrators can define the policy rules and assign them to the required API clients to reduce unauthorized activity and control access to API resource.
The API client access policy includes the following benefits:
- Ensures API usage is limited to approved resources.
- Provides API resources availability within specific time frames.
About the API Client Access Policy Page
On the API Client Access Policy page (Policy > API Client Access Policy), you can do the following:
- [Add an API client access policy rule](/zidentity/adding-api-client-access-policy-rule).
- Search for an API client access policy rule by name.
- View the list of API client access policy rules. For each policy rule, you can see:
- **Rule Name**: The name of the API client access policy rule.
-
**API Clients**: The list of API clients to which the policy rule is assigned.
Only one policy rule can be assigned to an API client at a time.
- **Criteria**: The API resources and time parameters defined in the policy rule.
- **Rule Action**: The action (**Allow **or **Block**) that is defined for the policy rule.
- **Rule Status**: The status (**Active** or **Expired**) of the policy rule.
-
[Edit an API client access policy rule](/zidentity/editing-or-deleting-items).
If you update the policy rule that is associated with the API client, then the access token is also updated. Ensure to use the valid access token. To learn more, see [About Access Tokens](/zidentity/about-access-tokens).
-
[Delete an API client access policy rule](/zidentity/editing-or-deleting-items).
You cannot delete the policy rule if any API client is associated with it.
- View details of an API client access policy rule.
![API client access policy page with all the fields annotated.](/downloads/zidentity/integration/oneapi-authentication/about-api-client-access-policy/About-api-client-access-policy.png)