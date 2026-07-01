---
type: concept
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[sources/configure-your-annotator|Configure your Annotator]]"
  - "[[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
---

# Annotators

Annotators are reusable behavior-tree nodes that perform perception work. They commonly inherit from `BaseAnnotator`, implement `update`, read inputs from the CAS, and write annotations or visualization output.

The custom annotator tutorial builds `MyFirstAnnotator`, which reads a point cloud from the CAS and logs its size. The pipeline tutorials show standard annotators such as `CollectionReaderAnnotator`, `ImagePreprocessorAnnotator`, `PointcloudCropAnnotator`, `PlaneAnnotator`, `PointCloudClusterExtractor`, and `ClusterColorAnnotator`.

## Related

- [[concepts/common-analysis-structure|Common Analysis Structure]]
- [[concepts/annotator-configuration|Annotator Configuration]]
- [[workflows/create-annotator|Create Annotator]]
