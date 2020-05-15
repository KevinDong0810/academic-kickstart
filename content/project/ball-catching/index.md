---
title: Ball Catching
summary: Mobile manipulator ball catching with a Deep Neural Network-based controller
tags:
- Mobile Manipulator
- Motion Planning
- Inverse Dynamics Learning
- Learning-based Control
- Deep Learning
date: "2020-05-14T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

reading_time: true
math: true

image:
  caption: Mobile manipulator ball catching
  focal_point: Smart

links:
url_pdf: https://arxiv.org/abs/2003.07489
url_video: https://www.youtube.com/watch?v=4uCvzurthS4

---

Mobile manipulators consist of a moving platform equipped one or more mechanical arms. Unlike traditional fixed manipulators used in assembly lines, mobile manipulators have extended workspace and better dexterity, thus they can cope with more complex environments and challenging tasks, like house cleaning and warehouse pickup. Regarded as the new solution of industry automation, mobile manipulators are receiving more and more attentions both from universities like MIT [^1] and robot companies like KUKA [^2]. Maybe one day we can buy a mobile manipulator to home and ask it to prepare for breakfast everyday. 

{{< figure library="true" src="fixed_manipulator.png" title="Fixed manipulators at the assembly line." numbered="true" lightbox="true" >}}

Current researches of mobile manipulators usually focus on collaborative tasks under slow motions. Researchers tend to keep the base static while the arm is moving, or vice versa, like [FIGURE 2](#figure-a-mobile-manipulator-grasping-object) shown below. However, this is not necessarily the best that robot can do. Instead, we believe that mobile manipulators are capable of accurate high-speed motions, which can further improve their efficiency. After all, you may not want your robot grasp a cup of coffee and move slowly to you.

{{< figure library="true" src="nvidia_robot.gif" title="A mobile manipulator grasping object." numbered="true" lightbox="true" >}}

In this project we want to demonstrate accurate high-speed motions of mobile manipulator via the ball catching benchmark task. In this task, a human operator throws a (tennis) ball towards the robot, and then the robot needs to predict the ball’s trajectory, select the optimal catching pose and then control itself to the exact pose at the exact time. 

{{< figure library="true" src="ball_catching.gif" title="The mobile manipulator ball catching setup." numbered="true" lightbox="true" >}}

This task is very challenging because of the following three reasons:
- **Real-time computation**: Typically, the ball will only be in the air for one second. This means that the ball trajectory prediction, robot motion planning and robot joint control need to be done within such a short time. Even with a powerful computer, special care must be taken when designing the robot algorithms for real-time performance.
- **High precision in position and time**: To achieve a successful catching, the robot needs to be in the exact position at the exact time. In this project, we attach a metal bottle at the robot’s palm, as shown in the figure below. This design leaves  position error tolerance on each side, which is very challenging when the robot is moving at high speed.
- **Controlling wheel-driven bases**: In general, the base’s control accuracy is much lower than the robot arm (e.g. base $\pm 5mm$[^3] vs arm $\pm 0.05mm$[^4] ) due the difference of driving mechanism. Thus, extra efforts are needed to accurately control the base.

Given these three challenges above, accurate high-speed motion generation for mobile manipulator ball catching has not been widely explored, with a few very notable exceptions. To solve these unique challenges, in this project we introduce: _(i)_ a bi-level motion planning scheme that generates smooth trajectories despite nonlinear constraints in real time, and _(ii)_ a learning-based controller improving tracking accuracy and enabling the mobile manipulator to follow trajectories sufficiently accurately. The whole algorithm framework is shown in [FIGURE 4](#figure-diagram-of-the-overall-system). 

{{< figure library="true" src="system_diagram.png" title="Diagram of the overall system." numbered="true" lightbox="true" >}}

For more details, check our paper at [ArXiv](https://arxiv.org/abs/2003.07489) and videos at [YouTube](https://www.youtube.com/watch?v=4uCvzurthS4).

[^1]: https://www.therobotreport.com/toyota-research-institute-teaches-mobile-robot-housework/
[^2]: https://www.kuka.com/en-gb/products/mobility/mobile-robots/kmr-iiwa
[^3]: https://www.kuka.com/en-ca/products/mobility/mobile-robots/kmr-quantec
[^4]: https://www.universal-robots.com/media/50880/ur10_bz.pdf

