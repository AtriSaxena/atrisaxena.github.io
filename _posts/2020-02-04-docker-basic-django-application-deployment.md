---
title: "A beginner's guide to Docker and Deploying Django Application on Docker"
categories:
  - Projects
classes: wide
tags:
  - docker
  - django
  - docker cheatsheet
  - docker container
---

![](https://i.imgur.com/nn2lLNf.jpg)


If you are into the field of programming or techie, chances are you must have heard of Docker Containers helpful for improving security, reproducibility and scalability in software development and data science. Even some of the BIG DADDY of tech companies like Google, VMWare and Amazon are building services to support it. 

<p align="center">
  <img src="https://media.makeameme.org/created/docker-i-see.jpg">
</p>

I think it's important to understand some of the basics of docker. So, you can keep up with the new technology. In this blog we will learn about the basic fundamentals of the "Containers" and how it compares with the Virtual Machines. After that we will create a Django web app container.

## What is Docker?

Docker is software developed by Docker Inc. It was presented to the general public on 13 March, 2013, since than it has got many improvements and expanding into IT Industry. 

Docker solved the problem into the IT industry, which was dependency and compilation problem since docker created independent and isolated environments. These environments are called "Containers".

## But, Is Docker Containers a Virtual Machine? 

This is most asked question and confuse many. The answer is: actually not quite. Both containers and VM have similar goals: to isolate an application and its dependencies into a self-contained unit that can run anywhere. The main difference between containers and VMs is in their architecture approach.  

Let's understand the difference closely.

## Virtual Machine

Virtual Machines are the emulation of the real computer which execute programs like a real computer. VMs shared the hardware resource of the computer using a "hypervisor".

**Wait...What are hypervisor?** 🤔

A hypervisor is a computer software, firmware or hardware that creates and runs virtual machines. A hypervisor is sometimes also called a virtual machine manager(VMM). The hypervisor runs on the physical machine called as "host machines". This host machine shares the Hardware resources such as RAM and CPU. And the VM which is running on the host machine is often called as "guest machine". This guest consists of both the application and whatever it needs to run such as system binaries and libraries. These guest machine also has the hardware stack, virtualized network adapters, storage and CPU.

As, mentioned above a guest machine can either run on hosted hypervisor or bare metal hypervisor. In hosted hypervisor the hosted operating system is more important for managing the hardware driver instead of the hypervisor. This layers between the hardware and hypervisor creates more resource overhead, which lowers the performance of the VM.

On the other hand bare metal hypervisor tackles the performance issue by installing on and running from the host machine's hardware. Since it runs directly on the hardware it doesn't need any host operating system to run on. Unlike the hosted hypervisor, a bare metal hypervisor has its own drivers. This results in better performance, scalibility and stability.


<p align="center">
  <img src="https://i.imgur.com/iBHxafD.png">
</p>

As you can see in the diagram, VMs package up the virtual hardware, a kernel (i.e. OS)and user space for each new VM.

## Containers 

A container provides operating system level virtualization by abstracting the "user-space" unlike VMs which provides hardware virtualization.

You will see what i mean as we get more about the containers. 

A container looks like a VM for all purpose. For example, they have private space, run commands, private Network interface and IP address, mount file system etc.

But one big difference between containers and VM is that container **Share** the host system kernel with other containers.

<p align="center">
  <img src="https://i.imgur.com/WLIGk7L.png">
</p>


This diagram shows that container package up just user space and not kernel or virtual hardware like a VM does. Each container gets its own isolated space to allow multiple containers to run on a single host machine. We can also see that operating system level architecture is being shared across containers. The only part that is created is just bins and libs. This makes containers so lightweight.

## Why Use Docker as a Developer? 

Uptill now, just have understand many advantages of docker containers. Here are benefit of using Docker:

- Docker is fast. You can start/stop your application running on docker within few seconds.

- You can create/destroy containers faster.

- Docker is multi-platform. You can lauch on any platform.

- No more difficulties in managing the environment. Once docker is configured, you will never have to reinstall your dependencies manually again.

- You keep your work-space clean, as each of your environments will be isolated and you can delete them at any time without impacting the rest.

- It will be easier to deploy your project on your server to put it online.

## Fundamental Docker Concepts

Now that we have got the big picture in place, let's go through the fundamentals parts of Docker:

![](https://i.imgur.com/f24gJpJ.png)

## Docker Engine

Docker Engine is the layer on which docker runs. It's a light weight runtime which manages the containers, images, builds etc. It runs natively on Linux system and is made up of:

- A Docker Client that communicates with Docker Daemon to execute commands.

- A Docker Daemon that runs in the host computer.

- A REST API for interacting with the Docker Daemon remotely.

### Docker Client

Docker Client you can think of it as a UI for Docker. It communicates the intructions to the Docker Daemon.

### Docker Daemon

Docker Daemon is actually which is running commands. It recives the command from the Docker Client like building, running and distributing the container. The Docker Daemon runs on the host machine, but as a user, you never directly communicate directly with the daemon.

### Dockerfile

A Dockerfile is where you can write the instructions to build a Docker Image. These instructions can be, RUN, EXPOSE, etc. 

### Docker Image

Docker Images are the read only templates which you create from the instructions written in the Dockerfile. Each instructions in the Dockerfile adds a layer to the Image, with layers representing a portion of the images file system that either adds to or replaces the layer below it. Docker uses a Union File System to achieve this.

### Docker Container

A Docker container, wraps an application's software into an invisible box with everything the application needs to run. That includes the operating system, application code, runtime, system tools etc. Docker containers are built off Docker images. Since images are read-only, Docker adds a read-write file system over the read-only file system of the image to create a container.

Moreover, then creating the container, Docker creates a network interface so that the container can talk to the local host, attaches an available IP address to the container, and executes the process that you specified to run your application when defining the image.

Once you’ve successfully created a container, you can then run it in any environment without having to make changes.

## Let's create your first application.

Pheww! Lot's of technical details. Let's show you to create a Django Application on Docker Container.

**1. Install Docker on Your Machine.**

- For Ubuntu: 

First Update the Package:

```
sudo apt update
```

Next, Install docker with apt-get:

```
sudo apt install docker.io
```

Finally, verify that Docker is installed correctly.

```
sudo docker run hello-world
```

- *For MacOS*: you can follow [this link.](https://docs.docker.com/docker-for-mac/install/)

- *For Windows*: you can follow [this link.](https://docs.docker.com/docker-for-mac/install/)

**2. Create your project:**

To create your first Docker application create a folder on your computer and install Django. 

Install Django if you don't have installed

```
pip install django
```

**3. Create a Django Project**

```
django-admin startproject mysite
```

create 'requirement.txt' and copy these packages:

```
Django
```

**4. Edit the Dockerfile**

Create 'Dockerfile', A Dockerfile is where you write the instructions to build a Docker image. These instructions can be:

- RUN apt-get y install some-package: to install a software package.
- EXPOSE 8000: to expose a port
- ENV to pass an environment variable

 Once you’ve got your Dockerfile set up, you can use the docker build command to build an image from it. Here's is Dockerfile:

 <script src="https://gist.github.com/AtriSaxena/7e888a962696a35ce0474f7b4256f5e4.js"></script>

5. Create the Docker Image

Once your code is ready, and the Dockerfile is written, all you have to do is create your image to contain your application:

```
docker build -t djangosite .
```

The ’-t’ option allows you to define the name of your image. In our case, we have chosen ’djangosite’ but you can put what you want.

6. Run the Docker Image

Once the image is created, your code is ready to be launched.

```
docker run -d -p 8000:8000 djangosite
```

You need to put the name of your image after ‘docker run’.

Open 'http://localhost:8000' in your browser. You will see Django page.

7. Push your Docker Container to Docker Hub. Docker Hub is a community where you can publicly post your Docker Images. 

- Signup to the [Docker Hub](https://hub.docker.com) by opening link into browser.
- Once you have created the docker hub account, login via the command line via ``sudo docker login``. You'll need to supply your username & password as you are logging into website. 

After, successful login you will see a message like this: 

```
Login Succeeded
```

- We need to tag our docker Image before we can upload it. Think of this step as giving our container a name.

First, run ``sudo docker images`` and locate the `Image Id` for our djangosite.

Now let's tag our Image. For tagging follow the formatting as below:

```
# Format
sudo docker tag <your image id> <your docker hub id>/<app name>

# My extact command
sudo docker tag ddb507b8a017 atrisaxena/djangosite
```


Now, we can push our container to the Docker Hub. From the shell run:

```
#Format
sudo docker push <your docker hub name>/<app-name>

#My exact command
sudo docker push atrisaxena/ssd-detection-app
```

Now, if you back and check your Docker Container Image in your Docker Hub website.


<p align="center">
  <img src="https://media.tenor.com/images/384c692244d19b34ae5368026bf1cc48/tenor.gif">
</p>


## Conclusion

I hope you’re now equipped with the knowledge you need to learn more about Docker and maybe even use it in a project one day.

As always, drop me a line in the comments if I’ve made any mistakes or can be helpful in anyway! 😁

