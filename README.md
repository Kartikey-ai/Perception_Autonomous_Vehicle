# EUFS Autonomous Simulation

**https://gitlab.com/eufs/eufs_sim**

ROS/Gazebo simulation packages for driverless FSAE vehicles.

![simulation](https://eufs.eusa.ed.ac.uk/wp-content/uploads/2018/05/eufsa-sim.jpg)

### Contents
1. [Install Prerequisites](#requirements)
2. [Compiling and running](#compiling)
3. [Sensors](#sensors)

## Setup Instructions
### 1. Install Prerequisites <a name="requirements"></a>
##### - Install Ubuntu 16.04 LTS
##### - Install [ros-kinetic-desktop-full](http://wiki.ros.org/kinetic/Installation)
##### - Install ROS packages:
* ros-kinetic-ackermann-msgs
* ros-kinetic-twist-mux
* ros-kinetic-joy
* ros-kinetic-controller-manager
* ros-kinetic-robotnik-msgs
* ros-kinetic-velodyne-simulator
* ros-kinetic-effort-controllers
* ros-kinetic-velocity-controllers
* ros-kinetic-joint-state-controller
* ros-kinetic-gazebo-ros-control

Or if you are lazy like my here's a one-liner.
```
sudo apt-get install ros-kinetic-ackermann-msgs ros-kinetic-twist-mux ros-kinetic-joy ros-kinetic-controller-manager ros-kinetic-robotnik-msgs ros-kinetic-velodyne-simulator ros-kinetic-effort-controllers ros-kinetic-velocity-controllers ros-kinetic-joint-state-controller ros-kinetic-gazebo-ros-control ros-kinetic-robotnik-msgs
```


### 2. Compiling and running <a name="compiling"></a>

Create a workspace for the simulation if you don't have one:
```mkdir -p ~/ros/eufs_ws/src```
Copy the contents of this repository to the `src` folder you just created.

Navigate to your workspace and build the simulation:
```
cd ~/ros/eufs_ws
catkin_make
```
_Note:_ You can use `catkin build` instead of `catkin_make` if you know what you are doing.

To enable ROS to find the EUFS packages you also need to run
```source /devel/setup.bash```
_Note:_ source needs to be run on each new terminal you open. You can also include it in your `.bashrc` file.

Now you can finally run our kickass simulation!!
```roslaunch eufs_gazebo small_track.launch```

An easy way to control the car is via
```roslaunch robot_control rqt_robot_control.launch```

### 3. Additional sensors <a name="sensors"></a>
Additional sensors for testing are avilable via the `ros-kinetic-robotnik-sensor` package. Some of them are already defined in `eufs_description/robots/eufs.urdf.xarco`. You can simply commment them in and attach them appropriately to the car.


**Sensor suit of the car by default:**

* VLP16 lidar
* ZED Stereo camera
* IMU
* GPS
* odometry


![LiDAR View](https://user-images.githubusercontent.com/67441175/125790316-02379bbc-f311-4f8a-94c7-64c193623c8e.jpeg)
![LiDAR View](https://user-images.githubusercontent.com/67441175/125790318-7b978ded-bfc4-4869-95d5-54ff367d3175.jpeg)



### Lidar based

This is completly based on lidar data (velodyne 16) and therefore there is a need to install pcl in your system for point cloud processong and conversion of point cloud to cones cluster.

### Commands

- roslaunch eufs_gazebo small_track.launch
- roslaunch robot_control robot_control.launch
- rosrun pointcloud_process final_script.py
