# Customizing Landmine Installer
Source: https://help.zscaler.com/deception/customizing-landmine-installer
PDF: https://help.zscaler.com/pdf/com/en/1531317.pdf

When you install a landmine agent, it is installed with the service name Landmine, by default. You can customize the name, display name, and description of the landmine service to prevent the agent from being fingerprinted.
To customize the landmine agent installer properties:
- Go to **Settings** > **Endpoint Settings** > **Agent Configuration**.
-
Under the **Landmine Installer Customizations **section:
-
**Name**: Edit the landmine agent service name. The default name is **Landmine**.
- The landmine agent service name should be unique. To avoid conflicts with existing services, make sure to check the names of the services running in the systems where you want to install the landmine decoys before configuring the landmine agent service name.
- For macOS endpoints, the landmine agent is installed under the `/Applications` directory with the installation directory matching the landmine service name entered in the **Name **field.
- For Linux endpoints, the default name **Landmine **is always used for the installation folder name and changes to the **Name **property are not applied.
-
**Display name**: Edit the landmine agent service display name. The default display name is **landmine**.
- Changes to this field apply only to Windows-based landmine agents.
- If you want to customize the landmine properties, Zscaler recommends modifying the properties before installing any agents. If you want to change the landmine properties after landmine agents are deployed, and you prefer to have consistency across previous and future landmine installations, you need to uninstall the existing landmine agents in these endpoints and then reinstall them.
-
**Description**: Enter a description of the landmine agent service.
Changes to this field apply only to Windows-based landmine agents.
[See image.](#landmine-installer-customization)
- Click **Save**.
[]![Customize landmine installer properties](/downloads/deception/deceive/landmine-decoys/landmine-settings/customizing-landmine-installer/zscaler-deception-landmine-installer-customization.png)