---
type: concept
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/reading-data-from-a-database|Reading data from a Database]]"
---

# Database Storage

RoboKudo can record and replay perception data through MongoDB instead of reading directly from a robot or bag file. The source describes this as useful for faster development and for avoiding some transform lookup problems.

The storage workflow starts RoboKudo with the `storage` analysis engine, plays a ROS bag, triggers the visualizer storage action, and later runs `demo_from_storage` to read the stored data. Multiple scenes can be separated by setting `StorageWriter` and camera config database names.

## Related

- [[workflows/use-database-storage|Use Database Storage]]
- [[reference/commands|Commands]]
