---
title: Lakehouse tutorial - Ingest data into the lakehouse
description: In this tutorial, you ingest more dimensions and fact tables from the Wide World Importers (WWI) into the lakehouse.
ms.reviewer: sngun
ms.author: arali
author: ms-arali
ms.topic: tutorial
ms.custom:
  - build-2023
  - ignite-2023
ms.date: 07/19/2024
---

# Lakehouse tutorial: Ingest data into the lakehouse

In this tutorial, you ingest more dimensional and [fact tables](../data-warehouse/dimensional-modeling-fact-tables.md) from the Wide World Importers (WWI) into the lakehouse.

## Prerequisites

- If you don't have a lakehouse, you must [create a lakehouse](tutorial-build-lakehouse.md).

## Ingest data

In this section, you use the **Copy data activity** of the Data Factory pipeline to ingest sample data from an Azure storage account to the **Files** section of the lakehouse you created earlier.

1. Select **Workspaces** in the left navigation pane, and then select your new workspace from the **Workspaces** menu. The items view of your workspace appears.

1. From the **+New** menu item in the workspace ribbon, select **Data pipeline**.

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\create-data-pipeline.png" alt-text="Screenshot showing how to create a new data pipeline.":::

1. In the **New pipeline** dialog box, specify the name as **IngestDataFromSourceToLakehouse** and select **Create**. A new data factory pipeline is created and opened.

1. Next, set up an HTTP connection to import the sample World Wide Importers data into the Lakehouse. From the list of **New sources**, select **View more**, search for **Http** and select it.

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\select-http-connection.png" alt-text="Screenshot showing where to select the HTTP source.":::

1. In the **Connect to data source** window, enter the details from the table below and select **Next**.

   | Property | Value |
   |---|---|
   | URL | `https://assetsprod.microsoft.com/en-us/wwi-sample-dataset.zip` |
   |Connection | Create a new connection |
   | Connection name | wwisampledata |
   | Data gateway | None|
   | Authentication kind | Anonymous |

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\configure-http-connection.png" alt-text="Screenshot showing the parameters to configure the Http connection.":::

1. In the next step, enable the **Binary copy** and choose **ZipDeflate (.zip)** as the **Compression type** since the source is a .zip file. Keep the other fields at their default values and click **Next**.

    :::image type="content" source="media\tutorial-lakehouse-data-ingestion\select-compression-type.png" alt-text="Screenshot showing how to choose a compression type.":::

1. In the **Connect to data destination** window, specify the **Root folder** as **Files** and click **Next**. This will write the data to the *Files* section of the lakehouse.

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\configure-destination-connection.png" alt-text="Screenshot showing the destination connection settings of the lakehouse.":::

1. Choose the **File format** as **Binary** for the destination. Click **Next** and then **Save+Run**. You can schedule pipelines to refresh data periodically. In this tutorial, we only run the pipeline once. The data copy process takes approximately 10-15 minutes to complete.

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\destination-file-format.png" alt-text="Screenshot showing the destination file format.":::

1. You can monitor the pipeline execution and activity in the **Output** tab. You can also view detailed data transfer information by selecting the glasses icon next to the pipeline name, which appears when you hover over the name.

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\pipeline-status.png" alt-text="Screenshot showing the status of the copy pipeline activity.":::

1. After the successful execution of the pipeline, go to your lakehouse (**wwilakehouse**) and open the explorer to see the imported data.

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\item-view-select-lakehouse.png" alt-text="Screenshot showing how to navigate to the lakehouse.":::

1. Verify that the folder **WideWorldImportersDW** is present in the **Explorer** view and contains data for all tables.

   :::image type="content" source="media\tutorial-lakehouse-data-ingestion\validate-destination-files.png" alt-text="Screenshot showing the source data is copied into the Lakehouse explorer.":::

1. The data is created under the **Files** section of the lakehouse explorer. A new folder with GUID contains all the needed data. Rename the GUID to **wwi-raw-data**

To load incremental data into a lakehouse, see [Incrementally load data from a data warehouse to a lakehouse](../data-factory/tutorial-incremental-copy-data-warehouse-lakehouse.md).

## Next step

> [!div class="nextstepaction"]
> [Prepare and transform data](tutorial-lakehouse-data-preparation.md)
