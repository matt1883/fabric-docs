---
title: Direct Lake mode and Power BI reporting
description: Learn how to build Power BI reports on top of lakehouse data in Microsoft Fabric
ms.reviewer: snehagunda
ms.author: tvilutis
author: tedvilutis
ms.topic: conceptual
ms.custom:
  - build-2023
  - ignite-2023
ms.date: 04/24/2024
ms.search.form: Lakehouse Power BI Reporting
---

# How Direct Lake mode works with Power BI reporting

In Microsoft Fabric, when the user creates a lakehouse, the system also provisions the associated SQL analytics endpoint and default semantic model in Direct Lake mode. You can add tables from the lakehouse into the default semantic model by going to the SQL analytics endpoint and clicking the **Manage default semantic model** button in the **Reporting** ribbon. You can also create a non-default Power BI semantic model in Direct Lake mode by clicking **New semantic model** in the lakehouse or SQL analytics endpoint. The non-default semantic model is created in Direct Lake mode and allows Power BI to consume data by creating Power BI reports, explores, and running user-created DAX queries in Power BI Desktop or the workspace itself. The default semantic model created in the SQL analytics endpoint can be used to create Power BI reports but has some [other limitations](/fabric/data-warehouse/semantic-models).

When a Power BI report shows data in visuals, it requests it from the semantic model. Next, the semantic model accesses a lakehouse to consume data and return it to the Power BI report. For efficiency, the semantic model can keep some data in the cache and refresh it when needed. [Direct Lake overview](/fabric/get-started/direct-lake-overview) has more details. 

Lakehouse also applies V-order optimization to delta tables. This optimization gives unprecedented performance and the ability to quickly consume large amounts of data for Power BI reporting.

:::image type="content" source="media\power-bi-reporting\dataset.png" alt-text="Screenshot of the default semantic model landing page." lightbox="media\power-bi-reporting\dataset.png":::

## Setting permissions for report consumption

The semantic model in Direct Lake mode is consuming data from a lakehouse on demand. To make sure that data is accessible for the user that is viewing Power BI report, necessary permissions on the underlying lakehouse need to be set.

One option is to give the user the *Viewer* role in the workspace to consume all items in the workspace, including the lakehouse, if in this workspace, semantic models, and reports. Alternatively, the user can be given the *Admin, Member, or Contributor* role to have full access to the data and be able to create and edit the items, such as lakehouses, semantic models, and reports. 

In addition, non-default semantic models can utilize a [fixed identity](/fabric/get-started/direct-lake-fixed-identity) to read data from the lakehouse, without giving report users any access to the lakehouse, and users be given permission to access the report through an [app](/power-bi/collaborate-share/service-create-distribute-apps). Also, with fixed identity, non-default semantic models in Direct Lake mode can have row-level security defined in the semantic model to limit the data the report user sees while maintaining Direct Lake mode. SQL-based security at the SQL analytics endpoint can also be used, but Direct Lake mode will fall back to DirectQuery, so this should be avoided to maintain the performance of Direct Lake. 

## Related content

- [Default Power BI semantic models in Microsoft Fabric](../data-warehouse/semantic-models.md)
