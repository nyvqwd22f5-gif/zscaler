# Ranges & Limitations
Source: https://help.zscaler.com/zdx/ranges-limitations
PDF: https://help.zscaler.com/pdf/com/en/1358871.pdf

This article lists the ranges and limitations for applications, probes, alerts, rules, webhooks, and other ZDX features, based on subscription level. All values are per organization unless noted otherwise.
If you need to increase maximum limits for your organization, send a request to Zscaler Support.
Applications and Probes
The following table shows the ranges and limitations for [Applications and Probes](/zdx/configuration) settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Total Number ofInternet Web Applications | 512 | 512 | 512 | 512 |
| Active Probes (per tenant) | 3 | 7 | 30 | 100 |
| Active Probes (per user) | 3 | 7 | 30 | 30 |
| Total Number of Cloud Path and Web Monitoring Probes | 512 | 512 | 512 | 512 |
| Active Probes | 6 | 13 | 30 | 100 |
| Probing Interval | 15 minutes | 5 minutes | 5 minutes | 5 minutes |
| Page Fetch Time Server Redirects | Not supported | Not supported | Not supported | Supported |
| ZDX Autosense (Webex Call Quality) | Not supported | Not supported | Supported | Supported |
| ZDX Autosense (Zoom Call Quality) | Not supported | Not supported | Supported | Supported |
| ZDX Autosense (Microsoft Teams Call Quality) | Not supported | Supported | Supported | Supported |
Analytics
The following table shows the support settings for [Analytics](/zdx/analytics):
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Hop View (Granular Expanded Cloud Path) | Supported | Supported | Supported | Supported |
| Software and Device Inventory | Not supported | Not supported | Supported | Supported |
| Process Inventory | Not supported | Not supported | Not supported | Supported |
| Software Patch Inventory | Supported | Supported | Supported | Supported |
| UCaaS Monitoring | Not supported | Microsoft Teams Call Quality (only) | Supported | Supported |
| UCaaS Monitoring (tenant limit) | Not supported | 40 | 40 | 40 |
| Root Cause Analysis | Not supported | Not supported | Supported | Supported |
| System-Generated Reports | Not supported | Not supported | Supported | Supported |
| Incidents | Not supported | Not supported | Not supported | Supported |
| ZDX Snapshots | Not supported | Not supported | Supported | Supported |
| Self Service | Not supported | Not supported | Not supported | Supported |
| Data Explorer Views | Not supported | Not supported | 30 | 100 |
| Data Explorer Applications | Not supported | Not supported | 1 | 4 |
| Data Explorer Metrics | Not supported | Not supported | 1 | 4 |
| Wi-Fi | Not supported | Not supported | Supported | Supported |
| ZIA PSE Health | Supported | Supported | Supported | Supported |
| Hosted Monitoring* | Supported only as add-on | Supported only as add-on | Supported only as add-on | 1 probe per 1,000 users for each hosted location |
| Network Intelligence | Not supported | Not supported | Not supported | Supported |
| Device Health Dashboard | Not supported | Not supported | Not supported | Supported |
| Device Events Reports | Not supported | Not supported | Supported | Supported |
*Identical ranges and limitations across add-ons for Standard, Microsoft 365, and Advanced subscriptions.
Alerts
The following table shows the ranges and limitations for [Alerts](/zdx/alerts) settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Total Alerts | 512 | 512 | 512 | 512 |
| Total Active Alerts (Alerts with Incident Correlation) | Up to 3 | 10 | 25 | 100 |
| Total Alert Rules | Up to 3 | 10 | 25 | 100 |
| Dynamic Alerting | Not supported | Not supported | Supported | Supported |
Diagnostics
The following table shows the ranges and limitations for [Diagnostics](/zdx/diagnostics) settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Total Diagnostics Sessions | Not supported | 25 | 25 | 100 |
| Total Active Sessions | Not supported | 25 | 25 | 100 |
Integrations and Data Retention
The following table shows the ranges and limitations for Integrations and Data Retention settings:
| **Feature** | **Standard** | **Microsoft 365** | **Advanced** | **Advanced Plus** |
| ----------- | ------------ | ----------------- | ------------ | ----------------- |
| Webhooks | Not supported | 10 | 10 | 50 |
| ZDX APIs | Not supported | Supported for Microsoft 365 events | Supported | Supported |
| Query LimitData Retention | 2 days | 14 days | 14 days | 14 days |
| Query LimitTime Span Selection Range | 2 to 24 hours | 2 to 48 hours | 2 to 48 hours | 2 to 48 hours |
| ZDX Snapshots | Not supported | Not supported | 90 days | 90 days |
| ZDX Copilot | Not supported | Not supported | Not supported | Supported |
| Workflow Automation | Not supported | Not supported | Not supported | Supported |
[]Organization
The following table shows the ranges and limitations for Organization settings:
| Feature | Limit |
| ------- | ----- |
| Admin Users per Organization | 10K adminsAdmin users can reside in Zscaler Internet Access (ZIA) or Zscaler Private Access (ZPA). |
| Active Admins | 255 active adminsAdmins connected to the cloud are considered active admins. |