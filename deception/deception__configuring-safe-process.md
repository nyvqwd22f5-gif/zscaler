# Configuring a Safe Process
Source: https://help.zscaler.com/deception/configuring-safe-process
PDF: https://help.zscaler.com/pdf/com/en/1531455.pdf

You can configure a process with a few filters and mark them as safe. These processes do not generate security events when accessing the decoy lures.
To configure a process as safe:
- Go to **Settings **> **Endpoint Settings **> **Safe Processes**.
-
Click **Add Safe Process**.
The **Safe Process Details** window appears.
[See image.](#deception-add-safe-process-option)
-
In the **Safe Process Details** window:
- Select **Enabled**.
- (Optional) Enable **Check process tree **to include the safe process as part of the process tree check when generating events. Decoy interactions that involve process trees with these safe processes do not generate events.
- **Name**: Enter a unique identifier for the safe process (e.g., `notepad++`).
-
Configure at least one of the following fields to identity a safe process:
-
**Selection Type**:** **Choose the type of executable path you want to use for identifying a safe process. If you want to use regular expression for the path value, select **Executable Path Regex **from the drop-down menu, and enter the regex expression in the **Executable Path Regex **field (e.g., `Mcafee.*\.exe`). If you want to use an absolute path value, select **Executable File Path **from the drop-down menu, and enter the absolute path value in the **Executable File Path **field. (e.g., `C:\Program Files\Notepad++\notepad++.exe`).
You can use regular expressions for path values if the processes that you want to mark as safe have names with predictable string of characters, such as version number.
[See image.](#regex-path-value)
- **Executable File Hash**: Enter the executable file hash (e.g., `06EB891AAF62499719416B53F2CC9428D0ADE77C80A664A7F3A177F596E06BA7`).
- **Certificate Issuer**: Enter the certificate issuer name (e.g., `CN=DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1, O="DigiCert, Inc.", C=US`).
- **Certificate Serial**: Enter the certificate serial number (e.g., `03AA6492DE9D96A90A4BCA97BEADB44A`).
- **Certificate Thumbprint**: Enter the certificate thumbprint (e.g., `A731D48CD8E2A99BB91F7C096F40CEDF3A468BA6`).
If more than one field is configured, a process is classified as safe process only if all of the field values match with their respective attributes of the process.
[See image.](#deception-safe-process-config-details)
-
Click **Save**.
The safe process is added.
[See image.](#deception-safe-process-added)
[]![Add Safe Process option](/downloads/deception/settings/endpoint-settings/safe-processes/configuring-safe-process/zscaler-deception-add-safe-process-button.png)
[]![Configuring a safe process with filters](/downloads/deception/settings/endpoint-settings/safe-processes/configuring-safe-process/zscaler-deception-safe-processes-details-new.jpg)
[]![Safe process added](/downloads/deception/settings/endpoint-settings/safe-processes/configuring-safe-process/zscaler-deception-safe-process-added.png)
[]
![RegEx Path Value](/downloads/deception/settings/endpoint-settings/safe-processes/configuring-safe-process/zscaler-deception-regex-safe-processs-new.jpg)