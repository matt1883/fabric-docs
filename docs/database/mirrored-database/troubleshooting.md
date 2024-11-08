---
title: "Troubleshoot Fabric mirrored databases"
description: Troubleshooting scenarios, workarounds, and links for mirrored databases in Microsoft Fabric.
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.reviewer: imotiwala, roblescarlos, maprycem, cynotebo
ms.date: 11/08/2024
ms.topic: troubleshooting
ms.search.form: Fabric Mirroring
---

# Troubleshoot Fabric mirrored databases

Scenarios, resolutions, and workarounds for Microsoft Fabric mirrored databases.

[!INCLUDE [feature-preview-note](../../includes/feature-preview-note.md)]

## Resources

Review the troubleshooting section of frequently asked questions for each data source:

- [Troubleshoot Mirroring Azure SQL Database](azure-sql-database-troubleshoot.md) and [FAQ about Mirroring Azure SQL Database](azure-sql-database-mirroring-faq.yml)
- [Troubleshoot Mirroring Azure Cosmos DB](azure-cosmos-db-troubleshooting.yml) and [FAQ about Mirroring Azure Cosmos DB](azure-cosmos-db-faq.yml)
- [Troubleshoot Mirroring Snowflake](snowflake-mirroring-faq.yml#troubleshoot-mirroring-snowflake-in-microsoft-fabric)
- [FAQ about Mirroring Azure Databricks](azure-databricks-faq.yml)

Review limitations documentation for each data source:

- [Limitations in Microsoft Fabric mirrored databases from Azure SQL Database (Preview)](azure-sql-database-limitations.md)
- [Limitations in Microsoft Fabric mirrored databases from Azure Cosmos DB (Preview)](azure-cosmos-db-limitations.md)
- [Limitations in Microsoft Fabric mirrored databases from Azure Databricks (Preview)](azure-databricks-limitations.md)
- [Limitations in Microsoft Fabric mirrored databases from Snowflake](snowflake-limitations.md)

## Stop replication

When you select **Stop replication**, OneLake files remain as is, but incremental replication stops. You can restart the replication at any time by selecting **Start replication**. You might want to do stop/start replication when resetting the state of replication, after source database changes, or as a troubleshooting tool.  

## Troubleshoot

This section contains general Mirroring troubleshooting steps.

#### I can't connect to a source database

1. Check your connection details are correct, server name, database name, username, and password.
1. Check the server is not behind a firewall or private virtual network. Open the appropriate firewall ports.

#### No views are replicated

Currently, views are not supported. Only replicating regular tables are supported.

#### No tables are being replicated

1. Check the monitoring status to check the status of the tables. For more information, see [Monitor Fabric mirrored database replication](monitor.md).
1. Select the **Configure replication** button. Check to see if the tables are present in the list of tables, or if any Alerts on each table detail are present.

#### Columns are missing from the destination table

1. Select the **Configure replication** button.
1. Select the Alert icon next to the table detail if any columns are not being replicated.

#### Some of the data in my column appears to be truncated

The Fabric warehouse does not support **VARCHAR(max)** it only currently supports **VARCHAR(8000)**.

#### Data doesn't appear to be replicating

In the **Monitoring** page, the date shown is the last time data was successfully replicated.

#### I can't change the source database

Changing the source database is not supported. Create a new mirrored database.

## Limits error messages 

These common error messages have explanations and mitigations:

| **Error message** | **Reason** | **Mitigation** |
|:--|:--|:--|
| "The replication is being throttled due to destination space limit." | There's a maximum of 10 TB of storage space in destination per Mirrored database. The replication is being throttled due to destination space limit. | In the source database, drop tables, remove data, or shard. |
| "The tables count may exceed the limit, there could be some tables missing."| There's a maximum of 500 tables. | In the source database, drop or filter tables. If the new table is the 500th table, no mitigation required. |
| "The replication is being throttled and expected to continue at YYYY-MM-DDTHH:MM:ss." | There's a maximum of 1 TB of change data captured per Mirrored database per day. | Wait for throttling to end. |

## Related content

- [What is Mirroring in Fabric?](overview.md)
- [Monitor Fabric mirrored database replication](monitor.md)
