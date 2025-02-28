# Differential picker robot 
 This project involves the development of an autonomous differential drive robot equipped with a pick-and-place arm. The robot is designed to navigate dynamic environments, perform SLAM (Simultaneous Localization and Mapping), and execute pick-and-place tasks autonomously. The project leverages ROS (Robot Operating System), Gazebo for simulation, and MoveIt for motion planning.

Features
Autonomous Navigation: The robot can navigate through dynamic environments using SLAM.

Pick and Place Arm: The robot is equipped with a manipulator arm for picking and placing objects.

Simulation: The robot's performance is tested in a simulated environment using Gazebo.

Motion Planning: MoveIt is used for motion planning and control of the robotic arm.

Modular Design: The robot's components are designed using Fusion 360 and converted into URDF for simulation.

Hardware Components
Differential Drive System: For locomotion.

Pick and Place Arm: For manipulating objects.

LiDAR Sensor: For environment mapping and obstacle detection.

Software Components
ROS Noetic: The primary framework for robot control and simulation.

Gazebo: For simulating the robot in a realistic environment.

MoveIt: For motion planning and control of the robotic arm.

Fusion 360: For designing the 3D model of the robot.

Ubuntu 20.04: The operating system used for development.

Setup Instructions
# **3D model built in Fusion 360 converted to Urdf file**
![alt text](https://github.com/Shyjojose/differential_picker_robot/blob/main/screenshot/Screenshot%202024-06-27%20162012.png)

    $ cd ~/catkin_ws/src/
    $ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
    $ cd ~/catkin_ws && catkin_make
## Easy install of the project file

     $ cd ~/catkin_ws/src/
     $ git clone  https://github.com/Shyjojose/differential_pricker_robo.git
     $ cd ~/catkin_ws && catkin_make
     $ source devel/setup.bash
 
## launching riviz for map making 

    $ roslaunch finaldesign_description  gazebo.launch

![alt text]([screnshot/SCREEN2.png](https://github.com/Shyjojose/differential_picker_robot/blob/main/screenshot/SCREEN2.png))

    $ roslaunch finaldesign_description  slam.launch

! need to add displays in the riviz tool 

![alt text]([screnshot/screen3.png](https://github.com/Shyjojose/differential_picker_robot/blob/main/screenshot/screen3.png))

click add-> By display type> RobotModel <br>
click add-> by topic -> map <br>
click add-> by topic -> LaserSCan <br>

    $ roslaunch finaldesign_description keyboard.launch

## run robot to make map and save it use below code 

    $ rosrun map_server map_saver -f ~/map

## for navigation run gazebo.launch then navigation.launch in different terminal 

    $ roslaunch finaldesign_description  gazebo.launch
    $ roslaunch finaldesign_description navigation.launch map_file:=$HOME/map.yaml

 ## need to add the displays for the riviz tool
![alt text]([screnshot/screen4.png](https://github.com/Shyjojose/differential_picker_robot/blob/main/screenshot/screen4.png))

click add-> By display type> RobotModel <br>
click add-> by topic -> map <br>
click add-> by topic -> LaserSCan <br>
click add-> by topic -> /global_costmap ->/costmap-> map <br>
click add-> by topic -> /local_costmap ->/costmap-> map <br>
click add-> by topic -> LaserSCan <br>
click add-> by topic -> /NavfnROs ->/plan ->path <br>
set the 2d post estimate and also give final 2d navigaton goal <br>


 # moveit_arm movement

launch gazebo with moveit in riviz

    $ roslaunch moveit demo_gazebo.launch


![alt text]([screnshot/screen5.png](https://github.com/Shyjojose/differential_picker_robot/blob/main/screenshot/screen5.png))

click Planning-> select Planning group arm -> start state intitial -> goal state final <br>
click Planning -> select planning group grab -> start state random -> goal state random <br>
clinck plan and execute 



