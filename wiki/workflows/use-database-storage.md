---
type: workflow
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/reading-data-from-a-database|Reading data from a Database]]"
---

# Use Database Storage

Use this workflow to store perception input in MongoDB and replay it later.

## Steps

1. Install MongoDB as described for the target ROS version.
2. Start RoboKudo with `_ae=storage`.
3. Play the test bag or ROS 2 bag.
4. In the visualizer, trigger storage from the `ImagePreprocessor` output as the source page describes.
5. Start RoboKudo with `_ae=demo_from_storage` to read from storage.
6. For multiple scenes, configure `StorageWriter.Descriptor().parameters.db_name` and the `config_mongodb_playback.py` camera config.

## Source

- [[sources/reading-data-from-a-database|Reading data from a Database]]
