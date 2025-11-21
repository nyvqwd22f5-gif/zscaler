# Deploying Kerberos for Internet & SaaS Virtual Service Edges
Source: https://help.zscaler.com/unified/deploying-kerberos-internet-saas-virtual-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1495736.pdf

Zscaler supports authentication using Kerberos, an industry-standard security protocol. To learn more about Kerberos benefits, features, and limitations, see [About Kerberos Authentication](/unified/about-kerberos-authentication). Before deploying Kerberos for Internet & SaaS Virtual Service Edge, see [Kerberos Requirements](/unified/about-kerberos-authentication#kerberos-requirements), [Kerberos Deployment Guidelines](/unified/kerberos-authentication-deployment-guidelines), and [Deploying Kerberos](/unified/deploying-kerberos-authentication).
To deploy Kerberos authentication for a Virtual Service Edge:
- Go to **Administration **>** Identity **>** Internet & SaaS **>** Internet Authentication Settings**.
- On the **Default Settings** page, under **Kerberos Authentication**, select **Enable Kerberos**. You must enable Kerberos in order for the **Enable Kerberos** option to appear within the **Edit Location** window.
- Click **Save**.
- Use the following hostname format for a forward proxy or Kerberos PAC file entry:
- [Forward Proxy](#forward-proxy)
- [Kerberos PAC File](#pac-file)
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Location Management**.
-
On the **Locations** page, click the **Edit** icon for the location you want to use Kerberos authentication.
The **Edit Location** window appears.
-
In the **Edit Location** window:
- Select **Enforce Authentication**.
- Select **Enable Kerberos Authentication**.
To learn more, see [Configuring Locations](/unified/configuring-locations).
If Kerberos is enabled only in Authentication Settings and not in the Virtual Service Edge location configuration, all forward proxy traffic landing on ports 80/9443/DPPC-Port using the hostname format `vzen-``<Cluster IP Address>``-``<Company ID>``.gateway.``<Cloud Name>``.net` will do normal authentication, except port 8800. If the Virtual Service Edge location has Kerberos enabled, then all ports will use Kerberos authentication.
The Virtual Service Edge redirects traffic to gateway authentication for ports 8800 and 8443 if Kerberos is enabled for the location. You can avoid bypassing of Kerberos authentication for these ports by adding the following parameter to the `vzen_custom.conf` file:
[SME]
spnego_krb_noport_bypass=1
[-end-of-SME-]
The following caveats apply to this configuration:
- If Kerberos is enabled for a location with the `spnego_krb_noport_bypass=1` parameter set in the `vzen_custom.conf` file, then all the ports that the Virtual Service Edge is listening on, enforces Kerberos authentication.
- The pauth_port (8080) enforces digest authentication irrespective of the `spnego_krb_noport_bypass=1` parameter set in the `vzen_custom.conf` file or either Kerberos or digest authentication being enabled for the location.
- The Kerberos port (8800) enforces Kerberos authentication irrespective of the `spnego_krb_noport_bypass=1` parameter set in the `vzen_custom.conf` file or Kerberos authentication being enabled for the location.
- Click **Save** and activate the change.
[]The hostname format depends on the [deployment mode](/unified/adding-virtual-service-edge-instances#deployment-mode) of the Virtual Service Edge:
- For cluster deployment mode, use the [cluster IP address](/unified/adding-virtual-service-edge-clusters#cluster-ip-address):
vzen-<Cluster IP Address>-<Company ID>.gateway.<Cloud Name>.net
For example:
vzen-10-66-63-22-370255.gateway.zscalertwo.net
- For standalone deployment mode, use the [proxy IP address](/unified/adding-virtual-service-edge-instances#proxy-ip-address) of the Virtual Service Edge instance:
vzen-<Proxy IP Address>-<Company ID>.gateway.<Cloud Name>.net
For example:
vzen-10-66-63-21-370255.gateway.zscalertwo.net
[]Use the following hostname format for the Kerberos PAC file:
return "PROXY vzen-10-66-63-22-370255.gateway.<Cloud Name>.net:80; DIRECT";}