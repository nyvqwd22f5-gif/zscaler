# About User Risk Scores
Source: https://help.zscaler.com/zpa/about-user-risk-scores
PDF: https://help.zscaler.com/pdf/com/en/1485761.pdf

The user risk score estimates your organization's risk exposure from a particular user. User risk scores are generated based on a user’s DLP violations, risky behavior, unsanctioned cloud application usage, and other suspicious factors. You can [add user risk scores as a criteria type](/zpa/configuring-access-policies) to access policy rules. This lets you identify and quantify risky user behavior, so you can apply access policies to prevent inappropriate access and further enhance your role-based access control. You can [edit and override user risk scores](/zpa/editing-user-risk-scores) as necessary to adjust risk scores to your specific needs.
User risk scores provide the following benefits and enable you to:
- Configure stronger user-specific policies by applying user-level risk exposure.
- Adjust user risk scores to meet user-level requirements for your organization.
User risk scores are not supported in [User Portals](/zpa/about-user-portals) or [Privileged Remote Access Portals](/zpa/accessing-privileged-remote-access-portal).
About the User Risk Scores Page
On the User Risk Scores page (Authentication > User Authentication > User Risk > User Risk Scores), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the User Risk Scores page to reflect the most current information.
-
Filter the information that appears in the table. By default, the **IdP Name** filter is applied and can be cleared. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
When an IdP gets deleted, all user risk scores associated with the users of that IdP are also deleted. The **IdP Name** filter no longer shows the name of the IdP that was deleted.
- View a list of user risk scores. For each user risk score, you can see:
- **Username**: The username associated to the user risk score.
- **Risk Source**: The risk source (e.g., **ZIA**).
- **Risk Score**: The risk score (**Low**, **Medium**, **High**, **Critical**).
- **Risk Expiry**: The date the user risk score expires.
- **Last Updated**: The date the user risk score was last updated.
- **Overridden Risk Score**: Indicates the overridden risk score (**Low**, **Medium**, **High**, **Critical**).
- **Overridden Risk Expiry**: The date the overridden user risk score expires.
- [Override the current risk score](/zpa/editing-user-risk-scores).
- [Edit the current risk score](/zpa/editing-user-risk-scores).
- Reset an overridden risk score to its original risk score value.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
![Viewing and Managing User Risk Scores](/downloads/zpa/authentication/user-risk-scores/about-user-risk-scores/zpa-user-risk-scores.png)