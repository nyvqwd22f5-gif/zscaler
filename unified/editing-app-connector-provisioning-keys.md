# Editing App Connector Provisioning Keys
Source: https://help.zscaler.com/unified/editing-app-connector-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1496086.pdf

To edit an App Connector provisioning key:
- Go to the **App Connector Provisioning Keys** page (Infrastructure > Private Access > Components > App Connector Keys).
-
In the table, locate the App Connector provisioning key you want to modify and click the **Edit icon**.
Only keys that can be viewed or exported after creation appear in the table.
App Connector provisioning keys that are managed by Zscaler are read only and cannot be edited.
The **Edit App Connector Provisioning Key **window appears.
- In the** Edit App Connector Provisioning Key **window, you can only modify the following fields:
- **View or Export Provisioning Key After Creation**: Disable this option to hide the provisioning key from the **Provisioning Key **column of the table and disable copying or downloading the key after creation. If disabled, you cannot enable this option. If this option is enabled, you can disable it at a later time. This option is enabled by default.
- **Name**: The provisioning key name. When [adding a new App Connector](/unified/configuring-app-connectors#pk), the provisioning key name is automatically assigned as a prefix for the name of each App Connector enrolled with it. Meaning that all App Connectors in a given App Connector group will use the same prefix in its name. If you edit the key name, it cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Maximum Reuse of Provisioning Key**:** **The maximum number of instances where this key can be used to enroll an App Connector. Zscaler recommends setting this option to the number of App Connectors you plan to deploy immediately, to reduce the possibility of compromise.
- **Signing Certificate**: The signing certificate (i.e., [enrollment (CA) certificate](/unified/about-enrollment-ca-certificates)) for this provisioning key. For example, if your certificate expires, you might need to select a new certificate. All App Connectors deployed with this key will have their certificates signed with this signing certificate. You can click **Clear Selection** to remove any selections.
If any of your App Connectors were deployed with a signing certificate that has expired, and you’ve configured a new certificate, the App Connectors will automatically re-deploy using the new certificate.
![Editing an App Connector provisioning key](/downloads/zpa/app-connector-management/app-connector-provisioning-keys/editing-connector-provisioning-keys/zpa-edit-app-connector-provisioning-key-window.png)
- Click **Save**.