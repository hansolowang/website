---
title: "Simulation in Robotics"
date: 2018-05-05
---

_I wrote this while a sophomore at UW-Madison. It is awesome to look back and see how much I have grown. I feel blessed (added 11/11/2024)_

The first things that comes to mind on the topic of simulation is Neo(Keanu Reaves) fighting Agent Smith(Hugo Weaving) in the Matrix. The film describes a future where reality perceived by humans is actually a simulated reality created by evil machines. This nefarious reality is so real that most humans cannot tell the difference and live their lives in the simulated reality. 

With the above example in mind, lets talk about simulation in robotics. Functionally, robotics simulation uses digital representation, a digital twin, to enable dynamic interaction with robotic models in a virtual environment. Using this digital representation, engineers and researchers can prototype engineering designs without building a physical copy or conducting real world experiments. Imagine yourself as a sensor engineer, you are unsure what the scan pattern of a newly designed laser scanner in CAD. Instead of manufacturing a prototype, you can put in the specs to a simulator to generate the scan pattern. This is something I worked on during an internship at Cepton. At Tesla, we use simulators to enable Autopilot to perform virtual test drives instead of real ones. With the rapid advancement of computational power, simulations can accelerate the engineering design of hardware and software. 

There are many different levels of simulations, each requiring different expertise and fidelity. Say we have a team of engineers designing a Mars rover. Engineers that design the rover wheels are interested to understand the interaction between rigid or deformable terrain on the treads can use simulations to collect massive amounts of data in a simulated environment that mimicks Mar's gravity and soil composition[(chrono::FSI)](https://www.youtube.com/watch?v=MdFI7rWLxiw). Another team of engineers is asking for massive quantities of sensor data to train an object detection models for a full self driving car, we can collect sensor data using ray tracing sensor models[(chrono::sensor)](https://www.youtube.com/watch?v=NG-B7deTA9g). Lastly, a team of engineers working on vehicle path planning would like to test their algorithms on edge case scenerios such as a children jay walking. We can use simulations to test the vehicle's response to edge cases. 

There are a few caveats when using simulation to accelerate engineering design: 

  1. The quality of simulation results are dependent on the fidelity of the virtual environment:
  2. Behavior learned in simulation does not translate well to the real world
  3. There are no objective metrics on the fidelity of a simulation



The issues above limit the proliferation of simulations in engineering development. A high fidelity simulation can be an expensive project for any company to undertake. You will need an army of 3D artists to create the virtual models and environments, qualified engineers with domain expertise to program the physics of the environment. Despite the best efforts of artists and engineers, the rich diverse real world is quite impossible to replicate with current technology. Using the examples videos above, simulations tend to be monotone and plain compared to real world. Because of this, algorithms and models can have different behaviors in simulation compared to real world. 

Amazing progress have been made to improve simulations. However, given the complexity of simulation. There exists no objective metric on how "real" a simulation is. This becomes an interesting conundrum, how do we objectively measure improvement of a simulator? There can be qualitative comparisons, i.e, it looks better. There are no known quantitative analysis on the fidelity of a simulation and how it compares to the real world.