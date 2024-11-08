---
title: Hello world tutorial for Apache Airflow Job
description: Learn to get started with the Apache Airflow Job and run a Hello World dag.
ms.reviewer: abnarain
ms.author: abnarain
author: abnarain
ms.topic: tutorial
ms.custom:
  - build-2024
ms.date: 04/15/2024
---

# Tutorial: Run Hello-world DAG in Apache Airflow Job

> [!NOTE]
> Apache Airflow job is powered by Apache Airflow. </br> [Apache Airflow](https://airflow.apache.org/) is an open-source platform used to programmatically create, schedule, and monitor complex data workflows. It allows you to define a set of tasks, called operators, that can be combined into directed acyclic graphs (DAGs) to represent data pipelines.

In this tutorial, you'll run a hello-world DAG in Apache Airflow Job. This tutorial focuses on familiarizing users with the features and environment of the Apache Airflow Job.

## Prerequisites

To get started, you must complete the following prerequisite:

- Enable Apache Airflow Job in your Tenant.

  > [!NOTE]
  > Since Apache Airflow job is in preview state, you need to enable it through your tenant admin. If you already see Apache Airflow Job, your tenant admin may have already enabled it.

  1. Go to Admin Portal -> Tenant Settings -> Under Microsoft Fabric -> Expand 'Users can create and use Apache Airflow Job (preview)' section.

  2. Click Apply.

     :::image type="content" source="media/apache-airflow-jobs/enable-apache-airflow-job-tenant.png" alt-text="Screenshot to enable Apache Airflow in tenant." lightbox="media/apache-airflow-jobs/enable-apache-airflow-job-tenant.png":::

### Create an Apache Airflow Job

1. You can use an existing workspace or [Create a new workspace](../get-started/create-workspaces.md).

2. Expand `+ New` dropdown -> Click on More Options -> Under `Data Factory` section -> Select Apache Airflow Job (preview)

   :::image type="content" source="media/apache-airflow-jobs/more-options.png" lightbox="media/apache-airflow-jobs/more-options.png" alt-text="Screenshot shows click on more options.":::

   :::image type="content" source="media/apache-airflow-jobs/apache-airflow-project.png" alt-text="Screenshot to select Apache Airflow job.":::

3. Give a suitable name to your project and click on the "Create" button.

### Create a DAG File

1. Click on "New DAG file" card -> Give the name to the file and Click on "Create" button.

   :::image type="content" source="media/apache-airflow-jobs/name-directed-acyclic-graph-file.png" alt-text="Screenshot to name the DAG file.":::

2. A boilerplate DAG code is presented to you. You can edit the file as per your requirements.

   :::image type="content" source="media/apache-airflow-jobs/boilerplate-directed-acyclic-graph.png" lightbox="media/apache-airflow-jobs/boilerplate-directed-acyclic-graph.png" alt-text="Screenshot presents boilerplate DAG file in Microsoft Fabric.":::

3. Click on "Save icon".

   :::image type="content" source="media/apache-airflow-jobs/click-on-save-icon.png" lightbox="media/apache-airflow-jobs/click-on-save-icon.png" alt-text="Screenshot presents how to save DAG file in Microsoft Fabric.":::

### Monitor your Apache Airflow DAG in Apache Airflow UI

1. The saved dag files are loaded in the Apache Airflow UI. You can monitor them by clicking on the "Monitor in Apache Airflow" button.

   :::image type="content" source="media/apache-airflow-jobs/monitor-directed-acyclic-graph.png" alt-text="Screenshot to monitor the Airflow DAG.":::

   :::image type="content" source="media/apache-airflow-jobs/directed-acyclic-graph-in-ui.png" alt-text="Screenshot presents the loaded Airflow DAG.":::

## Related Content

[Quickstart: Create an Apache Airflow Job](../data-factory/create-apache-airflow-jobs.md)
