---
id: backgroundcheck-boilerplate-add-workflow-tests
title: Add Workflow function tests
sidebar_label: Test Workflow code
description: How to test Workflow code
tags:
- testing
- developer guide
- go sdk
---

<!-- DO NOT EDIT THIS FILE DIRECTLY.
THIS FILE IS GENERATED from https://github.com/temporalio/documentation/blob/main/sample-apps/python/backgroundcheck_boilerplate/tests/workflow_dacx_test.py. -->

This is a unit test written in Python using the pytest library.

The test checks the `execute_workflow` method of the `BackgroundCheck` Workflow.

The test creates a new `WorkflowEnvironment` and a `Worker` with a Task Queue and the `BackgroundCheck` Workflow and `ssn_trace_activity` activity.

Then, it executes the `BackgroundCheck.run` method with a social security number and a unique ID, and asserts that the result is equal to "pass".

The test is marked with `@pytest.mark.asyncio` to indicate that it is an asynchronous test.

<div class="copycode-notice-container"><div class="copycode-notice"><img data-style="copycode-icon" src="/icons/copycode.png" alt="Copy code icon" /> Sample application code information <img id="i-id146514284" data-event="clickable-copycode-info" data-style="chevron-icon" src="/icons/chevron.png" alt="Chevron icon" /></div><div id="copycode-info-id146514284" class="copycode-info">The following code sample comes from a working and tested sample application. The code sample might be abridged within the guide to highlight key aspects. Visit the source repository to <a href="https://github.com/temporalio/documentation/blob/main/sample-apps/python/backgroundcheck_boilerplate/tests/workflow_dacx_test.py">view the source code</a> in the context of the rest of the application code.</div></div>

```python
import uuid

import pytest

from temporalio.testing import WorkflowEnvironment
from temporalio.worker import Worker

from activities.ssntraceactivity_dacx import ssn_trace_activity
from workflows.backgroundcheck_dacx import BackgroundCheck
# ...
@pytest.mark.asyncio
async def test_execute_workflow():
    task_queue_name = str(uuid.uuid4())
    async with await WorkflowEnvironment.start_time_skipping() as env:
        async with Worker(
            env.client,
            task_queue=task_queue_name,
            workflows=[BackgroundCheck],
            activities=[ssn_trace_activity],
        ):
            assert "pass" == await env.client.execute_workflow(
                BackgroundCheck.run,
                "555-55-5555",
                id=str(uuid.uuid4()),
                task_queue=task_queue_name,
            )
```