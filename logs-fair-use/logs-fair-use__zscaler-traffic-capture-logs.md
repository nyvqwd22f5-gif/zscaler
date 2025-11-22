# Zscaler Traffic Capture Logs
Source: https://help.zscaler.com/logs-fair-use/zscaler-traffic-capture-logs
PDF: https://help.zscaler.com/pdf/com/en/1463506.pdf

By accessing the Zscaler Traffic Capture service, you provide Zscaler the right to create PCAP files based on traffic and optionally decrypted content processed by Zscaler Internet Access (ZIA).
PCAP files can be created in multiple ways:
- Event-based capture: Available for supported actions in ZIA policies when a violation is matched.
- Capture-control: Available for Internet Access traffic based on your specific criteria.
A PCAP file contains captured network packet data, including headers and payload, associated with a specific policy criteria match, up to and including the specific connection depth that is created from a matching policy. You can limit the amount of data captured per matched policy and limit the frequency of capture (e.g., sampling 1 out of 10 or 100 transactions).
PCAP files are delivered directly to an external storage location provided by you. In order to ensure continuous delivery of the PCAP files, Zscaler retains the files in Streaming SIMD Extensions (SSE) memory for a limited period of time. Zscaler does not write PCAP files to disk.