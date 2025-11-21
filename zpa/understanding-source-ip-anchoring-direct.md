# Understanding Source IP Anchoring Direct
Source: https://help.zscaler.com/zpa/understanding-source-ip-anchoring-direct
PDF: https://help.zscaler.com/pdf/com/en/1485671.pdf

Source IP Anchoring Direct is a set of ZPA configurations that supports [Source IP Anchoring](/zia/about-source-ip-anchoring) forwarding policies when Zscaler Internet Access (ZIA) is in [disaster recovery](/zia/about-disaster-recovery) mode. When ZIA is configured for disaster recovery, the ZPA Source IP Anchoring configurations must be changed to the Source IP Anchoring Direct configurations to ensure proper forwarding during a ZIA disaster recovery event.
To configure ZPA Source IP Anchoring client policies for Source IP Anchoring Direct, you must change or verify the following configurations for the duration of a ZIA disaster recovery event:
- [Client Forwarding Policy Configuration](#clientforwardingpolicy)
- [Access Policy Configuration](#accesspolicyconfiguration)
[]The [Client Forwarding Policy](/zpa/configuring-client-forwarding-policies) rule configured for Source IP Anchoring must be changed as follows:
- Go to **Policy** > **Client Forwarding Policy**.
- Change the client forwarding policy rules:
-
For the domain-based application rule with **Segment Groups** and **Client Types** > **Client Connector** criteria, change the **Rule Action** from **Bypass ZPA** to **Forward to ZPA**.
[See image.](#SegmentGroupsandClientConnector-ForwardtoZPA)
- For the IP address-based application rule with **Segment Groups**, change the **Rule Action** from **Only Forward Allowed Applications** to **Forward to ZPA**.
[]Some [Access Policy configurations](/zpa/configuring-access-policies) support Source IP Anchoring but do not support Source IP Anchoring Direct. The following Access Policy configurations prevent Source IP Anchoring Direct from working:
- Any Access Policy rule that blocks access to Zscaler Client Connectors. For example, Application Segment (or Segment Groups) and Client Type > Client Connector with the Block Access rule action enabled.
- Any Access Policy rule that results in the Default Rule.
If you plan to use the Source IP Anchoring Direct configurations, Zscaler recommends that you ensure there is an Access Policy that allows access to the applications from Zscaler Client Connectors. To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).
Restoring Source IP Anchoring after Source IP Anchoring Direct
When the ZIA disaster recovery event ends, revert the [Client Forwarding Policy](/zpa/configuring-client-forwarding-policies) rule and [Access Policy](/zpa/configuring-access-policies) rule configured for Source IP Anchoring Direct back to the Source IP Anchoring configuration as follows:
- [Client Forwarding Policy Configuration](#restore-sipa-cfp)
- [Access Policy Configuration](#restore-sipa-ap)
[]The Client Forwarding Policy rule configured for Source IP Anchoring Direct must be changed as follows:
- Go to **Policy** > **Client Forwarding Policy**.
- Change the client forwarding policy rules:
- For the domain-based application rule with **Segment Groups** and **Client Types** > **Client Connector** criteria, change the **Rule Action** from **Forward to ZPA** to **Bypass ZPA**.
- For the IP address-based application rule with **Segment Groups**, change the **Rule Action** from **Forward to ZPA** to **Only Forward Allowed Applications**.
[See image.](#SegmentGroupsandClientConnector-BypassZPA)
[]The Access Policy rule configured for Source IP Anchoring Direct must be changed as follows:
- Go to **Policy** > **Access Policy**.
- Change the Access Policy rules:
- For domain-based applications, ensure that you allow the Source IP Anchoring client (ZIA Service Edge client type) to access the applications.
- For IP address-based applications, configure the following rules:
- Rule 1: Select the **Block Access** rule action and add all the client types, except the **ZIA Service Edge** client type for the Source IP Anchoring application segments. This rule prevents application download on the Zscaler Client Connector.
- Rule 2: Select the **Allow Access** rule action and add only the **ZIA Service Edge** client type for the Source IP Anchoring application segments.
[![Segment Groups and Client Connector with Forward to ZPA Rule Action.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/understanding-source-ip-anchoring-direct/ClientForwardingPolicySegmentGroupsandClientConnector-ForwardtoZPA_0.png)
]
[![Segment Groups and Client Connector with Bypass ZPA Rule Action.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/understanding-source-ip-anchoring-direct/ClientForwardingPolicySegmentGroupsandClientConnector-BypassZPA.png)
]