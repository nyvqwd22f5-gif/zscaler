# Configuring the Lure Settings Module
Source: https://help.zscaler.com/deception/configuring-lure-settings-module
PDF: https://help.zscaler.com/pdf/com/en/1531308.pdf

The Lure Settings module enables you to use IP addresses instead of hostnames of decoys in lures. This setting affects all the lures in the landmine policy.
To configure lure settings for a landmine policy:
- Go to **Deceive **> **Landmine **> **Policies**.
-
In the landmine policies table, locate the landmine policy you want to use to deploy the lure settings on the endpoints, and click the **Edit **icon.
[See image.](#option-to-edit-policy)
-
In the policy configuration window, click **Lure Settings**, and configure the required settings:
- **Use IP addresses instead of hostnames of decoys in lures**: Enable to ensure that IP addresses are used instead of hostnames for decoys across the landmine policy.
- **Custom Username Configuration**: Enable and choose a dataset from the **Username Datalist** drop-down menu. When this option is enabled, usernames for session and credential lures are selected randomly from this list.
[See image.](#zd-lure-settings)
- Click **Save**.
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/configuring-lure-settings-module/deception-landmine-policy-edit-one.png)
[]![Configuring Lure Settings](/downloads/deception/deceive/landmine-decoys/policies/configuring-lure-settings-module/deception-lure-settings-new.png)