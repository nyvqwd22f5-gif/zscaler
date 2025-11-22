# About Sign-On Policies
Source: https://help.zscaler.com/unified/about-sign-on-policies
PDF: https://help.zscaler.com/pdf/com/en/1505096.pdf

The Admin Sign-On Policy page displays all the sign-on rules configured for the users. The sign-on rules determine whether to allow or deny a user from accessing the Zscaler service. You can use different attributes to configure rules and apply them to the users.
The sign-on policy is not applicable to the super admin (admin@<vanityurl>.zslogin.net). Super admin is the primary user account that was created when onboarding your tenant.
Sign-On policies provide the following benefits and enable you to:
- Configure policies to control which users within your organization can access the Admin Portal.
- Enforce condition-based access control for the users, such as [trusted IP locations](/unified/about-trusted-ip-locations) and [trusted IP location groups](/unified/about-trusted-ip-location-groups).
About the Admin Sign-On Policy Page
On the Admin Sign-On Policy page (Administration > Admin Management > Administrator Management > Sign-On Policies), you can do the following:
- [Add a sign-on rule](/unified/configuring-admin-sign-policy).
- View a list of all configured sign-on rules. For each rule, you can see:
- **Rule Order**: The policy rule's order number. Sign-on rules are evaluated in ascending numerical order.
- **Rule Name**: The name of the rule.
- **Criteria**: The criteria that triggers the rule.
-
**Rule Action**: The action (Allow or Deny) taken when a rule is triggered.
ZIdentity follows the Allow rule by default, so unless a Deny rule is created, it implicitly allows everything.
- **Rule Status**: The status (Enabled or Disabled) of the rule.
- **Description**: The description of the rule, if available.
- Edit a sign-on rule.
- Delete the sign-on rule.
- Enable or disable a sign-on rule.
![Admin Sign-On Policy page](/downloads/zidentity/policies/about-sign-on-policies/adminSign-on-policy.png)