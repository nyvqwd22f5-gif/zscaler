# Configuring an Endpoint Credential Exposure Scan
Source: https://help.zscaler.com/itdr/configuring-endpoint-credential-exposure-scan
PDF: https://help.zscaler.com/pdf/com/en/1531686.pdf

[Watch a video on Endpoint Credential Exposure.](https://fast.wistia.net/embed/iframe/rfq1kuvn5v)
You can configure a credential exposure scan on the [endpoint agents](/itdr/about-endpoint-settings) installed in Zscaler ITDR to identify credential vulnerabilities and potential privilege escalation points.
To configure a credential exposure scan:
- Go to **ITDR **> **Manage** > **Endpoint Credential Exposure**.
-
Click **Add Configuration**.
[See image.](#add-config)
-
In the **Configuration Details** window:
- **Configuration Name**: Enter the name for the configuration.
- **Scan frequency: **Select a scan frequency (**Daily**, **Weekly**, **Monthly**, or **Quarterly**).
- **Scan Time (UTC)**: Enter a scan time.
- **Password Analysis**: Enable or disable password hashing using custom salt. This setting is enabled by default.
[See image.](#add-config-details)
- Click **Save**.
The endpoint agent is added for scanning at the scheduled frequency. You can also run an [on-demand scan](/itdr/triggering-demand-credential-exposure-scan) to scan the endpoints as necessary.
After the endpoint is scanned for credential vulnerabilities, you can view the results on the [Endpoint Credential Exposure dashboard](/itdr/about-endpoint-credential-exposure-dashboard).
[]![The Add Configuration button on the Endpoint Credential Exposure page](/downloads/itdr/configuring-endpoint-credential-exposure-scan/itdr-ece-add-configuration.png)
[]![The Configuration Details window](/downloads/itdr/configuring-endpoint-credential-exposure-scan/itdr-credential-add-config-details.png)