---
page_type: sample
languages:
- CLI Cosmsodb 
products:
- azure-cosmosdb 
description: "This sample demonstrates how to enable cosmosdb diagnostics setting by code when you want to have the log   "

---
#Enable Diagnostics setting by code 

## About this sample

> This sample demostrate how to enable diagnostics setting by code for cosmosdb 


### Overview

how to enable diagnostics setting in cosmosdb though the portal is easy , but how to do this by code with no portal access , this is the purpose of this article 


## How to run this sample

Create using Azure CLI
Use the az monitor diagnostic-settings create command to create a diagnostic setting with Azure CLI. See the documentation for this command for descriptions of its parameters.


Following is an example CLI command to create a diagnostic setting using all three destinations.

Azure CLI

```Shell
az monitor diagnostic-settings create  \
--name Cosmosdb-Diagnostics \
--resource /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myresourcegroup/providers/Microsoft.DocumentDB/databaseAccounts/ZZZZ \
--logs    '[{"category": "DataPlaneRequests","enabled": true},{"category": "ControlPlaneRequests","enabled": true},{"category": "QueryRuntimeStatistics","enabled": true},{"category": "MongoRequests","enabled": false},{"category": "PartitionKeyStatistics","enabled": true},{"category": "PartitionKeyRUConsumption","enabled": true},{"category": "CassandraRequests","enabled": false},{"category": "GremlinRequests","enabled": false}]' \
--metrics '[{"category": "Requests","enabled": true}]' \
--workspace /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourcegroups/myresourcegroup/providers/microsoft.operationalinsights/workspaces/MYlog 
--storage-account /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myresourcegroup/providers/Microsoft.Storage/storageAccounts/mystorageaccount \
--event-hub-rule /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myresourcegroup/providers/Microsoft.EventHub/namespaces/myeventhub/authorizationrules/RootManageSharedAccessKey

...

You can enable or not each category by changing false to true 
{"category": "DataPlaneRequests","enabled": true}

in this sample we enable the 3 output 
  Storage 
  Event hub 
  and log analytics 





