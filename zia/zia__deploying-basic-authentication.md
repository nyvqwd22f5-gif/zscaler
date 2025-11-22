# Deploying Basic Authentication
Source: https://help.zscaler.com/zia/deploying-basic-authentication
PDF: https://help.zscaler.com/pdf/com/en/1498521.pdf

This article provides instructions on deploying Basic authentication for your organization.
Basic authentication can be deployed for the following workflows:
- [User Enrollment](#user-enrollment)
- [Authenticating Traffic](#authenticating-traffic)
[]To deploy Basic authentication for user enrollment:
- On the Authentication Default Settings page (**Administration **> **Authentication Settings**), ensure that the **Hosted DB **is selected for User Repository Type and **Form-Based **is selected for Authentication Type.
- [Create and activate a user in the ZIA Admin Portal.](/zia/adding-users)
-
Use the following API POST command to enroll users:
`POST /users/<userId>/enroll
Payload:
{
"authMethods" : ["BASIC"],
"password" : "<password>"
}
`
Enter the `<userId>` and `<password>` for the configured user.
See the [ZIA API documentation](/zia/user-management) for more information.
- [Save and activate your changes](/zia/saving-and-activating-changes-zia-admin-portal). This computes an HA1 value and propagates it across the Zscaler service.
[]To deploy Basic authentication for traffic:
- On the Authentication Default Settings page (**Administration **> **Authentication Settings**), ensure that **Hosted DB **is selected for User Repository Type and **Form-Based **is selected for Authentication Type.
-
[Configure a location](/zia/configuring-locations) using your desired forwarding proxy method. Make sure to select **Enforce Authentication **and **Enable Basic Authentication**.
If you enable **Enforce Surrogate IP for Known Browsers**, you must select **Cookie and Proxy **for **Supported Authentication Methods** for IP surrogacy to work.
- [Save and activate your changes](/zia/saving-and-activating-changes-zia-admin-portal).