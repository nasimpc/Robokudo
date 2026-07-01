---
type: reference
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[sources/configure-your-annotator|Configure your Annotator]]"
  - "[[sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
  - "[[sources/reading-data-from-a-database|Reading data from a Database]]"
  - "[[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# Code Entrypoints

Important code paths, classes, and APIs mentioned in the source mirrors.

## Analysis Engines

- `robokudo/descriptors/analysis_engines/demo.py` - built-in demo pipeline.
- `robokudo/descriptors/analysis_engines/storage` - storage pipeline name used for recording data.
- `demo_from_storage` - analysis engine used to read stored data.
- `query_complex.py` - ROS 2 advanced query example.
- `rk_tutorial/descriptors/analysis_engines/my_demo.py` - custom copied demo pipeline in the package tutorial.

## Annotators

- `BaseAnnotator` - base class used by custom annotators.
- `CollectionReaderAnnotator` - reads camera, bag, or storage input.
- `ImagePreprocessorAnnotator` - prepares image and point cloud data.
- `PointcloudCropAnnotator` - demonstrates descriptor-based configuration.
- `PlaneAnnotator`, `PointCloudClusterExtractor`, `ClusterColorAnnotator` - standard pipeline annotators from the tutorials.
- `QueryAnnotator` - starts the `/robokudo/query` action server and places queries into the CAS.

## Query APIs

- `robokudo_msgs/ObjectDesignator` - object-centric query/result data.
- `robokudo_msgs/Query` - ROS action type for the query interface.
- `BBIdentifier.QUERY_ANSWER` - ROS 1 blackboard key for query answers.
- `QueryHandler.send_answer` - ROS 2 helper used to send query answers.
- `catch_and_raise_to_blackboard` - decorator used to surface query failures.

## Storage APIs

- `StorageWriter.Descriptor().parameters.db_name` - database selection for stored scenes.
- `config_mongodb_playback.py` - camera config used when reading a specific MongoDB database.
