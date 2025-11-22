# Creating a Zero Trust Network Decoy
Source: https://help.zscaler.com/deception/creating-zero-trust-network-decoy
PDF: https://help.zscaler.com/pdf/com/en/1531285.pdf

[Watch a video on Creating Zero Trust Network Decoys.](https://fast.wistia.net/embed/iframe/jra2iq1bd6)
Zero Trust Network decoys are decoy network assets that mimic servers, databases, and other internal applications in your network environment that are frequently targeted during scanning and lateral movement. These decoys run on a dedicated cloud environment hosted by Zscaler and are made available to an adversary using Zscaler Private Access (ZPA) via Zscaler Client Connector. You can create Zero Trust Network decoys on the production application segment in ZPA.
Prerequisites
[]Before creating a Zero Trust Network decoy, make sure that the following prerequisites are met:
- You have a provisioned ZPA tenant ID.
- Zscaler Client Connector is installed on the endpoints.
-
There are free FQDNs that are not assigned to any of the existing systems in the ZPA service. For real applications, ports must be available on the real production ZPA application segment to which you want to add a decoy. For example, if you want to add a MySQL database decoy service on a real production ZPA application segment, which is a web server with ports 80 and 443 used, then port 3306 must be available to add a decoy service.
This prerequisite is not applicable to new ZPA decoys for real applications in ZPA.
Creating a Zero Trust Network Decoy
To create a Zero Trust Network decoy:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Network Decoys** > **Zero Trust Network**.
-
Click **Add Decoys**.
[See image.](#deception-zero-trust-add-decoy-option)
- []On the **Zero Trust Network Decoy Detail** page, under the **General** tab:
- **Enabled**: Select to enable the Zero Trust Network decoy.
- Choose one of the following options:
- [Create a Zero Trust Network decoy in ZPA.](#deception-create-zpa-decoys)
- [Create a Zero Trust Network decoy of a production application in ZPA.](#deception-create-zpa-real-app)
- Click the **Services** tab to view, customize, enable, or disable the services that the network decoy will host. To learn more, see [Configuring Services for a Network Decoy](/deception/configuring-services-network-decoy).
-
Click **Submit**.
The decoy is created. The red status icon (![Red decoy deployment status icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-red-status-icon.png)
) next to the decoy indicates that the decoy is inactive.
[See image.](#zero-trust-decoy-inactive-status)
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys).
-
Go to **Deceive** > **Network Decoys** > **Zero Trust Network**.
The decoy is deployed and active. The status icon turns green (![Green decoy deployment status icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-green-status-icon.png)
).
[See image.](#zero-trust-decoy-active-status)
-
[]**Personality**: Select a decoy based on the network segment from the drop-down menu.
When you select a decoy personality, the FQDN field is automatically configured to reflect the selected personality.
- **FQDN**: This field is automatically populated. Click the **Autogenerate** icon (![Autogenerate icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-auto-generate-icon.png)
) to generate another FQDN suggestion, or manually enter a hostname or FQDN of your choice.
-
**Network Decoy Groups**: Select an existing decoy group from the drop-down menu, or click **Create Decoy Group** to create a new decoy group.
​[See image.](#configure-zero-trust-network-details)
- []**Real App**: Enable to add a Zero Trust Network decoy service on unused ports of a real or production ZPA application segment.
- **Personality**: Select a decoy based on the production application segment from the drop-down menu.
- **Application Segment**: Enter at least three characters to search for a ZPA production application segment. Zscaler supports only those application segments that have at least one FQDN.
- **FQDN**: Select an FQDN from the drop-down menu. All FQDNs that belong to the selected application segment are automatically populated.
-
**Network Decoy Groups**: Select an existing decoy group from the drop-down menu, or click **Create Decoy Group** to create a new decoy group.
[See image.](#deception-config-zero-trust-zpa-prod-app)
[]Creating Zero Trust Network Decoys Based on AI-Powered Recommendations
Manually analyzing Zero Trust Network decoy configuration and deciding on hostnames, services, and service configurations such as datasets and banners can be time consuming. Deception leverages AI to generate recommendations with preselected datasets, banners, services, and ports. This simplifies decoy creation and deployment, and reduces manual effort.
For AI-powered recommendations to work, you must have a minimum of 5 [application segments](/zpa/about-applications) with non-wildcard FQDNs in ZPA.
To create Zero Trust Network decoys based on AI-powered recommendations:
- [Stop the decoys](/deception/starting-and-stopping-decoys).
-
Go to **Deceive** > **Network Decoys** > **Zero Trust Network**.
[See image.](#deception-ai-zpa-add-recomm)
-
Click **AI-Powered Recommendations**.
The hostnames (FQDNs) and port configurations from the applications segments in ZPA are fetched, the information is supplied to AI, and decoy recommendations are generated.
[See image.](#deception-ai-zpa-process-recomm)
-
Verify the recommendations.
[See image.](#deception-ai-zpa-recomm-create-decoys)
-
Click **Save**.
The decoys are created. The red status icon (![Red decoy deployment status icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-red-status-icon.png)
) next to the decoys indicate that the decoy is inactive.
[See image.](#deception-ai-zpa-recomm-created-not-deployed)
- [Start the decoys](/deception/starting-and-stopping-decoys).
-
Go to **Deceive** > **Network Decoys** > **Zero Trust Network**.
The decoys are deployed and active. The status icon turns green (![Green decoy deployment status icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-green-status-icon.png)
).
[See image.](#deception-ai-zpa-recomm-created-and-deployed)
After the decoys are created, you can [test](/deception/testing-network-decoy) them to simulate an attack.
Make sure that there are no FQDN-port combinations conflicting with any of the existing application segments in ZPA.
You can select the **Deception** filter on the [Application Segments](/zpa/about-applications) page in ZPA to view the Zero Trust Network decoys.
[]![Add a Zero Trust Network ](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-zero-trust-add-decoys-option-3.png)
[]![Configure a Zero Trust Network Decoy](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-config-zero-trust-network-decoy-1.png)
[]![Configure a Zero Trust Network Decoy of a production app in ZPA](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-config-zero-trust-network-decoy-zpa-prod-app.png?1678861425)
[]![Zero Trust Network decoy created but inactive](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-zero-trust-network-decoys-inactive-4.png)
[]![Zero Trust Network decoy deployed and active](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-zero-trust-network-decoys-deployed-1.png)
[]![Add AI-powered Zero Trust Network decoys](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-ai-zpa-add-recomm-2.png)
[]![Process AI-powered recommendations](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-ai-zpa-process-recomm-1.png)
[]![View AI-powered recommendations](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-ai-zpa-recomm-provided-1.png)
[]![Zero Trust Network decoys created but inactive](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-ai-zpa-recomm-decoys-created-not-deployed-3.png)
[]![Zero Trust Network decoys deployed and active](/downloads/deception/deceive/network-decoys/creating-zero-trust-network-decoy/zscaler-deception-ai-zpa-recomm-decoys-deployed-3.png)