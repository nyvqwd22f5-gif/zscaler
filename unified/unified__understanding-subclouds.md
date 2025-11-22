# Understanding Subclouds
Source: https://help.zscaler.com/unified/understanding-subclouds
PDF: https://help.zscaler.com/pdf/com/en/1495236.pdf

A [subcloud](/unified/about-subclouds) is a subset of Internet & SaaS Public Service Edges, which are full-featured secure internet gateways that inspect all web traffic bi-directionally for malware, and enforce security, compliance, and next-generation firewall (NGFW) policies. Internet & SaaS Public Service Edges are deployed in Zscaler data centers around the globe, so when your users move to a different location, they can access the internet from any device and the Internet & SaaS Public Service Edges protect their traffic and apply your corporate policies.
If certain requirements make forwarding traffic to the Internet & SaaS Public Service Edges less than ideal, you can extend Zscaler's patented cloud architecture to your organization's premise by deploying [Private Service Edges](/unified/understanding-private-service-edge) or [Virtual Service Edges](/unified/about-virtual-service-edges).
A subcloud can be a subset of Internet & SaaS Public Service Edges, a subset of Private Service Edges, or a subset of both Internet & SaaS Public Service Edges and Private Service Edges. A subcloud cannot be a subset of Internet & SaaS Public Service Edges in only one data center.
Using a Subcloud
Zscaler always recommends that organizations forward traffic to the Internet & SaaS Public Service Edges in the Zscaler cloud. They are deployed in active-active mode all over the world, to ensure availability and redundancy. Zscaler monitors and maintains its Internet & SaaS Public Service Edges worldwide to ensure 24/7 availability.
The service uses geolocation technology to find the Internet & SaaS Public Service Edge closest to the user and forwards web traffic to that Internet & SaaS Public Service Edge, which in some cases might be less than ideal. For example, you might be required to forward web traffic to the Internet & SaaS Public Service Edges in a specific region only, but if a remote user has traveled outside of it, then web traffic might be forwarded to an Internet & SaaS Public Service Edge located outside of your preferred region. In such a case, an organization can use a subcloud to ensure that traffic is forwarded to your preferred Internet & SaaS Public Service Edges.
Following are the different types of subclouds that Zscaler can set up, depending on an organization's requirements:
- [Internet & SaaS Public Service Edges](#Public-ZEN-link)
- [Internet & SaaS Private Service Edges](#Service-Private_ZEN-link)
- [Internet & SaaS Public Service Edges and Private Service Edges](#Public-service-ZEN-link)
The illustrations used in these sections are for example purposes only and the locations listed are subject to change.
Setting Up a Subcloud
If you are interested in having a subcloud for your organization, submit a ticket to Zscaler Support. The Zscaler service sets up the subcloud if your organization has access only to limited, restricted, or private data centers.
The subcloud name can contain up to 32 characters, including alphabet (both upper and lower cases), numerals, or hyphen (-). The first and last character must always be an alphabet or a numeral.
Using PAC File Variables
If you want to use a PAC file to forward your web traffic to a subcloud, you must use a custom PAC file that doesn't use the variables `gateway.``<Zscaler cloud>` and `${GATEWAY}` in its return statement. Otherwise, web traffic is forwarded to the nearest public Internet & SaaS Public Service Edge, which might not be an Internet & SaaS Public Service Edge in your subcloud.
To ensure your web traffic is always forwarded to the Internet & SaaS Public Service Edges specified in the subcloud:
- Use the following variables for applications that don't support PAC files:
gateway.<Subcloud>.<Zscaler cloud>
secondary.gateway.<Subcloud>.<Zscaler cloud>
- Use the following variables in PAC files:
${GATEWAY.<Subcloud>.<Zscaler cloud>}
${SECONDARY.GATEWAY.<Subcloud>.<Zscaler cloud>}
- Use the following variables for Kerberos:
${GATEWAY.<Subcloud>.<Zscaler cloud>_HOST}
${SECONDARY.GATEWAY.<Subcloud>.<Zscaler cloud>_HOST}
Each subcloud is associated with a DNS name, which resolves the Internet & SaaS Public Service Edges in that subcloud. Replace `<Subcloud>` with the DNS name of the subcloud, and replace `<Zscaler cloud>` with your cloud name.
For example, if you want to restrict the traffic forwarding within the data centers only in the US, then configure your PAC files to use the Zscaler-managed subcloud CONUS for any of the following clouds:
- zscaler.net
- zscalertwo.net
- zscalerthree.net
Use the variables `${GATEWAY.CONUS.``<Zscaler cloud>``}` and `${SECONDARY.GATEWAY.CONUS.``<Zscaler cloud>``}` in the return statement of your PAC file.
Subcloud Failover
After you edit the data center list for a subcloud from the [Subclouds](/unified/about-subclouds) page in the Admin Portal, it takes about 5 minutes for the changes to be reflected in Zscaler Hosted PAC files. Zscaler Client Connector automatically refreshes the Application Profile PAC every 15 minutes and picks up the subcloud change on the next sync which overlaps with the Application Profile PAC being updated. Users should be redirected about 10–20 minutes after the subcloud changes are activated.
It is also possible to trigger a failover more rapidly by manually requesting an app policy update in the Zscaler Client Connector. This can shorten the failover time to 5 minutes.
Ensure that the Application Profile PAC has been updated to reflect the subcloud changes prior to requesting an app policy update.
To update the app policy:
- Open Zscaler Client Connector on the client machine.
- Go to **More**.
- Click **Update Policy** next to** App Policy** to immediately sync the Application Profile PAC.
[]For organizations that need to forward web traffic to Internet & SaaS Public Service Edges in a specific region only, a subcloud that consists of only Internet & SaaS Public Service Edges located in that region can be created. For example, if you need to forward web traffic to Internet & SaaS Public Service Edges that are located in Europe only (for compliance or regulatory requirements), you can use a subcloud that consists of Internet & SaaS Public Service Edges in Europe, as shown in the following illustration.
![Geographical map of Zscaler public ZENs](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/about-traffic-forwarding/what-subcloud/public_zens_map.png)
[]If you want your web traffic to be forwarded to only Internet & SaaS Private Service Edges, a subcloud that consists of only your Internet & SaaS Private Service Edge can be created. This ensures that your traffic does not get forwarded to Internet & SaaS Public Service Edges. In the following illustration, the subcloud's name is *Safemarch*.
![Map of North and South American Zscaler public ZENs and subcloud containing private ZENs](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/about-traffic-forwarding/what-subcloud/zia_private_service_edge_pzens.png)
[]If you want your web traffic to be forwarded to certain Internet & SaaS Public Service Edges and Private Service Edges, a subcloud that consists of only your preferred Internet & SaaS Public Service Edges and Private Service Edges can be created. This ensures that your traffic is only forwarded to the Internet & SaaS Public Service Edges in that subcloud. In the following illustration, the subcloud's name is *Safemarch2*.
![Map of North and South American Zscaler public ZENs and subcloud containing public and private ZENs](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/about-traffic-forwarding/what-subcloud/zia_public_service_edge_private_service_edge_pzens.png)