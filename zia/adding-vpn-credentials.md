# Adding VPN Credentials
Source: https://help.zscaler.com/zia/adding-vpn-credentials
PDF: https://help.zscaler.com/pdf/com/en/1399486.pdf

Configuring a VPN credential is one of the tasks you must complete when configuring an IPSec VPN tunnel. To learn more, see [Configuring an IPSec VPN Tunnel](/zia/configuring-ipsec-vpn-tunnel). You can add up to 16,000 credentials. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zia/ranges-limitations#VPNCredentials). You can also add or remove multiple VPN credentials by [importing a CSV file](/zia/importing-vpn-credentials-csv-file).
To add a VPN credential:
- Go to **Administration** > **VPN Credentials**.
- Click **Add VPN Credential**.
- Choose the **Authentication Type **that is used to identify the peer, and configure it accordingly:
- [FQDN](#fqdn)
- [IP](#ip)
You can edit or delete an existing XAUTH VPN credential from the ZIA Admin Portal. However, you cannot add a new XAUTH VPN credential.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If you have entered a **User ID**, it is automatically converted to lowercase after clicking **Save**.
- []**Managed By**: If this VPN credential is being managed by an [SD-WAN partner](/zia/about-partner-integration-management), search for and select their name from the drop-down menu. If this VPN credential is not being managed by a partner, choose **Self**.
- **User ID**:** **Enter the FQDN of the peer. The FQDN can be up to 256 characters. It must be valid and cannot include special characters (e.g., <, @, [], etc.) or end in a period (e.g., safemarch.).
- **New Pre-Shared Key**:** **Enter a pre-shared key. The pre-shared key can be up to 255 characters.
- **Confirm**** New Pre-Shared Key**:** **Re-enter the pre-shared key.
- **Comments**: (Optional) Enter additional notes or information.
- []**IP Address**:** **Choose the IP address** **of your local gateway.
The static IP addresses that appear in the drop-down menu are the addresses that are provisioned for your organization. To learn more, see [Self-Provisioning of Static IP Addresses](/zia/self-provisioning-static-ip-addresses). If you want Zscaler to provision your static IP addresses, submit them to Zscaler Support so that they can be properly added to the menu under **IP Address**.
- **New Pre-Shared Key**:** **Enter the pre-shared key. The pre-shared key can be up to 255 characters.
- **Confirm**** New Pre-Shared Key**:** **Re-enter the pre-shared key.
- **Comments**: (Optional) Enter additional notes or information.