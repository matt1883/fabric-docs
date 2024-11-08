---
title: Explore Microsoft sources in Fabric Real-Time hub
description: This article shows how to explore Microsoft sources in Fabric Real-Time hub. It provides details on the Microsoft sources page in the Real-Time hub user interface.
author: mystina
ms.author: majia
ms.topic: how-to
ms.custom:
  - build-2024
ms.date: 09/04/2024
---

# Explore Microsoft sources in Fabric Real-Time hub (preview)

When you navigate to Real-Time hub in Fabric, you see the following three tabs in the user interface (UI). This article covers the **Microsoft sources** page.

[!INCLUDE [preview-note](./includes/preview-note.md)]

| Tab | Description |
| --- | ----------- |
| Data streams | You see all data streams that are actively running in Fabric that you have access to. The list includes streams from Fabric eventstreams and KQL tables that you have access to. | 
| Microsoft sources | You see all Microsoft sources that you have access to and connect to Fabric. The current supported Microsoft sources are: <ul><li>Azure Event Hubs</li><li>Azure IoT Hub</li><li>Azure SQL DB Change Data Capture (CDC)</li><li>Azure Cosmos DB CDC</li><li>PostgreSQL DB CDC</li><li>MySQL Database CDC</li><li>Azure SQL Managed Instance Change Data Capture (CDC)</li></ul> |
| Fabric events | You can monitor and react to the following events: <ul><li>Fabric Workspace Item events</li><li>Azure Blob Storage events</li></ul><p>These events can be used to trigger other actions or workflows, such as invoking a data pipeline or sending a notification via email. You can also send these events to other destinations via eventstreams.</p> |

## Microsoft sources page

:::image type="content" source="./media/explore-data-streams/real-time-hub-microsoft-sources-menu.png" alt-text="Screenshot that shows the Microsoft sources page of the Real-Time hub.":::

### Columns

| Column | Description |
| ------ | ----------- |
| Name | Name of the Microsoft resource. |
| Source | Type of the source. For example: Azure Event Hubs Namespace. |
| Subscription | Name of the Azure subscription that contains the Azure resource. |
| Resource group | Name of the Azure resource group that has the Azure resource. |
| Region | Region name of Azure resource. |

:::image type="content" source="./media/explore-data-streams/real-time-hub-microsoft-sources-columns.png" alt-text="Screenshot that shows the Microsoft sources page of the Real-Time hub with columns highlighted.":::

### Filters

The following filters are available at the top for you to narrow down easily to the desired Microsoft resource:

| Filter | Description |
| ------ | ----------- |
| Source | You can filter on the desired type of Microsoft source. |
| Subscription |  You can filter on the desired Azure subscription name. |
| Resource group | You can filter on the desired Azure resource group name. |
| Region | You can filter on the desired region name. |

:::image type="content" source="./media/explore-data-streams/real-time-hub-microsoft-sources-filters.png" alt-text="Screenshot that shows the Microsoft sources page of the Real-Time hub with filters highlighted.":::

### Search

You can also search your Microsoft resource using the search bar by typing in the name of the source.

:::image type="content" source="./media/explore-data-streams/real-time-hub-microsoft-sources-search.png" alt-text="Screenshot that shows the search box on the Real-Time hub Microsoft sources page." lightbox="./media/explore-data-streams/real-time-hub-microsoft-sources-search.png":::

### Actions

Here are the actions available on resources in the **Microsoft sources** page. When you move the mouse over a resource, you see a connect button and an ellipsis (...). When you select the ellipsis (...) button, you see the connect button here too.

| Action | Description |
| ------ | ----------- |
| Connect | Connect Fabric to your Microsoft resource. |

:::image type="content" source="./media/explore-data-streams/real-time-hub-microsoft-sources-actions.png" alt-text="Screenshot that shows the actions available for resources on the Real-Time hub Microsoft sources page." lightbox="./media/explore-data-streams/real-time-hub-microsoft-sources-actions.png":::

For more information, see [Microsoft sources](supported-sources.md#microsoft-sources).

## Related content

- [Explore Azure blob storage events](get-azure-blob-storage-events.md)
- [Explore Fabric workspace item events](create-streams-fabric-workspace-item-events.md)
