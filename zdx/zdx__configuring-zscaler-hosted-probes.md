# Configuring Zscaler Hosted Probes
Source: https://help.zscaler.com/zdx/configuring-zscaler-hosted-probes
PDF: https://help.zscaler.com/pdf/com/en/1505996.pdf

Zscaler Hosted Probes operate from within the Zscaler cloud infrastructure as a multitenant service. The service allows you to logically group Web and Cloud Path probes into independent collections to set up your own tests for monitoring performance. As an extension to ZDX probes for predefined and custom applications, Zscaler Hosted probes monitor the performance of a specific service or application directly from a Zscaler data center to an endpoint destination. To learn about hosted probe metrics, see [Understanding Hosted Monitoring](/zdx/understanding-zscaler-hosted-monitoring).
Prerequisites
Before configuring Zscaler Hosted probes, ensure:
-
Your ZDX subscription level supports Hosted Monitoring. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
Zscaler Hosted probes and companion probes count towards your Hosted Monitoring probes.
- Your ZDX role has the proper permission level. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Creating a Collection
Consolidate your probes by creating a Collection:
- Go to **Configuration **> **Zscaler Hosted Probes**.
- In the **Collections** pane, click **Add**.
- Enter a collection name. Accepted characters are A–Z, 0–9, underscore (_), and space ( ).
-
Click the **Confirm **icon.
[See image.](#img_collection_name)
Adding a Zscaler Hosted Probe
After creating your collection, add a probe to the collection:
- Go to **Configuration **> **Zscaler Hosted Probes**. If you have more than one collection, select the collection to which you're adding a probe.
- Click **Add Probe**.
- In the **Select a Probe Type** tab, select a Web or Cloud Path probe configuration, and then click **Next**:
- [Configuring a Web probe.](#select-web-probe-type)
- [Configuring a Cloud Path probe.](#select-cp-probe-type)
To learn more about managing your active probes, see [Managing a Zscaler Hosted Probes](/zdx/managing-zscaler-hosted-probes).
[]Web probe configuration consists of the following steps:
- [a. Web Probe](#config-web)
- [b. Additional Options](#config-web-add-opt)
- [c. (Optional) Companion Probe](#config-web-companion)
- [d. (Optional) Add Alerts](#config-web-alert)
- [e. Review](#config-web-review)
![Configure a Web probe](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/zdx-zprobe-selectprobetype-web.png)
[]
- **Probe Name**: Enter a probe name. The maximum length is 64 characters. Accepted characters are alphanumeric and a limited range of symbols, such as underscore (_), hyphen (-), space ( ), forward slash (/), period (.), pipe symbol (|), and parentheses ().
- **Status**: Select **Enable **or **Disable**. **Enable** is selected by default.
- **Destination URL or IP address (IPv4 or IPv6)**: Enter the web destination (HTTP or HTTPS URL) or an IP address.
- **Request Header**: Enter the HTTP request header name and value to pass as part of the probe.
- **HTTP Response Status Code**: By default, **Informational responses (100–199)** and **Successful responses (200–299)** are selected.
- **Timeout (seconds)**: The default timeout is set to `60` seconds.
- **Run Frequency (minutes)**: Enter the number of minutes that indicates how frequently your probe should run. The default frequency can vary, based on your subscription plan. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- **Follow Redirect**: Select **Enable** or **Disable** to follow redirect URLs.
- **Maximum Redirects**: Enter the number of times the probe attempts to follow the HTTP redirect before it is considered failed. The default is `5` redirects. If **Follow Redirect** is disabled, **Maximum Redirects **is also disabled.
- **Zscaler Hosted Locations**: From the drop-down menu, select the Zscaler data centers from where the probe is running.
[See image.](#img_config-web)
Click **Next**.
[]
- **Default HTTP Version**: Select the version of HTTP that is used.
- **Override DNS**: Select **Enable** to alter DNS settings. **Disable** is the default setting.
- **Override**: If **Override DNS** is set to **Enable**, you can select to override the **DNS Server** or **DNS Resolution**.
- **DNS Server**: If **Override DNS** is set to **Enable**, you can enter a DNS Server.
- **Cache DNS Results**: **Enable** to cache the DNS results. **Disable** is the default setting.
[See image.](#img_config-web-add-opt)
Click **Next**.
[]Pair the Web probe with a Cloud Path probe. Companion probe supports Cloud Path probe configuration by entering the following fields:
- **Companion Probe Type**: Select **Cloud Path Probe**.
- **Status**: **Enable **the companion probe for use. **Enable** is selected by default.
- **Protocol**: Select the protocol from the drop-down menu (e.g., ICMP, TCP). The default is TCP.
- **Hop Count**: Enter the maximum number of Cloud Path hops allowed before reaching the destination. If the hop count exceeds this setting, the probe run has failed. The default setting is `30` hops, the maximum setting is `64`, and the minimum setting is `10`.
- **Packet Count**: Enter the number of probe packets to send per hop discovery that have the same Time to Live (TTL) value. The default setting is `3` packets, the maximum setting is `11` packets, and the minimum setting is `1` packet.
- **Interval (ms)**: Enter the time interval between probe packets with the same TTL. Probe packets of incremental TTL are paced evenly within this time interval. The number of iterations or cycles is defined by the configured **Packet Count**. The default is `1000`, the maximum is `10000`, and the minimum is `1000`.
- **Timeout (ms)**: Enter the time to wait for a response to a probe packet before considering loss. The default is `500`, the maximum is `2000`, and the minimum is `500`.
[See image.](#img_config-web-comp)
Click **Next**.
When the Web probe resolves to an IP address, then the Cloud Path probe runs to the same IP address.
[]
- Click **Add**.
- Click **Create New Template** to add a new alert template or select an existing alert with predefined criteria. Each existing template is noted with a color for High, Medium, or Low alert severity. Alert templates are useful when reusing settings for alert rules. To learn more about alert templates and alert rules, see [About Templates](/zdx/about-templates) and [About Rules](/zdx/about-rules).
- Click **Next**.
![Configure an alert with a template](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/zdx-zprobe-add-alerts.png)
[]
- Click **Add**.
- Click **Create New Template** to add a new alert template or select an existing alert with predefined criteria. Each existing template is noted with a color for High, Medium, or Low alert severity. Alert templates are useful when reusing settings for alert rules. To learn more about alert templates and alert rules, see [About Templates](/zdx/about-templates) and [About Rules](/zdx/about-rules).
- Click **Next**.
![Configure an alert with a template](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/zdx-zprobe-add-alerts.png)
[]
On the **Review **tab, confirm your configuration, and click **Submit**. The probe is added to your collection.
[]
On the **Review **tab, confirm your configuration, and click **Submit**. The probe is added to your collection.
[]Cloud Path probe configuration consists of the following steps:
- [a. Cloud Path Probe](#config-cloud)
- [b. (Optional) Add Alerts](#config-cloud-alert)
- [c. Review](#config-cloud-review)
![Configure a Cloud Path probe](/downloads/tech-pubs-drafts/zdx-draft-articles/doc-58562-doc-additional-advanced-cloud-path-ui-work-configuring-zscaler-hosted-probes/zdx-zprobe-selectprobetype-cloud_0.png)
[]
- **Probe Name**: Enter a probe name. The maximum length is 64 characters. Accepted characters are alphanumeric and a limited range of symbols, such as underscore (_), hyphen (-), space ( ), forward slash (/), period (.), pipe symbol (|), and parentheses ().
- **Status**: Select **Enable **or **Disable**. **Enable** is selected by default.
- **Protocol**: Select the protocol from the drop-down menu (e.g., ICMP, TCP). The default is TCP.
- **End-to-end Metrics Probing Type**: Select the method for assessing end-to-end network performance metrics, such as latency, jitter, and packet loss. The available options depend on the selected protocol:
- **For TCP Protocol:**
- **None (Default)**: No additional probing is performed.
- **Prefer SACK**: Uses TCP Selective Acknowledgment (SACK) to measure retransmission efficiency, ideal for lossy or high-latency networks.
- **Force SACK**: Forces SACK probing, even if the destination does not explicitly advertise support.
- **Force SYN**: Sends SYN packets for lightweight, connectionless probing.
- **For ICMP Protocol:**
- **None (Default)**: No additional probing is performed.
- **ICMP**: Measures network performance using Internet Control Message Protocol (ICMP) probes.
- **Probing Type (TCP Only)**: Specify the method for running traceroutes when TCP is selected. The default setting is **SYN**.
- **SYN**: Sends SYN packets to perform path discovery.
- **SACK**: Uses TCP Selective Acknowledgment (SACK) for connection-based path discovery and network diagnostics.
- **Capture PMTU**: Enable or disable Path Maximum Transmission Unit (PMTU) discovery to detect packet size-related issues along the network path.
- **Enabled**: Automatically detects the MTU size along the network path.
- **Disabled**: Disables automatic MTU detection.
- **DSCP Configuration**: Select the Differentiated Services Code Point (DSCP) value to specify a priority for packets sent during probing.
- **Best Effort (DSCP 0)**: Default traffic prioritization.
- **CS1–CS7**: Levels indicating progressively higher priority.
- **AF11–AF43**: Assured forwarding classifications to manage packet drop precedence.
- **EF PHB (DSCP 46)**: Best for expedited forwarding and high-priority traffic management.
- **Voice Admit (DSCP 44)**: Specialized configuration for voice traffic prioritization.
- **Run Frequency (minutes)**: Enter the number of minutes that indicate how frequently your probe should run. The default frequency can vary, based on your subscription plan. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- **Hop Count**: Enter the maximum number of Cloud Path hops allowed before reaching the destination. If the hop count exceeds this setting, the probe run has failed. The default setting is `30` hops, the maximum setting is `64`, and the minimum setting is `10`.
- **Packet Count**: Enter the number of probe packets to send per hop discovery that have the same Time to Live (TTL) value. The default setting is `3` packets, the maximum setting is `11` packets, and the minimum setting is `1` packet.
- **Interval (ms)**: Enter the time interval between probe packets with the same TTL. Probe packets of incremental TTL are paced evenly within this time interval. The number of iterations or cycles is defined by the configured **Packet Count**. The default is `1000`, the maximum is `10000`, and the minimum is `1000`.
- **Timeout (ms)**: Enter the time to wait for a response to a probe packet before considering loss. The default is `500`, the maximum is `2000`, and the minimum is `500`.
- **Host**: Enter the host IP address or fully qualified domain name for the host (i.e., the IPv4 IP address, as IPv6 is not supported).
- **Zscaler Hosted Locations**: From the drop-down menu, select the Zscaler data centers from where the probe is run.
[See image.](#img_config-cloud-add)
Click **Next**.
[]![Add a collection](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/zdx-zprobe-config-add-collection-name.png)
[]
![Zscaler Hosted additional parameters](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/zdx-zprobe-webprobe-configuration-3.png)
[]
![Configure Additional Options](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/zdx-zprobe-web-add-opt_1.png)
[]
![Configure a Companion probe for the Web probe](/downloads/zdx/configuration/probes/configuring-zscaler-hosted-probes/zdx-zprobe-web-comp.png)
[]
![Configure Cloud Path probe parameters](/downloads/tech-pubs-drafts/zdx-draft-articles/doc-58562-doc-additional-advanced-cloud-path-ui-work-configuring-zscaler-hosted-probes/zdx-zprobe-cloud-configuration-UI.png)