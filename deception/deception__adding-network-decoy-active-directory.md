# Adding an Internal Network Decoy to an Active Directory Domain
Source: https://help.zscaler.com/deception/adding-network-decoy-active-directory
PDF: https://help.zscaler.com/pdf/com/en/1531282.pdf

You can add an Internal network decoy to an Active Directory (AD) domain and AD DNS as an AD decoy computer object to make it look like a legitimate domain-joined system. AD decoy computers detect AD enumeration activities and AD-related exploits.
Before adding an Internal network decoy as a decoy computer object, you must [add an AD domain](/deception/adding-active-directory-domain).
To add an Internal network decoy to an AD domain as a decoy computer:
- Go to **Deceive** > **Network Decoys > Internal**.
- Select an Internal network decoy that you want to add as an AD decoy computer.
-
Under **Actions**, click the **Edit** icon.
[See image.](#edit-decoy-ad)
-
In the **Network Decoy Detail** window, on the **Active Directory** tab:
- Enable **Add to Active Directory** to add the network decoy as a computer object in an AD domain.
- Select an operating system (OS) from the **Select OS Attribute **drop-down menu. The OS details appear in the properties of the decoy computer object in the AD.
- Select an AD domain from the **Domain **drop-down menu.
- Select or enter the complete organization unit (**OU**) path:
- If you configure an AD domain with credentials, the OU paths are automatically listed in the drop-down menu.
- If you configure an AD domain without credentials, manually enter the OU path.
- (Optional) Enter the **Description** of the AD decoy computer.
[See image.](#configure-decoy-AD)
- Click **Submit**.
-
[Start the decoys](/deception/starting-and-stopping-decoys#start-decoys).
The network decoy is added. To create an AD decoy computer in the AD domain with configuration details such as OS, OU path, etc., [run the AD deployment script](/deception/running-decoy-deployment-script-active-directory).
For AD decoy computer created in domains managed by [server agents](/deception/installing-server-agent), you don't have to manually run the deployment scripts. The server agent automates AD decoy deployment.
You can view the AD decoy computer objects on the [Decoy Computers](/deception/viewing-active-directory-decoy-computers) page.
[See image.](#deception-view-ad-comp-object)
[]![Edit a network decoy](/downloads/deception/deceive/network-decoys/adding-network-decoy-active-directory/zscaler-deception-ad-decoy-computer-edit-nw-decoy.png)
[]![Configure an AD computer object](/downloads/deception/deceive/network-decoys/adding-network-decoy-active-directory/zscaler-deception-ad-decoy-computer-config-details.png)
[]![View and manage AD decoy computer objects](/downloads/deception/deceive/network-decoys/adding-network-decoy-active-directory/zscaler-deception-ad-decoy-computer-page-1.png)