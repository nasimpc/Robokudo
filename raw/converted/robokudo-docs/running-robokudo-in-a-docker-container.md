---
type: converted-source
status: generated
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/docker_rk.html
source_type: html
---

<!-- Generated markdown mirror. Do not edit manually; regenerate from the HTML source. -->

# Running RoboKudo in a Docker container

In this tutorial, we are providing instructions on how to start RoboKudo in a docker container which is currently only working on NVIDIA GPUs. So, before jumping to the tutorial please make sure that you’ve installed the NVIDIA container toolkit.

If you like to run RoboKudo from docker then at the very beginning you have to build the RoboKudo docker image by using the Dockerfile from the RoboKudo repository (ROS1, ROS2) which contains all the necessary dependencies and setup instructions.

Warning

This tutorial is only tested for ROS 1.

In order to build the Docker container, please go to the robokudo repository on your filesystem and then execute the following command:

```bash
sudo docker build --no-cache --pull -t robokudo_container .
```

Please wait until the installation has finished completely.

Now, you have to give the permission to the container to access the host’s machine X Server for graphics support. Although, there are several ways to get graphics to work from inside of a docker container, the simplest (least secure) of the approaches is to execute xhost local:root which allows docker to use the host machine’s X11 socket. For that open a new terminal to run xhost local:root.

Note

You only have to run xhost local:root once each time when you log into the machine. These settings persist per login session.

After that, you can start roscore on your host machine in a new terminal. By default, we will start RoboKudo such that it can access the network of your Host to access the roscore.

roscore no longer exists in ROS 2. You can continue with the tutorial without starting it.

Now, it’s time to run the docker image that you build earlier. Since RoboKudo uses a 3D visualization window, we have to pass some additional information to the start of the docker container to be able to run the RoboKudo 3D window properly. For that use the below docker run command:

```bash
docker run -it --net=host --gpus all --env="NVIDIA_DRIVER_CAPABILITIES=all" --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" robokudo_container bash
```

Note

The following step is for NVIDIA graphics card which is the recommended to open the RoboKudo 3D visualization window.

If you’re inside of the docker container, you can run RoboKudo by the following command:

```bash
rosrun robokudo main.py
```

```bash
ros2 run robokudo_ros main
```

Then the RoboKudo 3D visualization windows should be pop-up like shown in the previous image.

Note

If you are running RoboKudo on a laptop with a NVIDIA GPU, you might run into problems with docker and GPU (GL) workloads. Either switch your GPU to ‘discrete mode’ in the BIOS or use the prime-select tool from the nvidia-prime package before starting RoboKudo via Docker. Example call: sudo prime-select nvidia
