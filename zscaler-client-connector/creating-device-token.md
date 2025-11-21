# Creating a Device Token
Source: https://help.zscaler.com/zscaler-client-connector/creating-device-token
PDF: https://help.zscaler.com/pdf/com/en/1317681.pdf

If you configure the Zscaler Client Connector Portal as your identity provider (IdP), users automatically enroll with Zscaler Client Connector. Users and their devices authenticate using a device token generated in the Zscaler Client Connector Portal.
Zscaler must enable this feature.
To generate the device token:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left menu, select** Client Connector IdP**.
- Under **Manage Device Tokens**, click **Create Device Token**.
- In the **Create Device Token** window, do the following:
- **Enter** **Password**: Enter a password that is at least six characters and includes at least one alphabetic character and a number. This password is only needed to generate the token and is not needed after that.
- **Token** **Description**: Enter a description that helps you track the device token.
- Click** Create Device Token**.
The token you generate appears in the table under **Manage Device Tokens**. You can create up to 16 tokens.