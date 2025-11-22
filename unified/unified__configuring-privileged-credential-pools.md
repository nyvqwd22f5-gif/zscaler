# Configuring Privileged Credential Pools
Source: https://help.zscaler.com/unified/configuring-privileged-credential-pools
PDF: https://help.zscaler.com/pdf/com/en/1524961.pdf

To add a privileged credential pool:
- Go to **Policies **> **Access Control **> **Clientless** > **Privileged Credentials > Credential Pools**.
- Click **Add**.
The **Add Privileged Credential Pool** window appears.
- In the **Add Privileged Credential Pool** window:
- **Name**: Enter a name for the privileged credential pool. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Type**: Select a sign-in protocol type.
- **Username-Password**: Select if you are using an RDP protocol.
- **SSH Key**: Select if you are using an SSH protocol.
- **Password**: Select if you are using a VNC or RealVNC option.
- **Privileged Credentials**: Select the privileged credentials you want to group from the drop-down menu.
You cannot change the protocol type after it’s been created and saved.
![The Add Privileged Credential Pool window in the Admin Portal ](/downloads/zpa/privileged-remote-access-management/privileged-credentials/configuring-privileged-credential-pools/Add%20Cred%20Pool.png)
- Click **Save**.