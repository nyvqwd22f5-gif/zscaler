# About Zscaler Client Connector App Profiles
Source: https://help.zscaler.com/zscaler-client-connector/about-zscaler-client-connector-app-profiles
PDF: https://help.zscaler.com/pdf/com/en/1317636.pdf

In the Zscaler Client Connector Portal, you can configure [app profiles](/zscaler-client-connector/configuring-zscaler-client-connector-profiles) by adding policy rules to each profile. You can select the order of precedence among the rules and to whom each rule applies (all users or different groups of users). When a user enrolls the app with the Zscaler service, the app uses the order of precedence and identity of the user to download an app profile with the appropriate policy rule. To learn more, see [Zscaler Client Connector Profile Rule Example](/zscaler-client-connector/zscaler-app-profile-rule-example).
The app checks for profile updates and downloads any changes whenever users log out and back into the app or restart their computers.
App profiles provide the following benefits and allow you to:
- Control whether users must enter an admin-provided password to log out of, disable, exit, or uninstall the app.
- Select the forwarding profile for Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) services.
- Determine whether the app can install the Zscaler SSL certificate on users' devices to allow SSL inspection of traffic forwarded by the app for the ZIA service.
- Control how the app generates logs and the maximum size of its log files for the ZIA service.
- Quickly locate an app profile using the search feature.
- Easily view, edit, copy, and delete app profiles.
About the App Profiles Page
On the App Profiles page, you can do the following:
- View app profile rules for a specific platform.
- [Configure a new app profile rule](/zscaler-client-connector/configuring-zscaler-app-profiles).
- [Search for an app profile](/zscaler-client-connector/searching-app-profile).
- View a list of all configured app profile rules.
- [Copy an existing profile that you can customize to create a new profile](/zscaler-client-connector/copying-app-profile).
- [Edit items in the Zscaler Client Connector Portal](/zscaler-client-connector/editing-or-deleting-items-zscaler-client-connector-portal) or [view the policy token for an app profile rule](/zscaler-client-connector/viewing-policy-token-zscaler-app-profile).
- [Delete items in the Zscaler Client Connector Portal](/zscaler-client-connector/editing-or-deleting-items-zscaler-client-connector-portal).
- View the default policy.
![About Configuring Zscaler Client Connector Profiles](/downloads/client-connector/zscaler-client-connector-profile-management/about-zscaler-client-connector-profiles/App%20Profiles%20page_1195.png)