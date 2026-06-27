---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/reading-data-from-a-database|Reading data from a Database]]"
---

# Database Storage

RoboKudo can use MongoDB to store and replay perception data. The source tutorial frames this as a development aid because replaying from a database can be faster than live sensors or bag files and can avoid some transform lookup problems.

## Flow

- Start RoboKudo with the storage analysis engine.
- Wait until the system initializes.
- Feed sensor data from a bag file or robot.
- Close RoboKudo after data is recorded.
- Read stored data back through a storage-oriented analysis engine.

## Related

- [[wiki/workflows/use-database-storage|Use Database Storage]]
- [[wiki/concepts/pipelines|Pipelines]]
- [[wiki/reference/commands|Commands]]
