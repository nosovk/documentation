---
id: service-availability
title: Service availability - Temporal Cloud
sidebar_label: Availability
sidebar_position: 3
description: The operating envelope of Temporal Cloud includes availability, regions, throughput, and latency.
slug: /cloud/service-availability
toc_max_heading_level: 4
keywords:
- explanation
- operations
- temporal cloud
- throughput
tags:
- explanation
- operations
- temporal-cloud
- throughput
---

<!-- THIS FILE IS GENERATED. DO NOT EDIT THIS FILE DIRECTLY -->

The operating envelope of Temporal Cloud includes availability, regions, throughput, latency, and limits.
If you need more details, [contact us](https://pages.temporal.io/contact-us).

## Available regions {#regions}

**Where is Temporal Cloud available?**

Developers and applications can access Temporal Cloud from any location with internet connectivity, irrespective of where the Temporal Cloud resources (Namespaces) are located.

Temporal Cloud is compatible with applications deployed in various cloud environments or data centers.

To minimize latency, we advise creating your Namespace in a region geographically close to your Workers' hosting location.

Currently, Temporal Cloud operates in several regions on Amazon Web Services (AWS):

| Area          | Code           | Region            |
| ------------- | -------------- | ----------------- |
| Asia Pacific  | ap-northeast-1 | Tokyo             |
| Asia Pacific  | ap-south-1     | Mumbai            |
| Asia Pacific  | ap-southeast-1 | Singapore         |
| Asia Pacific  | ap-southeast-2 | Sydney            |
| Europe        | eu-central-1   | Frankfurt         |
| Europe        | eu-west-1      | Ireland           |
| Europe        | eu-west-2      | London            |
| North America | ca-central-1   | Central Canada    |
| North America | us-east-1      | Northern Virginia |
| North America | us-east-2      | Ohio              |
| North America | us-west-2      | Oregon            |
| South America | sa-east-1      | São Paulo         |

_**Your Workers and Client code aren't required to be hosted on AWS.**_

## Throughput expectations {#throughput}

**What kind of throughput can I get with Temporal Cloud?**

A Namespace has a default quota of 200 [Actions](/cloud/pricing#action) per second with spikes up to 400 Actions per second.
However, Temporal Cloud can provide more than 150,000 Actions per second.

If your Action rate exceeds your quota, Temporal Cloud throttles Actions until the rate matches your quota.
Actions like Start or Signal Workflow Execution always receive higher priority than other Actions, even when throttled.

To raise your quota, create a [support ticket](/cloud/support#support-ticket).

## Latency Service Level Objective (SLO) {#latency}

**What kind of latency can I expect from Temporal Cloud?**

Temporal Cloud aims for a latency SLO of 200ms per region for p99.
In June 2023, Temporal measured latency over a week-long period for starting and signaling Workflow Executions as follows:

- For `StartWorkflowExecution`: p90 latency was 90ms, and p99 latency was 125ms.
- For `SignalWorkflowExecution`: p90 latency was 53ms, and p99 latency was 95ms.
- For `SignalWithStartWorkflowExecution`: p90 latency was 87ms, and p99 latency was 116ms.

As Temporal continues working on improving latencies, these numbers will progressively decrease.

Latency observed from the Temporal Client is influenced by other system components like the Codec Server, egress proxy, and the network itself.
Increased latency might result from concurrent operations on the same Workflow Execution.
