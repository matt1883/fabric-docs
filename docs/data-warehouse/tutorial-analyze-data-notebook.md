---
title: Data warehouse tutorial - analyze data with a notebook
description: In this tutorial step, learn how to analyze Fabric data with a T-SQL notebook or using Shortcuts
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.reviewer: prlangad
ms.date: 09/20/2024
ms.topic: tutorial
ms.custom:
  - build-2023
  - ignite-2023
---

# Tutorial: Analyze data with a notebook

**Applies to:** [!INCLUDE [fabric-se-and-dw](includes/applies-to-version/fabric-se-and-dw.md)]

In this tutorial, learn about how you can use analyze data using [T-SQL notebook](#option-1-create-a-t-sql-notebook-on-the-warehouse) or using a notebook with a [Lakehouse shortcut](#option-2-create-a-lakehouse-shortcut-and-analyze-data-with-an-notebook).

## Option 1: Create a T-SQL notebook on the warehouse

To get started, create a T-SQL notebook in one of the following two ways:

1. Create a T-SQL notebook from the Microsoft Fabric Warehouse homepage. Navigate to the **Data Warehouse** workload, and choose **Notebook**.

1. Select **+ Warehouses** and add the `WideWorldImporters` warehouse. Select the `WideWorldImporters` warehouse from **OneLake data hub** dialog box.

   :::image type="content" source="media/tutorial-analyze-data-notebook/add-warehouses-button.png" alt-text="Screenshot from the Fabric portal of the Add Warehouses button underneath Warehouses in the All sources area of the Explorer." lightbox="media/tutorial-analyze-data-notebook/add-warehouses-button.png":::

1. Create a T-SQL notebook from the warehouse editor. From your `WideWorldImporters` warehouse, from the top navigation ribbon, select __New SQL query__ and then __New SQL query in notebook__.

   :::image type="content" source="media/tutorial-analyze-data-notebook/create-tsql-notebook-from-editor.png" alt-text="Screenshot from the Fabric portal of the New SQL query in notebook menu option." lightbox="media/tutorial-analyze-data-notebook/create-tsql-notebook-from-editor.png":::

1. Once the notebook is created, you can see `WideWorldImporters` warehouse is loaded into the explorer, and the ribbon shows T-SQL as the default language.

1. Right-click to launch the **More** menu option on the `dimension_city` table. Select **SELECT TOP 100** to generate a quick SQL template to explore 100 rows from the table.

   :::image type="content" source="media/tutorial-analyze-data-notebook/tsql-notebook-select-top-100.png" alt-text="Screenshot from the Fabric portal of the SELECT TOP 100 rows option.":::

1. Run the code cell and you can see messages and results.

   :::image type="content" source="media/tutorial-analyze-data-notebook/tsql-notebook-top-100-results.png" alt-text="Screenshot from the Fabric portal of the SELECT TOP 100 results." lightbox="media/tutorial-analyze-data-notebook/tsql-notebook-top-100-results.png":::


## Option 2: Create a lakehouse shortcut and analyze data with an notebook

First, we create a new lakehouse. To create a new lakehouse in your [!INCLUDE [product-name](../includes/product-name.md)] workspace:

1. Select the `Data Warehouse Tutorial` workspace in the navigation menu.
1. Select **+ New** > **Lakehouse**.

    :::image type="content" source="media/tutorial-analyze-data-notebook/new-lakehouse-menu.png" alt-text="Screenshot from the Fabric portal showing the + New menu. Lakehouse is boxed in red.":::

1. In the **Name** field, enter `ShortcutExercise`, and select **Create**.
1. The new lakehouse loads and the **Explorer** view opens up, with the **Get data in your lakehouse** menu. Under **Load data in your lakehouse**, select the **New shortcut** button.

    :::image type="content" source="media/tutorial-analyze-data-notebook/lakehouse-load-data-new-shortcut.png" alt-text="Screenshot from the Fabric portal showing the Load data in your lakehouse menu on the landing page. The New shortcut button is boxed in red." lightbox="media/tutorial-analyze-data-notebook/lakehouse-load-data-new-shortcut.png":::

1. In the **New shortcut** window, select the button for **Microsoft OneLake**.

    :::image type="content" source="media/tutorial-analyze-data-notebook/new-shortcut-onelake.png" alt-text="Screenshot from the Fabric portal showing the New shortcut window. The button for Microsoft OneLake is boxed in red." lightbox="media/tutorial-analyze-data-notebook/new-shortcut-onelake.png":::

1. In the **Select a data source type** window, scroll through the list until you find the **Warehouse** named `WideWorldImporters` you created previously. Select it, then select **Next**.
1. In the OneLake object browser, expand **Tables**, expand the `dbo` schema, and then select the checkbox for `dimension_customer`. Select **Next**. Select **Create**.
1. If you see a folder called `Unidentified` under **Tables**, select the **Refresh** icon in the horizontal menu bar.

    :::image type="content" source="media/tutorial-analyze-data-notebook/lakehouse-explorer-refresh-button.png" alt-text="Screenshot from the Fabric portal showing the refresh button on the horizontal menu bar, and the Unidentified tables under ShortcutExercise in the Lakehouse explorer.":::

1. Select the `dimension_customer` in the **Table** list to preview the data. The lakehouse is showing the data from the `dimension_customer` table from the [!INCLUDE [fabric-dw](includes/fabric-dw.md)]!

    :::image type="content" source="media/tutorial-analyze-data-notebook/lakehouse-table-preview.png" alt-text="Screenshot from the Fabric portal showing the data preview of the dimension_customer table." lightbox="media/tutorial-analyze-data-notebook/lakehouse-table-preview.png":::

1. Next, create a new notebook to query the `dimension_customer` table. In the **Home** ribbon, select the dropdown list for **Open notebook** and choose **New notebook**.
1. In the **Explorer**, select the **Lakehouses** source folder. 
1. Select, then drag the `dimension_customer` from the **Tables** list into the open notebook cell. You can see a PySpark query has been written for you to query all the data from `ShortcutExercise.dimension_customer`. This notebook experience is similar to Visual Studio Code Jupyter notebook experience. You can also open the notebook in VS Code.

    :::image type="content" source="media/tutorial-analyze-data-notebook/drop-dim-customer-notebook.png" alt-text="Screenshot from the Fabric portal notebook view. An arrow indicates the path to select dimension_customer, then drag and drop it into the open notebook cell.":::

1. In the **Home** ribbon, select the **Run all** button. Once the query is completed, you will see you can easily use PySpark to query the [!INCLUDE [fabric-dw](includes/fabric-dw.md)] tables!

    :::image type="content" source="media/tutorial-analyze-data-notebook/data-notebook-run-all-results.png" alt-text="Screenshot from the Fabric portal showing the results of running the notebook to display data from dimension_customer." lightbox="media/tutorial-analyze-data-notebook/data-notebook-run-all-results.png":::

## Next step

> [!div class="nextstepaction"]
> [Tutorial: Create cross-warehouse queries with the SQL query editor](tutorial-sql-cross-warehouse-query-editor.md)
