# Configuring Machine Provisioning Keys
Source: https://help.zscaler.com/unified/configuring-machine-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1491396.pdf

Within the Admin Portal, you can add a Machine Provisioning Key and a corresponding Machine Group. The Machine Provisioning Key is used to:
- Associate the Zscaler Client Connector with a [Machine Group](/unified/about-machine-groups).
- Enable [Machine Tunnels for Pre-Windows Login](/unified/deploying-machine-tunnels-pre-windows-login) to gain access to internal applications even when the device's Zscaler Client Connector is not connected to Private Applications.
To add a new Machine Provisioning Key:
- Go to** Administration **>** Identity **>** Private Access **>** Machine Provisioning Keys**.
- Click **Add Machine Provisioning Key**.
- In the **Add Machine Provisioning Key** window:
- [1. Signing Certificate](#step1)
- [2. Machine Group](#step2)
- [3. Create Machine Provisioning Key](#step3)
- [4. Review](#step4)
- [5. Provisioning Key Details](#step5)
[]The signing certificate is required for enrolling machines. You need to create a signing certificate before adding a new provisioning key.
On the **Signing Certificate** tab:
- Select a signing certificate from the drop-down menu.
- You can click **Clear Selection** to remove any selections.
[See image.](#image_signingcert)
- Click **Next**.
[]On the **Machine Group** tab, choose one of the following options:
- [Choose an existing Machine Group](#existinggrp)
- [Create a new Machine Group](#newgrp)
- []Select an existing group from the drop-down menu. You can click **Clear Selection** to remove any selections.
[See image.](#image_machinegrp)
- Click **Next**.
- []Click **Create Machine Group**.
- **Name**: Enter a name for the group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the group.
- **Status**: Make sure **Enabled** is selected.
[See image.](#image_machinegrp-create)
- Click **Next**.
- []On the **Create Machine Provisioning Key** tab:
- **Name**: Enter a name for the key. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Make sure **Enabled** is selected.
- **Allow Re-Enrollment**: Enable to allow for the re-enrollment of machines using the same machine provisioning key. This setting is disabled by default.
[See image.](#image_key)
- Click **Next**.
- []On the **Review **tab, review your configuration settings.
[See image.](#image_review)
- Click **Save**.
- []On the **Provisioning Key Details** tab, copy the provisioning key. You can click the **Copy icon** to copy the key to your clipboard.
[See image.](#image_reviewdoc)
- Click **Done**.
[]![Select a signing certificate when adding a Machine Provisioning Key](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/configuring-machine-provisioning-keys/unified-add-machine-pkey-cert.png)
[]![Select a machine group when adding a Machine Provisioning Key](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/configuring-machine-provisioning-keys/unified-select-machine-group.png)
[]![Add a machine group when adding a Machine Provisioning Key](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/configuring-machine-provisioning-keys/unified-add-machine-group.png)
[]![Create a Machine Provisioning Key when adding a Machine Provisioning Key](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/configuring-machine-provisioning-keys/unified-add-machine-provisioning-key.png)
[]![Review a machine provisioning key when adding a Machine Provisioning Key](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/configuring-machine-provisioning-keys/unified-review-step.png)
[]![Copy the machine provisioning key when adding a Machine Provisioning Key](/downloads/unified/administration/private-applications/identity/idp-device-configuration/machine-authentication/configuring-machine-provisioning-keys/unified-machine-pkey-details.png)