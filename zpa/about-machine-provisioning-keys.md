# About Machine Provisioning Keys
Source: https://help.zscaler.com/zpa/about-machine-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1484686.pdf

[Watch a video about machine provisioning keys.](https://fast.wistia.net/embed/iframe/11naj2mw13)
The provisioning key is a text string that is generated when you [add a machine provisioning key](/zpa/configuring-machine-provisioning-keys) in the ZPA Admin Portal. You need to add the key to a [Zscaler Client Connector profile rule](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#windows) for Windows or macOS. When added, the provisioning key functions like an ID to the machine, and it enables the ZPA cloud to verify the machine's authenticity prior to logging into Windows or macOS.
Provisioning keys should be treated as secrets and properly protected because they can create a resource for a tenant. The provisioning key must also be secured and not transmitted or stored in clear text.
Machine provisioning keys provide the following benefits and allow you to:
- Associate the Zscaler Client Connector with a machine group.
- Enable Machine Tunnels for Pre-Windows Login to gain access to internal applications even when the device's Zscaler Client Connector is not connected to ZPA.
The following is an example of a machine provisioning key:
3|api.private.zscaler.com|ITfVkU6RBiV8X9fboO3kV3rbBUz5nYBQYfRV03/E0ghCaLgJg5/LmJnjYqF1s53xqClW3/OZXgFTbeAMrPy4utlB6fV5t36wRedYYSgr4I2gXBftPPk5PPOQJ5b5+w178hlWrJeIU8WbdjjF5f5iJPlUBileIqieEUskqwNgzehZ+3B37DitvAjS8RvVxRQwDR31mfcxAzMxCGuDW31eCz3b50NisU1ujGCGyuna+0hFMx02NJ76HogurPr4VZI1MMQcocW5xk6CMyBP8cPJ9Ja7MqrB2/wTSzk7ctGb2t72/EIdr2+7eyCGDO8/AkZRUfqyUPGGXvipsmG51QysnCO/6xvSMNBjcR/3qrZ9A9Ec8GuoiQHkzOfGvhCbbQ+v
Before logging into Zscaler Client Connector, you must [configure machine provisioning keys and machine groups](/zpa/configuring-machine-provisioning-keys) in order to use a machine tunnel to establish a connection to a service. To learn more, see [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels).
Provisioning keys are considered confidential information and must be kept in a safe place. For each provisioning key, a **Copy Provisioning Key** option is provided to copy the key to your clipboard.
About the Machine Provisioning Keys Page
On the Machine Provisioning Keys page (Authentication > Device Authentication > Machine Provisioning Keys), you can:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Machine Provisioning Keys page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a machine provisioning key.](/zpa/configuring-machine-provisioning-keys)
- Expand all rows in the table to see more information about each provisioning key.
- View a list of all the provisioning keys that are configured for your organization. For each provisioning key, you can see:
- **Name**: The name of the key. This is the name you see when adding the key to a Zscaler Client Connector profile rule. To learn more, see [Configuring Zscaler Client Connector Profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#windows).
- **Machine Group**: The machine groups that are using this provisioning key.
- **Status**: Indicates whether the machine provisioning key is enabled or disabled.
- **Provisioning Key**: The key needed to enable the ZPA cloud to verify the machine's authenticity prior to logging in to Windows.
- This entry is blank if you disabled the **View or Export Provisioning Key After Creation** option when [adding a machine provisioning key.](/zpa/configuring-machine-provisioning-keys)
-
Copy the provisioning key to your clipboard. When deploying a machine, you are prompted to enter the key.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [adding a machine provisioning key](/zpa/configuring-machine-provisioning-keys). If the provisioning key doesn't appear, and a backup of the provisioning key isn't securely stored in an external credential vault, a new key must be generated. A new provisioning key can be created and attached to the same machine.
- [Edit a configured provisioning key.](/zpa/edit-machine-provisioning-key)
- Delete a provisioning key.
-
Download the provisioning key as a text file.
This icon is hidden for security purposes if you disabled the **View or Export Provisioning Key After Creation** option when [adding a machine provisioning key](/zpa/configuring-machine-provisioning-keys).
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Machine Groups](/zpa/about-machine-groups) page to manage your machine groups.
![Viewing and Managing Machine Provisioning Keys](/downloads/zpa/authentication/machine-authentication/about-machine-provisioning-keys/zpa-machine-provisioning-keys-blur_1.png)