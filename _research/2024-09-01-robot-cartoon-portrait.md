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

The code starts from a selfie or portrait image and uses Python-based vision tools to segment the face into meaningful drawing regions such as eyes, eyebrows, lips, hair, and the face outline. Instead of treating the image as a single bitmap, the program breaks the portrait into separate feature paths. This makes the output more useful for robotic drawing because each facial component can be converted into its own trajectory and controlled independently.

After generating the image-space paths, the project converts pixel trajectories into the robot's world frame. This step is important because the robot cannot directly use image coordinates; it needs physical target points that correspond to locations on the drawing surface. The pipeline then calculates robot joint angles through inverse kinematics so the arm can reach each point along the portrait path.

The robot motion side of the project focuses on making the drawing executable and smooth. The generated trajectories are intended for force-controlled drawing, using a trapezoidal velocity profile with motion points sampled every 4 milliseconds. This helps the robot maintain more consistent contact with the surface while moving through the portrait paths, rather than simply jumping between points.

Key outputs from the repository include segmented facial-feature trajectories, CSV path files for the portrait components, world-frame trajectory conversions, inverse-kinematics joint angle calculations, and robot-control scripts for executing the drawing. The result is a research prototype that bridges the gap between a high-level portrait image and low-level robotic arm commands.

[GitHub repository](https://github.com/ramrow/robot_cartoon_protrait)
