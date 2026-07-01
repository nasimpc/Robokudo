---
type: workflow
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
---

# Run Demo Pipeline

Use this workflow to start the built-in `demo` analysis engine and play test sensor data.

## Steps

1. Download the test bag or ROS 2 archive from the source page.
2. Start `roscore` for ROS 1; skip it for ROS 2.
3. Run RoboKudo with `_ae=demo`.
4. Play the bag in a second terminal.
5. Focus the 2D visualizer and use left/right arrows or `n`/`p` to inspect annotator outputs.

## Commands

See [[reference/commands|Commands]] for the ROS 1 and ROS 2 command blocks.

## Source

- [[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]
