# About VPN Credentials
Source: https://help.zscaler.com/zia/about-vpn-credentials
PDF: https://help.zscaler.com/pdf/com/en/1399481.pdf

[Watch a video about VPN Credentials.](https://fast.wistia.net/embed/iframe/f2ki5pnuhc)
[]In an IPSec VPN Tunnel, two peers use a negotiation process called IKE (Internet Key Exchange) to define the security mechanisms they use to protect their communications. IKE has two phases. In the first negotiation phase, the peers define the security parameters they use to communicate in the second phase. The peers exchange VPN credentials to identify each other and authenticate. The VPN credentials can either be a pre-shared key or XAUTH; however, both peers must use the same VPN credential method and key for successful authentication.
Zscaler no longer supports adding a new XAUTH VPN credential, but you can edit or delete the existing entries from the ZIA Admin Portal.
In the ZIA Admin Portal, you can configure VPN credentials by either adding each credential individually or adding multiple credentials with a CSV file.
Configuring a VPN credential is one of the tasks you must complete when configuring an IPSec VPN tunnel. To learn more, see [Configuring an IPSec VPN Tunnel](/zia/configuring-ipsec-vpn-tunnel).
The VPN Credentials page provides the following benefits and enables you to:
- Configure VPN credentials for your organization for establishing IPSec VPN tunnels between your organization and the Zscaler data centers for forwarding internet-bound traffic to the Zscaler service.
- Import or delete multiple VPN credentials for different authentication types using a CSV file to reduce the configuration effort for the administrator.
About the VPN Credentials Page
[]On the VPN Credentials page (Administration > VPN credentials), you can do the following:
- [Add a VPN credential](/zia/adding-individual-vpn-credentials).
- [Import VPN credentials using a CSV file](/zia/importing-vpn-credentials-csv-file).
- Download a **Sample Import CSV file** and use it as a template to add or remove VPN credentials. Using the sample CSV file as a guide ensures that the format of your entries is correct before you [import the information](/zia/importing-vpn-credentials-csv-file).
- View a list of VPN credentials that are configured for your organization. For each VPN credential, you can see the following:
- **User/Certificate ID**: The User ID or IP address for the VPN credential. You can sort this column.
- **Authentication Type**: The authentication type used to identify the peer, FQDN, XAUTH, or IP. You can sort this column.
- **Location**: The name of the location associated with the VPN credential
- **Comments**: Displays any comments about the VPN credential, if available. You can sort this column.
- **Managed By**: The name of the partner that manages the VPN credential. To learn more, see [About Partner Integrations](/zia/about-partner-integration-management).
- [Edit a VPN credential](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- Filter a VPN credential search by **Authentication Type**.
- Search for a VPN credential.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
![VPN Credentials page within the Admin Portal](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/about-vpn-credentials/zia-vpncredentialspage.png)