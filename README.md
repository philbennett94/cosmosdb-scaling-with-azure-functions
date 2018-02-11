# cosmosdb-scaling-with-azure-functions
Example of how to use Azure Functions to scale a Cosmos DB collection.

- Tutorial: `Scaling_On_429_AZFX.pdf`
- Function Code: `CosmosScaling.cs`

**Requirements**

You will need an Azure account from which you can provision an instance of Cosmos DB (SQL API preffered), and an Azure Function App.

**What does it do?**

*NOTICE: The guide assumes the user has a basic understanding of Microsoft Azure and Visual Studio* 
This guide will walk you through creating an Azure function that scales up throughput on a Cosmos DB collection when a throttling (429 error) alert is fired. To achieve this functionality, we will (1) write an azure function to scale throughput on a collection, (2) publish the function to Azure, and (3) connect the function to a CosmosDB account alert using an http webhook. Some things to consider before implementing this solution: The solution only scales up, but can be used to scale down if you supply a negative value for the CosmosDB_RUIncrement settings attribute. It is suggested to implement a limit on scaling to keep your bill manageable. Alerts are set at the account level meaning that this function will be triggered any time a resource under the account, for which the alert was set, is throttled.
