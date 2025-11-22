# Managing App Connector Provisioning Keys
Source: https://help.zscaler.com/zsdk/managing-app-connector-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1508351.pdf

After your App Connector provisioning keys are provisioned, you can see them displayed on the App Connector Provisioning Keys page.
To manage App Connector provisioning keys on the App Connector Provisioning Keys page (Configuration & Control > Private Infrastructure > App Connector Management > App Connector Provisioning Keys), you can:
- [Edit an App Connector provisioning key.](#edit)
- [Delete an App Connector provisioning key.](#delete)
[]
-
Click the **Edit** icon on the App Connector provisioning key you want to modify.
The **Edit App Connector Provisioning Key** window appears.
-
In the **Edit App Connector Provisioning Key** window:
- **Name**: Enter the provisioning key name. When [adding a new App Connector](/zsdk/managing-app-connectors#pk), the provisioning key name is automatically assigned as a prefix for the name of each App Connector enrolled with the provisioning key. If you edit the key name, it cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Maximum Reuse of Provisioning Key**:** **Enter the maximum number of instances where this key can be used to enroll an App Connector.
- **App Connector Group**: This field cannot be modified.
- **Signing Certificate**: The signing certificate (i.e., [enrollment (CA) certificate](/zpa/about-EnrollmentCertificates)) for this provisioning key. For example, if your certificate expires, you might need to select a new certificate. All App Connectors deployed with this key have their certificates signed with this signing certificate. You can click **Clear Selection** to remove any selections.
[See image.](#img_edit)
- Click **Save**.
[]
-
Click the **Delete** icon on the App Connector provisioning key you want to delete.
The **Confirm: Delete Action** window appears.
-
Click **Delete** to confirm the deletion of the App Connector provisioning key.
[See image.](#img_delete)
[]
![Edit App Connector Provisioning Key Window](/downloads/zsdk/getting-started/provisioning/managing-app-connector-provisioning-keys/Edit-App-Connector-Provisioning-Keys.png)
[]![Confirm Deletion Window](/downloads/zsdk/getting-started/provisioning/managing-app-connector-provisioning-keys/Delete-App-Connector-Provisioning-Key.png)