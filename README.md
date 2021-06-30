# Use-Turtlebot3-and warehouse_simulation_toolkit-with-SLAM-approach-on-ROS
Use Turtlebot3 and warehouse_simulation_toolkit with SLAM approach to create and save a map using ROS tools; RViz, and Gazebo

Set the Environment:
  1. Download and Install Ubuntu 18.04 on a Virtual Machine.
  2. ROS-Melodic must be installed on an Ubuntu 18.04 virtual machine following this link: https://wiki.ros.org/melodic/Installation/Ubuntu
  3. Create a workspace named catkin_ws (or another name, however, make sure to change the name in the next steps too!) following this link: http://wiki.ros.org/catkin/Tutorials/create_a_workspace
  4. Install TurtleBot3 Packages inside catkin_ws:
  ```$ cd ~/catkin_ws/src/
  $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/DynamixelSDK.git
  $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
  $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git
  $ cd ~/catkin_ws && catkin_make
  $ echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
  ```
  5. Set TurtleBot3 Model Name (Waffle_pi):
  ```
  $ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
  ```
  
Turtlebot3 SLAM Simulation:
  1. Install Gazebo simulation package:
  ```$ cd ~/catkin_ws/src/
  $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
  $ cd ~/catkin_ws && catkin_make
  ```
  2. Launch simulation world with Gazebo:
  ```$ export TURTLEBOT3_MODEL=waffle_pi
  $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
  ```
  3. Run SLAM node:
  ```$ export TURTLEBOT3_MODEL=waffle_pi
  $ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
  ```
  4. Tele_Operate TurtleBot3:
  ```$ export TURTLEBOT3_MODEL=waffle_pi
  $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
  ```
  5. Save the the map:
  ```
  $ rosrun map_server map_saver -f ~/map
  ```
  
  
  
A warehouse_simulation_toolkit SLAM Simulation:
1. Add a Prerequisite ROS package:
```
$ sudo apt-get install ros-melodic-hector-trajectory-server ros-melodic-slam-gmapping ros-melodic-navigation
```
2. Clone the repository:
```$ cd ~/catkin_ws/src
$ git clone https://github.com/wh200720041/warehouse_simulation_toolkit.git
$ cd ..
$ catkin_make
$ source ~/catkin_ws/devel/setup.bash
```
3. Launch simulation world:
```
$ roslaunch warehouse_simulation warehouse_simulation.launch
```
4. Navigation Simulation with RViz:
   click 2d nav goal button on rviz (Upper bar), then choose the required point.

  



