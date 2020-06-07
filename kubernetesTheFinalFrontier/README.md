# Kubernetes: The Final Frontier 

<img src="images/enterprise.png" width="550" height="250">

*This is an introduction to Kubernetes tutorial. 
The continuing mission: to explore the strange new worlds of microservices, containerization, and their management. 
To seek out new skills and new adventures. 
To boldly go where no one has gone before!*

This is a hands on tutorial! I will be giving time during the tutorial to follow along with me and install MiniKube, create a sample deployement, create a docker image, and launch a web application. It might not be possible for you to do all these things in real-time with me (as installation can always take a long time!), but the video will be available and these instructions will walk you through. Thank you and see you in the stars! 

### Installing MiniKube
The Kubernetes docs have a fanastic guide to installing minikube on Linux, Mac, or Windows. Reminder, you will need to have a hypervisor installed, which might take some time. I am personally using VirutalBox.

https://kubernetes.io/docs/tasks/tools/install-minikube/



### Starting MiniKube
After installation is complete. You will want to start your first minikube kubernertes cluster

```minikube start -p final --vm-driver=virtualbox``` 

<img src="images/miniKubeStart.png" width="650" height="250">

Take note here, I am using virutalbox (and so I specified that).

```minikube status```

<img src="images/minikubeStatus.png" width="650" height="150">
