# Viewing Password Analysis Details and Remediating Issues
Source: https://help.zscaler.com/itdr/viewing-password-analysis-details-remediate-issues
PDF: https://help.zscaler.com/pdf/com/en/1531851.pdf

The Details page provides details on password weaknesses and attributes for the privileged and non-privileged accounts in an Active Directory (AD) domain. Make sure to [enable attribute collection](/itdr/enabling-active-directory-attribute-collection) for Zscaler ITDR to collect AD user account attributes.
To view password analysis details:
- Go to **ITDR** > **Dashboard** > **Password Analysis**.
- Click the **Details** tab.
-
Select an AD domain to view the following password details for that particular domain:
- **Sam Account Name**: The username of the AD user account.
- **User Principal Name**: The AD user account username and domain in an email address format.
- **Password Last Set**: The date and time the password was last changed.
- **Password Reuse Count**: The total number of times a password is reused across AD user accounts within a domain, which increases security risks.
- **Password Rotation**: Indicates whether a unique password is used by an AD user account each time a password is changed. Some users tend to reuse the same 2 or 3 passwords during rotation. ITDR checks the user account's password history to verify that no previously used passwords have been reused. You can select **True** or **False** from the drop-down menu to filter the details.
- **Is Privileged Account**: Indicates if the AD user account is privileged or not. You can select **Yes** or **No** from the drop-down menu to filter the accounts. A green check mark indicates a privileged account, and a red **X** indicates a non-privileged account.
- **Password Weakness**: View passwords based on the following weaknesses:
- **Crackable**: Passwords that can be easily cracked.
- **Leaked**: Passwords found in publicly exposed databases.
- **Weak Password List**: Assess the exposure risks based on the following options:
- **Crackable Passwords**: Passwords that can be easily guessed or cracked using brute force or dictionary attacks.
- **Custom Keywords Dictionary**: Passwords that match a predefined list of organization-specific weak keywords.
- **Have I Been Pwned**: Passwords that have appeared in publicly known data breaches.
- **Have I Been Pwned (Top 1 Million)**: Passwords that are most frequently used and exposed from breached databases.
- **Keyboard Walks**: Passwords created using predictable keyboard patterns (e.g., qwerty, 123456, etc.).
- **Leaked Dictionaries**: Passwords found in various leaked credential databases available online.
- **Actions**: Remediate AD users with weak passwords.
[See image.](#itdr-pwd-any-details-page)
Remediating AD Users with Weak Passwords
On the Details page, you can remediate privileged and non-privileged AD user accounts with password weaknesses and attributes.
To remediate AD users:
- On the **Details** tab, select an AD domain to view the password details for that domain.
- Do one of the following:
-
Select an AD user account. Under **Actions**, click the **Remediation** icon, and then select a remediation action. For example, select **Disable User**.
[See image.](#itdr-ad-rem-pwd-single)
-
Select multiple AD user accounts. Click **Remediations**, and then select a remediation action to run in bulk. For example, select **Reset Password**.
[See image.](#itdr-ad-rem-pwd-bulk)
- Click **OK** in the confirmation window.
[]![View password analysis details](/downloads/itdr/dashboard/password-analysis/viewing-password-analysis-details/itdr-ad-password-analysis-details-tab-2.png)
[]![Select a remediation action](/downloads/itdr/dashboard/password-analysis/running-remediations-ad-identities-password-weaknesses/itdr-ad-rem-password-analysis-details-single-2.png)
[]![Select a remediation action](/downloads/itdr/dashboard/password-analysis/running-remediations-ad-identities-password-weaknesses/itdr-ad-rem-password-analysis-details-bulk-1.png)