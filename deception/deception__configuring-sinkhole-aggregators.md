# Configuring a Sinkhole for Aggregators
Source: https://help.zscaler.com/deception/configuring-sinkhole-aggregators
PDF: https://help.zscaler.com/pdf/com/en/1531392.pdf

When attackers connect to a decoy, they have no outbound access from that decoy to any other systems, either from your network or the internet. In some cases, you might want to allow outbound connections to a list of known servers and ports to enable functionalities, such as Active Directory (AD) user authentication in shared services, analysis of Command and Control (C2) traffic of malware, or permitting lateral movement in heavily controlled lab environments. To provide outbound traffic from decoys for legitimate reasons, you can configure a sinkhole as a single point in your network where outbound access from the decoys to only a few specified IP addresses (systems) and services (ports) is allowed.
To configure a sinkhole for an aggregator:
- Go to **Settings** > **Topology** > **Aggregators**.
- Select an aggregator for which you want to configure a sinkhole.
-
Under the **Sinkhole** column, click **Add**.
[See image.](#add-sinkhole-icon)
-
In the **Sinkhole Details** window:
- Select **Enabled**.
- From the **Network** drop-down menu, select a network where the sinkhole IP address must be configured.
- For **IP**, enter the IP address (within the network segment you have selected).
- For **Rules**, click **Add** to add an outbound rule for the sinkhole.
- Enter an IP address or CIDR list of IP addresses.
- Enter a port number.
[See image.](#config-sinkhole)
-
Click **Save**.
The sinkhole is configured. You can click **Edit** to edit the configuration.
[See image.](#sinkhole-configured)
[]![Add sinkhole button on the Aggregators page](/downloads/deception/settings/topology/aggregators/configuring-sinkhole-aggregators/zscaler-deception-add-sinkhole.png)
[]![Configure sinkhole details for an Aggregator](/downloads/deception/settings/topology/aggregators/configuring-sinkhole-aggregators/zscaler-deception-sinkhole-details.png)
[]![Sinkhole configured](/downloads/deception/product-documentation/settings/topology/aggregator-service-backend/configuring-sinkhole-aggregators/zscaler-deception-sinkhole-added.png)