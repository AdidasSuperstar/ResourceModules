# VPN Gateways Connections `[Microsoft.Network/vpnGateways/connections]`

This module deploys VPN Gateways Connections.

## Navigation

- [Resource Types](#Resource-Types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Network/vpnGateways/vpnConnections` | [2021-05-01](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Network/2021-05-01/vpnGateways/vpnConnections) |

## Parameters

**Required parameters**
| Parameter Name | Type | Description |
| :-- | :-- | :-- |
| `name` | string | The name of the VPN connection. |
| `vpnGatewayName` | string | The name of the VPN gateway this VPN connection is associated with. |

**Optional parameters**
| Parameter Name | Type | Default Value | Allowed Values | Description |
| :-- | :-- | :-- | :-- | :-- |
| `connectionBandwidth` | int | `10` |  | Expected bandwidth in MBPS. |
| `enableBgp` | bool | `False` |  | Enable BGP flag. |
| `enableDefaultTelemetry` | bool | `True` |  | Enable telemetry via the Customer Usage Attribution ID (GUID). |
| `enableInternetSecurity` | bool | `False` |  | Enable internet security. |
| `enableRateLimiting` | bool | `False` |  | Enable rate limiting. |
| `ipsecPolicies` | array | `[]` |  | The IPSec policies to be considered by this connection. |
| `remoteVpnSiteResourceId` | string | `''` |  | Reference to a VPN site to link to |
| `routingConfiguration` | object | `{object}` |  | Routing configuration indicating the associated and propagated route tables for this connection. |
| `routingWeight` | int | `0` |  | Routing weight for VPN connection. |
| `sharedKey` | string | `''` |  | SharedKey for the VPN connection. |
| `trafficSelectorPolicies` | array | `[]` |  | The traffic selector policies to be considered by this connection. |
| `useLocalAzureIpAddress` | bool | `False` |  | Use local Azure IP to initiate connection. |
| `usePolicyBasedTrafficSelectors` | bool | `False` |  | Enable policy-based traffic selectors. |
| `vpnConnectionProtocolType` | string | `'IKEv2'` | `[IKEv1, IKEv2]` | Gateway connection protocol. |
| `vpnLinkConnections` | array | `[]` |  | List of all VPN site link connections to the gateway. |


### Parameter Usage: `routingConfiguration`

```json
"routingConfiguration": {
    "associatedRouteTable": {
        "id": "/subscriptions/<<subscriptionId>>/resourceGroups/validation-rg/providers/Microsoft.Network/virtualHubs/SampleVirtualHub/hubRouteTables/defaultRouteTable"
    },
    "propagatedRouteTables": {
        "labels": [
            "default"
        ],
        "ids": [
            {
                "id": "/subscriptions/<<subscriptionId>>/resourceGroups/validation-rg/providers/Microsoft.Network/virtualHubs/SampleVirtualHub/hubRouteTables/defaultRouteTable"
            }
        ]
    },
    "vnetRoutes": {
        "staticRoutes": []
    }
}
```

## Outputs

| Output Name | Type | Description |
| :-- | :-- | :-- |
| `name` | string | The name of the VPN connection |
| `resourceGroupName` | string | The name of the resource group the VPN connection was deployed into |
| `resourceId` | string | The resource ID of the VPN connection |
