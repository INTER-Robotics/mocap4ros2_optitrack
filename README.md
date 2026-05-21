# ROS2 Driver for Optitrack Motive

## Installation:

Clone the repository in your workspace:
```
git clone https://github.com/INTER-Robotics/mocap4ros2_optitrack
```
Install the dependencies:
```
vcs import < mocap4ros2_optitrack/dependency_repos.repos
```
Compile the workspace:
```
colcon build --symlink-install --cmake-args -DCMAKE_BUILD_TYPE=Release
```
Source workspace:
```
source install/setup.bash
```

## Configuration:

Modify the file "mocap4ros2_optitrack/mocap4r2_optitrack_driver/config/mocap4r2_optitrack_driver_params.yaml" in accordance to your setup.

## Usage:

Launch optitrack system:
```
ros2 launch mocap4r2_optitrack_driver optitrack2.launch.py
```
Check that Optitrack configuration works fine and is connected. 

If everything seems correct, you should activate node, as the driver is a lifecycle node. 
```
ros2 lifecycle set /mocap4r2_optitrack_driver_node activate
```
RViz:
```
ros2 launch mocap4r2_marker_viz mocap4r2_marker_viz.launch.py mocap4r2_system:=optitrack
```

## Possible errors
If connection is established (in the bash it is indicated) but you are not able to see your rigid bodies and/or markers in RViz it is a problem with the Firewall Configuration. You should allow the connection through the appropiate ports in both, Motive (Windows) and ROS2 Driver (Ubuntu) machines. 
