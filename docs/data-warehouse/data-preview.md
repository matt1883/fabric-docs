---
title: View data in the Data preview
description: Learn about using the Data preview in Microsoft Fabric.
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.reviewer: jacindaeng
ms.date: 09/20/2024
ms.topic: how-to
ms.custom:
  - build-2023
  - ignite-2023
ms.search.form: Data preview # This article's title should not change. If so, contact engineering.
---
# View data in the Data preview in Microsoft Fabric

**Applies to:** [!INCLUDE [fabric-se-and-dw-and-mirrored-db](includes/applies-to-version/fabric-se-and-dw-and-mirrored-db.md)]

The **Data preview** is one of the three switcher modes along with the Query editor and Model view within Synapse Data Warehouse in Microsoft Fabric that provides an easy interface to view the data within your tables or views to preview sample data (top 1,000 rows).

- You can also [query the data](query-warehouse.md) in your warehouse with multiple tools with a [SQL connection string](connectivity.md).
- You can use the [SQL query editor](sql-query-editor.md) to write T-SQL queries from the [!INCLUDE [product-name](../includes/product-name.md)] portal.
- You can build queries graphically with the [Visual query editor](visual-query-editor.md).

## Get started

After creating a warehouse and ingesting data, select a specific table or view from the **Object explorer** that you would like to display in the data grid of the Data preview page.

:::image type="content" source="media/data-preview/data-preview.png" alt-text="Screenshot of the data grid on the Data preview screen within the warehouse." lightbox="media/data-preview/data-preview.png":::

 - **Search value** – Type in a specific keyword in the search bar and rows with that specific keyword will be filtered. In this example, "New Hampshire" is the keyword and only rows containing this keyword are shown. To clear the search, select the `X` inside the search bar.

    :::image type="content" source="media/data-preview/search-bar.png" alt-text="Screenshot of searching New Hampshire in the search bar within the data preview of the warehouse." lightbox="media/data-preview/search-bar.png":::

 - **Sort columns (alphabetically or numerically)** – Hover over the column title to see the **More Options (...)** button appear. Select it to see the "Sort Ascending" and "Sort Descending" options.

    :::image type="content" source="media/data-preview/sort-data-preview.png" alt-text="Screenshot of selecting on the context menu within data preview to sort ascending or descending." lightbox="media/data-preview/sort-data-preview.png":::

 - **Copy value** – Select a specific cell in the data preview and press `Ctrl + C` (Windows) or `Cmd + C` (Mac).

## Considerations and limitations

 - Only the top 1,000 rows can be shown in the data grid of the Data preview.
 - The Data preview view changes depending on how the columns are sorted or if there's a keyword that is searched.

## Related content

- [Define relationships in data models for data warehousing](data-modeling-defining-relationships.md)
- [Model data in the default Power BI semantic model in Microsoft Fabric](default-power-bi-semantic-model.md)
