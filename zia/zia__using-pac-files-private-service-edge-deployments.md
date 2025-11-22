# Using PAC Files for Private Service Edge Deployments
Source: https://help.zscaler.com/zia/using-pac-files-private-service-edge-deployments
PDF: https://help.zscaler.com/pdf/com/en/1400576.pdf

Following are some additional requirements if your organization uses PAC files to forward traffic to Private Service Edges:
- Enable a policy on the corporate firewall to allow devices to retrieve PAC files from the Zscaler PAC servers. To learn more, see [Firewall Configuration Requirements for Private Service Edge Deployments](/zia/firewall-configuration-requirements-for-private-service-edge-deployments). If the PAC files are used only when users are remote or telecommuting, this step is not required.
- When an organization uses Private Service Edges, Zscaler creates a subcloud that maps the domain names `GATEWAY.``<Subcloud Name>``.``<Cloud Name>` and `SECONDARY.GATEWAY.``<Subcloud Name>``.``<Cloud Name>` to the IP addresses of the Private Service Edges and any ZIA Public Service Edges that you want to use. This ensures that your web traffic is sent to the specified Public Service Edges only.
Because of this, ensure that the PROXY statement in your PAC file specifies the following:
${GATEWAY.<Subcloud Name>.<Cloud Name>_FX}
${SECONDARY.GATEWAY.<Subcloud Name>.<Cloud Name>_FX}
For example:
return "PROXY ${GATEWAY.example.zscaler.net_FX}:80; PROXY ${SECONDARY.GATEWAY.example.zscaler.net_FX}:80; DIRECT"
To learn more, see [Writing a PAC File](/zia/writing-pac-file).