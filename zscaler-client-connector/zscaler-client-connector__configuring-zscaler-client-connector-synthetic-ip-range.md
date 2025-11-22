# Configuring the Zscaler Client Connector Synthetic IP Range
Source: https://help.zscaler.com/zscaler-client-connector/configuring-zscaler-client-connector-synthetic-ip-range
PDF: https://help.zscaler.com/pdf/com/en/1450566.pdf

You can configure your organization to use a Zscaler Client Connector IP range beyond the default range of 100.64.0.0/16 for your Zscaler Private Access (ZPA) applications. Enter a range between 100.64.0.0/16–100.127.0.0./16 in the** Zscaler Client Connector Synthetic IP Range** field.
If your LAN network operates on the same synthetic IP range that Zscaler Client Connector uses for ZPA, enable **Drop Non-Zscaler Packets in Synthetic IP Range** to have Zscaler Client Connector block non-Zscaler packets destined for the synthetic IP range.
This option is disabled by default. When disabled, non-Zscaler packets are bypassed.
![Client Connector Synthetic IP Range](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-synthetic-ip-range/updated%20article%20mananging%20the%20Zscaler%20Synthetic%20IP%20Range.png)