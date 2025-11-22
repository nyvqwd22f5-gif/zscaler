# Ranges & Limitations
Source: https://help.zscaler.com/cloud-branch-connector/ranges-limitations
PDF: https://help.zscaler.com/pdf/com/en/1420771.pdf

This article lists the ranges and limitations for rules, policies, fields, and other features.
[]Groups
The following table shows group ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Group Name | 255 characters |
| Network Services Groups | 126 groups |
| Source IP Address Groups | 4,000 groups |
| Destination Groups (Destination IP or FQDN Groups) | 4,000 groups |
| Fully Qualified Domain Names (FQDNs) or IP Addresses per Group | 8,000 addresses |
| Cloud Connector Groups | 1,000 groups |
| Branch Connector Groups | 1,000 groups |
| Virtual Machines (VMs) per Group | 16 VMs |
| Application Segment Groups | 600 groups |
[]Locations
The following table shows location ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Locations | 1,000 locations |
| Location Name | 255 characters |
| Location Templates | 500 templates |
[]NSS
The following table shows ranges and limitations for Nanolog Streaming Service (NSS) filter feeds:
| Feature | Limit |
| ------- | ----- |
| NSS Servers | 2 servers |
| NSS Feeds per Server | 8 feeds |
| NSS Users per Feed | 1,024 users |
| NSS Departments per Feed | 1,024 departments |
| NSS Locations per Feed | 1,024 locations |
| NSS Clients per Feed | 1,024 clients |
| NSS Threat Names per Feed | 1,024 threat names |
[]Organization
The following table shows the ranges and limitations for information related to the organization:
| Feature | Limit |
| ------- | ----- |
| Address Line 1 | 10,240 bytes |
| Address Line 2 | 10,240 bytes |
| City/State/ZIP | 1,024 bytes |
| Name/Title/Phone/Alternate Phone | 1,024 bytes |
| Admin Users per Organization | 10K admins |
| Admin User Login ID | 128 characters |
| Admin User Email | 254 characters |
| Admin User Name | 256 characters |
| Admin User Comments | 10,240 bytes |
| Admin User Password | 100 characters |
| Admin Roles | 64 roles |
| Identity Providers | 16 identity providers |
[]Forwarding
The following table shows the forwarding ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Traffic Forwarding Rules | 1,020 rules |
| Log & Control Forwarding Rules | 1,020 rules |
| Domains/FQDNs per Organization | 1,024 domains/FQDNs |
| Domains/FQDNs per Rule | 1,024 domains/FQDNs |
| ZIA Gateways | 1,000 gateways |
| Log and Control Gateways | 1,000 gateways |
| DNS Gateways | 255 gateways |
| DNS Control Policy Rules | 1,020 rules |
| Application Segments | 50,000 segments |
| Description | 10,240 characters |
[]Provisioning and Configuration
The following table shows the provisioning and configuration ranges and limitations:
| Feature | Limit |
| ------- | ----- |
| Cloud Provisioning Templates | 1,000 templates |
| Branch Configuration Templates | 1,000 templates |
| Branch Connector Static Routes | 32 routes |
| Branch Connector DHCP Server Static Leases | 32 leases |
| Branch Connector Virtual local area networks (VLANs) per Interface | 9 subinterface VLANs and one main untagged VLAN per interface, or 10 subinterface VLANs without the main untagged VLAN |
Zero Trust Gateways
| **Feature** | **Limit** |
| ----------- | --------- |
| Amazon Web Services (AWS) Accounts per Gateway | 128 AWS accounts |
| Traffic Tests | 128 tests |
| Endpoints | 128 per availability zone (AWS recommends 50 per availability zone) |
Partner Integrations
| **Feature** | **Limit** |
| ----------- | --------- |
| AWS Accounts per Organization | 512 accounts |
| AWS Accounts per Group | 96 accounts |
| Regions in an AWS Account | 32 regions |
| AWS Groups per Organization | 128 groups |
| Cloud Connector Groups per AWS Group | 64 groups |
| Microsoft Azure Accounts per Organization | 128 accounts |
| Regions in an Azure Account | 32 regions |
| Subscriptions in an Azure Account | 32 subscriptions |
| Cloud Connector Groups in an Azure Account | 64 groups |
| Google Cloud Platform (GCP) Accounts per Organization | 128 accounts |
| Projects in a GCP Account | 64 projects |
| Cloud Connector Groups in a GCP Account | 64 groups |