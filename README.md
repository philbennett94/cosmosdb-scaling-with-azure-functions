# cosmosdb-scaling-with-azure-functions
An example of how to use Azure Functions to scale a Cosmos DB collection.

- Tutorial: `Scaling_On_429_AZFX.pdf`
- Function Code: `CosmosScaling.cs`

**Requirements**

You will need an Azure account from which you can provision an instance of Cosmos DB (SQL API preffered), and an Azure Function App.

**What does it do?**

*NOTICE: The guide assumes the user has a basic understanding of Microsoft Azure and Visual Studio* 

This guide will walk you through creating an Azure function that scales up throughput on a Cosmos DB collection when a throttling (429 error) alert is fired. The guide will step through the following processes:

  1. Write an azure function to scale throughput on a collection.
  2. Publish the function to Azure.
  3. connect the function to a CosmosDB account alert using a webhook. 

**For your consideration** 

The solution only scales up, but can be used to scale down if you supply a negative value for the CosmosDB_RUIncrement settings attribute. It is suggested to implement a limit on scaling to keep your bill manageable. Alerts are set at the account level meaning that this function will be triggered any time a resource under the account, for which the alert was set, is throttled.
