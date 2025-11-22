# Managing Device Profiles
Source: https://help.zscaler.com/zsdk/managing-device-profiles
PDF: https://help.zscaler.com/pdf/com/en/1531170.pdf

Device profiles are a set of criteria that are evaluated when the ZSDK Private Service Edges receive access requests to your application segments. Zscaler recommends reviewing your device profiles periodically to ensure security evaluation is required for your devices that have access to your application segments.
You can configure up to 200 device profiles. For each device profile, you can select up to 50 UUIDs while all other criteria are limited to 10. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations).
[]Adding a Device Profile
To add a device profile:
- Go to** Configuration & Control** > **Apps** > **Device Profile**.
- Click **Add**.
-
In the **Add New Device Profile** window:
- **Name**: Enter the name of the device profile.
- **Description**: (Optional) Enter the description of the device profile to describe its functionality.
-
**Add Criteria**: Select which criteria you want to evaluate for the device profile from the drop-down menu and complete the necessary configuration for each one. **UUID** is selected as a criterion by default. To remove a criterion, click the **Delete** icon.
You can select multiple criteria by choosing a criterion and entering its configuration value and then proceeding to select other criteria. You can use the same criteria and enter another value (e.g., you can enter up to 50 UUIDs with different configurations).
- **UUID**: Enter the universally unique identifier of the device.
- **Hardware Identifier**: Enter the hardware identifier.
- **Hardware Model**: Enter the hardware model.
- **OS Version**: Enter the OS version.
[See image.](#img_add)
- Click **Save**.
[]Editing a Device Profile
To edit a device profile:
- Go to** Configuration & Control** > **Apps** > **Device Profile**.
- Click the **Edit** icon for the device profile you want to modify.
-
In the **Update Device Profile** window, modify the fields as necessary.
[See image.](#img_update)
- Click **Save**.
[]Deleting a Device Profile
To delete a device profile:
- Go to** Configuration & Control** > **Apps** > **Device Profile**.
-
Click the **Delete** icon for the device profile you want to delete.
[See image.](#img_delete)
- Click **Delete** to confirm the deletion of the selected device profile.
[]
![Create a device profile to monitor access to your mobile applications](/downloads/zsdk/applications/application-management/managing-device-profiles/zsdk-device-profile-add-1_0.png)
[]
![Edit the device profile by modifying the fields](/downloads/zpa/browser-access/managing-chrome-posture-profiles/zsdk-device-profile-update_0.png)
[]
![Confirm deletion of the device profile](/downloads/zpa/browser-access/managing-chrome-posture-profiles/zsdk-device-profile-delete.png)