---
type: converted-source
status: generated
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/configure_your_annotator.html
source_type: html
---

<!-- Generated markdown mirror. Do not edit manually; regenerate from the HTML source. -->

# Configure your Annotator

When applying computer vision methods, you are often faced with many parameters that need to be tweaked in order to adapt the algorithm to your use case.
RoboKudo supports parameterizing your Annotators very flexibly, so that you are able to define in your Analysis Engine how the Annotator should be parameterized.
This allows you to have specific parameters directly encoded in the Analysis Engine for your specific use case.

## Configuring the PointCloudCropAnnotator

To understand the concept of Annotator Parametrization, we will look at one of the standard RoboKudo Annotators: The PointCloudCropAnnotator.
If you open the corresponding sourcecode of that Annotator (robokudo/src/robokudo/annotators/pointcloud_crop.py), you will see a class called Descriptor in that Annotator:

```python
class PointcloudCropAnnotator(BaseAnnotator):
    """
    Crop a subset of points from a pointcloud data based on min/max X,Y,Z values.
    The crop is either done in sensor coordinates (default) or relative to the world frame.
    """

    class Descriptor(BaseAnnotator.Descriptor):
        class Parameters:
            def __init__(self) -> None:
                self.min_x: float = -2.0
                self.min_y: float = -2.0
                self.min_z: float = -9.0
                self.max_x: float = 2.0
                self.max_y: float = 2.0
                self.max_z: float = 3.0
                self.relative_to_world: bool = False  # Decide if the Crop should be done in the sensor/camera coordinates
                # or if the PC should be transformed with CASViews.VIEWPOINT_CAM_TO_WORLD first

        parameters = Parameters()  # overwrite the parameters explicitly to enable auto-completion
    
    ...
```

The Descriptor class is used to describe meta information about each Annotator. This also includes Parameters that are used during the execution of the Annotator.
Since the PointCloudCropAnnotator is cropping PointCloud data in 3D (x,y,z), we have multiple parameters defined which are used to check which points in the pointcloud should be left out.

If the default values do not fit your use case, you can easily set these parameters in your Analysis Engine.
We assume that you have completed the tutorial about the creation of your own RK package. Please go to your rk_tutorial folder and open your my_demo AnalysisEngine.

It should look like this:

```python
from rk_tutorial.annotators.my_first_annotator import MyFirstAnnotator

from robokudo.analysis_engine import AnalysisEngineInterface
from robokudo.annotators.collection_reader import CollectionReaderAnnotator
from robokudo.annotators.image_preprocessor import ImagePreprocessorAnnotator
from robokudo.annotators.plane import PlaneAnnotator
from robokudo.annotators.pointcloud_cluster_extractor import PointCloudClusterExtractor
from robokudo.annotators.pointcloud_crop import PointcloudCropAnnotator
from robokudo.descriptors import CrDescriptorFactory
from robokudo.idioms import pipeline_init
from robokudo.pipeline import Pipeline


class AnalysisEngine(AnalysisEngineInterface):
    def name(self) -> str:
        return "my_demo"

    def implementation(self) -> Pipeline:
        """Create a basic pipeline that does tabletop segmentation."""
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
            ]
        )
        return seq
```

We will now add the parametrization to the PointCloudCropAnnotator by simple instantiating the Descriptor from it and set the parameters.
After that, we pass the Descriptor to the constructor of the PointCloudCropAnnotator in the Analysis Engine:

```python
from rk_tutorial.annotators.my_first_annotator import MyFirstAnnotator

from robokudo.analysis_engine import AnalysisEngineInterface
from robokudo.annotators.collection_reader import CollectionReaderAnnotator
from robokudo.annotators.image_preprocessor import ImagePreprocessorAnnotator
from robokudo.annotators.plane import PlaneAnnotator
from robokudo.annotators.pointcloud_cluster_extractor import PointCloudClusterExtractor
from robokudo.annotators.pointcloud_crop import PointcloudCropAnnotator
from robokudo.descriptors import CrDescriptorFactory
from robokudo.idioms import pipeline_init
from robokudo.pipeline import Pipeline


class AnalysisEngine(AnalysisEngineInterface):
    def name(self) -> str:
        return "my_demo"

    def implementation(self) -> Pipeline:
        """Create a basic pipeline that does tabletop segmentation."""
        kinect_config = CrDescriptorFactory.create_descriptor("kinect_wo_tf")

        # Setting the parameters in the Descriptor of the PointCloudCropAnnotator
        pc_crop_descriptor = PointcloudCropAnnotator.Descriptor()
        pc_crop_descriptor.parameters.min_x = 0
        pc_crop_descriptor.parameters.max_x = 0.5
        pc_crop_descriptor.parameters.min_y = -0.5
        pc_crop_descriptor.parameters.max_y = 0.5
        pc_crop_descriptor.parameters.min_z = 0.8
        pc_crop_descriptor.parameters.max_z = 1.8


        seq = Pipeline("RWPipeline")
        seq.add_children(
            [
                robokudo.idioms.pipeline_init(),
                CollectionReaderAnnotator(descriptor=kinect_config),
                ImagePreprocessorAnnotator("ImagePreprocessor"),
                # Passing the Descriptor to the Annotator
                PointcloudCropAnnotator(descriptor=pc_crop_descriptor),
                PlaneAnnotator(),
                PointCloudClusterExtractor(),
                MyFirstAnnotator(),
            ])
        return seq
```

If you start this Analysis Engine, you should now see that the PointCloud in the 3D Visualizer of the PointcloudCropAnnotator is significantly smaller.

## Configuring your own Annotator

After seeing the example from the PointCloudCropAnnotator, add some parameters to your MyFirstAnnotator.
The key steps are:

Add a Descriptor class into your Annotator which has a Parameters subclass.

Change the constructor of your Annotator so that it takes a descriptor argument. This argument should then be passed to the super().__init__ call of your MyFirstAnnotator. __init__ method. Check out the PointCloudCropAnnotator source for an example.

Create a Descriptor instance of your MyFirstAnnotator in your Analysis Engine and pass it to the constructor of MyFirstAnnotator when creating your pipeline.

If you want to access the parameters inside your Annotator code, you can use self.descriptor.parameters.NAME_OF_PARAMETER. For example, in PointCloudCropAnnotator the min_x Parameter is accessed by self.descriptor.parameters.min_x.
