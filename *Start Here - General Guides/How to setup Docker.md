

## What is Docker?

Docker is an open-source platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so that you can deliver software quickly. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.

Docker is a platform for developers and sysadmins to build, run, and share applications with containers. The use of containers to deploy applications is called containerization. Containers are not new, but their use for easily deploying applications is.

Containerization is becoming increasingly popular because containers are:



*   Lightweight: containers leverage and share the host kernel, making them much more efficient in terms of system resources than virtual machines.
*   Portable: you can build locally, deploy to the cloud, and run anywhere.
*   Loosely coupled: containers are highly self-sufficient and encapsulated, allowing you to replace or upgrade one without disrupting others.
*   Scalable: you can increase and automatically distribute container replicas across a datacenter.
*   Secure: containers apply aggressive constraints and isolations to processes without any configuration required on the part of the user.


### Images and containers

Fundamentally, a container is a running process, with some added encapsulation features applied to it in order to keep it isolated from the host and from other containers. One of the most important aspects of container isolation is that each container interacts with its own private filesystem; this filesystem is provided by a Docker image. An image includes everything needed to run an application - the code or binary, runtimes, dependencies, and any other filesystem objects required.


### Containers and virtual machines

A container runs natively on Linux and shares the kernel of the host machine with other containers. It runs a discrete process, taking no more memory than any other executable, making it lightweight.

By contrast, a virtual machine (VM) runs a full-blown ‘guest’ operating system with virtual access to host resources through a hypervisor. In general, VMs incur a lot of overhead beyond what is being consumed by your application logic.


## Installation


### Mac



1. Download the installer from [https://hub.docker.com/editions/community/docker-ce-desktop-mac/](https://hub.docker.com/editions/community/docker-ce-desktop-mac/)
2. Double-click Docker.dmg to open the installer, then drag the Docker icon to the Applications folder.
3. Double-click Docker.app in the Applications folder to start Docker. 

Visit [https://docs.docker.com/docker-for-mac/install/](https://docs.docker.com/docker-for-mac/install/) for more information.


### Windows



1. Download the installer from [https://hub.docker.com/editions/community/docker-ce-desktop-windows/](https://hub.docker.com/editions/community/docker-ce-desktop-windows/)
2. Double-click Docker Desktop Installer.exe to run the installer.
3. Follow the instructions on the installation wizard to accept the license, authorize the installer, and proceed with the install.
4. When prompted, authorize the Docker Desktop Installer with your system password during the installation process. Privileged access is needed to install networking components, links to the Docker apps, and manage the Hyper-V VMs.
5. Click Finish on the setup complete dialog and launch the Docker Desktop application.

Visit [https://docs.docker.com/docker-for-windows/install/](https://docs.docker.com/docker-for-windows/install/) for more information.


### Linux

Docker provides .deb and .rpm packages for the most common Linux distros such as Ubuntu, Debian, and CentOS. Installation to Linux is not a straightforward procedure and requires some knowledge about package management.

Visit [https://docs.docker.com/engine/install/#server](https://docs.docker.com/engine/install/#server) for more information.


## Using Docker to Contribute to WordPress

Many WordPress projects have switched to use Docker because it’s easier and more lightweight than Vagrant or other similar setups. At the moment you can use Docker to contribute to WordPress Core or WordCamp.org environment.

Visit [https://github.com/WordPress/wordpress-develop](https://github.com/WordPress/wordpress-develop) to learn how to set up and use the Docker containers for WordPress Core development.

Visit [https://github.com/WordPress/wordcamp.org/blob/production/.docker/readme.md](https://github.com/WordPress/wordcamp.org/blob/production/.docker/readme.md) to learn how to set up and use the Docker containers for WordCamp.org environment development.
