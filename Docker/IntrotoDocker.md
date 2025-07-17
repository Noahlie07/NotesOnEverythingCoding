# Docker  

## What is Docker
Docker is a virtualization tool (think VMs) which simplifies development and deployment of softwares.  

Docker bunches up a software/program's code, configuration, packages installed, operating system used, all in a container. This container can be easily shared between developers and between developers and servers due to its tidy and lightweight nature, which can then be ran in local computers easily with a few commands.  

## Docker Vs Virtual Machines  

Docker:
- Lightweight
- Can be shared
- Only acts as an OS's Application Layer. Docker is linux-based btw. Need Docker Desktop if we are trying to run docker containers on a Windows kernel.
  
Kernel:
- Heavy
- Difficult to share due to its heavy nature
- Contains both OS Application layer and kernel (thereby basically is a computer of its own)

## Basics of Docker

#### What is contained in Docker Desktop?
1. Docker Engine - Docker's server which handles all of docker's images and containers
2. Docker CLI client - allows us to write command lines to docker's server through our command prompt
3. GUI client - also has GUI for communicating with Docker's engine

#### Docker Images Vs Docker Containers  

Docker Images:
-  an application artifact, which not only includes the application's source code, but also its complete environment configuration (including programming language configuration, any tools used, environment variables (ex. files and directories), operating system, etc)

Docker Containers:
- the thing that actually runs the image / running instance of an image.
- multiple containers can run the same image (if you want to run an application on multiple containers)
