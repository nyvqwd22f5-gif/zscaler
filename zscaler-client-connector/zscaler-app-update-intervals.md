# Zscaler Client Connector Update Intervals
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-app-update-intervals
PDF: https://help.zscaler.com/pdf/com/en/1330276.pdf

Zscaler Client Connector automatically updates at the set intervals:
- Every 15 minutes, Zscaler Client Connector downloads the PAC files of the app profiles and forwarding profiles.
- Every 80 minutes, Zscaler Client Connector connects for policy updates from the app profiles, forwarding profiles, and administration settings.
If the PAC file URLs are changed, it automatically updates every 80 minutes because this counts as a profile change.
- Every 2 hours, Zscaler Client Connector checks for software updates.
You cannot configure these intervals. If the user manually updates the policy from their device, Zscaler Client Connector updates immediately.