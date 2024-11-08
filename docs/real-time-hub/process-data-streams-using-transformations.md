---
title: Process data streams in Real-Time hub
description: This article describes how to process data streams in Real-Time hub. Process using transformations in eventstreams, add KQL destination to send it to a KQL table and analyze it, and set alerts.
author: mystina
ms.author: majia
ms.topic: how-to
ms.custom:
  - build-2024
ms.date: 09/10/2024
---

# Process data streams in Fabric event streams  (preview)

The Add source experience, Microsoft sources page, and Fabric events page in Real-Time hub allow you to create streams for the supported sources. After you create these streams, you can process them, analyze them, and set alerts on them. This article explains how to process data streams using transformations supported in Fabric event streams.

[!INCLUDE [preview-note](./includes/preview-note.md)]

## Open eventstream

In Real-Time hub, when you create streams to get events from the [supported sources](supported-sources.md), an [eventstream](../real-time-intelligence/event-streams/overview.md) is created for you. You can open the parent eventstream for a stream by using one of the following ways:

- **Add source** experience:

    At the end of creating this stream, on the **Review and create** page, you see the **Open eventstream** link to open the eventstream associated with the stream in an editor.
-*All data streams* page:

    Move the mouse over a stream whose parent is an eventstream, and select the **Open** link, on select **... (ellipsis)**, and then select **Open eventstream**.
- **Detail page**:

    From the **All data streams** page select a stream whose parent is an eventstream to see the stream details. From the ribbon select **Open eventstream**.  

## Add transformations to the stream

After you open the eventstream in an editor, you can add transformations such as Aggregate, Expand, Filter, Group by, Manage fields, and Union, to transform or process the data streaming into Fabric, and then send the output data from transformations into supported destinations. For more information about transformations, see [Supported transformation operations](../real-time-intelligence/event-streams/route-events-based-on-content.md#supported-operations).

:::image type="content" source="./media/process-data-streams-using-transformations/transform-operations.png" alt-text="Screenshot that shows the transformation operations available on a stream.":::

## Related content

After you process data in the stream, you can send the output data to [destinations](../real-time-intelligence/event-streams/add-manage-eventstream-destinations.md)  supported by Fabric event streams.
