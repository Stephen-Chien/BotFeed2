---
date: 2021-03-05 12:26:40
layout: post
title: A Guide To All Things States - The Development Philosophy Behind State Machines
image: >-
  https://res.cloudinary.com/dohsdvjjj/image/upload/v1607304240/kelly-sikkema-YK0HPwWDJ1I-unsplash_ywtauy.jpg
optimized_image: >-
  https://res.cloudinary.com/dohsdvjjj/image/upload/c_scale,w_380/v1607304240/kelly-sikkema-YK0HPwWDJ1I-unsplash_ywtauy.jpg
category: robotics
tags:
  - science
author: lawsonwright, brandonpae
paginate: true
---


What are State Machines?
	
  
  A state machine is a method of representing the status of a robot at a given point. The robot’s immediate state is changed based on certain inputs, often called conditions or events. For instance, if a robot is in a forward drive state and moving forward, but a range sensor indicates that the robot is less than 12 inches away from a wall, the robot transitions from a forward drive state to a turn drive state, so that the robot can turn away from the wall. State machines are highly useful in FTC’s autonomous period as they are an effective way to map the actions that a robot should perform in a given program and it is relatively straightforward to define the events that will make the robot transition from one state to the next.

![picture](https://res.cloudinary.com/dohsdvjjj/image/upload/v1617655359/ok_fceajc.png)

What Makes a State Machine Good?

	Making a “good” state machine is not only highly subjective, but also widely debated. While each team should create one that works best for them, we nevertheless are going to try and provide some useful pointers and tips that we think would benefit all teams. First, make sure your code is structured and framed well. FTC generally uses Java for their code, which makes enforcing a rigid and uniform structure amongst states very easy. Teams should take advantage of either interfaces or abstract classes in order to define the universal functionality of each state and the exact implementation later on. For example, an interface could specify that each state must have three methods: start, update, and stop. When someone makes a new state, they just need to define what happens in these three methods. This means that all states will have the exact same functionality -- they can start, update, and stop. Furthermore, this means that some element of your code might not know how a state functions, or even what type of state it is, but it still can call those three basic methods to make it work. Another tip that teams using state machines should consider is auxiliary helper classes. If you have two states that are pretty similar and both to a similar task, consider making a new class to handle that task. This way, each state can call that class. As a general rule of thumb, you do not want to have any duplicate code because doing so makes it less organized, more prone to breaking, and harder to iterate. In conclusion, state machines can be a powerful tool for any robotics team and there are many ways to design an effective and efficient state machine system. 








