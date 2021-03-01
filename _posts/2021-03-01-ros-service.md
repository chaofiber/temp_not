---
title: "ROS services"
excerpt_separator: "<!--more-->"
categories:
  - Tech
tags:
  - ros
classes: wide
---

- ROS services
  - Request/response communication between nodes is realized with services. (One node is service client, and the other node is service server)
  - Similar in structure to messages, services are defined in `.srv` files.
    - request part and the response part. This service will require some knowledge from its giver node and give information to the receiver node.
  - `rosservice list` : See the available services.
  - `rosservice type sevice_name`: we get the name of the service
  - `rosservice show roscpp_tutorials/TwoInts`: show the service definition.
  - `rosservice call ---`: call the service.
- ROS actions (actionlib)
  - Similar to service calls, but provide possibility to cancel the task/receive feedback on the progress.
  - Similar to structure to services, action are defined in `.action` files. Actions are implemented with a set of topics.
  - Action definition file consists of goal, result and feedback messages.
  - Topics and Services: the former is a one-way continuous data flow, and the latter is with short triggers or calculations.
- ROS time
  - Normally, ROS uses the PC's system clock as time source, for simulations or playback, it is convenient to work with a simulated time. (should always use the ROS time APIs)
  - `rosparam set use_sim_time true`
  - `ros::Time begin = ros::Time::now()`
  - `ros::Duration`
  - `ros::Rate`
- ROS bags
  - A format for storing message data, binary format with file extension `.bag`. Suited for logging and recording datasets for later visualization and analysis.
  - `rosbag record --all`: record topics in a bag. It will be saved automatically with the start data and time as prefix.
  - `rosbag info bag_name.bag`
  - `rosbag play bag_name.bag`
  - `rosbag play --rate 0.5 bag_name.bag`: rate is used to slow down the play (for simulate time only)
    - `--clock`: work with simulation time
    - `--loop`
- Debugging strategies
  - Compile and run code often to catch bugs early
  - Understand compilation and runtime error messages
  - Use analysis tools to check data flow (`rosnode info, rostopic echo, roswtf, rqt_graph` etc.)
  - Visualize and plot data (Rviz, RQT Multiplot etc)
  - Divide program into smaller steps and check intermediate results (`ROS_INFO, ROS_DEBUG`, etc.)
  - Make your code robust with argument and return value checks and catch exceptions.
  - Extend and optimize only once a basic version works.
  - If things do not make sense, clean the workspace.
  - Learn new tools:
    - debug mode for catkin configuration
    - use debugger breakpoints, e.g. In Eclipse
    - Write **unit tests** and integration tests to discover bugs.
      - Unit tests feed a known input to, and expect a known output of your code. 
      - Tests the interface of your code
        - Forces you to reason about its contract.
      - Integrations tests check the functionality and behavior of your program
      - Automated tests reduce the risk of bugs, and regressions.
- ROS2
  - ROS1 was not designed with all of today's use cases in mind. Never really designed for Real-time. It is initially designed for PR2 (stanford)
  - ROS2 new use cases:
    - Teams of robots
    - Not suited for bare-metal types of micro controlled
    - Not real time communication
    - Lossy networks
    - Uses in research & industry
    - API redesign
  - Nodes only contact if they have compatible service settings.





