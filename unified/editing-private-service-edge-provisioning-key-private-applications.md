# Editing a Private Service Edge Provisioning Key for Private Applications
Source: https://help.zscaler.com/unified/editing-private-service-edge-provisioning-key-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1496556.pdf

To edit a Private Service Edge provisioning key:
- Go to the **Private Service Edge Provisioning Keys **page (Infrastructure > Private Applications > Components > Service Edge Keys).
-
In the table, locate the Private Service Edge provisioning key you want to modify and click the **Edit **icon.
Only keys that can be viewed or exported after creation appear in the table.
Provisioning keys that are managed by Zscaler are read only and cannot be edited.
The **Edit Provisioning Key **window appears.
- In the **Edit Provisioning Key** window, you can only modify the following fields:
- **View or Export Provisioning Key After Creation**: Disable this option to hide the provisioning key in the **Provisioning Key** column of the table and disable copying or downloading the key after creation. If disabled, you cannot enable this option after creation. If this option is enabled, you can disable it at a later time. This option is enabled by default.
- **Name**: The provisioning key name. When [adding a new Private Service Edge for Private Applications](/unified/configuring-private-service-edges-private-applications), the provisioning key name is automatically assigned as a prefix for the name of each Private Service Edge enrolled with it. Meaning that all Private Service Edges in a given Private Service Edge group will use the same prefix in its name. If you edit the key name, it cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Maximum Reuse of Provisioning Key**: The maximum number of instances where this key can be used to enroll a Private Service Edge.
- **Signing Certificate**: The signing certificate (i.e., [enrollment (CA) certificate](/unified/about-enrollment-ca-certificates)) for this provisioning key. For example, if your certificate expires, you might need to select a new certificate. All Private Service Edges deployed with this key will have their certificates signed with this signing certificate. You can click on the Signing Certificate field and click **Clear Selection** to remove any selections.
If any of your Private Service Edges were deployed with a signing certificate that has expired, and you have configured a new certificate, the Private Service Edges will automatically re-deploy using the new certificate.
![Edit Private Service Edge Provisioning Key window](/downloads/zpa/private-service-edge-management/private-service-edge-provisioning-keys/editing-a-zpa-private-service-edge-provisioning-key/zpa-edit-pse-provisioning-key-window_0.png)
- Click **Save**.