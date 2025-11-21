# Understanding Isolation of Miscellaneous and Unknown Category in Internet & SaaS
Source: https://help.zscaler.com/unified/understanding-isolation-miscellaneous-and-unknown-category-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1526376.pdf

Admins who have [Isolation integrated with Internet & SaaS](/unified/configuring-internet-saas-isolation) have the ability to isolate [URL categories](/unified/about-url-categories) using [Internet & SaaS policies](/unified/configuring-smart-browser-isolation-policy). Depending on your organization's level of Isolation access, you may only have the ability to isolate the category "Miscellaneous or Unknown."
If you have the Miscellaneous and Unknown Category subscription, Isolation makes a preconfigured [isolation profile](/unified/creating-isolation-profiles-internet-saas) for you when you first log in. This profile is different from the [default isolation profiles](/unified/default-isolation-profiles-isolation) that are made for different levels of Isolation access upon first login.
The fields for this profile have certain functionalities permanently enabled, others permanently disabled, and some that the admin can change. Below are the settings automatically defined for this isolation profile:
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
Admins can [edit](/unified/editing-your-isolation-profile-internet-saas) the following fields after the preconfigured profile is created:
- Turbo Mode
- Debug Mode
- Root Certificate
- Read-Only Isolation
- Region Selection
To learn more, see [Editing Your Isolation Profile for Internet & SaaS](/unified/editing-your-isolation-profile-internet-saas).