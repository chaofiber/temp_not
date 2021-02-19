---
title: "Learning Control"
excerpt_separator: "<!--more-->"
categories:
  - Project
  - Blog
tags:
  - project
classes: wide
---

I would like to elaborate on my motivation for learning control for robotics in two aspects: 1). How I learn the challenges of control for robotics and how reinforcement learning can help exploit the limit of robotics  2). How reinforcement learning is facing difficulties and may still need to leverage knowledge from control.

In my semester thesis [[1](https://about.2cni.com/_docs/semester_thesis.pdf)], I explored the possibility of utilizing a Model Predictive Control(MPC)-feedback strategy to track the optimized trajectory on a wheeled-legged ANYmal robot. Despite the great potential MPC as a controller brings to the robotics community, it shows some limitations:

  - **The computational burden is huge**. For a high dimensional robot, whose dynamic is often non-linear, the MPC requires a fast and reliable solver to coincide with the frequency of low-level torque controller, and to avoid local optimum as much as possible.

  - **MPC under complex terrain is challenging**. A single stair in the ground could turn the optimization into non-convex. Some convexification techniques and approximations are required. This problem together with the computation issues let the MPC under complex terrains more challenging.

Reinforcement learning can handle such problems in the following way:

  - Although training the RL network can take a lot of time, the inference time when executing the policy is negligible. The problem then boils down to how to lean this policy accurately and robustly.

  - Reinforcement learning-based approaches have shown their power in generalizing to complex unknown terrains. The way reinforcement learning, or more specifically, in this case, representation learning treats the terrain's information is usually by extracting features from the data and project them into a latent space. [[2](https://robotics.sciencemag.org/content/robotics/5/47/eabc5986.full.pdf)] has used a teacher-student representation learning technique to recover information such as terrain information, robot state, etc.

However, the planning problem is not well solved as far as I know by current approaches. Most of the current RL experiments are trying to solve the problem of how to conducting basic motions such as walking and turning and in what direction, but we still need to solve the planning problem in the future. There is one paper [[3](<https://ieeexplore.ieee.org/iel7/7083369/7339444/09028188.pdf>)] that uses the terrain map and a deep neural network to extract information out of it, and used transition feasibility to solve the semi-static gait schedule problem, and I think that will be an interesting direction.

An inevitable problem is how to cross the sim-to-reality gap when we use reinforcement learning. I have an understanding of this as my undergraduate thesis is about exploiting multi-sensory robotic data and use this representation for reinforcement learning tasks. We only restricted our experiments on simulation as transferring to reality was difficult. Purely exploring the performance of an RL approach may not be ideal for robotics applications. And that brings me back to the necessity of MPC.

  - Given all the environment data, MPC is still very powerful and accurate in controlling the motion of a robot. MPC encodes the known model and constraints and it would be an information loss if we ignore those. One example is the trajectory generator [[4](http://proceedings.mlr.press/v87/iscen18a/iscen18a.pdf)], where the author defines the trajectory by setting some key parameters, and the trajectory class remains unchanged. We would expect MPC to have similar functions in a reinforcement learning framework.

  - There are multiple approaches trying to incorporate MPC and Learning directly. The uncertainties in a general MPC framework can be replaced with a learning-based unit, such as a Kalman filter. [[5](https://arxiv.org/pdf/2003.03200.pdf)] tries to summarize practical ways of integrating reinforcement learning into MPC by approximating the terminal and stage cost by a neural network, and it shows that this approach can be used to solve sparse reward problems. MPC can also serve as guidance for reinforcement learning as shown in [[6](https://arxiv.org/pdf/1909.05197.pdf)] where the control Hamiltonian is used as an objective for the policy to optimize over.

To conclude, due to the computational difficulty and modeling challenges in complex situations, RL will be a promising replacement for the model-based control approach. However, we can still benefit from the prior knowledge MPC can bring us. With the belief of the high probability and potential of leveraging learning into control, I finished my motivation letter.
