# About Machine Provisioning Keys
Source: https://help.zscaler.com/unified/about-machine-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1491391.pdf

The provisioning key is a text string that is generated when you [add a Machine Provisioning Key](/unified/configuring-machine-provisioning-keys) in the Admin Portal. You need to add the key to a [Zscaler Client Connector profile rule](/unified/configuring-zscaler-client-connector-app-profiles#windows) for Windows. Once added, the provisioning key functions like an ID to the machine, and it enables the Private Applications cloud to verify the machine's authenticity prior to logging into Windows.
Machine Provisioning Keys provide the following benefits and allow you to:
- Associate the Zscaler Client Connector with a Machine Group.
- Enable Machine Tunnels for Pre-Windows Login to gain access to internal applications even when the device's Zscaler Client Connector is not connected to Private Applications.
Below is an example of a Machine Provisioning Key:
3|api.private.zscaler.com|ITfVkU6RBiV8X9fboO3kV3rbBUz5nYBQYfRV03/E0ghCaLgJg5/LmJnjYqF1s53xqClW3/OZXgFTbeAMrPy4utlB6fV5t36wRedYYSgr4I2gXBftPPk5PPOQJ5b5+w178hlWrJeIU8WbdjjF5f5iJPlUBileIqieEUskqwNgzehZ+3B37DitvAjS8RvVxRQwDR31mfcxAzMxCGuDW31eCz3b50NisU1ujGCGyuna+0hFMx02NJ76HogurPr4VZI1MMQcocW5xk6CMyBP8cPJ9Ja7MqrB2/wTSzk7ctGb2t72/EIdr2+7eyCGDO8/AkZRUfqyUPGGXvipsmG51QysnCO/6xvSMNBjcR/3qrZ9A9Ec8GuoiQHkzOfGvhCbbQ+v
Before logging into Zscaler Client Connector, you must [configure Machine Provisioning keys and Machine groups](/unified/configuring-machine-provisioning-keys) in order to use a machine tunnel to establish a connection to a service. To learn more, see [About Machine Tunnels](/unified/about-machine-tunnels).
Provisioning keys are considered confidential information and must be kept in a safe place. For each provisioning key, a COPY PROVISIONING KEY option is provided, so you can copy the key to your clipboard.
About the Machine Provisioning Keys Page
On the Machine Provisioning Keys page (Administration > Identity > Private Access > Machine Provisioning Keys), you can:
- Expand all of the rows in the table to see more information about each provisioning key.
- [Add a machine provisioning key.](/unified/configuring-machine-provisioning-keys)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all the provisioning keys that are configured for your organization. For each provisioning key, you can see:
- **Name**: The name of the key. This is the name you see when adding the key to a Zscaler Client Connector profile rule. To learn more, see [Configuring Zscaler Client Connector Profile](/unified/configuring-zscaler-client-connector-app-profiles#windows).
- **Machine Group**: The machine group(s) that are using this provisioning key.
- **Status**: Indicates whether the machine provisioning key is enabled or disabled.
- Copy the Provisioning Key to your clipboard. When deploying a machine, you are prompted to enter the key.
- [Edit a configured provisioning key.](/unified/editing-machine-provisioning-keys)
- Delete a provisioning key.
- Download the provisioning key to your system in a file format.
![Viewing the Machine Provisioning Keys page](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/about-machine-provisioning-keys/unified-machine-provisioning-keys-page.png)