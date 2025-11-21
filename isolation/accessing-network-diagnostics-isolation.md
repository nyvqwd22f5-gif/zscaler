# Accessing Network Diagnostics in Isolation
Source: https://help.zscaler.com/isolation/accessing-network-diagnostics-isolation
PDF: https://help.zscaler.com/pdf/com/en/1373976.pdf

If you experience latency issues during your isolation session, you can check the link latency information for the isolated browser in the Isolation Network Diagnostics window.
To view the Network Diagnostics for your active isolated session:
- Go to the **Isolation Browser Menu**.
- Click **Network Diagnostics**. You can also bring up this window by using the keyboard shortcut CTRL+Shift+D.
[See image.](#isolation-menu)
The Network Diagnostics window will appear. This window has live, real-time statistics of network latency for WebSocket and HTTP connectivity. The percentile statistics indicate the distribution of latency across pings. You can view the logs of each connectivity type made by the following statistics:
- **Last Value**: The last ping latency.
- **Number of Pings**: The total pings sent.
- **Maximum**: The worst value logged.
- **99%**: When 99% of pings have below indicated value.
- **75%**: When 75% of pings have below indicated value.
- **Mean**: When 50% of pings have below indicated value.
- **Standard Deviation**: The variance across pings.
[See image.](#Network-Diagnostics-Window)
If you notice latency statistics that are unusually high or inconsistent, you can save the information captured in the Network Diagnostics window to share as a report with Zscaler Support so they can further diagnose the issue.
To save the Network Diagnostics information as a report:
- Open the **Network Diagnostics** window
- Click **Save Report**. By default, the report is saved to your device as a text file.
You can then send an email to Zscaler Support with the Network Diagnostics report attached and note the latency issues you've experienced.
[]![Cloud Browser isolation menu](/downloads/zscaler-tech-pubs-style-guide/draft-articles/accessing-network-diagnostics-isolation/Isolation-Menu_admin-at-zscaler.png)
[]![Networks Diagnostics Window](/downloads/zia/cloud-browser-isolation/accessing-network-diagnostics-isolation/Network-Diagnostics-Window2.png)