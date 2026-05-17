---
title: "Dockerizing Your CPP Projects"
date: 2024-02-18
---

In this post, I will share how to create a docker environment for C++ projects targeted for Ubuntu. 

# It works on my machine but fails on CI!
C++ does not provide an default package manager like Cargo in Rust, pip in python, or npm in JavaScript, etc. Third party libraries are added using a mix of techniques such as installing from Linux distro's repositories (apt-get), or git submodules, or half-baked solutions like Conan. Unfortunately they all have disadvantages:

- Installing with apt-get rarely make the environment identical as CI/CD. Especially after updating and upgrading the 3rd parties. 
- Using git submodules requries the building the third parties in the source tree. If the libraries are large (Boost, OpenCV, Qt), this may slow down the build that engineers become reluctant to switch branches or do a clean build.
- Conan requires writing python code... which IMHO is a tad much.

# Docker 
My preferred solution to the above problems is to create a Docker image and work on the project inside a container based on the image. The following are some advantages of this workflow.

- A Docker environment is *ISOLATED*! It is not affected by any environment variables, libraries, or settings specific to the engineer's workstation. It is different from a virtual machine (VM). Here is a great [blog post](https://nickjanetakis.com/blog/comparing-virtual-machines-vs-docker-containers) that explains the difference.
- A Docker environment is *REPRODUCIBLE*! It enables the encapsulation of an entire environment, including dependencies, libraries, and configurations. You can specify the exact versions of software packages. This ensures that code runs consistentily across different machines, making it easier to reproduce results and collaborate with others.
- A Docker environment is *PORTABLE*! It is easy to deploy the container on your workstation, cloud platforms, or edge devices.
- A Docker environment can be *VERSION CONTROLLED*! Tag the docker images with meaningful names. It allows engineers to pick between environments from the regristry.

I use Docker Compose for multi-container orchestration, i.e., a container for the robotics stack and another container for the simulation environment. The following is an example of a client container sending a list of integers to the server, the server returns the sum of the integer, the client then stores the sum to a file on the host machine.

[code](https://github.com/WangHanSolo/docker_example)