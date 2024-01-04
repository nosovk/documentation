---
id: how-to-add-custom-search-attributes-to-workflow-executions-at-start-time-in-python
title: How to set custom Search Attributes in Python
sidebar_label: Set custom Search Attributes
description: To set custom Search Attributes, use the `search_attributes` parameter of 'start_workflow()'.
tags:
- search attribute
- python sdk
- code sample
---

<!-- DO NOT EDIT THIS FILE DIRECTLY.
THIS FILE IS GENERATED from https://github.com/temporalio/documentation/blob/main/sample-apps/python/your_visibility/starter_dacx.py. -->

To set custom Search Attributes, use the `search_attributes` parameter of the ['start_workflow()'](https://python.temporal.io/temporalio.client.Client.html#start_workflow) method.

<div class="copycode-notice-container"><div class="copycode-notice"><img data-style="copycode-icon" src="/icons/copycode.png" alt="Copy code icon" /> Sample application code information <img id="i-id-232567295" data-event="clickable-copycode-info" data-style="chevron-icon" src="/icons/chevron.png" alt="Chevron icon" /></div><div id="copycode-info-id-232567295" class="copycode-info">The following code sample comes from a working and tested sample application. The code sample might be abridged within the guide to highlight key aspects. Visit the source repository to <a href="https://github.com/temporalio/documentation/blob/main/sample-apps/python/your_visibility/starter_dacx.py">view the source code</a> in the context of the rest of the application code.</div></div>

```python
# ...
    handle = await client.start_workflow(
        GreetingWorkflow.run,
        id="search-attributes-workflow-id",
        task_queue="search-attributes-task-queue",
        search_attributes={"CustomKeywordField": ["old-value"]},
    )
```