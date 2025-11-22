# Understanding Isolation of Miscellaneous & Unknown Category in ZIA
Source: https://help.zscaler.com/isolation/understanding-isolation-miscellaneous-and-unknown-category-zia
PDF: https://help.zscaler.com/pdf/com/en/1518406.pdf

Admins who have [Isolation integrated with Zscaler Internet Access (ZIA)](/isolation/configuring-zia-isolation) have the ability to isolate [URL categories](/zia/about-url-categories) using [ZIA policies](/zia/configuring-smart-browser-isolation-policy). Depending on your organization's level of [Isolation](/isolation/what-is-isolation) access, you might only have the ability to isolate the category *Miscellaneous & Unknown*.
If you have the Miscellaneous & Unknown Category subscription, Isolation makes a preconfigured [isolation profile](/isolation/creating-isolation-profiles-zia) for you when you first log in. This profile is different from the [default isolation profiles](/isolation/default-isolation-profiles-isolation) that are made for different levels of Isolation access upon first login. Additionally, a ZIA URL filtering rule with the category of Miscellaneous & Unknown is automatically created and enabled by default. The rule is disabled by default for existing tenants, but it is enabled by default for new tenants.
The fields for this profile have certain functionalities permanently enabled, others permanently disabled, and some that the admin can change. The following are the settings automatically defined for this isolation profile:
- **Name**: Misc & Unknown
- **Enable Turbo Mode**: Enabled
- **PAC File URL**: Use Recommended Pac file URL
- **Override PAC File**: Disabled
- **Enable Debug Mode**: Disabled
- **Root Certificate**: Default Zscaler Root Certificate
- **Allow Copy & Paste From**: Disabled
- **Allow File Transfer**: Disabled
- **Allow Print**: Disabled
- **Read-Only Isolation**: Enabled
- **View office files in Isolation**: Disabled
- **Allow local browser rendering**: Disabled
- **Application Deep Linking**: Disabled
- **Votiro CDR**: Disabled
- **Region Selection**: All
- **Isolation Banner**: Default
- **Persist Browser Isolation URL bar**: Disabled
- **Isolation Experience**: Native Browser Experience
- **Enable Watermarking**: Disabled
- **Persistent State**: Disabled
Admins can [edit](/isolation/editing-your-isolation-profile-zia) the following fields after the preconfigured profile is created:
- Turbo Mode
- Debug Mode
- Root Certificate
- Read-Only Isolation
- Region Selection
To learn more, see [Editing Your Isolation Profile for ZIA](/isolation/editing-your-isolation-profile-zia).