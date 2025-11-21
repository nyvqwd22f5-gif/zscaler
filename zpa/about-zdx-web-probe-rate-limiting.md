# About ZDX Web Probe Rate Limiting
Source: https://help.zscaler.com/zpa/about-zdx-web-probe-rate-limiting
PDF: https://help.zscaler.com/pdf/com/en/1485131.pdf

Rate limits throttle the number of successful connections per application segment for ZPA Public Service Edges or ZPA Private Service Edges when using web probes for Zscaler Digital Experience (ZDX) integrations.
The system will rate limit if there are more than:
- 50 web probe requests per second to the server for an individual ZPA Public Service Edge
- 35 web probe requests per second to the server for an individual ZPA Private Service Edge
For example, if the max rate limit is 50 requests per second, only 50 successful connections are allowed to the server within each second.
Rate limits protect your application servers when integrating with ZDX. To adjust the rate limits of web probes, contact Zscaler Support.