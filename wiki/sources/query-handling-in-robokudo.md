---
type: converted-source
status: generated
created: 2026-06-28
updated: 2026-06-28
source_file: raw/sources/robokudo-docs/query_interface.html
source_type: html
---

<!-- Generated markdown mirror. Do not edit manually; regenerate from the HTML source. -->
# Query handling in RoboKudo

In the previous tutorials, we have used RoboKudo to continuously analyze the incoming sensor data and visualize the results. When integrating the system with a robot, often you are triggering the perception process during specific times in your high-level program when needed. And additionally, you might supply additional information what to look for, like for example `'a red cup on a table'`.

This is why RoboKudo offers a **Query Interface**, which allows you to formulate such queries to state the required perception task(like the `'red cup on table'` in the example above). In this tutorial, we will look at the central components to work with this interface.

## General idea

To handle queries, you need the following three key components:

1. Query retrieval in the pipeline: Receive the query, annotate it into the CAS and trigger the pipeline execution.
2. Interpret the query in your Annotators: Make your Annotators react to the query that is currently being processed.
3. Generate a query answer / result: Generate the result that should be send back to the caller.

## Query retrieval in the pipeline

In order to make RoboKudo offer the QueryInterface, please add `robokudo.annotators.query.QueryAnnotator(),` into your pipeline right after the `robokudo.idioms.pipeline_init(),` Behavior. The `QueryAnnotator` will launch a ROS Action Server that is offering [an Action of Type ‘robokudo_msgs/Query’](https://gitlab.informatik.uni-bremen.de/robokudo/robokudo_msgs/-/blob/main/action/Query.action). The main datastructure in this Action is [a robokudo_msgs/ObjectDesignator](https://gitlab.informatik.uni-bremen.de/robokudo/robokudo_msgs/-/blob/main/msg/ObjectDesignator.msg). It features typical object-centric attributes that the robot can fill out to formulate how the object to be detected should look like or where it has to be located.

When the `QueryAnnotator` is visited in the Behavior Tree traversal, it will check if a new Query has been received. If no new Query is received, the Annotator will return `Running`. Otherwise, it will annotate the Query into the CAS and return `Success` to allow the Behavior Tree to proceed to the actual perception pipeline to analyze the sensor data.

## Interpret the query in your Annotators

After receiving the query, you will want to inspect the Query in your Annotators to check for the requested attributes. Access to it is provided by a predefined view in the CAS. The following code shows an example how to access it and react to it:

```python
self.query = self.get_cas().query
if self.obj.type == 'Cup':
  # Load model for cup detection
  # ...
```

## Generate a query answer / result

At the end, you want to send back a result for the received query. This is done by placing your query answer onto the Blackboard of the Behavior Tree. The ActionServer in the `QueryAnnotator` will then pick up that answer and send the result to the caller of the Query. In the following, you can see an example taken from an Annotator:

**ROS 1**

```python
# .... your imports ...
from robokudo_msgs.msg import QueryResult, ObjectDesignator
from robokudo.identifier import BBIdentifier
from py_trees.blackboard import Blackboard

# The result of a Query is typically a list of ObjectDesignator instances
query_result = QueryResult()

object_designator = ObjectDesignator()
object_designator.type = 'Cup'
object_designator.color.append('red')
query_result.res.append(object_designator)

blackboard = Blackboard()
blackboard.set(BBIdentifier.QUERY_ANSWER, query_result)
# Clear the query after we've answered it to indicate the the query is processed
self.get_cas().set(CASViews.QUERY, None)
```

**ROS 2**

```python
# .... your imports ...
from robokudo_msgs.msg import ObjectDesignator
from robokudo_msgs.action import Query
from robokudo.utils.query import QueryHandler

# The result of a Query is typically a list of ObjectDesignator instances
query_result = Query.Result()

object_designator = ObjectDesignator()
object_designator.type = 'Cup'
object_designator.color.append('red')
query_result.res.append(object_designator)

QueryHandler.send_answer(query_result)
```

Typically, such an Annotator would be at the end of the pipeline in your Analysis Engine, to conclude the perception pipeline and generate the final result based on the partial results in the CAS.

## Sending a query to RoboKudo

After starting RoboKudo with a `QueryAnnotator` in your analysis engine, you will get a new ROS action server at `/robokudo/query`.

**ROS 1**

You can either write an action client to send a request to this action server or use the `axclient.py` ROS node from the [actionlib_tools package](http://wiki.ros.org/actionlib_tools) for a graphical user interface. In ROS Noetic, you can install `ros-noetic-actionlib-tools` to get it.

> **Note**
>
> There is a [tutorial on axclient.py usage here](http://wiki.ros.org/actionlib_tutorials/Tutorials/Calling%20Action%20Server%20without%20Action%20Client#Use_axclient_from_actionlib). Please note though, that the axclient.py node is now in the actionlib_tools package. This is currently wrong in the linked tutorial. The call should look like this:
> ```bash
> rosrun actionlib_tools axclient.py /robokudo/query
> ```

**ROS 2**

You can either write an action client to send a request to this action server as [described here](https://docs.ros.org/en/jazzy/Tutorials/Intermediate/Writing-an-Action-Server-Client/Py.html#writing-an-action-client) or use the command line interface:

```bash
ros2 action send_goal /robokudo/query robokudo_msgs/Query '{<goal content as dict/json>}'
```

> **Tip**
>
> Writing queries directly on the cli can be a bit cumbersome, you can also use a json file to store the query and use:
> ```bash
> ros2 action send_goal /robokudo/query robokudo_msgs/Query "$(cat /path/to/your/query.json)"
> ```
> **Note**
>
> Axclient.py is not available in ROS 2, sadly there are no GUI alternatives yet.

## Indicating a failure

If one of your Annotators encounters an error and you are not able to generate a valuable answer after the perception process, you can send back a failure to the action caller. This can also include an error message to provide more details on the actual cause of the failure.

We need two components for this: A decorator on the individual Annotator that should be able to return an error and an exception for the actual failure.

Many built-in Annotators of RoboKudo already have this Decorator. If you are creating your own Annotator, make sure that its `update` method is annotated with the `@robokudo.utils.error_handling.catch_and_raise_to_blackboard` decorator.

> **Note**
>
> When your Annotator is extending/inheriting from the ThreadedAnnotator class, annotate the decorator on your compute() method instead.

After adding the decorator, you can simply indicate a failure by raising an exception. The text of the exception will be fed back to the caller of the action.

Below, you can find a minimal example:

```python
from py_trees.common import Status
from robokudo.utils.error_handling import catch_and_raise_to_blackboard


@catch_and_raise_to_blackboard
def update(self) -> Status:
    self.color = self.get_cas().color_image

    if self.color is None:
      raise Exception("No Color image available")
```

## Sending feedback during running perception queries

It is also possible to provide (ROS Action) feedback during the analysis of a query. You can simply add your feedback after getting the corresponding queue from the Blackboard:

**ROS 1**

```python
feedback_queue: queue.Queue = blackboard.get(BBIdentifier.QUERY_FEEDBACK)
feedback_queue.put(f"I'm still computing...")
```

**ROS 2**

```python
QueryHandler.send_feedback_str("I'm still computing...")
```
