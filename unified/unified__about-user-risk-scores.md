# About User Risk Scores
Source: https://help.zscaler.com/unified/about-user-risk-scores
PDF: https://help.zscaler.com/pdf/com/en/1491346.pdf

The user risk score estimates your organization's risk exposure from a particular user. User risk scores are generated based on a user’s DLP violations, risky behavior, unsanctioned cloud application usage, and other suspicious factors. You can [add user risk scores as a criteria type](/unified/configuring-access-policies) to access policy rules. This lets you identify and quantify risky user behavior, so you can apply access policies to prevent inappropriate access and further enhance your role-based access control. You can [edit and override user risk scores](/unified/editing-and-overriding-user-risk-scores) as necessary to adjust risk scores to your specific needs.
User risk scores provide the following benefits and enable you to:
- Configure stronger user-specific policies by applying user-level risk exposure.
- Adjust user risk scores to meet user-level requirements for your organization.
User risk scores are not supported in [User Portals](/unified/about-user-portals) or [Privileged Remote Access Portals](/unified/accessing-privileged-remote-access-portal).
About the User Risk Scores Page
On the User Risk Scores page (Administration > Identity > Private Access > User Risk Scores), you can do the following:
- View a list of user risk scores. For each user risk score, you can see:
- **Username**: The username associated to the user risk score.
- **Risk Source**: The risk source (e.g., **ZIA**).
- **Risk Score**: The risk score (**Low**, **Medium**, **High**, **Critical**).
- **Risk Expiry**: The date the user risk score expires.
- **Last Updated**: The date the user risk score was last updated.
- **Overridden Risk Score**: Indicates the overridden risk score (**Low**, **Medium**, **High**, **Critical**).
- **Overridden Risk Expiry**: The date the overridden user risk score expires.
-
Filter the information that appears in the table. By default, the **IdP Name** filter is applied and can be cleared.
When an IdP gets deleted, all user risk scores associated with the users of that IdP are also deleted. The **IdP Name** filter no longer shows the name of the IdP that was deleted.
- [Override the current risk score](/unified/editing-and-overriding-user-risk-scores).
- [Edit the current risk score.](/unified/editing-and-overriding-user-risk-scores)
- Reset an overridden risk score to its original risk score value.
- [Modify the display of columns in the table.](/unified/using-tables)
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they are viewable. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables).
- Hide the filters on the page by clicking the **Filter** icon (![zpa-show-hide-filter-icon.png](/downloads/zpa/authentication/user-risk-scores/about-user-risk-scores/zpa-show-hide-filter-icon.png)
). Click the icon again to show the filters.
- Refresh the User Risk Scores page to reflect the most current information.
![Viewing and Managing User Risk Scores](/downloads/zpa/authentication/user-risk-scores/about-user-risk-scores/zpa-user-risk-scores-page.png)