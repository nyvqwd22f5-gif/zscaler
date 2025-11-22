# Understanding Source IP Anchoring Direct
Source: https://help.zscaler.com/unified/understanding-source-ip-anchoring-direct
PDF: https://help.zscaler.com/pdf/com/en/1492221.pdf

Source IP Anchoring Direct is a set of configurations that supports [Source IP Anchoring](/unified/understanding-source-ip-anchoring) forwarding policies when in [disaster recovery](/unified/about-disaster-recovery-settings) mode. When configured for disaster recovery, the Source IP Anchoring configurations must be changed to the Source IP Anchoring Direct configurations to ensure proper forwarding during a disaster recovery event.
To configure Source IP Anchoring client policies for Source IP Anchoring Direct, you must change or verify the following configurations for the duration of a disaster recovery event:
- [Client Forwarding Policy Configuration](#clientforwardingpolicy)
- [Access Policy Configuration](#accesspolicyconfiguration)
[]The [Client Forwarding Policy](/unified/configuring-client-forwarding-policies) rule configured for Source IP Anchoring must be changed as follows:
- Go to the **Client Forwarding Policy** page (Infrastructure > Private Access > Client Connector Policies > Client Forwarding Policies).
- Change the client forwarding policy rules:
-
For the domain-based application rule with **Segment Groups** and **Client Types** > **Client Connector** criteria, change the **Rule Action** from **Bypass Private Applications **to **Forward to Private Applications**.
[See image.](#segment-groups-cc)
- For the IP address-based application rule with **Segment Groups**, change the **Rule Action** from **Only Forward Allowed Applications** to **Forward to Private Applications**.
[]Some [Access Policy configurations](/unified/configuring-access-policies) support Source IP Anchoring but do not support Source IP Anchoring Direct. The following Access Policy configurations prevent Source IP Anchoring Direct from working:
- Any Access Policy rule that blocks access to Zscaler Client Connectors. For example, Application Segment (or Segment Groups) and Client Type > Client Connector with the Block Access rule action enabled.
- Any Access Policy rule that results in the Default Rule.
If you plan to use the Source IP Anchoring Direct configurations, Zscaler recommends that you ensure there is an Access Policy that allows access to the applications from Zscaler Client Connectors. To learn more, see [Configuring Access Policies](/unified/configuring-access-policies).
Restoring Source IP Anchoring after Source IP Anchoring Direct
When the disaster recovery event ends, revert the [Client Forwarding Policy](/unified/configuring-client-forwarding-policies) rule and [Access Policy](/unified/configuring-access-policies) rule configured for Source IP Anchoring Direct back to the Source IP Anchoring configuration as follows:
- [Client Forwarding Policy Configuration](#restore-sipa-cfp)
- [Access Policy Configuration](#restore-sipa-ap)
[]The Client Forwarding Policy rule configured for Source IP Anchoring Direct must be changed as follows:
- Go to the **Client Forwarding Policy **page (Infrastructure > Private Access > Client Connector Policies > Client Forwarding Policies).
- Change the client forwarding policy rules:
- For the domain-based application rule with **Segment Groups** and **Client Types** > **Client Connector** criteria, change the **Rule Action** from **Forward to Private Applications **to **Bypass Private Applications**.
- For the IP address-based application rule with **Segment Groups**, change the **Rule Action** from **Forward to Private Applications **to **Only Forward Allowed Applications**.
[See image.](#forward-as-bypass)
[]The Access Policy rule configured for Source IP Anchoring Direct must be changed as follows:
- Go to the **Access Policy **page (Policies > Access Control > Private Applications > Access Policy).
- Change the Access Policy rules:
- For domain-based applications, ensure that you allow the Source IP Anchoring client to access the applications.
- For IP address-based applications, configure the following rules:
- Rule 1: Select the **Block Access** rule action and add all the client types, except the **Service Edge** client type for the Source IP Anchoring application segments. This rule prevents application download on the Zscaler Client Connector.
- Rule 2: Select the **Allow Access** rule action and add only the **Service Edge** client type for the Source IP Anchoring application segments.
[][![Segment Groups and Client Connector with Forward to ZPA Rule Action.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/understanding-source-ip-anchoring-direct/ClientForwardingPolicySegmentGroupsandClientConnector-ForwardtoZPA_0.png)
]
[][![Segment Groups and Client Connector with Bypass ZPA Rule Action.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/understanding-source-ip-anchoring-direct/ClientForwardingPolicySegmentGroupsandClientConnector-BypassZPA.png)
]