# Configuring Machine Provisioning Keys
Source: https://help.zscaler.com/zpa/configuring-machine-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1484691.pdf

Within the ZPA Admin Portal, you can add a machine provisioning key and a corresponding machine group. The machine provisioning key is used to:
- Associate the Zscaler Client Connector with a [machine group](/zpa/about-machine-groups).
- Enable [Machine Tunnels for Pre-Windows Login](/zpa/deploying-machine-tunnels-pre-windows-login) to gain access to internal applications even when the device's Zscaler Client Connector is not connected to ZPA.
To add a new machine provisioning key:
- Go to **Authentication **>** Device Authentication **>** Machine Provisioning Keys**.
- Click **Add**.
- In the **Add Machine Provisioning Key** window:
- [1. Signing Certificate](#step1)
- [2. Machine Group](#step2)
- [3. Create Machine Provisioning Key](#step3)
- [4. Review](#step4)
- [5. Provisioning Key Details](#step5)
[]The signing certificate is required for enrolling machines. You need to [create a signing certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates) before adding a new provisioning key.
On the **Signing Certificate** tab:
- Select a signing certificate from the drop-down menu.
- You can click **Clear Selection** to remove any selections.
[See image.](#image_signingcert)
- Click **Next**.
[]On the **Machine Group** tab, choose one of the following options:
- [Select Machine Group](#existinggrp)
- [Create Machine Group](#newgrp)
-
[]Select an existing group from the drop-down menu. You can click **Clear Selection** to remove any selections.
If you choose to use an existing provisioning key, only keys that can be viewed or exported after creation appear in the drop-down menu.
[See image.](#image_machinegrp)
- Click **Next**.
- []Click **Create Machine Group**.
- **Name**: Enter a name for the group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description of the group.
- **Status**: Make sure **Enabled** is selected.
[See image.](#image_machinegrp-create)
- Click **Next**.
- []On the **Create Machine Provisioning Key** tab:
- **View or Export Provisioning Key After Creation:** Select this option if you want to view, copy, or download the provisioning key after creation. This option is enabled by default. If disabled, you cannot enable this option at a later time.
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
[]![Step 1 to select a signing certificate in the Add Machine Provisioning Key Window within ZPA Admin Portal](/downloads/zpa/configuring-machine-provisioning-keys/zpa-addmachinetoken-choosecert_0.png)
![Step 2 to select a machine group in the Add Machine Provisioning Key Window within ZPA Admin Portal](/downloads/zpa/configuring-machine-provisioning-keys/zpa-addmachinetoken-machinegrp.png)
[]
[]![Step 2 to create a machine group in the Add Machine Provisioning Key Window within ZPA Admin Portal](/downloads/zpa/configuring-machine-provisioning-keys/zpa-addmachinetoken-machinegrp-create.png)
[]![Step 3 to create a provisioning key in the Add Machine Provisioning Key Window within ZPA Admin Portal](/downloads/zpa/authentication/machine-authentication/configuring-machine-provisioning-keys/omit-mpkeys_0.png)
[]![Step 4 to review a provisioning key in the Add Machine Provisioning Key Window within ZPA Admin Portal](/downloads/zpa/configuring-machine-provisioning-keys/zpa-addmachinetoken-review_0.png)
[]![Step 5 to copy a key in the Add Machine Provisioning Key Window within ZPA Admin Portal](/downloads/zpa/authentication/machine-authentication/configuring-machine-provisioning-keys/zpa-addmachinetoken-reviewdoc.png)