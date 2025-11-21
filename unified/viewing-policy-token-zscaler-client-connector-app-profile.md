# Viewing the Policy Token for a Zscaler Client Connector App Profile
Source: https://help.zscaler.com/unified/viewing-policy-token-zscaler-client-connector-app-profile
PDF: https://help.zscaler.com/pdf/com/en/1494461.pdf

After you save your Zscaler Client Connector [app profile](/unified/about-zscaler-client-connector-app-profiles), a policy token is automatically generated for the profile.
You need this policy token if you want to use the [STRICTENFORCEMENT install option](/unified/customizing-zscaler-client-connector-install-options-msi) which requires users to enroll with Zscaler Client Connector before accessing the Internet. The policy that corresponds with this policy token is enforced for the app until the user enrolls. After the user enrolls, this policy is replaced with the app profile policy that matches the user based on their group affiliation.
To view the policy token for an app profile:
- In the Admin Portal, go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select the operating system, and click the **Edit** icon for the app profile.
![Viewing a policy token](/downloads/unified/networking/client-connector/application-profiles/zscaler-client-connector-profile-management/viewing-policy-token-zscaler-client-connector-app-profile/client-connector-view-policy-token.png)