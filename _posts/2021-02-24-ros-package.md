---
title: "ROS package"
excerpt_separator: "<!--more-->"
categories:
  - Tech
classes: wide
---

- ROS packages: It contains source code, launch files, configuration files, message definitions, data and documentation. (ROS software organization form)
  - separate nessage definition packages from other packages. So other packages can also use this package message.
    - `package_name_msgs`: usually contains all definitions of actions, messages and service.
  - `package.xml`: defines the properties of the package:
    - Package name
    - version number
    - Authors
    - **Dependencies on other packages.**
      - `<buildtool_depend>catkin</buildtool_depend>`
      - regular depend: `<depend>roscpp</depend>`
      - build depend: only needed in the build process `<build_depend>`
      - build export depend, transitive dependency, only used for   other packages in their building process. `<build_export_depend`
  - `CMakeLists.txt`
    - It is the input to the CMake build system.
    - Required CMake version
    - Package Name
    - Configure C++ standard and compile features
    - Find other CMake.catkin packages needed for build (`find_package()`)
    - Other staff...(quite long)
    - `target_link_libraries` etc.

- ROS C++ Client Library (roscpp)
  - Initialization and spinning
    - `ros::init()`
    - `ros::NodeHandle` is the access point for communications with the ROS system.
    - `ros::ok()`: hecks if a node should keep running (exceptions: ctrl+c or `ros::shutdown()`)
    - `ros::spinOnce()`: processes incoming messages via callbacks, answer signals from the ros system. Call this often.
  - Node handle
    - `nh_ = ros::NodeHandle()`: publick (default) node handle
    - `nh_private_ = ros::NodeHandle("~")`: private
    - `nh_eth_ = ros::NodeHandle("eth")`: namespace: `/namespace/eth/topic`
  - Logging
    - Mechanism fo rlogging human readable text from nodes in the console and to log files. `ROS_INFO`. Automatic logging to console, log file and `/rosout` topic.
      - Two styles: `ROS_INFO()`: printf styple, and `ROS_INFO_STREAM()`: cout syle.
      - Need to address the `output` varialbe in the launch file as `screen`.
  - Subscriber
    - When a message is received, callback function is called with the contents of the message as arguments. -- callback function has to be defined.
    - Start listening to a topic by calling the method `subscribe()`
    - `ros::spin()` useful when it is a reactive nodes, only respondes to other messages.
  - Publisher
    - `ros::Publisher chatterPublisher = nn.advertise<std_msgs:String>("chatter",1)`
      - 1: queue_sizee
    - use `chatterPublisher.publish(message)` to publish the message contents.
    - `ros::spinOnce()`: looks like a regular call, ros need to do some housekeeping.
    - `looprate::sleep` make sure the frequency is achieved.
  - Parameters
    - Nodes use this to store and retrieve parameter at runtime. Based used for static data such as configuration parameters. Parameters can be defined in launch file or separate YAML files.
    - `<rosparam command="load" file=XXX.yaml />` under the node.
    - `rosparam list`
    - `rosparam get parameter_name` etc.  
    - `nodeHandle.getParam(parameter_name,variable)`
      - can reterive global and relative parameter (related to node handle), therefore, typically use the private node handle.

- RViz:
  - 3D visualization tool for ROS. (Not simulation)



