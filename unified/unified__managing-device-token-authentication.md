# Managing Device Token Authentication
Source: https://help.zscaler.com/unified/managing-device-token-authentication
PDF: https://help.zscaler.com/pdf/com/en/1505606.pdf

ZIdentity manages the device token authentication for Zscaler Client Connector. The device tokens created in the Zscaler Client Connector are passed to ZIdentity to be authenticated for registered domains.
You need to first [create the device token](/unified/creating-device-token) in the Zscaler Client Connector before authenticating the device token in ZIdentity.
To enable device token authentication:
-
Go to **Administration** > **Identity **> **ZIdentity** > **IdP** **Device Token**.
The **Client Connector Device Token **page appears.
-
On the **Client Connector Device Token** page:
- **Allow All Domains**: Enable to authenticate all registered domains with the device token.
- **Domains**: Select the required domains that must be authenticated with the device token.
- **Enable Just-in-Time (JIT) Provisioning**: Enable to automatically enroll users to ZIdentity.
[See image.](#zsl-devicetokenpage)
-
Click **Save**.
Users can access the domains with their registered devices.
[]![ZCC device token authentication](/downloads/zslogin/authentication/managing-device-token-authentication/zidentity-device-token_0.png)