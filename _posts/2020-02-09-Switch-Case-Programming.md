---
date: 2020-02-07 12:26:40
layout: post
title: Switch Case Programming 
description: FTC programming 
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559820489/js-code_n83m7a.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559820489/js-code_n83m7a.jpg
category: code
tags:
  - robotics
  - tips
author: brandonpae
---

## FTC Programming

Today, I will give an introduction to switch-case programming in FTC, which is a useful tool for an autonomous program. In autonomous, there are a variety of activities that must be completed, including turning and driving. However, when using encoders in auton, we must consistently check if the motors have reached the desired target position. If not, then we continue to execute the action (i.e driving forward). However, since the core of the autonomous program happens in the loop() function, we cannot simply have a list of while-loops to check the position since that would throw an error.

Instead, we can use the power of the switch-case structure. First, we can set up a switch-case within the loop() method and have the first “step” be equal to 1. As a result, the code below executes on the first iteration:

![code](https://res.cloudinary.com/dohsdvjjj/image/upload/v1607306348/brandoncode_vyima2.png)

Now, what does this code do? First, it will set a servo position to 0.92, then call a method called DriveTrain(), which tells the robot to move to the encoder position associated with 10 inches. Then, we calculate this encoder position using calculateTicks() and set it to the target position for the motors. Afterward, we set the step variable (responsible for determining which case to execute) to 0, and nextStep to 2. With the break statement, the control flow will leave the switch case structure and then go to case 0 on the next iteration of loop(), since the step is now 0.


![codeaswell](https://res.cloudinary.com/dohsdvjjj/image/upload/v1607306352/brandoncode1_d745ti.png)

Now, what happens in case 0? First, we check if each motor has reached its target position. If it has not, then we call a power function to adjust the power sent to the motors with PID control. Then, we break out of the current case. However, because the step variable has not changed, when the loop() function runs the switch-case again, this case will be called again, checking if the action has been completed.

If the motors have all reached their target position (with a margin of error of 20 ticks) then we update step to be equal to nextStep. But what is nextStep? Earlier, in case 1, we set nextStep equal to 2, meaning that step is now equal to 2! Afterward, we break from the case, and when the switch-case is run again, we now execute case 2, which is the next action!

Using this simple yet powerful construct, coders can quickly program tasks in autonomous such as driving, turning, setting servo positions, and much more! For example, in the next case we could use similar code to case 1 but change the distance, and now set nextStep equal to 3, since we are currently executing case 2. Furthermore, this method is also very easy to debug, since we can constantly print which case the code is currently executing. For both new and experienced coders, I highly recommend this type of control structure!
