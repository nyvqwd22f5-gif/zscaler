# Configuring Smart Browser Isolation Policy
Source: https://help.zscaler.com/zia/configuring-smart-browser-isolation-policy
PDF: https://help.zscaler.com/pdf/com/en/1402926.pdf

You can configure a Smart Browser Isolation policy that automatically isolates potentially malicious web content using the AI/ML models. This policy identifies suspicious websites and decrypts them using SSL Inspection and presents the users with a rendition of the actual websites in a remote browser using [Isolation](/zia/about-cloud-browser-isolation).
Enable the **Inspect Inbound Traffic** and **Inspect Outbound Traffic** toggles on the **Malware Protection** page (**Policy** > **Malware Protection** > **Malware Policy**) for the **Smart Browser Isolation** policy to work.
To configure the Smart Browser Isolation policy:
- Go to **Policy** > **Secure Browsing **> **Smart Isolate**.
-
**Enable AI/ML based Smart Browser Isolation**: Enable this option to protect users from suspicious websites hosting malicious active content using AI/ML models, which continually identify suspicious domains. Enabling this option automatically creates an editable SSL inspection rule to decrypt suspicious websites. When this feature is enabled, the following options appear:
- **Users**: Select the users to which the policy applies. You can select up to 32 users. If you select no values, policy evaluation ignores this criterion.
-
**Groups**: Select the groups to which the policy applies. You can select up to 32 groups. If you select no values, policy evaluation ignores this criterion.
Contact Zscaler Support to increase the limit of **Users** or **Groups**.
-
**Browser Isolation Profile**: You can choose the isolation profile to which the policy applies.
Ensure to [create isolation profiles](/zia/creating-isolation-profile-cloud-browser-isolation) for your organization in the ZIA Admin Portal for them to be available in this field.
[See image.](#smart-isolate)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
![Smart Isolate Page showing the Smart Browser Isolate and Cloud Browser Isolation sections](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-smart-browser-isolation-policy-draft-doc57092/Smart%20Isolate.png)
[]