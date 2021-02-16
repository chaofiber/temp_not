---
permalink: /project/
title: "Projects"
classes: wide
---

### MPC-feedback Trajectory Optimization for Wheeled-legged Robots


![alt text](/assets/images/bio-photo.jpg "title")

- Wheeled-legged robots can cope with tough terrains in an energy-efficient way with the help of wheels, while it also preserves its ability to negotiate complex terrains through the presence of the leg.  To achieve various tasks in different terrains, trajectory optimization (TO) is required to serve as guidance.  Furthermore, a model predictive control (MPC) feedback planner is utilized to track this reference trajectory. In this thesis, we model the robot as a single rigid body, and the customized TOWR is used to handle the wheeled-legged robot trajectory optimization problem.  The tracking reference is converted into joint space via inverse kinematics and be fed into MPC as guidance.  We achieve this by adding the trajectory to the cost term of  the  MPC.  A  whole-body  controller  is  used  to  generate  torque  commands  for the real robots.  The framework is verified on simulation and hardware.  We show that such a framework can be modularized and TOWR can be replaced by other optimizers.   MPC  can  help  correct  the  infeasibility  of  the  trajectory  to  make  it physically practicable, as well as smooth the trajectory to avoid wild motions.  Such a trajectory-correction scheme can be further explored to realize online trajectory computing and tracking.
