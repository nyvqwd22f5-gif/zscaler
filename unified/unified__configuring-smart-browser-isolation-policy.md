# Configuring Smart Browser Isolation Policy
Source: https://help.zscaler.com/unified/configuring-smart-browser-isolation-policy
PDF: https://help.zscaler.com/pdf/com/en/1494406.pdf

You can configure a Smart Browser Isolation policy that automatically isolates potentially malicious web content using the AI/ML models. This policy identifies suspicious websites and decrypts them using SSL inspection and presents the users with a rendition of the actual websites in a remote browser using Isolation.
Enable the **Inspect Inbound Traffic** and **Inspect Outbound Traffic** toggles on the **Malware Protection** page (**Policies **>** Cybersecurity **>** Inline Security **>** Malware Protection **>** Malware Policy**) for the **Smart Browser Isolation** policy to work.
To configure the Smart Browser Isolation policy:
- Go to **Policies **>** Cybersecurity **>** Inline Security **>** Secure Browsing**.
- On the **Smart Isolate **tab:
- **Enable AI/ML based Smart Browser Isolation**: Enable this option to protect users from suspicious websites hosting malicious active content using AI/ML models, which continually identify suspicious domains. Enabling this option automatically creates an editable SSL inspection rule to decrypt suspicious websites. When this feature is enabled, the following options appear:
- **Users**: Select the users to which the policy applies. You can select up to 32 users. If you select no values, policy evaluation ignores this criterion.
-
**Groups**: Select the groups to which the policy applies. You can select up to 32 groups. If you select no values, policy evaluation ignores this criterion.
Contact Zscaler Support to increase the limit of **Users **or **Groups**.
-
**Browser Isolation Profile**: You can choose the isolation profile to which the policy applies.
Ensure to [create isolation profiles](/unified/creating-isolation-profiles-internet-saas) for your organization in the Admin Portal for them to be available in this field.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).