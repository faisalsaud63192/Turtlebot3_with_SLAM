# Turtlebot3_with_SLAM
## Requirements:
* Use Turtlebot3 with SLAM to create a map and save the map
## Steps: 
1. I installed Ubuntu 18.04 and ROS Melodic with Gazebo and Rviz Simulator ([see](https://github.com/faisalsaud63192/Robot_Arm_Control_in_ROS/blob/main/README.md)) .
* I will Install ROS 1 on Remote PC using the following comand
-  `sudo apt update`
-  `sudo apt upgrade`  
-  `wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh`
-  `chmod 755 ./install_ros_melodic.sh `
-  `bash ./install_ros_melodic.sh` 
2. Install Dependent ROS 1 Packages
- `sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers`
  3. Install TurtleBot3 Packages
  - ` sudo apt-get install ros-melodic-dynamixel-sdk`
  - `sudo apt-get install ros-melodic-turtlebot3-msgs` 
  - `sudo apt-get install ros-melodic-turtlebot3`
  4. Install Simulation Package where the TurtleBot3 Simulation Package requires turtlebot3 and turtlebot3_msgs packages as prerequisite. Without these prerequisite packages, the Simulation cannot be launched.
  - `cd ~/catkin_ws/src/`
  - `git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`
  - `cd ~/catkin_ws && catkin_make`
  - Then write `cd` or open new terminal and write `source ~/catkin_ws/devel/setup.bash`
  5. Launch Simulation World.
  - Empty world with a robot called "burger" 
  - `export TURTLEBOT3_MODEL=burger`
  - `roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch` 
  
  ![burger robot](https://github.com/faisalsaud63192/Turtlebot3_with_SLAM/blob/main/empty%20world%20burger.png)
  
  - TurtleBot3 World with a robot called "waffle"
  - `export TURTLEBOT3_MODEL=waffle`
  - `roslaunch turtlebot3_gazebo turtlebot3_world.launch`

 ![1](https://github.com/faisalsaud63192/Turtlebot3_with_SLAM/blob/main/1.png)
 
 ![waffle](https://github.com/faisalsaud63192/Turtlebot3_with_SLAM/blob/main/waffle.png)
 
 6. I will use TurtleBot3 World with a robot called "waffle" to creat the map and save it.
 - Lunch the Gazebo environment with waffle robot `export TURTLEBOT3_MODEL=waffle` then `roslaunch turtlebot3_gazebo turtlebot3_world.launch`
 - Open new terminel to Run SLAM Node `export TURTLEBOT3_MODEL=waffle` then `roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`
 - Open a new terminal to control the waffel robot and scan the area using lidar sensor `export TURTLEBOT3_MODEL=waffle` then ` roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`. (in the terminal we will control the robot direction using W,A,S,D,X keybored keys).
 - keybored keys  W: Forward,  A: Left, S: Stop, D: Right, X: Backward.
 
 ![2](https://github.com/faisalsaud63192/Turtlebot3_with_SLAM/blob/main/2.png)
 
 ![rviz](https://github.com/faisalsaud63192/Turtlebot3_with_SLAM/blob/main/rviz_1.png)
 
 7. When the map is created successfully in Rviz, open new terminal and save it using the command `rosrun map_server map_saver -f ~/map`
 
 ![3](https://github.com/faisalsaud63192/Turtlebot3_with_SLAM/blob/main/3.png)
 
 ![map](https://github.com/faisalsaud63192/Turtlebot3_with_SLAM/blob/main/map1.png)
 
 - simulation video in 1_Turtlebot3 with SLAM.webm file
 
 -Task is done
 
