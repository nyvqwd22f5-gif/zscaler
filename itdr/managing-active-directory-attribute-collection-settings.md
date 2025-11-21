# Managing Active Directory Attribute Collection Settings
Source: https://help.zscaler.com/itdr/managing-active-directory-attribute-collection-settings
PDF: https://help.zscaler.com/pdf/com/en/1531833.pdf

Zscaler ITDR collects Active Directory (AD) domain object (users and computers) attributes. After an AD domain is configured for scanning, attribute collection is enabled by default. The Windows endpoint agent assigned for scanning the AD domain collects the attributes. You can also schedule the scan frequency.
To manage AD attribute collection:
- Go to **ITDR** > **Manage **> **Active Directory Posture**.
-
Locate the AD domain for which you want to enable or disable attribute collection, and click the **Edit** icon.
[See image.](#itdr-enable-attr-coll-edit)
-
In the **Scan Agents Details** window, under **Attribute Collection**:
- **Enabled: **Attribute collection is enabled by default. Click the toggle to disable it.
- **Scan Frequency**: Select a scan frequency (**Weekly** or **Monthly**) for attribute collection.
[See image.](#Scan_agent_details)
- Click **Submit**.
[]![The Edit icon for an AD domain](/downloads/itdr/itdr/active-directory-posture-scan/enabling-active-directory-attribute-collection/itdr-ad-posture-edit-icon.png)
[]![Enable AD attribute collection and frequency](/downloads/itdr/itdr/active-directory-posture-scan/enabling-active-directory-attribute-collection/itdr-ad-enable-attribute-collection-config.png)