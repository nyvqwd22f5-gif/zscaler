# Configuring a Safe Process
Source: https://help.zscaler.com/itdr/configuring-safe-process
PDF: https://help.zscaler.com/pdf/com/en/1531660.pdf

You can configure a process with a few filters and mark them as safe. Marking trusted processes as safe prevents generating false positives.
To configure a process as safe:
- Go to **Settings** > **Endpoint Settings** > **Safe Processes**.
-
Click **Add Safe Process**.
[See image.](#deception-add-safe-process-option)
- In the **Safe Process Details** window:
- Select **Enabled **to enable the safe process.
- **Name**: Enter a unique identifier for the safe process (e.g., `notepad++`).
-
**Selection Type**: Select one of the following executable paths to identify a safe process.
- If you want to use an absolute path value, select **Executable File Path **from the drop-down menu, and enter the absolute path value in the **Executable File Path **field. (e.g., `C:\Program Files\Notepad++\notepad++.exe`).
- If you want to use regular expression for the path value, select **Executable Path Regex **from the drop-down menu, and enter the regex expression in the **Executable Path Regex **field (e.g., `*mcafee.*\.exe`).
[See image.](#selection-type)
You can use regular expressions for path values if the processes that you want to mark as safe have names with a predictable string of characters, such as a version number. [See image.](#selection-type-regex)
- **Executable File Hash**: Enter the executable file hash (e.g., `06EB891AAF62499719416B53F2CC9428D0ADE77C80A664A7F3A177F596E06BA7`).
- **Certificate Issuer**: Enter the certificate issuer name (e.g., `CN=DigiCert Trusted G4 Code Signing RSA4096 SHA384 2021 CA1, O="DigiCert, Inc.", C=US`).
- **Certificate Serial**: Enter the certificate serial number (e.g., `03AA6492DE9D96A90A4BCA97BEADB44A`).
- **Certificate Thumbprint**: Enter the certificate thumbprint (e.g., `A731D48CD8E2A99BB91F7C096F40CEDF3A468BA6`).
[See image.](#itdr-safe-process-config-details)
-
Click **Save**.
The safe process is added.
[]![Add Safe Process option](/downloads/itdr/endpoint-settings/safe-processes/configuring-safe-process/itdr-add-safe-process.png)
[]![Configure a safe process with filters](/downloads/deception/deceive/landmine-decoys/safe-processes/configuring-safe-process/zscaler-deception-safe-process-newone.jpg)
[]![itdr-safe-process-selection.png](/downloads/itdr/endpoint-settings/safe-processes/configuring-safe-process/itdr-safe-process-selection.png)
![itdr-selection-type-regex.png](/downloads/itdr/endpoint-settings/safe-processes/configuring-safe-process/itdr-selection-type-regex.png)
[]