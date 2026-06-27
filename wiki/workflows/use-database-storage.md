---
type: workflow
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/reading-data-from-a-database|Reading data from a Database]]"
---

# Use Database Storage

Use this workflow to record perception data into MongoDB and replay it for development.

## Steps

1. Install and start MongoDB.
2. Start RoboKudo with the storage analysis engine.
3. Wait for initialization.
4. Feed sensor data from the sample bag file or a live robot.
5. Close RoboKudo after recording.
6. Start the relevant storage-reading analysis engine to replay stored data.

## Notes

If using sensors other than the tutorial sample bag, adapt the storage analysis engine, collection reader, and camera config.

## See Also

- [[wiki/concepts/database-storage|Database Storage]]
- [[wiki/reference/commands|Commands]]
