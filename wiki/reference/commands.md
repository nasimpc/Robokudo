---
type: reference
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[wiki/sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[wiki/sources/reading-data-from-a-database|Reading data from a Database]]"
  - "[[wiki/sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# Commands

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

## Database Storage

```bash
apt install mongodb
rosrun robokudo main.py _ae=storage
rosbag play test.bag
```

## Docker

```bash
sudo docker build --no-cache --pull -t robokudo_container .
xhost local:root
docker run -it --net=host --gpus all \
  --env="NVIDIA_DRIVER_CAPABILITIES=all" \
  --env="DISPLAY" \
  --env="QT_X11_NO_MITSHM=1" \
  --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
  robokudo_container bash
```

## Related

- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
- [[wiki/concepts/pipelines|Pipelines]]
