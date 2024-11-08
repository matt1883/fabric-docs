---
title: "Data loss prevention policies in Microsoft Fabric"
description: "Learn about how Microsoft Purview Data Loss Prevention policies work in Microsoft Fabric."
author: paulinbar
ms.author: painbar
ms.service: fabric
ms.subservice: governance
ms.topic: concept-article #Don't change
ms.date: 09/26/2024

#customer intent: As a Fabric administrator, security or compliance admin, or data owner, I want to understand how Microsoft Purview data loss prevention policies work in Microsoft Fabric.

---

# Data loss prevention policies in Fabric

This article describes Microsoft Purview Data Loss Prevention (DLP) policies in Fabric. The target audience is Fabric administrators, security and compliance teams, and Fabric data owners.

## Overview

To help organizations detect and protect their sensitive data, Fabric supports [Microsoft Purview Data Loss Prevention (DLP) polices](/microsoft-365/compliance/dlp-learn-about-dlp). When a DLP policy for Fabric detects a [supported item type](#supported-item-types) containing sensitive information, a policy tip can be attached to the item that explains the nature of the sensitive content, and an alert can be registered on the data loss prevention **Alerts** page in the Microsoft Purview compliance portal for monitoring and management by administrators. In addition, email alerts can be sent to administrators and specified users.

This article describes how DLP in Fabric works, lists considerations and limitations as well as licensing and permissions requirements, and explains how DLP CPU usage is metered. For more information, see:
 
* [Configure a DLP policy for Fabric](./data-loss-prevention-configure.md) to see how to configure DLP policies for Fabric.
* [Respond to a DLP policy violation in Fabric](./data-loss-prevention-respond.md) to see how to respond when a policy tip tells you your lakehouse or semantic model has a DLP policy violation.
* [Monitor DLP policy violations in Fabric](./data-loss-prevention-monitor.md) to see how to sign in to the Microsoft Purview portal to see details about DLP violation alerts.

## Considerations and limitations

* DLP policies for Fabric are defined in the [Microsoft Purview compliance portal](https://go.microsoft.com/fwlink/p/?linkid=2077149).

* DLP policies apply to workspaces. Only workspaces hosted in Fabric or Premium capacities are supported. For more information, see [Microsoft Fabric concepts and licenses](../enterprise/licenses.md).

* DLP evaluation workloads impact capacity. Currently, DLP for Fabric is available at no additional cost, but this is subject to change. Check this document and the Fabric blog for updates.

* DLP policy templates aren't yet supported for Fabric DLP policies. When creating a DLP policy for Fabric, choose the "custom policy" option.

* Fabric DLP policy rules currently support sensitivity labels and sensitive info types as conditions.

* DLP policies for Fabric aren't supported for sample semantic models, [streaming datasets](/power-bi/connect-data/service-real-time-streaming), or semantic models that connect to their data source via [DirectQuery](/power-bi/connect-data/desktop-use-directquery) or [live connection](/power-bi/connect-data/desktop-directquery-about#live-connections). This includes semantic models with mixed storage, where some of the data comes via import-mode and some comes via DirectQuery.

* DLP policies for Fabric apply only on data in Lakehouse Tables/ folder stored in Delta format.

* DLP policies for Fabric support all the primitive Delta types except *timestamp_ntz*.

* DLP policies for Fabric aren't supported for the following Delta Parquet data types:
    * Binary, timestamp_ntz, Struct, Array, List, Map, Json, Enum, Interval, Void.
    * Data with LZ4, Zstd, and Gzip compression codecs.

* [Exact data match (EDM) classifiers](/microsoft-365/compliance/sit-learn-about-exact-data-match-based-sits) and [trainable classifiers](/microsoft-365/compliance/classifier-learn-about) aren't supported by DLP for Fabric. If you select an EDM or trainable classifier in the condition of a policy, the policy will yield no results even if the semantic model or lakehouse does in fact contain data that satisfies the EDM or trainable classifier. Other classifiers specified in the policy will return results, if any.

* DLP policies for Fabric aren't supported in the China North region. See [How to find the default region for your organization](../admin/find-fabric-home-region.md) to learn how to find your organization's default data region.

* Azure capacities aren't supported for DLP in Fabric in the following clusters:
    * WUS3
    * WUS2
    * SCUS

* Onboarding a new tenant to DLP can take a few hours, depending on the number of supported workspaces that are being onboarded.

## Licensing and permissions

### SKU/subscriptions licensing

Before you get started with DLP for Fabric, you should confirm your [Microsoft 365 subscription](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). The admin account that sets up the DLP rules must be assigned one of the following licenses:

* Microsoft 365 E5
* Microsoft 365 E5 Compliance
* Microsoft 365 E5 Information Protection & Governance
* Purview capacities

### Permissions

Data from DLP for Fabric can be viewed in [Activity explorer](/microsoft-365/compliance/data-classification-activity-explorer). There are four roles that grant permission to Activity explorer; the account you use for accessing the data must be a member of any one of them.

To view the Activity explorer, the account you use for accessing the data must be a member of any of the following roles or above.

* Compliance administrator
* Security administrator
* Compliance data administrator

## Supported item types

DLP policies for Fabric currently support the following item types.

* Semantic models
* Lakehouses

See [Considerations and limitations](#considerations-and-limitations) for exceptions.

## How do DLP policies for Fabric work

You define a DLP policy in the data loss prevention section of the Microsoft Purview portal. In the policy, you specify the sensitivity labels and/or sensitive info types you want to detect. You also specify the actions that will happen when the policy detects a semantic model or lakehouse that contains sensitive data of the kind you specified. DLP policies for Fabric support two actions:

* User notification via policy tips.
* Alerts. Alerts can be sent by email to administrators and users. Additionally, administrators can monitor and manage alerts on the **Alerts** tab in the compliance portal.

When a semantic model or lakehouse is evaluated by DLP policies, if it matches the conditions specified in a DLP policy, the actions specified in the policy occur. DLP policies are initiated by the following actions:

**Semantic models**:

A semantic model is evaluated against DLP policies whenever one of the following events occurs:

* Publish
* Republish
* On-demand refresh
* Scheduled refresh

>[!NOTE]
> DLP evaluation of the semantic model doesn't occur if either of the following is true:
> * The initiator of the event (publish, republish, on-demand refresh, scheduled refresh) is an account using service principal authentication.
> * The semantic model owner is a service principal.

**Lakehouse**:

A lakehouse is evaluated against DLP policies When the data within a lakehouse undergoes a change, such as getting new data, connecting a new source, adding or updating existing tables, and more.

## What happens when an item is flagged by a Fabric DLP policy

When a DLP policy detects an issue with an item:

* If "user notification" is enabled in the policy, the item will be marked in Fabric with an icon that indicates that a DLP policy has detected an issue with the item. Hover over the icon to display a hover card that provides an option to see the full details in a side panel. For more information about what you see in the side panel, see [Respond to a DLP violation in Fabric](./data-loss-prevention-respond.md).

    :::image type="content" source="./media/data-loss-prevention-overview/policy-tip-indication.png" alt-text="Screenshot of policy tip icon in the OneLake data hub.":::

    For semantic models, opening the details page will show a policy tip that explains the policy violation and how the type of sensitive information detected should be handled. Selecting **View all** opens a side panel with all the policy details.

    :::image type="content" source="./media/data-loss-prevention-overview/policy-tip-in-dataset-details.png" alt-text="Screenshot of policy tip on semantic model details page.":::

    >[!NOTE]
    > If you hide the policy tip, it doesn’t get deleted. It will appear the next time you visit the page.

    For lakehouses, the indication will appear in the header in edit mode, and opening the fly out makes it possible to see more details about the policy tips affecting the lakehouse. Selecting **View all** opens a side panel with all the policy details.

    :::image type="content" source="./media/data-loss-prevention-overview/policy-tip-in-lakehouse-details.png" alt-text="Screenshot of policy tip in lakehouse header flyout.":::

* If alerts are enabled in the policy, an alert will be recorded on the data loss prevention **Alerts** page in the Microsoft Purview portal, and (if configured) an email will be sent to administrators and/or specified users. For more information, see [Monitor and manage DLP policy violations](./data-loss-prevention-monitor.md).

## Related content

* [Configure a DLP policy for Fabric](./data-loss-prevention-configure.md).
* [Respond to a DLP policy violation in Fabric](./data-loss-prevention-respond.md).
* [Monitor and manage DLP policy violations](./data-loss-prevention-monitor.md)
* [Learn about data loss prevention](/purview/dlp-learn-about-dlp)