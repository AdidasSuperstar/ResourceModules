# Web/Function Apps `[Microsoft.Web/sites]`

This module deploys a web or function app.

## Navigation

- [Resource types](#Resource-types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)

## Resource types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Authorization/locks` | [2017-04-01](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Authorization/2017-04-01/locks) |
| `Microsoft.Authorization/roleAssignments` | [2021-04-01-preview](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Authorization/roleAssignments) |
| `Microsoft.Insights/diagnosticSettings` | [2021-05-01-preview](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Insights/2021-05-01-preview/diagnosticSettings) |
| `Microsoft.Network/privateEndpoints` | [2021-05-01](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Network/2021-05-01/privateEndpoints) |
| `Microsoft.Network/privateEndpoints/privateDnsZoneGroups` | [2021-05-01](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Network/2021-05-01/privateEndpoints/privateDnsZoneGroups) |
| `Microsoft.Web/sites` | [2021-03-01](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Web/2021-03-01/sites) |
| `Microsoft.Web/sites/config` | [2020-12-01](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Web/sites) |

## Parameters

**Required parameters**
| Parameter Name | Type | Allowed Values | Description |
| :-- | :-- | :-- | :-- |
| `kind` | string | `[functionapp, functionapp,linux, app]` | Type of site to deploy. |
| `name` | string |  | Name of the site. |

**Optional parameters**
| Parameter Name | Type | Default Value | Allowed Values | Description |
| :-- | :-- | :-- | :-- | :-- |
| `appInsightId` | string | `''` |  | Resource ID of the app insight to leverage for this resource. |
| `appServiceEnvironmentId` | string | `''` |  | The resource ID of the app service environment to use for this resource. |
| `appSettingsKeyValuePairs` | object | `{object}` |  | The app settings-value pairs except for AzureWebJobsStorage, AzureWebJobsDashboard, APPINSIGHTS_INSTRUMENTATIONKEY and APPLICATIONINSIGHTS_CONNECTION_STRING. |
| `authSettingV2Configuration` | object | `{object}` |  | The auth settings V2 configuration. |
| `clientAffinityEnabled` | bool | `True` |  | If client affinity is enabled. |
| `diagnosticEventHubAuthorizationRuleId` | string | `''` |  | Resource ID of the diagnostic event hub authorization rule for the Event Hubs namespace in which the event hub should be created or streamed to. |
| `diagnosticEventHubName` | string | `''` |  | Name of the diagnostic event hub within the namespace to which logs are streamed. Without this, an event hub is created for each log category. |
| `diagnosticLogCategoriesToEnable` | array | `[if(equals(parameters('kind'), 'functionapp'), createArray('FunctionAppLogs'), createArray('AppServiceHTTPLogs', 'AppServiceConsoleLogs', 'AppServiceAppLogs', 'AppServiceAuditLogs', 'AppServiceIPSecAuditLogs', 'AppServicePlatformLogs'))]` | `[AppServiceHTTPLogs, AppServiceConsoleLogs, AppServiceAppLogs, AppServiceAuditLogs, AppServiceIPSecAuditLogs, AppServicePlatformLogs, FunctionAppLogs]` | The name of logs that will be streamed. |
| `diagnosticLogsRetentionInDays` | int | `365` |  | Specifies the number of days that logs will be kept for; a value of 0 will retain data indefinitely. |
| `diagnosticMetricsToEnable` | array | `[AllMetrics]` | `[AllMetrics]` | The name of metrics that will be streamed. |
| `diagnosticSettingsName` | string | `[format('{0}-diagnosticSettings', parameters('name'))]` |  | The name of the diagnostic setting, if deployed. |
| `diagnosticStorageAccountId` | string | `''` |  | Resource ID of the diagnostic storage account. |
| `diagnosticWorkspaceId` | string | `''` |  | Resource ID of log analytics workspace. |
| `enableDefaultTelemetry` | bool | `True` |  | Enable telemetry via the Customer Usage Attribution ID (GUID). |
| `httpsOnly` | bool | `True` |  | Configures a site to accept only HTTPS requests. Issues redirect for HTTP requests. |
| `location` | string | `[resourceGroup().location]` |  | Location for all Resources. |
| `lock` | string | `'NotSpecified'` | `[CanNotDelete, NotSpecified, ReadOnly]` | Specify the type of lock. |
| `privateEndpoints` | array | `[]` |  | Configuration details for private endpoints. |
| `roleAssignments` | array | `[]` |  | Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'. |
| `serverFarmResourceId` | string | `''` |  | The resource ID of the app service plan to use for the site. |
| `setAzureWebJobsDashboard` | bool | `[if(contains(parameters('kind'), 'functionapp'), true(), false())]` |  | For function apps. If true the app settings "AzureWebJobsDashboard" will be set. If false not. In case you use Application Insights it can make sense to not set it for performance reasons. |
| `siteConfig` | object | `{object}` |  | The site config object. |
| `storageAccountId` | string | `''` |  | Required if app of kind functionapp. Resource ID of the storage account to manage triggers and logging function executions. |
| `storageAccountRequired` | bool | `False` |  | Checks if Customer provided storage account is required. |
| `systemAssignedIdentity` | bool | `False` |  | Enables system assigned managed identity on the resource. |
| `tags` | object | `{object}` |  | Tags of the resource. |
| `userAssignedIdentities` | object | `{object}` |  | The ID(s) to assign to the resource. |
| `virtualNetworkSubnetId` | string | `''` |  | Azure Resource Manager ID of the Virtual network and subnet to be joined by Regional VNET Integration. This must be of the form /subscriptions/{subscriptionName}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/virtualNetworks/{vnetName}/subnets/{subnetName}. |


### Parameter Usage: `appSettingsKeyValuePairs`

AzureWebJobsStorage, AzureWebJobsDashboard, APPINSIGHTS_INSTRUMENTATIONKEY and APPLICATIONINSIGHTS_CONNECTION_STRING are set separately (check parameters storageAccountId, setAzureWebJobsDashboard, appInsightId).
For all other app settings key-value pairs use this object.

```json
"appSettingsKeyValuePairs": {
    "value": [
        {
            "name": "key1",
            "value": "val1"
        },
        {
            "name": "key2",
            "value": "val2"
        }
    ]
}
```

### Parameter Usage: `authSettingV2Configuration`

The auth settings V2 configuration.

```json
"siteConfig": {
    "value": [
        // Check out https://docs.microsoft.com/en-us/azure/templates/microsoft.web/sites/config-authsettingsv2?tabs=bicep#siteauthsettingsv2properties for possible properties
    ]
}
```

### Parameter Usage: `siteConfig`

The site config.

```json
"siteConfig": {
    "value": [
        // Check out https://docs.microsoft.com/en-us/azure/templates/Microsoft.Web/sites?tabs=bicep#siteconfig for possible properties
    ]
}
```

### Parameter Usage: `privateEndpoints`

To use Private Endpoint the following dependencies must be deployed:

- Destination subnet must be created with the following configuration option - `"privateEndpointNetworkPolicies": "Disabled"`.  Setting this option acknowledges that NSG rules are not applied to Private Endpoints (this capability is coming soon). A full example is available in the Virtual Network Module.
- Although not strictly required, it is highly recommended to first create a private DNS Zone to host Private Endpoint DNS records. See [Azure Private Endpoint DNS configuration](https://docs.microsoft.com/en-us/azure/private-link/private-endpoint-dns) for more information.

```json
"privateEndpoints": {
    "value": [
        // Example showing all available fields
        {
            "name": "sxx-az-pe", // Optional: Name will be automatically generated if one is not provided here
            "subnetResourceId": "/subscriptions/<<subscriptionId>>/resourceGroups/validation-rg/providers/Microsoft.Network/virtualNetworks/sxx-az-vnet-x-001/subnets/sxx-az-subnet-x-001",
            "service": "<<serviceName>>" // e.g. vault, registry, file, blob, queue, table etc.
            "privateDnsZoneResourceIds": [ // Optional: No DNS record will be created if a private DNS zone Resource ID is not specified
                "/subscriptions/<<subscriptionId>>/resourceGroups/validation-rg/providers/Microsoft.Network/privateDnsZones/privatelink.blob.core.windows.net"
            ],
            "customDnsConfigs": [ // Optional
                {
                    "fqdn": "customname.test.local",
                    "ipAddresses": [
                        "10.10.10.10"
                    ]
                }
            ]
        },
        // Example showing only mandatory fields
        {
            "subnetResourceId": "/subscriptions/<<subscriptionId>>/resourceGroups/validation-rg/providers/Microsoft.Network/virtualNetworks/sxx-az-vnet-x-001/subnets/sxx-az-subnet-x-001",
            "service": "<<serviceName>>" // e.g. vault, registry, file, blob, queue, table etc.
        }
    ]
}
```

### Parameter Usage: `roleAssignments`

Create a role assignment for the given resource. If you want to assign a service principal / managed identity that is created in the same deployment, make sure to also specify the `'principalType'` parameter and set it to `'ServicePrincipal'`. This will ensure the role assignment waits for the principal's propagation in Azure.

```json
"roleAssignments": {
    "value": [
        {
            "roleDefinitionIdOrName": "Reader",
            "description": "Reader Role Assignment",
            "principalIds": [
                "12345678-1234-1234-1234-123456789012", // object 1
                "78945612-1234-1234-1234-123456789012" // object 2
            ]
        },
        {
            "roleDefinitionIdOrName": "/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11",
            "principalIds": [
                "12345678-1234-1234-1234-123456789012" // object 1
            ],
            "principalType": "ServicePrincipal"
        }
    ]
}
```

### Parameter Usage: `tags`

Tag names and tag values can be provided as needed. A tag can be left without a value.

```json
"tags": {
    "value": {
        "Environment": "Non-Prod",
        "Contact": "test.user@testcompany.com",
        "PurchaseOrder": "1234",
        "CostCenter": "7890",
        "ServiceName": "DeploymentValidation",
        "Role": "DeploymentValidation"
    }
}
```

### Parameter Usage: `userAssignedIdentities`

You can specify multiple user assigned identities to a resource by providing additional resource IDs using the following format:

```json
"userAssignedIdentities": {
    "value": {
        "/subscriptions/12345678-1234-1234-1234-123456789012/resourcegroups/validation-rg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/adp-sxx-az-msi-x-001": {},
        "/subscriptions/12345678-1234-1234-1234-123456789012/resourcegroups/validation-rg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/adp-sxx-az-msi-x-002": {}
    }
},
```

## Outputs

| Output Name | Type | Description |
| :-- | :-- | :-- |
| `name` | string | The name of the site. |
| `resourceGroupName` | string | The resource group the site was deployed into. |
| `resourceId` | string | The resource ID of the site. |
| `systemAssignedPrincipalId` | string | The principal ID of the system assigned identity. |
