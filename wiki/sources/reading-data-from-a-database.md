---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/database_storage.html
source_title: Reading data from a Database
source_type: html
ingested: 2026-06-27
sources: []
---

# Reading data from a Database

This tutorial uses MongoDB to store and replay perception data instead of reading directly from live sensors or bag files.

## Key Points

- Database-backed replay can speed development and avoid some transform lookup problems.
- MongoDB is the database system used by the tutorial.
- The storage flow is: start RoboKudo with the storage analysis engine, wait for initialization, feed live or bagged sensor data, then close RoboKudo.
- The tutorial assumes the sample bag file from earlier tutorials unless the storage analysis engine, collection reader, and camera config are adapted.
- The later sections cover reading stored data and storing multiple scenes.

## Connected Pages

- [[wiki/workflows/use-database-storage|Use Database Storage]]
- [[wiki/concepts/database-storage|Database Storage]]
- [[wiki/concepts/pipelines|Pipelines]]
- [[wiki/reference/commands|Commands]]
