---
title: "McAfee Network Security Platform connector for Microsoft Sentinel"
description: "Learn how to install the connector McAfee Network Security Platform to connect your data source to Microsoft Sentinel."
author: cwatson-cat
ms.topic: how-to
ms.date: 03/25/2023
ms.service: microsoft-sentinel
ms.author: cwatson
---

# McAfee Network Security Platform connector for Microsoft Sentinel

The [McAfee® Network Security Platform](https://www.mcafee.com/enterprise/en-us/products/network-security-platform.html) data connector provides the capability to ingest McAfee® Network Security Platform events into Microsoft Sentinel.

## Connector attributes

| Connector attribute | Description |
| --- | --- |
| **Log Analytics table(s)** | Syslog (McAfeeNSPEvent)<br/> |
| **Data collection rules support** | [Workspace transform DCR](/azure/azure-monitor/logs/tutorial-workspace-transformations-portal) |
| **Supported by** | [Microsoft Corporation](https://support.microsoft.com) |

## Query samples

**Top 10 Sources**

   ```kusto
   McAfeeNSPEvent
   | summarize count() by tostring(DvcHostname)
   | top 10 by count_
   ```
## Vendor installation instructions

> [!NOTE]
>  This data connector depends on a parser based on a Kusto Function to work as expected [**McAfeeNSPEvent**](https://aka.ms/sentinel-mcafeensp-parser) which is deployed with the Microsoft Sentinel Solution. This data connector has been developed using McAfee® Network Security Platform version: 10.1.x

1. Install and onboard the agent for Linux or Windows.

   Install the agent on the Server where the McAfee® Network Security Platform logs are forwarded.

   Logs from McAfee® Network Security Platform Server deployed on Linux or Windows servers are collected by **Linux** or **Windows** agents.

2. Configure McAfee® Network Security Platform event forwarding.

   Follow the configuration steps below to get McAfee® Network Security Platform logs into Microsoft Sentinel.
   
   1. While creating a profile, to make sure that events are formatted correctly, enter the following text in the Message text box:
   
      ```text
      <SyslogAlertForwarderNSP>:|SENSOR_ALERT_UUID|ALERT_TYPE|ATTACK_TIME|ATTACK_NAME|ATTACK_ID
      |ATTACK_SEVERITY|ATTACK_SIGNATURE|ATTACK_CONFIDENCE|ADMIN_DOMAIN|SENSOR_NAME|INTERFACE
      |SOURCE_IP|SOURCE_PORT|DESTINATION_IP|DESTINATION_PORT|CATEGORY|SUB_CATEGORY
      |DIRECTION|RESULT_STATUS|DETECTION_MECHANISM|APPLICATION_PROTOCOL|NETWORK_PROTOCOL|
      ```

## Next steps

For more information, go to the [related solution](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/azuresentinel.azure-sentinel-solution-mcafeensp?tab=Overview) in the Azure Marketplace.
