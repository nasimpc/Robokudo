---
type: converted-source
status: generated
created: 2026-06-28
updated: 2026-06-28
source_file: raw/sources/robokudo-docs/create_your_own_annotator.html
source_type: html
---

<!-- Generated markdown mirror. Do not edit manually; regenerate from the HTML source. -->
# Create your own Annotator

As described in [the Introduction](../introduction.html), RoboKudo is a multi-expert approach which employs multiple algorithms to annotate parts of the incoming sensor data. We usually call these components *Annotators*, since their main purpose is reasoning and annotating new features or information.

## Create the Annotator

We will create a very simple Annotator which will simply look for a PointCloud in the CAS and report the size of it.

First, please go to your `rk_tutorial` package and open the following path:

**ROS 1**

```bash
cd src/rk_tutorial/annotators
```

**ROS 2**

```bash
cd rk_tutorial/annotators
```

Here, you can simply create a new file called `my_first_annotator.py` with the following content:

```python
from timeit import default_timer

from py_trees.common import Status
from robokudo.annotators.core import BaseAnnotator


class MyFirstAnnotator(BaseAnnotator):

    def __init__(self, name: str = "MyFirstAnnotator") -> None:
        """Default construction. Minimal one-time init!"""
        super(MyFirstAnnotator, self).__init__(name)

    def update(self) -> Status:
        start_timer = default_timer()

        cloud = self.get_cas().cloud

        self.rk_logger.info(f"Cloud size is: {len(cloud.points)}")

        end_timer = default_timer()
        self.feedback_message = f"Processing took {(end_timer - start_timer):.4f}s"
        return Status.SUCCESS
```

Let us have a closer look at some key aspects of the Annotator. Every Annotator will inherit from the `BaseAnnotator` class, which is a child of a normal py_trees `Behaviour`. The main method for every Behaviour is the `update` method, which is called everytime the Behaviour is invoked. Please note, that code running in your `update` method should not exceed a runtime of a couple of milliseconds, to keep the overall Behaviour Tree reactive.

> **Note**
>
> In computer vision, we often need to run methods that exceed this time constraint. For this purpose, we have developed the `ThreadedAnnotator` which you can use in that case. It is an Annotator which keeps your workload running in a thread. Make sure to put your code into the `compute` method instead of `update` to make proper use of that functionality when using the `ThreadedAnnotator`.

Another key element is the access of the `CAS`, the common data structure for all Annotators. The CAS is basically a python dict with its key being predefinde in `CASViews` to help the consistent usage of the data in it.

Now we need to include your new annotator into your pipeline that you’ve defined in the previous tutorial.

## Integrate your Annotator into the Pipeline

Go to `rk_tutorial/src/rk_tutorial/descriptors/analysis_engines/my_demo.py` and paste the following content to it:

```python
from rk_tutorial.annotators.my_first_annotator import MyFirstAnnotator
from robokudo.descriptors import CrDescriptorFactory

from robokudo.analysis_engine import AnalysisEngineInterface
from robokudo.annotators.collection_reader import CollectionReaderAnnotator
from robokudo.annotators.image_preprocessor import ImagePreprocessorAnnotator
from robokudo.annotators.plane import PlaneAnnotator
from robokudo.annotators.pointcloud_cluster_extractor import PointCloudClusterExtractor
from robokudo.annotators.pointcloud_crop import PointcloudCropAnnotator
from robokudo.idioms import pipeline_init
from robokudo.pipeline import Pipeline


class AnalysisEngine(AnalysisEngineInterface):
    def name(self) -> str:
        return "my_demo"

    def implementation(self) -> Pipeline:
        """
        Create a basic pipeline that does tabletop segmentation
        """
        kinect_config = CrDescriptorFactory.create_descriptor("kinect_wo_tf")

        seq = Pipeline("RWPipeline")
        seq.add_children(
            [
                pipeline_init(),
                CollectionReaderAnnotator(descriptor=kinect_config),
                ImagePreprocessorAnnotator("ImagePreprocessor"),
                PointcloudCropAnnotator(),
                PlaneAnnotator(),
                PointCloudClusterExtractor(),
                MyFirstAnnotator(),
            ])
        return seq
```

Start that analysis engine and observe the output of your console where you have started RoboKudo. You should there see an output like the following:

```bash
robokudo  INFO  2022-06-30 19:08:54,052      my_first_annotator.py   in 24 MyFirstAnnotator.update    Cloud size is: 108262
```

Note: You might have to observe this directly after starting up RoboKudo in the case that tf Messages are spamming the output.
