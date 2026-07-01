---
type: converted-source
status: generated
created: 2026-06-28
updated: 2026-06-28
source_file: raw/sources/robokudo-docs/create_your_own_package.html
source_type: html
---

<!-- Generated markdown mirror. Do not edit manually; regenerate from the HTML source. -->
# Create your own RoboKudo package

RoboKudo offers methods to separate your own perception routines, analysis engines and much more into separate ROS packages. Let us start by creating a package called`rk_tutorial`. Make sure you are in the source folder of a catkin workspace and run:

**ROS 1**

```bash
rosrun robokudo rk_create_package rk_tutorial
```

**ROS 2**

```bash
ros2 run robokudo_ros rk_create_package rk_tutorial

# make sure to source your virtualenv before if you're using one
pip install -e ./rk_tutorial
```

The script will create a new ROS package that has the structure needed for RoboKudo:

**ROS 1**

```
'rk_tutorial'
|-src                       -> code and configuration base
   |-rk_tutorial            -> name of your package
      |-annotators
      |-descriptors
         |-analysis_engines -> Pipeline/Analysis Engine definitions (Behaviour Trees)
|-package.xml               -> catkin package xml
|-setup.py                  -> python install information
|-CMakeLists.txt            -> CMake file
```

**ROS 2**

```
'rk_tutorial'
|-rk_tutorial                   -> code and configuration base
  |-annotators
  |-descriptors
     |-analysis_engines -> Pipeline/Analysis Engine definitions (Behaviour Trees)
|-package.xml                   -> package metadata
|-setup.py                      -> python install information
|-setup.cfg                     -> python executable information for ros2 run
```

You can now add your own annotators and analysis engines(also called pipelines) that can use any component defined in the RoboKudo core package. If you want `rk_tutorial` to depend on other RoboKudo packages add them to the `package.xml` (ROS1 & ROS2) and `CMakeLists.txt` (ROS1 only).

To verify your new package, let us create your very first own analysis engine. Copy over the demo analysis engine from the RoboKudo core package (note the renaming of the file):

**ROS 1**

```bash
cd ~/robokudo_ws/src/
cp ./robokudo/robokudo/src/robokudo/descriptors/analysis_engines/demo.py \
    ./rk_tutorial/src/rk_tutorial/descriptors/analysis_engines/my_demo.py
```

**ROS 2**

```bash
cd ~/ros2_ws/src/
cp ./robokudo/robokudo/src/robokudo/descriptors/analysis_engines/demo.py \
    ./rk_tutorial/rk_tutorial/descriptors/analysis_engines/my_demo.py
```

Open `my_demo.py` and adapt in the `name` method the return value to `'my_demo'` instead of `'demo'`.

Please make sure to rebuild and source your workspace as described below:

**ROS 1**

```bash
cd ~/robokudo_ws
catkin build
source ~/robokudo_ws/devel/setup.bash
```

**ROS 2**

```bash
cd ~/ros2_ws
colcon build --merge-install
source ~/ros2_ws/install/setup.bash
```

After that, you can start your own analysis engine by executing:

**ROS 1**

```bash
rosrun robokudo main.py _ae=my_demo _ros_pkg=rk_tutorial
```

**ROS 2**

```bash
ros2 run robokudo_ros main _ae=my_demo _ros_pkg=rk_tutorial
```

It should show the same result as in the previous tutorial.
