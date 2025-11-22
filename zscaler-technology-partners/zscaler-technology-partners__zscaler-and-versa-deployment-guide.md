# Zscaler and Versa Deployment Guide
Source: https://help.zscaler.com/zscaler-technology-partners/zscaler-and-versa-deployment-guide
PDF: https://help.zscaler.com/pdf/com/en/1390346.pdf

The Zscaler and Versa Deployment Guide provides instructions on integrating Zscaler Internet Access (ZIA) with the Versa platform.
This guide explains how to configure automated IPSec tunnel provisioning from the Versa Director to ZIA. Versa Operating System (VOS) devices integrate with Zscaler using a site-to-site IPSec VPN tunnel from the customer premises equipment (CPE) to a Zscaler Public Service Edge. Versa Director provides workflow-based automation to configure IPSec tunnels from Versa SD-WAN CPEs to ZIA using the Zscaler API. You use template-based workflows to create the following tunnels and location:
- Two or more tunnels to primary and secondary Zscaler servers from each CPE for data forwarding.
- Location for each CPE.
Versa Director supports IPSec tunneling between the CPE to Zscaler servers. For multiple LAN VRs configured on the CPE, you can choose one or more VRs from which traffic is forwarded to Zscaler servers. For each internet link, a primary tunnel is created to the primary Public Service Edge and a backup tunnel is created to the secondary Public Service Edge.
[Zscaler and Versa Deployment Guide](/downloads/zscaler-technology-partners/t-z/zscaler-and-versa-deployment-guide/Zscaler-Versa-Deployment-Guide-FINAL.pdf) [Download PDF](/downloads/zscaler-technology-partners/t-z/zscaler-and-versa-deployment-guide/Zscaler-Versa-Deployment-Guide-FINAL.pdf)