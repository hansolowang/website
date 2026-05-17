---
title: "GPU Programming for Beginners"
date: 2018-03-04
---

GPU computing has been a buzzword of late. It has applications that include virtually every industry. For example, GPU programming has been used to accelerate image processing, audio signal processing, statistical physics, scientific computing, medical imaging, deep learning, computer vision, cryptography, games, just to name a few. 

So what exactly is GPU computing? 

Growing up in Minnesota, I loved building snow castles in the winter. Being a Lord of the Rings fan, I always tried creating fortresses like Helm’s Deep or Minas Tirith on the nearby hills. Needless to say I was never successful. Besides having the attention span of a gnat, I just couldn’t shovel snow fast enough. The question I’d like to ask today is how could I have shoveled faster? Well I could have digged faster, used a better shovel, or ask my siblings to help. 

Well, I am not just talking about building snow fortresses, each method mentioned above is an analogy to building a faster processor. Digging faster is equivalent to having a faster clock cycle for the processor, executing each step of computation faster. Using a better shovel is equivalent to doing more work per step. Asking my siblings is equivalent to Parallel Computing which is the focus of this article. 

GPU Computing in a sense is using many, many weaker, less powerful processors, instead of having a few very powerful processors. E.G my desktop CPU, Ryzen 5, has 6 powerful cores. While the GPU, RTX 2070 can have up to 2560 smaller CUDA cores. You can think of it this way, a CPU is designed to maximize the performance of a single task within a job; however the range of tasks is wide. On the other hand, a GPU uses thousands of smaller cores for a massive computation. 

GPU computing does not solve all the problems. Rather, they are powerful accelerators for existing infrastructure. GPU computing’s main mission is to offload compute-intensive portions of an application, while the remainder of the code runs on the CPU.