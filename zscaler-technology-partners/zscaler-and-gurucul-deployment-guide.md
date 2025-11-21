# Zscaler and Gurucul Deployment Guide
Source: https://help.zscaler.com/zscaler-technology-partners/zscaler-and-gurucul-deployment-guide
PDF: https://help.zscaler.com/pdf/com/en/1472111.pdf

The Zscaler and Gurucul Deployment Guide provides instructions on how to configure Zscaler Internet Access (ZIA) to work with Gurucul NGSIEM and UEBA products.
Gurucul NGSIEM improves data collection and infrastructure visibility, while automating and consolidating manual tasks related to correlation, analysis, investigation, and response actions. Gurucul User & Entity Behavior Analytics (UEBA) detects and responds quickly to threats based on an understanding of normal activity that continuously learns and adjusts to characterize suspicious and anomalous activity.
Gurucul integrates with ZIA using:
- Nanolog Streaming Service (NSS): NSS forwards ZIA logs over secure Syslog connection to Gurucul’s log collection endpoint, which requires the deployment of a Zscaler NSS Virtual Machine.
- Cloud NSS: Gurucul integrates with ZIA through Cloud NSS using either AWS S3 Integration or HTTP Endpoint.
- Log Streaming Service (LSS): ZPA can send logs to Gurucul using the Syslog endpoint.
[Zscaler and Gurucul Deployment Guide](/downloads/zscaler-technology-partners/operations/zscaler-and-gurucul-deployment-guide/Zscaler-Gurucul-Deployment-Guide-FINAL.pdf) [Download PDF](/downloads/zscaler-technology-partners/operations/zscaler-and-gurucul-deployment-guide/Zscaler-Gurucul-Deployment-Guide-FINAL.pdf)