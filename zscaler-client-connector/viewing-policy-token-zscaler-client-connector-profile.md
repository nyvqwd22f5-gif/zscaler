# Viewing the Policy Token for a Zscaler Client Connector Profile
Source: https://help.zscaler.com/zscaler-client-connector/viewing-policy-token-zscaler-client-connector-profile
PDF: https://help.zscaler.com/pdf/com/en/1328911.pdf

After you save your Zscaler Client Connector [profile](/zscaler-client-connector/about-zscaler-app-profiles), a policy token is automatically generated for the profile.
You need this policy token if you want to use the [STRICTENFORCEMENT install option](/zscaler-client-connector/customizing-zscaler-app-install-options-msi) which requires users to enroll with Zscaler Client Connector before accessing the Internet. The policy that corresponds with this policy token is enforced for the app until the user enrolls. After the user enrolls, this policy is replaced with the app profile policy that matches the user based on their group affiliation.
To view the policy token for an app profile:
- In the Zscaler Client Connector Portal, go to **App Profiles**.
- From the left-side of navigation, go to **Mobile Devices** or **Personal Computers**.
- Select the platform.
- Click the **Edit** icon.
![Configured App Profile Policies Example](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-profiles/viewing-policy-token-zscaler-app-profile/z-app-profile-policy-token.png)