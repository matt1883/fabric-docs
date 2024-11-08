---
title: Explore data streams in Fabric Real-Time hub
description: This article shows how to explore data streams in Fabric Real-Time hub. It provides details on the All data streams page in the Real-Time hub user interface.
author: mystina
ms.author: majia
ms.topic: how-to
ms.custom:
  - build-2024
ms.date: 09/03/2024
---

# Explore streams in Fabric Real-Time hub (preview)

When you navigate to Real-Time hub in Fabric, you can view all the data streams that are present in Fabric. There are four pages in the hub.

[!INCLUDE [preview-note](./includes/preview-note.md)]

## Expore streams using menus

| Menu | Description |
| --- | ----------- |
| [All data streams](explore-all-data-streams.md) | You see all data streams that you can access that are actively running in Fabric. The list includes streams from Fabric eventstreams and KQL tables that you can access. |
| My streams | The data streams that are actively running in Fabric that you can access. The list includes streams from Fabric eventstreams and KQL tables that you can access. |
| [Microsoft sources](explore-microsoft-sources.md) | All Microsoft sources that you have access to and connect to Fabric. The current supported Microsoft sources are: <ul><li>Azure Event Hubs</li><li>Azure IoT Hub</li><li>Azure SQL DB Change Data Capture (CDC)</li><li>Azure Cosmos DB CDC</li><li>PostgreSQL DB CDC</li><li>MySQL Database CDC</li><li>Azure SQL Managed Instance DB CDC</li></ul> |
| [Fabric events](explore-fabric-events.md) | You can monitor and react to the following events: <ul><li>Azure Blob Storage events</li><li>Fabric Workspace Item events</li></ul><p>These events can be used to trigger other actions or workflows, such as invoking a data pipeline or sending a notification via email. You can also send these events to other destinations via eventstreams.</p> |

:::image type="content" source="./media/explore-data-streams/real-time-hub.png" alt-text="Screenshot that shows the Real-Time hub." lightbox="./media/explore-data-streams/real-time-hub.png":::

## Related content

- [View data stream details](view-data-stream-details.md)
- [Preview data streams](preview-data-streams.md)
- [Endorse data streams](endorse-data-streams.md)
- [Explore fabric events](explore-fabric-events.md)
