# Configuring the Password Policy
Source: https://help.zscaler.com/zidentity/configuring-password-policy
PDF: https://help.zscaler.com/pdf/com/en/1499076.pdf

The Password Policy page allows you to configure policies that users must follow while creating or resetting passwords to access their ZIdentity Landing page.
To configure the password policy:
- Go to **Policy **> **Password**.
- Set the **Configuration Type** to **Default **or **Custom**. Zscaler recommends enabling **Default**.** **If you select **Custom,** you need to configure the following fields:
- **Password Length**: Set the minimum length of the password.
- **Minimum No. of Lowercase Letters**: Set the minimum number of lowercase letters required in the password.
- **Minimum No. of Uppercase Letters**: Set the minimum number of uppercase letters required in the password.
- **Minimum No. of Numeric Characters**: Set the minimum number of numeric characters required in the password.
- **Minimum No. of Special Characters**: Set the minimum number of special characters required in the password.
- **Password must not include company name, username, first name, or last name**: Turn on to restrict the user from including their company name, username, first name, or last name in the password.
-
**Reject reuse of last 5 passwords**: &amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;gt;
Turn on to restrict users from reusing their last 5 passwords. Passwords that are changed *after *a 24-hour gap fall under this criterion. Any password changes that occur *within *24 hours are disregarded by the ZIdentity service. For example, if you reset your password 3 times (the second reset being after 24 hours of the first reset, and the third reset being within 24 hours of the second reset), the second password change is disregarded and can be used again as a new password.
If the **Reject reuse of last 5 passwords** option is turned off, users can set any password regardless of what they used previously.
- **Deactivate user after 10 unsuccessful attempts**: &amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;gt;
Turn on to deactivate the user account after 10 unsuccessful login attempts.
- **Allow administrator to create or change user's password**: &amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;gt;
Turn on to allow the administrator to create or change user's password.
- **Enforce password change after the initial login**: &amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;gt;
Turn on to prompt users to change their password after the initial login.
- **Password expiration period (in days)**: &amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;gt;
Set the password expiration period after which users can reset their passwords. You can set the expiration period from 15 to 365 days.
[See image.](#password-policy)
- Click **Save**.
[]
![Password Policy page](/downloads/zslogin/policies/configuring-password-policy/zid-password-policy_0.png)