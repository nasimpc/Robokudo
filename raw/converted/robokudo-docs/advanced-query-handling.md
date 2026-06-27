---
type: converted-source
status: generated
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/Advanced_query_handling.html
source_type: html
---

<!-- Generated markdown mirror. Do not edit manually; regenerate from the HTML source. -->

# Advanced Query Handling

## Introduction

This tutorial builds upon the earlier query handling tutorial. It assumes you are already familiar with the basics of sending queries in RoboKudo. In this session, you’ll explore how RoboKudo handles queries using a behavior tree pipeline with support for validation, feedback, preemption, and results publishing.

By the end of this tutorial, you will:

Understand how the Query Interface works in RoboKudo.

Learn how queries are validated, processed, monitored, and canceled in a behavior tree.

See how live feedback and final results are handled dynamically.

Warning

This tutorial only works with ROS 2.

## Important Concepts

Term

Meaning

Why it matters

Query

A message asking the robot to do something (e.g., “recognize objects on the kitchen table”).

It starts the pipeline.

Feedback

Small updates showing the task is in progress.

Helps monitor that the perception system is alive and working.

Final Result

The final answer after the task finishes.

Relevant to other systems running on the robot to continue execution.

Preemption

(Advanced word for) Cancellation. If needed, we can stop a task early.

Allows to abort running perception tasks if the task is not relevant anymore or has to be replaced by another one. Supports reactivity.

Behavior Tree

A smart structure where tasks run in order and return SUCCESS, FAILURE, or RUNNING.

Makes building robot logic easy and modular.

## Full Working Example (query_complex.py)

Below is the full working Python code used to implement the behavior tree pipeline that handles a simple “numbers” query.

```python
from py_trees.common import Status
from py_trees.composites import Selector, Sequence
from py_trees.decorators import Inverter

from robokudo.analysis_engine import AnalysisEngineInterface
from robokudo.annotators.cluster_color import ClusterColorAnnotator
from robokudo.annotators.collection_reader import CollectionReaderAnnotator
from robokudo.annotators.image_preprocessor import ImagePreprocessorAnnotator
from robokudo.annotators.plane import PlaneAnnotator
from robokudo.annotators.pointcloud_cluster_extractor import PointCloudClusterExtractor
from robokudo.annotators.pointcloud_crop import PointcloudCropAnnotator
from robokudo.annotators.query import (
    GenerateQueryResult,
    QueryAnnotator,
    QueryFeedbackAndCount,
)
from robokudo.behaviours.action_server_checks import ActionServerNoPreemptRequest
from robokudo.descriptors import CrDescriptorFactory
from robokudo.idioms import pipeline_init
from robokudo.pipeline import Pipeline


class AnalysisEngine(AnalysisEngineInterface):
    def name(self) -> str:
        return "query_complex"

    def implementation(self) -> Pipeline:
        """Create a pipeline which responds to a query."""
        kinect_config = CrDescriptorFactory.create_descriptor("kinect")

        seq = Pipeline("RWPipeline")

        task_sequence = Sequence(name="TaskSequence", memory=True)
        task_sequence.add_children(
            [
                CollectionReaderAnnotator(descriptor=kinect_config),
                ImagePreprocessorAnnotator("ImagePreprocessor"),
                PointcloudCropAnnotator(),
                PlaneAnnotator(),
                PointCloudClusterExtractor(),
                ClusterColorAnnotator(),
                QueryFeedbackAndCount(count_until=50, return_code=Status.RUNNING),
            ]
        )

        # Combine preemption handling and task execution in a selector
        conditional_selector = Selector(name="ConditionalSelector", memory=False)
        conditional_selector.add_children(
            [
                Inverter(
                    name="Invert Preempt Request", child=ActionServerNoPreemptRequest()
                ),
                task_sequence,  # Run task sequence only if no preemption
            ]
        )

        seq.add_children(
            [
                pipeline_init(),
                QueryAnnotator(),
                conditional_selector,
                GenerateQueryResult(),
            ]
        )

        return seq
```

## Full Behavior Tree Overview

Here’s a visual map of the pipeline:

```
RootNodeWithGUI
├── VisManager
└── OPExperiments (WithMemory)
    ├── pipeline_init()
    ├── QueryAnnotator
    ├── ConditionalSelector (NoMemory)
    │   ├── Invert Preempt Request
    │   │   └── ActionServerNoPreemptRequest
    │   └── TaskSequence (WithMemory)
    │       ├── CollectionReaderAnnotator,
    │       ├── ImagePreprocessorAnnotator,
    │       ├── PointcloudCropAnnotator,
    │       ├── PlaneAnnotator,
    │       ├── PointCloudClusterExtractor,
    │       ├── ClusterColorAnnotator,
    │       └── QueryFeedbackAndCount,
    └── GenerateQueryResult
```

## QueryFeedbackAndCount – The Worker Node

A simple example node representing a long running task that sends feedback while running.

What it does:

Counts from 0 to 50.

Sends feedback after each number.

Key points:

Uses the QueryHandler to send feedback.

Returns RUNNING while still counting, and SUCCESS when finished.

## Preemption Handling with ConditionalSelector

```
ConditionalSelector (NoMemory)
├── Invert Preempt Request
│   └── ActionServerNoPreemptRequest
└── TaskSequence (WithMemory)
    ├── CollectionReaderAnnotator,
    ├── ImagePreprocessorAnnotator,
    ├── PointcloudCropAnnotator,
    ├── PlaneAnnotator,
    ├── PointCloudClusterExtractor,
    ├── ClusterColorAnnotator,
    └── QueryFeedbackAndCount,
```

What it does:

Always checks if a cancel request (preemption) has been issued.

If detected, stops execution immediately by succeeding early.

Otherwise, proceeds to run the full task sequence.

Why memory=False?

Cancellation status must be re-evaluated on every tick to react instantly.

Prevents stale decisions.

## ActionServerNoPreemptRequest and Inverter

What they do:

ActionServerNoPreemptRequest detects cancel requests via the blackboard.

If cancel is active → returns FAILURE.

Otherwise → returns SUCCESS.

The Inverter flips this result:

Cancellation → becomes SUCCESS (Selector stops task).

No cancellation → becomes FAILURE (Selector continues to task).

Why inversion is needed:

A Selector proceeds on first SUCCESS.

The inverter makes cancellation detectable as a SUCCESS condition.

## Action Client – How to Test the Pipeline

To test this query pipeline, you can use the query_test_client.py script (located in robokudo/robokudo/src/scripts/query_test_client.py).

This script sends a query, receives live feedback, and can cancel the task mid-way if needed.

This script is helpful for simulating real-world queries, verifying feedback flow, and testing cancellation behavior.

You can use the script as follows:

Start RoboKudo with the query_complex.py analysis engine:

```
python3 ~/ros2_ws/src/robokudo/robokudo/src/scripts/main.py _ae query_complex
```

In another terminal, run the bag file:

```bash
ros2 bag play ~/ros2_ws/test --loop
```

Run the query test client:

```
python3 ~/ros2_ws/src/robokudo/robokudo/src/scripts/query_test_client.py
```

The test client will send a query, receive live feedback, and can cancel the task mid-way if needed.
To cancel the goal mid-way, press ctrl+c in the terminal where you started the test client or let the client cancel it automatically after a given time with a CLI argument:

```
python3 ~/ros2_ws/src/robokudo/robokudo/src/scripts/query_test_client.py --preempt_timer=5.0
```

This will cancel the goal automatically after 5 seconds.

- Advanced Query Handling
- Introduction
- Important Concepts
- Full Working Example (query_complex.py)
- Full Behavior Tree Overview
- QueryFeedbackAndCount – The Worker Node
- Preemption Handling with ConditionalSelector
- ActionServerNoPreemptRequest and Inverter
- Action Client – How to Test the Pipeline
