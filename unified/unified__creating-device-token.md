# Creating a Device Token
Source: https://help.zscaler.com/unified/creating-device-token
PDF: https://help.zscaler.com/pdf/com/en/1491351.pdf

If you configure Zscaler Client Connector as your identity provider (IdP), users automatically enroll with Zscaler Client Connector. Users and their devices authenticate using a device token generated in the Admin Portal.
Zscaler must enable this feature.
To generate the device token:
- Go to **Infrastructure > Connectors > Client > Client Connector Hosted IdP**.
- Under **Manage Device Tokens**, click **Create Device Token**.
- In the **Create Device Token** window, do the following:
- **Enter** **Password**: Enter a password that is at least six characters and includes at least one alphabetic character and a number. This password is only needed to generate the token and is not needed after that.
- **Token** **Description**: Enter a description that helps you track the device token.
- Click** Create Token**.
The token you generate appears in the table under **Manage Device Tokens**. You can create up to 16 tokens.