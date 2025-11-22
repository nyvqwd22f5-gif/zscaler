# Adding Process-Based Applications to Bypass Traffic
Source: https://help.zscaler.com/unified/adding-process-based-applications-bypass-traffic
PDF: https://help.zscaler.com/pdf/com/en/1494546.pdf

You can add process-based applications in the Admin Portal to bypass traffic. Add information such as paths, executable signatures, and certificate attributes to help identify process-based applications that can frequently change. You can then select these applications in [App Profiles](/unified/configuring-zscaler-client-connector-app-profiles) to bypass traffic for both Zscaler Tunnel (Z-Tunnel) 1.0 and Z-Tunnel 2.0 when using the Windows Filtering Platform (WFP). You must enable** Install WFP Driver** in [App Profiles](/unified/configuring-zscaler-client-connector-app-profiles) to use Process-Based Application Bypass.
After you add the process-based application to the app profile, you must restart the application before traffic is bypassed.
To add a process-based application to bypass traffic:
-
In the Admin Portal, go to **Infrastructure > Common Resources > Application > Process Based**.
![Process-Based Application Bypass](/downloads/client-connector/zscaler-client-connector-profile-management/adding-process-based-applications-bypass-traffic/Add-Process-Based-Application_Bypass.png)
- Click the **Process-Based** tab.
- Click **Add Application**.
-
In the **Add Application **window, complete the following fields:
- **Name**: Enter the name of the process-based application.
-
**Path**: Enter the executable file names for the application. You can use wildcards or environment variables as follows:
- Wildcards:
-
Use a single asterisk (*) to match any full single path component. For example: `*\Program\Apps\MSApps\ms-teams.exe`.
You can’t use a wildcard for partial components.
- Use two asterisks (**) to match any number of consecutive path components. For example: `**\ms-teams.exe`.
- Environment variables: The following example shows how to use environment variables in a path: `%APPDATA%\Zoom\bin`.
Press `Enter` or click the **Add **icon after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` or clicking the **Add **icon when finished.
- **Matching Criteria**: Select one or more options from the drop-down menu and then complete the fields that display.
- **SHA 2 Signature**
- **Application Name**: Enter a unique name of the executable signature that distinguishes it from other signatures.
- **Application Signature**: Enter the hash of the executable file.
- **Certificate Signer**
- **Certificate Name**: Enter a unique name of the code signing certificate to distinguish it from other signatures.
- **Certificate Thumbprint**: Enter the Certificate Thumbprint. For Zscaler Client Connector for Windows, use File Explorer to locate the certificate thumbprint.
- Navigate to the Program Files folder where Zscaler is installed.
- Double-click **Zscaler **> **ZSATunnel**.
- Right-click the **ZSATunnel** file and select **Properties**.
- Click the **Digital Signatures** tab.
- Select the signature from the **Signature list** window and click **Details**.
- Click **View Certificate**.
- Click the **Details **tab.
- Scroll down and select **Thumbprint**.
- Copy and paste the thumbprint into the **Certificate Thumbprint** field.
- **Certificate Subject**
- **Certificate Name**: Enter a unique name of the certificate subject to distinguish it from other certificate subjects.
- **Certificate Subject**: Enter a name that matches the subject of the certificate.
![Add Application Windows Process Based Applications](/downloads/client-connector/zscaler-client-connector-profile-management/adding-process-based-applications-bypass-traffic/Add%20Application%20-%20Process%20Based.png)
- Click **Save**.