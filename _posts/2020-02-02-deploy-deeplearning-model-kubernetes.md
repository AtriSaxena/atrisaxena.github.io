---
title: "Deploy Your Deep Learning Model On Kubernetes With Python, Pytorch, Flask, and Docker"
categories:
  - Projects
tags:
  - docker
  - deep-learning
  - Kubernetes
  - google-cloud
---

![](https://i.imgur.com/CHBDWUF.png)

# **So, Easy Everyone can do it.**

This post will demonstrate a very simple method by which you can deploy your pytorch deep learning model easily for production using REST API with Flask, and deploy it using docker and kubernetes.

For anyone who doesn't know about docker and kubernetes need not to worry about. Just remember, Docker is a software platform using which you can create, deploy and manage virtualized application containers. While kubernetes is a container orchestration system for Docker containers which is is meant to coordinate clusters of nodes at scale in production in an efficient manner.

In this post, I am using Google Cloud from start to end. You can get free credit on signup to Google Cloud. So, you can also follow my steps easily and run everything with exact specifications. 
Let's go to it.

Note: If you get some error you can visit code from my github repository [ssd-object-detection](https://github.com/AtriSaxena/ssd-detection-app) or you can directly use my [docker image](https://hub.docker.com/r/atrisaxena/ssd-detection-app) and jump to deploying docker image to kubernetes.

# **Quick Outline**

1. Create your environment with Google Cloud. 
2. Serve a Deep Learning model as an API using Pytorch, Flask, and Docker.
3. Deploy said model with Kubernetes.
4. Bask in the glory of your newfound knowledge.

## **Step 1 - Create Environment With Google Cloud**

I am here using a simple Virtual Machine if you want to host your deep learning model on Nvidia GPU you can add GPU in this virtual machine. But using GPU is not provided in the free trial of GCloud. I will be showing you can host your pytorch model without GPU. The steps will remain very similar.

![](https://i.imgur.com/SQgtnfb.png)

To create your cloud Virtual machine click on "Compute Engine". 
Then click on "Create Instance"

You can see in the photo above that I have three instances already created.

The next step is to select the compute size for our instance. For this I choose 1vCPUs with 3.75 GB of memory. As, you want to deploy your deep learning model you can choose Nvidia K80 GPU to my instance. It's ok if GPU is not available.

![](https://i.imgur.com/vAMkPAV.png)

Next, we have to choose the operating system and disk size. I prefer using ubuntu 16.04 and disk size on average 30GB is more than enough for installing docker and creating the docker image for approx 1 GB.

![](https://i.imgur.com/CriQ8UI.png)

The final step before we create the VM is to set our Firewall rules to allow HTTP/S. Full transparency, I'm not sure if this step is required. I will show you how to edit the firewall settings to test our API on the VM before we deploy it to Kubernetes. So checking these boxes is not sufficient - there is more work to be done. I just haven't gone back to try this tutorial again without checking them.

![](https://i.imgur.com/YTNGDVa.png)

Now click "Create". Great, The hard part is done.

## **Step 2 - Build a Deep Learning Model using Pytorch.**

Now, let's SSH into our VM and start building our model. The easiest way to do this is to simply click the SSH icon next to your VM (below). This opens a terminal in your browser.

### **Installing Nvidia-Docker/ Docker**

To install Nvidia-Docker which use Nvidia GPU, you can take help from [this article](https://chunml.github.io/ChunML.github.io/project/Installing-NVIDIA-Docker-On-Ubuntu-16.04/). To install docker without GPU can use below scripts:

**1. Remove the existing version of Docker**

Firstly we need to remove the existing version of docker.

{% highlight python %}
sudo apt-get remove docker docker-engine docker.io

{% endhighlight %}

If docker is not installed on your machine, then apt-get will tell you that. It is totally fine.

**2. Installing Docker**

{% highlight python %}

sudo apt-get update
sudo apt-get install docker.io

{% endhighlight %}

**3. Verify the installation**

{% highlight python %}
sudo docker run hello-world

{% endhighlight %}

If you see an output that looks like the message below, you are all set.
```
Hello from Docker!
```
This message shows that your installation appears to be working correctly. To generate this message, Docker took the following steps: 
- The Docker client contacted the Docker daemon. 
- The Docker daemon pulled the "hello-world" image from the Docker Hub. (amd64) 
- The Docker daemon created a new container from that image which runs the    executable that produces the output you are       currently reading. 
- The Docker daemon streamed that output to the Docker client, which sent it    to your terminal.


**4. Create our Pytorch Object Detection Model**

So, I choose to create an pytorch object detection model which will detect object in the image. We are going to use SSD (Single Shot Multibox Detection) Model which is trained on VOC 2007 & VOC 2012 data. For this, we will use [repository](https://github.com/amdegroot/ssd.pytorch) by [amdegroot](https://github.com/amdegroot). 


We will write a short scirpt for hosting our Object Detection model and serve it with flask. 

For using the Docker the default flask behaviour when running an app locally is to serve the app on local host (127.0.0.1). But this causes problem when inside of a Docker container. The solution to this problem is calling `app.run()` specify the url as 0.0.0.0 like `app.run(host='0.0.0.0')`. Now our app is available on localhost as well as on the external IP.

So, let's get things working. 

First, let's create a new directory called `ssd-detection-app` and move into this directory

{% highlight python %}
mkdir ssd-detection-app
cd ssd-detection-app
{% endhighlight %}

Now let's clone the amdegroot repository of SSD 
detection model. 

{% highlight python %}

git clone https://github.com/amdegroot/ssd.pytorch .

{% endhighlight %}

Finally create a called `app.py`. You can use your text editor of your choice. I prefer using nano. To create and open `app.py` type:
{% highlight python %}
nano app.py

{% endhighlight %}

After opening file `app.py`, hit the `ctrl + V` to paste the following code.

<script src="https://gist.github.com/AtriSaxena/84569c0b302a6e3f6bf107860192f9a9.js"></script>


Once you pasted the code, you can save & exit by hitting `ctrl + X` than press `enter`.

We also need the weights file of the pre-trained model. For that, we will put model weight file in weights folder. 

{% highlight python %}

mkdir weights
cd weights
wget https://s3.amazonaws.com/amdegroot-models/ssd300_mAP_77.43_v2.pth


{% endhighlight %}


**5. Create a requirement.txt file**

Let's get back to our target. As we are going to run this code in docker container therefore we need to create a requirement.txt file. This file contain the few packages which need to be installed in docker container e.g., numpy, flask etc.

Just as before, create and open the `requirement.txt` file. Copy & Paste the following into file.

{% highlight python %}

opencv-python
numpy
requests
flask
pillow

{% endhighlight %}

**6. Create a Dockerfile**

Great let's create our Dockerfile. This file Docker will read to build and run our Project. 

Similary using nano create a `Dockerfile` and paste the following contents.

<script src="https://gist.github.com/AtriSaxena/1220db327f413134ea798e0bd97e785b.js"></script>

Here's what is going on. In Dockerfile, we are instructing to download a base image of pytorch with no cuda. If want to use with cuda than you can choose other docker image from this [github repository](https://github.com/anibali/docker-pytorch).

Than we are copying `requirement.txt` file and run it to install required packages. After that we then tell Docker to run our scipt via `python app.py`.

**7. Build Docker Container**

Now its the time to build and test our app. 

To build our Docker container, run following command: 
{% highlight python %}

sudo docker build -t ssd-detection-app:latest .

{% endhighlight %}


This will instruct the docker to build a container for the code located in our current working directory `ssd-detection-app`.

This whole operation will take few minutes for extracting the docker image and installing packages in listed in `requirement.txt`.

**8. Run the Docker Container**

Now let's run our docker container and test our object detection app.
{% highlight python %}


sudo docker run -d -p 5000:5000 ssd-detection-app
{% endhighlight %}

A quick note about the ports numbers, 5000:5000 tells the docker to make port no 5000 externally available and to forward our local app to the port which is also running on port no 5000.

Now, you check the status of your docker container by ``sudo docker ps -a``. You should something like below. 
```
[dockercompute@instance-3 ~]$ sudo docker ps -a
CONTAINER ID    IMAGE    COMMAND     CREATED    STATUS     PORTS        NAMES
d82f65802166    ssd-detection-app   "python app.py"  About an hour ago  Up About an hour          0.0.0.0:5000->5000/tcp   nervous_northcutt
```

**9. Test our model**

Now, our model is running, now we can test it by sending the request. We can send the dog image and model will return the json output of bounding box with label and probability. I have used this image below:

![](https://i.imgur.com/vB4MRSW.jpg)

From you computer instance terminal run:

```
curl -X POST -F image=@dog.jpg 'http://localhost:5000/predict'
```
Make sure to have dog.jpg image in your current directory. 

You will see a result like this below: 

```
{"predictions":[{"coords":"((1606.8755, 432.14508), 2049.419921875, 2592.420166015625)","label":"dog","probability":0.9924873113632202}],"success":true}

```

You can see from the result that our model correctly identified dog. Bravo! 
Now, we can deploy our docker container to the kubernetes Engine. Kubernetes engine helps to auto manage the containers running. It can scale up i.e., create new containers, scale down i.e., delete containers and restart containers. 

## Step3 - Deploy model with Kubernetes

This part is easy:

**1. Create a docker hub account if you don't have.**

The first thing we need to do is upload our docker image to [Docker Hub](https://hub.docker.com/). Now, we can tell kubernetes cluster to take docker image from docker hub.

**2. Login to your docker hub account**

Once you have created the docker hub account, login via the command line via ``sudo docker login``. You'll need to supply your username & password as you are logging into website. 

After, successful login you will see a message like this: 

```
Login Succeeded
```

Great, Let's move on to the next step.

**3. Tag your Docker Image**

We need to tag our docker Image before we can upload it. Think of this step as giving our container a name.

First, run ``sudo docker images`` and locate the `Image Id` for our ssd-detection-app.

The output should look something like this.

REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE ssd-detection-app    latest              ddb507b8a017        About an hour ago   1.61GB


Now let's tag our Image. For tagging follow the formatting as below:

```
# Format
sudo docker tag <your image id> <your docker hub id>/<app name>

# My extact command
sudo docker tag ddb507b8a017 atrisaxena/ssd-detection-app
```

**4. Push the Image to docker Hub.**

Now, we can push our container to the Docker Hub. From the shell run:

```
#Format
sudo docker push <your docker hub name>/<app-name>

#My exact command
sudo docker push atrisaxena/ssd-detection-app
```

Now, if you back and check your Docker Container Image in your Docker Hub website.
Get ready for the final step. 

**5. Create a Kubernetes Cluster**

From the Google Cloud console, select Kubernetes Engine

![](https://i.imgur.com/HOvfDnc.png)

Then create a new Kubernetes cluster

![](https://i.imgur.com/N71VjEC.png)

Next we’ll customize the size of the nodes in our cluster. I’ll select 4vCPUs with 15 GBs of RAM. You can try this with a smaller cluster. Remember, the default settings spin up 3 nodes, so your cluster will have 3X the resources of what your provision, i.e., in my case 45 GBs of Ram. 

![](https://i.imgur.com/av7Pjaj.png)

Now, just click create. It will take one to two minutes for your cluster to spin up. In the backend google created the VM and configure Kubernetes services automatically. 

Next, Connect to the cluster and click Run In Cloud Shell to bring up the console for the Kubernetes Cluster. A new shell will open in the Google cloud in the browser. 

![](https://i.imgur.com/7nC4mu4.png)

Now, we can run our Docker container in Kubernetes. Next you just need to run the kubectl command which will fetch the docker container from your Docker hub account and run the image. 

```
kubectl run ssd-detection-app --image=atrisaxena/ssd-detection-app --port 5000
```

In kubernetes, container runs inside pods. We can check the status of our pods by running ``kubectl get pods``. If you see "STATUS" as running you are all set.

Now that our pods are running we need to expose our pods on port 80 to the ourside world. This means anyone visiting the IP address of our deployment will able to access our API.It also means we don’t have to specify a pesky port number after our url like we did before (say goodbye to ``:5000``).

```
kubectl expose deployment ssd-detection-app --type=LoadBalancer --port 80 --target-port 5000
```

Few more steps to go. Now, we can determine status of our deployment by running. You will get the output something like this:

```
NAME                   TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)        AGE
ssd-detection-app   LoadBalancer   10.11.250.71   35.225.226.94   80:30271/TCP   4m
kubernetes   ClusterIP      10.11.240.1    <none>          443/TCP        18m
```

Grab the "EXTERNAL-IP" for your ssd-detection-app, on this IP you can send request to your model. It's time to call API, run following command in you local terminal(make sure dog.jpg image is there):

```
curl -X POST -F image=@dog.jpg 'http://<your service IP>/predict'
```

As you can see below, the API correctly returns the results 


```
{"predictions":[{"coords":"((1606.8755, 432.14508), 2049.419921875, 2592.420166015625)","label":"dog","probability":0.9924873113632202}],"success":true}

```

## Step 4 - Summary

In this tutorial, we learned about deploying deep learning object detection model to a REST API using pytorch and Django. We than used Docker to create Container and upload the container to the Docker Hub and deploy to the Kubernetes. 

With just few command we were able to deploy docker container on the Kubernetes Engine. 

There are still many topics to be explored such as, Kubernetes, Docker, Object detection approaches like SSD etc.

### How to get in Touch

If this tutorial is helpful to you please comment. It will keep me motivated to write more articles like this.

Connect with me on [LinkedIn](https://linkedin.com/in/atrisaxena)
[Github](https://github.com/atrisaxena)

Code for this post: [Github Repo](https://github.com/AtriSaxena/ssd-detection-app)




<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>

<script> (adsbygoogle = window.adsbygoogle || []).push({}); </script> 
