---
title: "Picasso Bot: Robot Cartoon Portrait Generation"
category: research_projects
permalink: /research/robot-cartoon-portrait/
excerpt: 'My first research project, completed in Fall 2024, focused on turning a selfie into robot-ready drawing trajectories so a robot arm could draw a cartoon-style portrait on a physical surface.'
date: 2024-09-01
venue: 'Fall 2024 Undergraduate Research, Rensselaer Polytechnic Institute'
link: 'https://github.com/ramrow/robot_cartoon_protrait'
---

This was my first research project, completed during Fall 2024 as a Research Assistant on the Picasso Bot project under Russell Sage Professor John Wen in RPI's Electrical, Computer, and Systems Engineering department. The project connects computer vision, image processing, path generation, inverse kinematics, and robot control into one pipeline: take a face image, simplify it into drawable portrait features, convert those features into motion trajectories, and send them to a robot arm that physically draws the portrait.

The main goal was to make portrait drawing more than a static image-processing exercise. A robot arm cannot draw directly from a raw image; it needs ordered paths, real-world coordinates, feasible joint commands, and smooth motion timing. This codebase builds that bridge. It takes an input portrait, extracts cartoon-like facial features, turns those features into trajectories, converts the trajectories into the robot's coordinate frame, and prepares the robot motion needed to draw the result on a surface.

The code starts from a selfie or portrait image and uses Python-based vision tools to segment the face into meaningful drawing regions such as eyes, eyebrows, lips, hair, and the face outline. Instead of treating the image as a single bitmap, the program breaks the portrait into separate feature paths. This makes the output more useful for robotic drawing because each facial component can be converted into its own trajectory and controlled independently. The pipeline prints the segmentation colors used by PyFacer and the dimensions of the input image, which helps with debugging and checking whether the input was interpreted correctly.

The trajectory-generation stage produces 13 separate CSV trajectory files: paths for both eyes, both eyebrows, the lips, the hair, and the face outline. That separation matters because portrait features have different shapes and drawing behavior. For example, an eyebrow path can be handled as a short contour, while the face outline and hair paths may require longer continuous movement. Keeping those features distinct makes the drawing process easier to inspect, tune, and send to the robot in a controlled order.

After generating the image-space paths, the project converts pixel trajectories into the robot's world frame. This step is important because the robot cannot directly use image coordinates; it needs physical target points that correspond to locations on the drawing surface. The pipeline then calculates robot joint angles through inverse kinematics so the arm can reach each point along the portrait path.

The robot motion side of the project focuses on making the drawing executable and smooth. The generated trajectories are intended for force-controlled drawing, using a trapezoidal velocity profile with motion points sampled every 4 milliseconds. This helps the robot maintain more consistent contact with the surface while moving through the portrait paths, rather than simply jumping between points. The force-control component is especially important because physical drawing depends on contact: the robot needs enough pressure to mark the page, but not so much that it damages the drawing surface or causes unstable motion.

The repository is organized around the full workflow. `experiment.py` is used to create the portrait trajectories from an input image. `integrated_client_fb_page.py` is used to run the drawing process on the robot. Supporting files such as `PathGenCartesian.py`, `RobotMotionController.py`, `robot_def.py`, `motion_toolbox.py`, and `lambda_calc.py` handle path generation, motion control, robot definitions, and related math for trajectory execution.

My work on this project gave me early research experience at the intersection of robotics and software systems. I worked with image segmentation, coordinate transforms, CSV trajectory generation, inverse kinematics, and robot-control timing. It also taught me how research code has to be more than a demo: the output must be structured clearly enough that the robot can use it, the intermediate files must be inspectable, and the motion pipeline has to account for real physical constraints.

Key outputs from the repository include segmented facial-feature trajectories, CSV path files for the portrait components, world-frame trajectory conversions, inverse-kinematics joint angle calculations, and robot-control scripts for executing the drawing. The result is a research prototype that bridges the gap between a high-level portrait image and low-level robotic arm commands, turning a personal image into a robot-drawn cartoon portrait.

[GitHub repository](https://github.com/ramrow/robot_cartoon_protrait)
