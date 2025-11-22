# About Network Performance
Source: https://help.zscaler.com/unified/about-network-performance
PDF: https://help.zscaler.com/pdf/com/en/1495921.pdf

You can use Zscaler Client Connector to collect traceroute information on the connection between devices and the Zscaler cloud, and store the results to check or troubleshoot network performance.
To collect traceroute information:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > Network Performance**.
- In the **Network Performance** tab, configure the following:
- Under **Collect Route Information Every**:
- To enable traceroute:
- Enter any value from **10 **to **1440** minutes. Zscaler Client Connector collects traceroute information for the number of minutes specified.
- To disable traceroute:
- Enter the value **0**. Zscaler Client Connector will not collect traceroute information.
- For** Collect Route Information on Network Change**, enable to allow Zscaler Client Connector to collect traceroute information when the device changes network states, e.g., moving from WiFi to cellular.
- For **Collect Route Information on Reported Issues or Exported Logs**, enable to allow Zscaler Client Connector to collect traceroute information when a user reports an issue or exports logs.
When Zscaler Client Connector collects the traceroute information, the information is stored locally in a log file directory. When a user reports an issue or exports logs, these traceroute log files are included.