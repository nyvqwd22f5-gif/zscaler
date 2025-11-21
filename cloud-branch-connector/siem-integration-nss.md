# SIEM Integration for NSS
Source: https://help.zscaler.com/unified/siem-integration-nss
PDF: https://help.zscaler.com/pdf/com/en/1519486.pdf

Cloud NSS allows you to instantly stream logs from the Zscaler Admin Portal directly into a compatible cloud-based security information and event management (SIEM) system. If you subscribe to Cloud NSS, you can enable direct cloud-to-cloud log streaming.
There are two reliable log delivery mechanisms in NSS:
- NSS to SIEM: NSS buffers the logs in the VM memory to increase its resiliency to transient network issues between SIEM and NSS. If the connection drops, NSS replays logs from the buffer, according to the Duplicate Logs setting.
- Cloud NSS to SIEM: If the connectivity between the cloud and NSS is interrupted, NSS misses logs that arrived at the Nanolog cluster during the interruption, and they are not delivered to the SIEM. After the connection is restored, the NSS one-hour recovery allows the Nanolog to replay logs up to one hour prior.
For Cloud & Branch Connector, consider only the NSS for Firewall configurations in the integration guides and ignore the NSS for Web configurations as they are not applicable.