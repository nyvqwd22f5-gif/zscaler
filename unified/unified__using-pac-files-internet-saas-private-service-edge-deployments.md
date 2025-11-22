# Using PAC Files for Internet & SaaS Private Service Edge Deployments
Source: https://help.zscaler.com/unified/using-pac-files-internet-saas-private-service-edge-deployments
PDF: https://help.zscaler.com/pdf/com/en/1495606.pdf

Following are some additional requirements if your organization uses PAC files to forward traffic to Internet & SaaS Private Service Edges:
- Enable a policy on the corporate firewall to allow devices to retrieve PAC files from the Zscaler PAC servers. To learn more, see [Firewall Configuration Requirements for Internet & SaaS Private Service Edge Deployments](/unified/firewall-configuration-requirements-internet-saas-private-service-edge-deployments). If the PAC files are used only when users are remote or telecommuting, this step is not required.
- When an organization uses Private Service Edges, Zscaler creates a sub-cloud that maps the domain names `GATEWAY.``<Subcloud Name>``.``<Cloud Name>` and `SECONDARY.GATEWAY.``<Subcloud Name>``.``<Cloud Name>` to the IP addresses of the Private Service Edges and any Internet & SaaS Public Service Edges that you want to use. This ensures that your web traffic is sent to the specified Public Service Edges only.
Because of this, ensure that the PROXY statement in your PAC file specifies the following:
${GATEWAY.<Subcloud Name>.<Cloud Name>_FX}
${SECONDARY.GATEWAY.<Subcloud Name>.<Cloud Name>_FX}
For example:
return "PROXY ${GATEWAY.example.zscaler.net_FX}:80; PROXY ${SECONDARY.GATEWAY.example.zscaler.net_FX}:80; DIRECT"
To learn more, see [Writing a PAC File](/unified/writing-pac-file).