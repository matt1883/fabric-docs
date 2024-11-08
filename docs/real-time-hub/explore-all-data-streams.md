---
title: Explore All data streams in Fabric Real-Time hub
description: This article shows how to explore All data streams in Fabric Real-Time hub. It provides details on the All data streams page in the Real-Time hub user interface.
author: mystina
ms.author: majia
ms.topic: how-to
ms.custom:
  - build-2024
ms.date: 09/16/2024
---

# Explore All data streams in Fabric Real-Time hub (preview)

When you navigate to Real-Time hub in Fabric, you can view data streams in different ways. For more information, see [Explore streams in Fabric Real-Time hub (preview)](explore-data-streams.md). This article covers the Real-Time hub **All data streams** page which allows you to see all data streams that you can access that are actively running in Fabric. Data streams include Fabric eventstreams and KQL tables.

[!INCLUDE [preview-note](./includes/preview-note.md)]

:::image type="content" source="media/explore-all-data-streams/hub-all-data-streams-menu.png" alt-text="Screenshot of the Real-Time hub All data streams page." lightbox="./media/explore-all-data-streams/hub-all-data-streams-menu.png":::

## All data streams page

### Columns

The **All data streams** page has the following columns:

| Column | Description |
| ------ | ----------- |
| Name | Name of the stream or KQL table. |
| Item | Name of the parent artifact. For a stream, it's the name of the eventstream. For a KQL table, it's the name of the KQL database. |
| Owner | Name of owner of the parent artifact. |
| Location | Name of workspace where the parent artifact is located. |
| Endorsement | Endorsement status of the parent artifact. |
| Sensitivity | Sensitivity status of the parent artifact. |

:::image type="content" source="./media/explore-all-data-streams/hub-all-data-streams-columns.png" alt-text="Screenshot that highlights the column names on the Real-Time hub All data streams page." lightbox="./media/explore-all-data-streams/hub-all-data-streams-columns.png":::

### Filters

The following filters are available at the top for you to narrow down easily to the desired stream:

| Filter | Description |
| ------ | --------- |
| Stream type | You can filter on the stream type. Either stream or table. |
| Owner | You can filter on the name of the owner of the parent artifact. For a stream, it's the owner of the parent eventstream. For a KQL table, it's owner of the parent KQL database. |
| Item | You can filter on the desired parent artifact name. For a stream, it's the name of the eventstream. For a KQL table, it's the name of the KQL database. |
| Location | You can filter on the desired workspace name. |

:::image type="content" source="media/explore-all-data-streams/real-time-hub-all-data-streams-filters.png" alt-text="Screenshot that highlights the Real Time hub All data streams page filters."  lightbox="media/explore-all-data-streams/real-time-hub-all-data-streams-filters.png":::

### Search

You can also search your streams/events using the search bar by typing in the name of stream.

:::image type="content" source="./media/explore-all-data-streams/real-time-hub-all-data-streams-search.png" alt-text="Screenshot that shows the search box on the Real-Time hub All data streams page." lightbox="./media/explore-all-data-streams/real-time-hub-all-data-streams-search.png":::

### Actions

Here are the actions available on streams from eventstreams from the **All data streams** page. Move the mouse over the data stream, select **... (ellipsis)** to see the actions.

| Action | Description |
| ------ | ----------- |
| Preview this data | Preview the data in the stream or derived stream. For more information, see [Preview data streams](preview-data-streams.md). |
| Open eventstream | Open parent eventstream of the stream. After you open the eventstream, you can optionally add transformations to [transform the data](../real-time-intelligence/event-streams/route-events-based-on-content.md#supported-operations) and [add destinations](../real-time-intelligence/event-streams/add-manage-eventstream-destinations.md) to send the output data to a supported destination. |
| Endorse | Endorse parent eventstream of the stream. For more information, see [Endorse data streams](endorse-data-streams.md). |

:::image type="content" source="./media/explore-all-data-streams/real-time-hub-all-data-streams-actions.png" alt-text="Screenshot that shows the actions available on streams in the Real-Time hub All data streams page." lightbox="./media/explore-all-data-streams/real-time-hub-all-data-streams-actions.png":::

Here are the actions available on a KQL table from the **All data streams** page.

| Action | Description |
| ------ | ----------- |
| Open KQL Database | Open parent KQL Database of the KQL table. |
| Endorse | Endorse parent KQL Database of the KQL table. For more information, see [Endorse data streams](endorse-data-streams.md). |

:::image type="content" source="./media/explore-all-data-streams/real-time-hub-kql-table-actions.png" alt-text="Screenshot that shows the actions available on KQL tables in the Real-Time hub All data streams page." lightbox="./media/explore-all-data-streams/real-time-hub-kql-table-actions.png":::

## Related content

- [View data stream details](view-data-stream-details.md)
- [Preview data streams](preview-data-streams.md)
- [Endorse data streams](endorse-data-streams.md)
- [Explore fabric events](explore-fabric-events.md)
