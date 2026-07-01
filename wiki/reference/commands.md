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

# Commands

This page collects command snippets from the source mirrors. Check the linked source before running commands in a live robot workspace.

## Test Data

```bash
curl https://robokudo.ai.uni-bremen.de/_static/test.bag --output ~/robokudo_ws/test.bag
curl https://robokudo.ai.uni-bremen.de/_static/test.tar.gz --output ~/Downloads/test.tar.gz
tar -xzf ~/Downloads/test.tar.gz -C ~/ros2_ws/
```

## Run Demo Pipeline

```bash
roscore
rosrun robokudo main.py _ae=demo
rosbag play ~/robokudo_ws/test.bag --loop
```

```bash
ros2 run robokudo_ros main _ae=demo
ros2 bag play ~/ros2_ws/test --loop
```

## Create Package

```bash
rosrun robokudo rk_create_package rk_tutorial
ros2 run robokudo_ros rk_create_package rk_tutorial
pip install -e ./rk_tutorial
```

```bash
cd ~/robokudo_ws
catkin build
source ~/robokudo_ws/devel/setup.bash
rosrun robokudo main.py _ae=my_demo _ros_pkg=rk_tutorial
```

```bash
cd ~/ros2_ws
colcon build --merge-install
source ~/ros2_ws/install/setup.bash
ros2 run robokudo_ros main _ae=my_demo _ros_pkg=rk_tutorial
```

## Query Handling

```bash
rosrun actionlib_tools axclient.py /robokudo/query
ros2 action send_goal /robokudo/query robokudo_msgs/Query '{<goal content as dict/json>}'
ros2 action send_goal /robokudo/query robokudo_msgs/Query "$(cat /path/to/your/query.json)"
```

## Advanced Query Test Client

```bash
python3 ~/ros2_ws/src/robokudo/robokudo/src/scripts/main.py _ae query_complex
ros2 bag play ~/ros2_ws/test --loop
python3 ~/ros2_ws/src/robokudo/robokudo/src/scripts/query_test_client.py
python3 ~/ros2_ws/src/robokudo/robokudo/src/scripts/query_test_client.py --preempt_timer=5.0
```

## Database Storage

```bash
apt install mongodb
rosrun robokudo main.py _ae=storage
rosbag play test.bag
ros2 run robokudo_ros main _ae=storage
ros2 bag play test/
rosrun robokudo main.py _ae=demo_from_storage
ros2 run robokudo_ros main _ae=demo_from_storage
```

## Docker

```bash
sudo docker build --no-cache --pull -t robokudo_container .
xhost local:root
docker run -it --net=host --gpus all   --env="NVIDIA_DRIVER_CAPABILITIES=all"   --env="DISPLAY"   --env="QT_X11_NO_MITSHM=1"   --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw"   robokudo_container bash
```

## Related

- [[reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
- [[concepts/pipelines|Pipelines]]
