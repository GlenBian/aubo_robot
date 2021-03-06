AUBO Robot

ROS-Industrial aubo_robot meta-package. See the ROS wiki page (http://wiki.ros.org/) for compatibility information and other more information.

This repository provides ROS support for the AUBO robots. This repo holds source code for indigo and kinetic. The corresponding robot controller software version is V4. For those versions < V4 see: http://wiki.ros.org/aubo_robot

Installation from Source
For the latest features and developments you might want to install from source.

First set up a catkin workspace (see this tutorials).
Then clone the repository into the src/ folder. It should look like /path/to/your/catkin_workspace/src/aubo_robot.
Make sure to source the correct setup file according to your workspace hierarchy, then use catkin_make to compile.

In order to make the robot work well, you need to install some packages related to MoveIt and industrial_core repository.

MoveIt! with a simulated robot
You can use MoveIt! to control the simulated robot.

For setting up the MoveIt! nodes to allow motion planning run:

roslaunch <robot_name>_moveit_config/launch/demo.launch

Then, select "Interact" and move the end-effector to a new goal 

In RVIZ, "Motion Planning" -> "Plan and Execute" to send trajectory to the sim robot  

Exit RViz and Ctrl-C the demo.launch window 


Usage with real Hardware
When operating an AUBO robot under ROS-Industrial control, make certain that no one is within the robot workspace and the e-stop is under operator control.

Don't forget to source the correct setup shell files and use a new terminal for each command!

To bring up the real robot, run:

roslaunch <robot_name>_moveit_config moveit_planning_execution.launch sim:=false robot_ip:=<robot's IP> 

Move the robot around manually (using a teach-pendant or similar method). 

Verify that the joint positions in RViz match the physical robot configuration. 

Repeat for every joint and orientation. 

CAUTION:
Mistakes made during this verification step can result in dangerous collisions. Experiment with using the MoveIt planning environment to command trajectories with the real robot. Be certain that an E-stop is close by whenever commanding robot motion. 
