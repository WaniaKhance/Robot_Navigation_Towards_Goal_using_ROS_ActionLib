# Robot Navigation Towards Goal using ROS ActionLib


## Server and Client Communication - Intelligent Systems and Robotics

* Introduction
  ------------

In this project, we described a system which allows robot to navigate through the environment in order to reach its goal. This system design is based on action server and action client communication via a ‘ROS Action Protocol’. To implement this system, we have used ROS Actionlib, which provides servers a standardized interface to execute long-running goals and interface to client for making requests. We have specified three basic actions including goal, feedback and result with which client and servers communicates. In this system design, the request for goal and its execution will be made from client’s end to server side via function calls and callbacks.


* Python Files Description
  ------------

The description for each program file is as follows:

1.	Navigate2D.action: This file defines the type and format of the goal, result, and feedback topics for the action. So, we have defined the goal as a Point using gemotery_msgs as it contains the 3D position of a point, feedback and result definition with float message type.

2.	Robot_point_publisher.py: the current point of robot with three axis coordinates will be asked in order to be published on the topic named as ‘robot/point’.

3.	Action_client.py: action messages are defined that specifies goal, feedback and result. The desired location of user will be sent to the action server in order to navigate the robot towards its goal. The response from server will be received as a feedback and result. 

4.	Action_server.py: to perform communication with client, action messages are defined here as well. To obtain the goal of the robot, the topic ‘robot/point’ will be subscribed. On a client call, the current location of the user and goal point are used to calculate the distance between them. A threshold is also defined that allows robot to move with the specific speed and notifies the client about the remaining distance through feedback. As soon as it reaches the threshold value, it stops the execution and returns the time taken during the navigation process.  

5.	Package by Catkin: build a package that depends on actionlib API. We have added actionlib_msgs in package section, action file in the action_files section and action_lib in the dependent messages section of CMakeLists.txt. Also, the actionlib_msgs and actionlib dependencies were added in the package.xml.   


* Requirements
  ------------

1.	Linux OS - Ubuntu 20.04 

2.	Python 3.7 or above 


* Output Results
  ------------
  
To run the above python files, the instructions are as follows:

1.	For building code and package files in catkin workspace, use catkin_make command.
2.	Run the roscore for ros nodes communication.
3.	Open terminal windows and source the setup.bash file in each window.
4.	Now, python files are ready to be executed.


![alt text](https://github.com/WaniaKhance/Robot_Navigation_Towards_Goal_using_ROS_ActionLib/blob/main/Picture5.png?raw=true)


