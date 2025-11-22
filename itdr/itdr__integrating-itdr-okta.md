# Integrating ITDR with Okta
Source: https://help.zscaler.com/itdr/integrating-itdr-okta
PDF: https://help.zscaler.com/pdf/com/en/1531694.pdf

Okta is a widely used identity and access management (IAM) platform, making it an attractive target for attackers seeking to compromise identity security due to its central role in managing user authentication and authorization across various applications and services. Zscaler ITDR integrates with Okta to enrich the identity metadata, identify real-time changes on an Okta identity, and perform actions on an Okta identity like activate user, suspend user, clear user sessions, etc.
The Okta system logs for threat detection are only retained for 14 days, after which they are permanently deleted.
To integrate ITDR with Okta:
- Go to **ITDR** > **Manage** > **Okta**.
-
On the **Okta **page:
- **Enabled**: Select to enable the integration with ITDR.
- **Base URL**: Enter the base URL of the Okta tenant (e.g., `https://customer.okta.com/`).
- **API Token**: Enter the bearer token generated on the Okta tenant.
[See image.](#itdr-integration-with-okta)
-
Click **Test** to test the connection.
If the credentials are valid and Okta can communicate with ITDR, a confirmation message appears indicating that the test is successful.
If the credentials do not match or Okta is unable to connect with ITDR, regenerate the API token on the Okta tenant, enter the new API token in the API token field, and test again.
- Click **Save**.
[]![itdr-integration-with-okta.png](/downloads/itdr/integrating-itdr-okta/itdr-integration-with-okta.png)