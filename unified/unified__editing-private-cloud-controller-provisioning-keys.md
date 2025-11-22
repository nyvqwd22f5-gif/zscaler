# Editing Private Cloud Controller Provisioning Keys
Source: https://help.zscaler.com/unified/editing-private-cloud-controller-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1528691.pdf

To edit a Private Cloud Controller provisioning key:
- Go to **Infrastructure** > **Private Access** > **Business Continuity** > **Private Cloud Controller Provisioning Keys**.
-
In the table, locate the Private Cloud Controller provisioning key you want to modify and click the **Edit **icon.
Private Cloud Controller provisioning keys that are managed by Zscaler are read only and cannot be edited.
Only keys that can be viewed or exported after creation appear in the table.
The **Edit Private Cloud Controller Provisioning Key **page appears.
- On the** Edit Private Cloud Controller Provisioning Key **page, you can only modify the following fields:
- **View or Export Provisioning Key After Creation**: Disable this option to hide the provisioning key from the **Provisioning Key** column of the table and disable copying or downloading the key after creation. If disabled, you cannot enable this option after creation. If this option is enabled, you can disable it at a later time. This option is enabled by default.
- **Name**: The provisioning key name. When adding a new Private Cloud Controller, the provisioning key name is automatically assigned as a prefix for the name of each Private Cloud Controller enrolled with it. Meaning that all Private Cloud Controllers in a given Private Cloud Controller group use the same prefix in its name. If you edit the key name, it cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Maximum Reuse of Provisioning Key**:** **The maximum number of instances where this key can be used to enroll a Private Cloud Controller.
- **Signing Certificate**: The signing certificate (i.e., [enrollment (CA) certificate](/unified/about-enrollment-ca-certificates)) for this provisioning key. All Private Cloud Controllers deployed with this key have their certificates signed with this signing certificate. You can click **Clear** to remove any selections. If your certificate expires, you might need to select a new certificate.
If any of your Private Cloud Controllers are deployed with an expired signing certificate, and you’ve configured a new certificate, the Private Cloud Controllers automatically re-deploy using the new certificate.
![Editing a Private Cloud Controller Provisioning Key](/downloads/zpa/business-continuity-management/private-cloud-controller-provisioning-keys/editing-private-cloud-controller-provisioning-keys/zpa-edit-private-cloud-controller-provisioning-key-page.png)
- Click **Save**.