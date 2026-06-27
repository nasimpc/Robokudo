---
type: converted-source
status: generated
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/database_storage.html
source_type: html
---

<!-- Generated markdown mirror. Do not edit manually; regenerate from the HTML source. -->

# Reading data from a Database

Instead of reading data directly from the running robot or from bag files, it is also possible to retrieve them from a database. This is usually faster for development and can also help with tf lookup problems. We use MongoDB as our database system.

Please make also sure that you have downloaded the ROS bag file from the previous tutorials and noted the location where you stored it.

## Prerequisites

Make sure to install MongoDB on your machine.
On Ubuntu, this can be done with:

```bash
apt install mongodb
```

Follow the official installation instructions for Ubuntu 24.04 (Noble).
Make sure to also start the service after the installation as indicated in the corresponding section in the documentation.

## Storing data: Idea

The overall idea of using the database storage and to prepare the necessary data import is as follows:

Start RoboKudo with the storage AE

Wait until it is fully initialized

Run the bag file with data you want to store in the DB OR get live sensor data from a real robot.

Close RoboKudo

Note

In the following, we will assume that you go through this tutorial with our test bag file. If you want to read data from other sensors, please look into the storage AE and adapt the CollectionReader and Camera config to your use case.

## Storing data: Let’s try it out

Start a roscore and RoboKudo and then feed in the sensor data that shall be recorded.
Please note, that after starting RoboKudo, you should switch with the visualizer the arrow keys to show the ImagePreprocessor. This allows you to see the data that has been recorded.

```bash
roscore
rosrun robokudo main.py _ae=storage # wait until initialized. Go to ImagePreprocessor in the Visualizer window

# Get some sensor data. In this example, from a ros bag
rosbag play test.bag
```

```bash
ros2 run robokudo_ros main _ae=storage # wait until initialized. Go to ImagePreprocessor in the Visualizer window

# Get some sensor data. In this example, from a ros bag
ros2 bag play test/
```

When the data is captured, close RoboKudo.
You can either see that the bag file play command has finished or you just cancel if you have recorded enough data for your liking.

Note

If you are not sure if data is read in, you can also check that the Pipeline in the Behaviour Tree is changing and getting data in the CollectionReader with the following command:

```bash
rosrun rqt_py_trees rqy_py_trees
```

```
py-trees-tree-viewer
```

## Reading data

Simply use any Analysis Engine (robokudo/descriptors/analysis_engines) and set it to use the Storage Interface in the CollectionReader.

Example:

```bash
rosrun robokudo main.py _ae=demo_from_storage
```

```bash
ros2 run robokudo_ros main _ae=demo_from_storage
```

The key change in the AE mentioned above, is highlighted here:

```
cr_storage_config = CrDescriptorFactory.create_descriptor("mongo")

seq = Pipeline("StoragePipeline")
seq.add_children(
    [
        ClearAnnotatorOutputs(),
         # Please note the descriptor argument, which gets the storage config
        CollectionReaderAnnotator(descriptor=cr_storage_config),
        ....
```

## Bonus: Store and read multiple scenes in your database

If you are frequently switching between the scenes that you need to work on, you can parametrize the CollectionReaderAnnotator and the StorageWriter to use specific data in your database.
An example for this could be, that you have multiple ROS bag files with different object setups or use cases and you want to store all of them in your database.

To record data to a different database, create a StorageWriter.Descriptor(), set parameters.db_name on it and pass the Descriptor to your StorageWriter initialization in the Analysis Engine (see our Tutorial on configuring your Annotator ).
To read from a specific database, adjust the db_name parameter in the CameraConfig of config_mongodb_playback.py in robokudo/descriptors/camera_configs.

- Reading data from a Database
- Prerequisites
- Storing data: Idea
- Storing data: Let’s try it out
- Reading data
- Bonus: Store and read multiple scenes in your database
