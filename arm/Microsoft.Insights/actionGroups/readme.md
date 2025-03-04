# Action Groups `[Microsoft.Insights/actionGroups]`

This module deploys an Action Group.

## Navigation

- [Resource Types](#Resource-Types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Authorization/roleAssignments` | [2021-04-01-preview](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Authorization/roleAssignments) |
| `microsoft.insights/actionGroups` | [2019-06-01](https://docs.microsoft.com/en-us/azure/templates/microsoft.insights/2019-06-01/actionGroups) |

## Parameters

**Required parameters**
| Parameter Name | Type | Description |
| :-- | :-- | :-- |
| `groupShortName` | string | The short name of the action group. |
| `name` | string | The name of the action group. |

**Optional parameters**
| Parameter Name | Type | Default Value | Description |
| :-- | :-- | :-- | :-- |
| `armRoleReceivers` | array | `[]` | The list of ARM role receivers that are part of this action group. Roles are Azure RBAC roles and only built-in roles are supported. |
| `automationRunbookReceivers` | array | `[]` | The list of AutomationRunbook receivers that are part of this action group. |
| `azureAppPushReceivers` | array | `[]` | The list of AzureAppPush receivers that are part of this action group. |
| `azureFunctionReceivers` | array | `[]` | The list of function receivers that are part of this action group. |
| `emailReceivers` | array | `[]` | The list of email receivers that are part of this action group. |
| `enabled` | bool | `True` | Indicates whether this action group is enabled. If an action group is not enabled, then none of its receivers will receive communications. |
| `enableDefaultTelemetry` | bool | `True` | Enable telemetry via the Customer Usage Attribution ID (GUID). |
| `itsmReceivers` | array | `[]` | The list of ITSM receivers that are part of this action group. |
| `location` | string | `'global'` | Location for all resources. |
| `logicAppReceivers` | array | `[]` | The list of logic app receivers that are part of this action group. |
| `roleAssignments` | array | `[]` | Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11' |
| `smsReceivers` | array | `[]` | The list of SMS receivers that are part of this action group. |
| `tags` | object | `{object}` | Tags of the resource. |
| `voiceReceivers` | array | `[]` | The list of voice receivers that are part of this action group. |
| `webhookReceivers` | array | `[]` | The list of webhook receivers that are part of this action group. |


### Parameter Usage: receivers

See [Documentation](https://docs.microsoft.com/en-us/azure/templates/microsoft.insights/2019-06-01/actiongroups) for description of parameters usage and syntax.

Example:

```json
"emailReceivers":{
  "value":[
    {
      "name": "TestUser_-EmailAction-",
      "emailAddress": "test.user@testcompany.com",
      "useCommonAlertSchema": true
    },
    {
      "name": "TestUser2",
      "emailAddress": "test.user2@testcompany.com",
      "useCommonAlertSchema": true
    }
  ]
},
"smsReceivers":{
  "value": [
    {
      "name": "TestUser_-SMSAction-",
      "countryCode": "1",
      "phoneNumber": "2345678901"
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

### Additional notes on parameters

- Receiver name must be unique across the ActionGroup
- Email, SMS, Azure App push and Voice can be grouped in the same Action. To do so, the `name` field of the receivers must be in the `RecName_-ActionType-` format where:
  - _RecName_ is the name you want to give to the Action
  - _ActionType_ is one of the action types that can be grouped together. Possible values are:
    - EmailAction
    - SMSAction
    - AzureAppAction
    - VoiceAction
- To understand the impact of the `useCommonAlertSchema` field, see [here](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-common-schema)

## Outputs

| Output Name | Type | Description |
| :-- | :-- | :-- |
| `name` | string | The name of the action group  |
| `resourceGroupName` | string | The resource group the action group was deployed into |
| `resourceId` | string | The resource ID of the action group  |
