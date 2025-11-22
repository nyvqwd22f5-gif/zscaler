# Configuring the Password Settings Module
Source: https://help.zscaler.com/deception/configuring-password-settings-module
PDF: https://help.zscaler.com/pdf/com/en/1531301.pdf

The Password Settings module in landmine policies enables you to create customized decoy credentials, which are placed in browser lures, session lures, and file decoys.
To configure password settings for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use to deploy customized decoy credentials in lures and decoys on endpoints, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
- In the policy configuration window:
- Click **Password Settings**.
- Select **Enabled** to deploy password settings when the policy is distributed.
- Enable or disable the following password characteristics per your requirements:
- **Must have special characters**
- **Must have at least one uppercase letter**
- **Must have digits**
- Enter the **Min Length** for the passwords.
- Enter the** Max Length** for the passwords.
-
Enter a list of **Password Keywords** that must be used as a part of the base password.
[See image.](#zd-password-settings)
Make sure that the password settings are similar to your organization's password policy. Use keywords matching your organization name, project name, or internal code name. Alternatively, you can use generic terms that are used in a weak password, as such weak passwords lure attackers.
- Click **Save**.
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-password-settings-module/deception-landmine-policy-edit-one.png)
[]![A screenshot of the Password Settings module in a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-password-settings-module/zscaler-deception-password-settings.png)