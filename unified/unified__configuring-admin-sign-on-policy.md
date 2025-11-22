# Configuring Admin Sign-On Policy
Source: https://help.zscaler.com/unified/configuring-admin-sign-on-policy
PDF: https://help.zscaler.com/pdf/com/en/1505101.pdf

The article describes how to add a sign-on policy from the [Sign-On Policy](/unified/about-sign-on-policies) page. You can add up to 256 policies.
Adding an Admin Sign-On Rule
To configure a sign-on rule:
- Go to **Administration > Admin Management > Administrator Management > Sign-On Policies**.
- Click **Add Rule**.
The **Add Admin** **Sign-On Policy **window appears.
- In the **Add** **Admin Sign-On Policy **window:
- **Rule Order**: Select the rule order. The sign-on policy automatically assigns the **Rule Order** number. Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order.
- **Name**: Enter a name for the rule. The maximum length is 31 characters.
- **Rule Status**: Enabled or disabled the sign-on rule.
- **Description**: Enter additional notes or information. The description cannot exceed 10,240 characters.
- Under the **Criteria **section, configure the criteria to either deny or allow the sign-on request. To add multiple criteria to the rule, click **Add More**. You can add up to 256 criteria.
- **Action**: Select whether you want to **Allow** or **Deny** the access request for the matching rule.
[See image.](#sign-on-policy)
- Click **Save**.
[]![Adding Admin Sign-On Policy](/downloads/zidentity/policies/configuring-sign-on-policy/add-sign-on-policy2.png)