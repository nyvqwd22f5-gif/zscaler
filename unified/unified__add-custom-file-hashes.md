# Adding or Removing Custom File Hashes
Source: https://help.zscaler.com/unified/add-custom-file-hashes
PDF: https://help.zscaler.com/pdf/com/en/1494336.pdf

In addition to the default [Sandbox policy](/unified/about-sandbox) rules, you can add custom MD5 hash values to the Denylist for your organization to block specific files that are applicable to Zscaler Sandbox analysis. You can also add custom MD5 hash values to the Allowlist to allow specific files access.
To add a custom MD5 hash to the Allowlist:
- Go to **Policies **> **Cybersecurity **>** Inline Security **> **Sandbox**, then click on the **Advanced Policy Settings** tab.
- Under **Allowlist**, paste or enter your custom MD5 hash value and click **Add items**.
[See image.](#allowlist)
- Optional: To add a comment to a URL, enter two forward slashes (//) after each URL entry. Separate each entry by pressing `Shift+Enter`.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
To add a custom MD5 hash to the Denylist:
- Go to **Policy** > **Sandbox**, then click on the **Advanced Policy Settings** tab.
- Under **Denylist**, paste or enter your custom MD5 hash value and click **Add items**.
[See image.](#denylist)
- Optional: To add a comment to a URL, enter two forward slashes (//) after each URL entry. Separate each entry by pressing `Shift+Enter`.
- Click **Save **and [activate the change](/unified/saving-and-activating-changes-admin-portal).
To remove a custom MD5 hash from the Allowlist or Denylist:
- Go to **Policy** > **Sandbox**, then click on the **Advanced Policy Settings** tab.
-
Click the **Delete** icon next to the specific value.
[See image.](#delete-hash-value)
-
Click the **Remove** drop-down and either **Remove All** or **Remove Page**.
- **Remove All** deletes all custom file MD5 hashes.
- **Remove Page** deletes only those custom file MD5 hashes on the currently selected page.
[See image.](#remove-hash-value)
[][![Enter custom hash values in the Denylist section of the Advanced Policy Settings for Sandbox](/downloads/zia/policies/sandbox/add-custom-file-hashes/sandbox-denylist.png)
]
[]![Add custom hash values in the Denylist section of the Advanced Policy Settings for Sandbox](/downloads/zia/policies/sandbox/add-custom-file-hashes/sandbox-allowlist.png)
[]![Delete hash value from Advanced Policy Settings tab in the Sandbox](/downloads/zia/policies/sandbox/add-custom-file-hashes/delete-hash-value.png)
[]![Remove a hash value from the Advanced Policy Settings tab in the Sandbox](/downloads/zia/policies/sandbox/add-custom-file-hashes/remove-hash-value.png)