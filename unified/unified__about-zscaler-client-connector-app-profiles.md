# About Zscaler Client Connector App Profiles
Source: https://help.zscaler.com/unified/about-zscaler-client-connector-app-profiles
PDF: https://help.zscaler.com/pdf/com/en/1493771.pdf

In the Admin Portal, you can configure [app profiles](/unified/configuring-zscaler-client-connector-app-profiles) by adding policy rules to each profile. You can select the order of precedence among the rules and to whom each rule applies (all users or different groups of users). When a user enrolls the app with the Zscaler service, the app uses the order of precedence and identity of the user to download an app profile with the appropriate policy rule. To learn more, see [Zscaler Client Connector Profile Rule Example](/unified/zscaler-client-connector-profile-rule-example).
The app checks for profile updates and downloads any changes whenever users log out and back into the app or restart their computers.
App profiles provide the following benefits and allow you to:
- Control whether users must enter an admin-provided password to log out of, disable, exit, or uninstall the app.
- Select the forwarding profile for Internet & SaaS and Private Applications services.
- Determine whether the app can install the Zscaler SSL certificate on users' devices to allow SSL inspection of traffic forwarded by the app for the Internet & SaaS service.
- Control how the app generates logs and the maximum size of its log files for the Internet & SaaS service.
- Quickly locate an app profile using the search feature.
- Easily view, edit, copy, and delete app profiles.
About the App Profiles Page
On the App Profiles page (Infrastructure > Connectors > Client > Platform Settings), you can do the following:
- View app profile rules for a specific platform.
- [Configure a new app profile rule](/unified/configuring-zscaler-client-connector-app-profiles).
- [Search for an app profile](/unified/searching-zscaler-client-connector-app-profile).
- View a list of all configured app profile rules.
- [Copy an existing profile that you can customize to create a new profile](/unified/copying-zscaler-client-connector-app-profile).
- Edit items in the Admin Portal or [view the policy token for an app profile rule](/unified/viewing-policy-token-zscaler-client-connector-app-profile).
- Delete items in the Admin Portal.
- View the default policy.
![About Configuring Zscaler Client Connector Profiles](/downloads/unified/networking/client-connector/application-profiles/zscaler-client-connector-profile-management/about-zscaler-client-connector-app-profiles/client-connector-app-profiles.png)