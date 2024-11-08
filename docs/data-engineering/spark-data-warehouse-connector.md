---
title: Spark connector for Microsoft Fabric Synapse Data Warehouse
description: Learn how to use a Spark connector to access and work with data from a Microsoft Fabric warehouse and the SQL analytics endpoint of a lakehouse.
author: ms-arali
ms.author: arali
ms.topic: how-to
ms.date: 09/30/2024
---

# Spark connector for Microsoft Fabric Synapse Data Warehouse

The Spark connector for Synapse Data Warehouse enables Spark developers and data scientists to access and work with data from [a warehouse and the SQL analytics endpoint of a lakehouse](../data-warehouse/data-warehousing.md#data-warehousing-items). The connector offers the following capabilities:

* You can work with data from a warehouse or SQL analytics endpoint in the same workspace or across multiple workspaces.
* The SQL analytics endpoint of a Lakehouse is automatically discovered based on workspace context.
* The connector has a simplified Spark API, abstracts the underlying complexity, and operates with just one line of code.
* While you're accessing a table or a view, the connector upholds security models defined at the SQL engine level. These models include object-level security (OLS), row-level security (RLS), and column-level security (CLS).
* The connector comes preinstalled within the Fabric runtime, which eliminates the need for separate installation.

> [!NOTE]
> The connector is currently in preview. For more information, see the [current limitations](spark-data-warehouse-connector.md#current-limitations) later in this article.  

## Authentication

Microsoft Entra authentication is an integrated authentication approach. Users sign in to the Microsoft Fabric workspace, and their credentials are automatically passed to the SQL engine for authentication and authorization. The credentials are automatically mapped, and users aren't required to provide specific configuration options.

### Permissions

To connect to the SQL engine, users need at least Read permission (similar to CONNECT permission in SQL Server) on the warehouse or SQL analytics endpoint (item level). Users also need granular object-level permissions to read data from specific tables or views. To learn more, see [Security for data warehousing in Microsoft Fabric](../data-warehouse/security.md).

## Code templates and examples

### Use a method signature

The following command shows the `synapsesql` method signature for the read request. The three-part `tableName` argument is required for accessing tables or views from a warehouse and the SQL analytics endpoint of a lakehouse. Update the argument with the following names, based on your scenario:

* Part 1: Name of the warehouse or lakehouse.
* Part 2: Name of the schema.
* Part 3: Name of the table or view.

```scala
synapsesql(tableName:String="<Part 1.Part 2.Part 3>") => org.apache.spark.sql.DataFrame
```
In addition to reading from a table or view directly, this connector also allows you to specify a custom or passthrough query, which gets passed to SQL engine and result is returned back to Spark.
```scala
spark.read.option(Constants.DatabaseName, "<warehouse/lakeshouse name>").synapsesql("<T-SQL Query>") => org.apache.spark.sql.DataFrame
```

While this connector auto discovers the endpoint for the specified warehouse / lakehouse, if you want to specify it explicitly, you can do it.
```
//For warehouse
spark.conf.set("spark.datawarehouse.<warehouse name>.sqlendpoint", "<sql endpoint,port>")
//For lakehouse
spark.conf.set("spark.lakehouse.<lakeshouse name>.sqlendpoint", "<sql endpoint,port>")
//Read from table
spark.read.synapsesql("<warehouse/lakeshouse name>.<schema name>.<table or view name>") 
```

### Read data within the same workspace

> [!IMPORTANT]
> Run these import statements at the beginning of your notebook or before you start using the connector:

>  For Scala
>
> `import com.microsoft.spark.fabric.tds.implicits.read.FabricSparkTDSImplicits._`
>
> `import com.microsoft.spark.fabric.Constants`

>  For PySpark (Python)
>
> `import com.microsoft.spark.fabric`
>
> `from com.microsoft.spark.fabric.Constants import Constants`

The following code is an example to read data from a table or view in a Spark DataFrame:

```python
df = spark.read.synapsesql("<warehouse/lakehouse name>.<schema name>.<table or view name>")
```

The following code is an example to read data from a table or view in a Spark DataFrame with a row count limit of 10:

```python
df = spark.read.synapsesql("<warehouse/lakehouse name>.<schema name>.<table or view name>").limit(10)
```

The following code is an example to read data from a table or view in a Spark DataFrame after you apply a filter:

```python
df = spark.read.synapsesql("<warehouse/lakehouse name>.<schema name>.<table or view name>").filter("column name == 'value'")
```

The following code is an example to read data from a table or view in a Spark DataFrame for selected columns only:

```python
df = spark.read.synapsesql("<warehouse/lakehouse name>.<schema name>.<table or view name>").select("column A", "Column B")
```

### Read data across workspaces

To access and read data from a data warehouse or lakehouse across workspaces, you can specify the workspace ID where your data warehouse or lakehouse exists and then lakehouse or data warehouse item id. This line provides an example of reading data from a table or view in a Spark DataFrame from the data warehouse or lakehouse with the specified workspace ID and lakehouse/data warehouse ID:

```python
# For lakehouse
df = spark.read.option(Constants.WorkspaceId, "<workspace id>").synapsesql("<lakehouse name>.<schema name>.<table or view name>")
df = spark.read.option(Constants.WorkspaceId, "<workspace id>").option(Constants.LakehouseId, "<lakehouse item id>").synapsesql("<lakehouse name>.<schema name>.<table or view name>")

# For data warehouse
df = spark.read.option(Constants.WorkspaceId, "<workspace id>").synapsesql("<warehouse name>.<schema name>.<table or view name>")
df = spark.read.option(Constants.WorkspaceId, "<workspace id>").option(Constants.DatawarehouseId, "<data warehouse item id>").synapsesql("<warehouse name>.<schema name>.<table or view name>")
```

> [!NOTE]
> When you're running the notebook, by default the connector looks for the specified data warehouse or lakehouse in the workspace of the lakehouse that's attached to the notebook. To reference a data warehouse or lakehouse from another workspace, specify the workspace ID and lakehouse or data warehouse item ID as above.

### Create a lakehouse table based on data from a warehouse

These lines of code provide an example to read data from a table or view in a Spark DataFrame and use it to create a lakehouse table:

```python
df = spark.read.synapsesql("<warehouse/lakehouse name>.<schema name>.<table or view name>")
df.write.format("delta").saveAsTable("<Lakehouse table name>")
```

## Troubleshoot

Upon completion, the read response snippet appears in the cell's output. Failure in the current cell also cancels subsequent cell executions of the notebook. Detailed error information is available in the Spark application logs.

## Current limitations

Currently, the connector:

* Supports data retrieval from Fabric warehouses and SQL analytics endpoints of lakehouse items.
* Fabric DW now supports `Time Travel` however this connector doesn't work for a query with time travel syntax. 
* Retains the usage signature like the one shipped with Apache Spark for Azure Synapse Analytics for consistency. However, it's not backward compatible to connect and work with a dedicated SQL pool in Azure Synapse Analytics.
* Column names with special characters will be handled by adding escape character before the query, based on 3 part table/view name, is submitted. In case of a custom or passthrough-query based read, users are required to escape column names that would contain special characters.

## Related content

* [Apache Spark runtimes in Fabric](runtime.md)
* [Apache Spark monitoring overview](spark-monitoring-overview.md)
* [Security for data warehousing in Fabric](../data-warehouse/security.md)
* [SQL granular permissions in Fabric](../data-warehouse/sql-granular-permissions.md)
