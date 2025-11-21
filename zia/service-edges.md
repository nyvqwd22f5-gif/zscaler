# Service Edges
Source: https://help.zscaler.com/zia/service-edges

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /virtualZenClusters`

Retrieves a list of ZIA Virtual Service Edge clusters. To learn more, see [About Virtual Service Edge Clusters](/zia/about-virtual-service-edge-clusters).

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | Search for a configured Virtual Service Edge cluster |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[VirtualZenCluster] |

## `POST /virtualZenClusters`

Adds a new Virtual Service Edge cluster. To learn more, see [Adding Virtual Service Edge Clusters](/zia/adding-virtual-service-edge-clusters).

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | VirtualZenCluster | No | Information about the Virtual Service Edge cluster |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VirtualZenCluster |

## `DELETE /virtualZenClusters/{virtualZenClusterId}`

Deletes the Virtual Service Edge cluster based on the specified ID

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| virtualZenClusterId | path | integer | Yes | The Virtual Service Edge cluster ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /virtualZenClusters/{virtualZenClusterId}`

Retrieves the Virtual Service Edge cluster based on the specified ID

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| virtualZenClusterId | path | integer | Yes | The Virtual Service Edge cluster ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VirtualZenCluster |

## `PUT /virtualZenClusters/{virtualZenClusterId}`

Updates the Virtual Service Edge cluster based on the specified ID

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| virtualZenClusterId | path | integer | Yes | The Virtual Service Edge cluster ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VirtualZenCluster |

## `GET /virtualZenNodes`

Retrieves the ZIA Virtual Service Edge for an organization. To learn more, see [About Virtual Service Edges](/zia/about-virtual-service-edges).

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| search | query | string | No | Search for a configured Virtual Service Edge |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | array[VirtualZenNode] |

## `POST /virtualZenNodes`

Adds a ZIA Virtual Service Edge for an organization. To learn more, see [Adding Virtual Service Edge Instances](/zia/adding-virtual-service-edge-instances).

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| body | body | VirtualZenNode | No | Information about the Virtual Service Edge |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VirtualZenNode |

## `DELETE /virtualZenNodes/{virtualZenNodeId}`

Deletes the ZIA Virtual Service Edge for an organization based on the specified ID

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| virtualZenNodeId | path | integer | Yes | The Virtual Service Edge ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| default | Successful Operation |  |

## `GET /virtualZenNodes/{virtualZenNodeId}`

Retrieves the ZIA Virtual Service Edge for an organization based on the specified ID

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| virtualZenNodeId | path | integer | Yes | The Virtual Service Edge ID |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VirtualZenNode |

## `PUT /virtualZenNodes/{virtualZenNodeId}`

Updates the ZIA Virtual Service Edge for an organization based on the specified ID

**Tags:** Service Edges
**Consumes:** application/json
**Produces:** application/json

| Name | In | Type | Required | Description |
| ---- | --- | ---- | -------- | ----------- |
| virtualZenNodeId | path | integer | Yes | The Virtual Service Edge ID |
| body | body | VirtualZenNode | No | Information about the Virtual Service Edge |

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | VirtualZenNode |

## Models
### EntityReference
This is an immutable reference to an entity that mainly consists of an ID and name
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| extensions | object | No | Additional information about the entity |
| externalId | string | No | An external identifier used for an entity that is managed outside of ZIA. Examples include `zpaServerGroup` and `zpaAppSegments`. This field is not applicable to ZIA-managed entities. |
| id | integer (int64) | No | A unique identifier for an entity |
| name | string | No | The configured name of the entity |

### VirtualZenCluster
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| defaultGateway | string | No | The IP address of the default gateway to the internet |
| id | integer (int32) | No | System-generated Virtual Service Edge cluster ID |
| ipAddress | string | No | The Virtual Service Edge cluster IP address. In a Virtual Service Edge cluster, the cluster IP address provides fault tolerance and is used to listen for user traffic. This interface doesn't explicitly get an IP address. The cluster IP address must be in the same VLAN as the proxy and load balancer IP addresses. |
| ipSecEnabled | boolean | No | A Boolean value that specifies whether to terminate IPSec traffic from the client at selected Virtual Service Edge instances for the Virtual Service Edge cluster |
| name | string | No | Name of the Virtual Service Edge cluster |
| status | string | No | Specifies the status of the Virtual Service Edge cluster. The status is set to ENABLED by default. |
| subnetMask | string | No | The Virtual Service Edge cluster subnet mask |
| type | string | No | The Virtual Service Edge cluster type |
| virtualZenNodes | array[EntityReference] | No | The Virtual Service Edge instances you want to include in the cluster. A Virtual Service Edge cluster must contain at least two Virtual Service Edge instances. |

### VirtualZenNode
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| clusterName | string | No | Virtual Service Edge cluster name |
| defaultGateway | string | No | The IP address of the default gateway to the internet |
| deploymentMode | string | No | Specifies the deployment mode. Select either STANDALONE or CLUSTER if you have the VMware ESXi platform. Otherwise, select only STANDALONE. |
| establishSupportTunnelEnabled | boolean | No | A Boolean value that indicates whether or not a support tunnel for Zscaler Support is enabled. Enable this option to allow the service to establish a support tunnel for Zscaler Support to access the Virtual Service Edge. |
| id | integer (int32) | No | System-generated identifier for the Virtual Service Edge. Ignored for POST and PUT requests. |
| inProduction | boolean | No | Represents the Virtual Service Edge instances deployed for production purposes |
| ipAddress | string | No | The IP address to which you forward the traffic. All user and server workload traffic is forwarded to the proxy IP address of the Virtual Service Edge. If the Virtual Service Edge has to receive and service traffic from users or workloads over the internet, ensure that this IP address has access to both the internet and users. |
| ipSecEnabled | boolean | No | A Boolean value that indicates whether IPSec is enabled. Enable this option to terminate IPSec traffic from the client at the Virtual Service Edge node. |
| loadBalancerIpAddress | string | No | The IP address of the load balancer. This field is applicable only when the 'deploymentMode' field is set to CLUSTER. |
| name | string | No | The Virtual Service Edge name |
| onDemandSupportTunnelEnabled | boolean | No | A Boolean value that indicates whether or not the On-Demand Support Tunnel is enabled |
| status | string | No | Indicates the Virtual Service Edge status |
| subnetMask | string | No | The corresponding subnet mask |
| type | string | No | The Virtual Service Edge subscription type |
| vzenSkuType | string | No | The Virtual Service Edge SKU type |
| zgatewayId | integer (int32) | No | The Zscaler service gateway ID |
