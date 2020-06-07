# Kubernetes: The Final Frontier 

<img src="images/enterprise.png" width="650" height="250" style="vertical-align:middle" >

*This is an introduction to Kubernetes tutorial. 
The continuing mission: to explore the strange new worlds of microservices, containerization, and their management. 
To seek out new skills and new adventures. 
To boldly go where no one has gone before!*

This is a hands on tutorial! I will be giving time during the tutorial to follow along with me and install MiniKube, create a sample deployement, create a docker image, and launch a web application. It might not be possible for you to do all these things in real-time with me (as installation can always take a long time!), but the video will be available and these instructions will walk you through. Thank you and see you in the stars! 

## Installing MiniKube
The Kubernetes docs have a fanastic guide to installing minikube on Linux, Mac, or Windows. Reminder, you will need to have a hypervisor installed, which might take some time. I am personally using VirutalBox.

https://kubernetes.io/docs/tasks/tools/install-minikube/



### Starting MiniKube
After installation is complete. You will want to start your first minikube kubernertes cluster

```minikube start -p final --vm-driver=virtualbox``` 

<img src="images/miniKubeStart.png" width="650" height="250">

Take note here, I am using virutalbox (and so I specified that).

```minikube status```

<img src="images/minikubeStatus.png" width="650" height="150">

## Running a Simple Application





## Deploying a Website 

Create a yaml file for our deployment by doing the following command: 

```kubectl create deployment webapp --image=amoran06/picardtips --dry-run=client -o yaml > webapp.yaml```

Open up the yaml with the editor of your choice (VIM for the WIN) and you should see something that looks like this: 

<img src="images/webApp.png" width="500" height="400">

Next step is we will need to add a containerPort to our yaml configuration file. This is an **important** step as our flash app that we created for our website is running on port 5000, and we need to make sure that is exposed via kubernetes. 

<img src="images/webAppContainerPort.png" width="500" height="400">

Now that we have generated and edited our yaml file, now its time to apply it. 

```kubectl apply -f webappl.yaml```

You should see: ```deployment.apps/webapp created``` if everything has gone to plan!

Next we want to be able to see our website, we are going to need to expose our deployment to the outside world by using a load balancer. This will give us an external IP address that we can hit in combination with the port 8080.  

```kubectl expose deployment webapp --type=LoadBalancer --port=8080 --target-port=5000```

You should see: ```service/webapp exposed``` if everything has worked! 

Let's just on our services and pods 

```kubectl get pods,services```

We should see both a service and pod named web-app. 
<img src="images/podsAndService.png" width="900" height="400">

Since we running locally we will need to create our loadbalancer by running minikube. 

```minikube service webapp``` 

The website Picard Tips should pop up in your local browser! Read the tips, they are great, thanks twitter! 
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Picard management tip: Keep a log of your journey. You will understand better by writing it down.</p>&mdash; Picard Tips (@PicardTips) <a href="https://twitter.com/PicardTips/status/1269388228248760320?ref_src=twsrc%5Etfw">June 6, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 




## Resources and Credit

The kubernetes docs are wonderful! https://kubernetes.io/docs/tutorials/hello-minikube/ This helped guide me in making this tutorial.

I was able to create this web application from this wonderful example: https://docker-curriculum.com/ I am not a web developer and so using the code found here https://github.com/prakhar1989/docker-curriculum/tree/master/flask-app to create my docker image was a life saver! Thanks to https://github.com/prakhar1989!! 
