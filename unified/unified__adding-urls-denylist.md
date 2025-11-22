# Adding URLs to the ATP URL Allowlist or Denylist
Source: https://help.zscaler.com/unified/adding-urls-denylist
PDF: https://help.zscaler.com/pdf/com/en/1494256.pdf

Manage URLs by adding them to the allowlist or denylist with the [Advanced Threat Protection policy](/unified/configuring-advanced-threat-protection-policy). You can grant specific URLs permissions to access designated websites, browsers, or applications by adding them to the Allowlist. URLs that have been added to the Allowlist are accessible even if they would otherwise be blocked by other security measures or policies. You can also add specific URLs to the Denylist to block access to these URLs and prevent users from accessing potentially malicious content.
To add a URL to the Allowlist or Denylist:
- Go to **Policies **>** Cybersecurity **>** Inline Security **>** Advanced Threat Protection**.
-
On the **Security Exceptions **page, under **Blocked Malicious URLs **, enter the URLs you want to allow or block for your organization.
[See image.](#blocked-malicious-urls)
You can view the list of blocked malicious URLs on the [Advanced Threat Protection Policy](/unified/configuring-advanced-threat-protection-policy#Malicious) page. Also, you can see the blocked URLs accessed by the users on the [Insights Logs](/unified/about-insights-logs) page. If you need further assistance, contact Zscaler Support.
- Optional: To add a comment to a URL, enter two forward slashes (//) after each URL entry. Separate each entry by pressing `Shift+Enter`.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
To learn how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).
[]![Add URLs you want to allow or block to the Blocked Malicious URLs list in Advanced Threat Protection](/downloads/zia/policies/advanced-threat-protection/adding-urls-denylist/blocked-malicious-urls.png)