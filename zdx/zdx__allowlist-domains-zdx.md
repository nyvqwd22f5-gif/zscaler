# Allowlist Domains for ZDX
Source: https://help.zscaler.com/zdx/allowlist-domains-zdx
PDF: https://help.zscaler.com/pdf/com/en/1355766.pdf

Certain destination domains are required to be placed on the allowlist on your corporate firewall or non-Zscaler proxy, including probes that are initiated by Zscaler Client Connector, as well as the monitored information sent by Zscaler Client Connector to the Zscaler cloud. If you are tunneling probe traffic through a GRE/IPSec tunnel at a corporate location, this action may be optional.
These domains are tied to IP addresses. Be sure to allow access to the following domains per Zscaler cloud:
ZIA
- gateway.<Zscaler Cloud Name>.net
- login.<Zscaler Cloud Name>.net
- mobile.<Zscaler Cloud Name>.net
- config.zscaler.com/<Zscaler Cloud Name>.net
- mtr.<Zscaler Cloud Name>.net
To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
ZDX
- login.zdxcloud.net
- pac.zdxcloud.net
- smres.zdxcloud.net
- https://d3l44rcogcb7iv.cloudfront.net
Zscaler Client Connector
- https://d32a6ru7mhaq0c.cloudfront.net
Ensure that certain domains or IPs are on the allowlist for Zscaler Client Connector. To learn more, see [Zscaler Client Connector Processes to Allowlist](/z-app/zscaler-app-processes-allowlist).