# Configuring Access to Distributed File Servers
Source: https://help.zscaler.com/zpa/configuring-access-distributed-file-servers
PDF: https://help.zscaler.com/pdf/com/en/1483926.pdf

The following methods can be used to configure access to Distributed File Servers (DFS) while using Kerberos for authentication:
- [Using a Wildcard Domain](#WildCardDomains)
- [Configure Separate Applications for DFS (with Kerberos) and SRV Resolution](#ApplicationsForDFSAndSRV)
- [Configure Separate Applications for File Servers and Domain Controllers, and SRV Resolution](#ApplicationsForFSAndDCAndSRV)
Zscaler recommends a dedicated App Connector Group for the File Server applications. These applications can be latency sensitive and may experience performance degradation if the associated App Connectors provide access to other applications as well.
The following list provides port descriptions for TCP and UDP:
- TCP/88: Kerberos
- TCP/464: Kerberos Password Change
- TCP/389: LDAP
- TCP/3268: Global Catalog
- TCP/3269: Global Catalog SSL (Optional)
- TCP/135: MSRPC
- TCP/139: Common Internet File Service (CIFS)
- TCP/445: CIFS
- UDP/88: Kerberos
- UDP/464: Kerberos Password Change
- UDP/389: LDAP
- UDP/636: LDAPS (Optional)
- UDP/138: NetBT datagram (File Server)
- UDP/123: NTP Service
- UDP/445: CIFS
To learn more, see [Configuring Application Segments](/zpa/about-application/onboard).
[]Within ZPA, [define an application](/zpa/about-application/onboard#tab1) in the application segment using a wildcard domain and associated ports, for example:
![Wildcard Domain Configuration for DFS](/downloads/zpa/documentation-knowledgebase/knowledge-base/how-do-i-configure-access-distributed-file-servers-zpa/config1_wildcard.png)
[]This configuration can be used when the same server is set up as a file server and domain controller.
Configuring the DFS with Kerberos
Within ZPA, [define an application](/zpa/about-application/onboard#tab1) in the application segment for DFS with Kerberos using wildcard domains and ports, for example:
![Wildcard Domain Configuration for DFS with Kerberos](/downloads/zpa/documentation-knowledgebase/knowledge-base/how-do-i-configure-access-distributed-file-servers-zpa/config2_dfs_kerberos.png)
Enabling SRV Resolution
ZPA requires an application to be defined as a wildcard with any port to resolve SRV records. So, for this application segment configuration, you are using a dummy port, Port 1, for SRV record DNS resolution. For example:
![Enabling SRV Resolution](/downloads/zpa/documentation-knowledgebase/knowledge-base/how-do-i-configure-access-distributed-file-servers-zpa/ZPAConfig_SRV1.png)
[]This configuration can be used when the domain controller and file server are set up on separate servers, as detailed in the image below.
![Distributed File Server (DFS) and Domain Controller (DC) on Separate Servers](/downloads/zpa/documentation-knowledgebase/knowledge-base/how-do-i-configure-access-distributed-file-servers-zpa/ZPA_DCAndFSOnSepServers.png)
Configuring the File Server
Within ZPA, [define an application](/zpa/about-application/onboard) for the file server using wildcard domains and ports, for example:
![Configuring an Application for DFS](/downloads/zpa/documentation-knowledgebase/knowledge-base/how-do-i-configure-access-distributed-file-servers-zpa/ZPAConfig_FS.png)
Configuring Kerberos on the Domain Controller
Within ZPA, [define an application](/zpa/about-application/onboard#tab1) in the application segment for Kerberos on the domain controller using wildcard domains and ports, for example:
![Configuring Kerberos on the Domain Controller](/downloads/zpa/documentation-knowledgebase/knowledge-base/how-do-i-configure-access-distributed-file-servers-zpa/ZPAConfig_DC.png)
Enabling SRV Resolution
ZPA requires an application to be defined as a wildcard with *any* port to resolve SRV records. So, for this application segment configuration you are using a dummy port, Port 1, for SRV record DNS resolution. For example:
![Enabling SRV Resolution](/downloads/zpa/documentation-knowledgebase/knowledge-base/how-do-i-configure-access-distributed-file-servers-zpa/ZPAConfig_SRV1.png)