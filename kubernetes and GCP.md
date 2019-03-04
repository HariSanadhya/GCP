**Kubernetes (k8s)** : an open-source system for automating deployment, scaling, and management of containerized applications.<br>
Link to Kubernetes tutorial : https://kubernetes.io/docs/tutorials/kubernetes-basics/<br>
Link to kubectl overview - https://kubernetes.io/docs/reference/kubectl/overview/<br>

Steps:
1. Create a Node.js server.
2. Create a Docker container image.
3. Create a container cluster.
4. Create a Kubernetes pod.
5. Scale up your services.

##### Create a Node.js server
create a javascript file named for example "myfile.js" using editors like vi, nano, gedit , emacs or GCP GUI web editor : https://cloud.google.com/shell/docs/features#web_editor<br>
Example contents of file<br>
**var http = require('http');<br>
var handleRequest = function(request, response) {<br>
  response.writeHead(200);<br>
  response.end("Hello World!");<br>
}<br>
var www = http.createServer(handleRequest);<br>
www.listen(8080);**<br>
Once the file is created, execute the javascript code using node - **node myfile.js**<br>
Using the toolbar at the top of the browser shell, use option "preview on port 8080" and web page should be opened with output as "Hello World!"<br>

##### Create a Docker container image<br>
create a plain text file, lets say "myDocFile" using any editor of your choice. Content would be:<br>
**FROM node:6.9.2<br>
EXPOSE 8080<br>
COPY server.js .<br>
CMD node server.js**<br>
Now build docker image using command - **docker build -t gcr.io/GCP_PROJECT_ID/myDocFile:v1 .**<br>
To test the docker image - **docker run -d -p 8080:8080 gcr.io/GCP_PROJECT_ID/myDocFile:v1**<br>
And then either use the toolbar at the top of the browser shell to select option "preview on port 8080" and web page should be opened with output as "Hello World!"<br>
OR use command **curl http://localhost:8080** and the output should be "Hello World!"<br>
Now find docker container ID by using command **docker ps**<br>
Stop the docker container - **docker stop DOCKER_CONTAINER_ID**<br> 
Push the docker image to google container registory - **gcloud docker -- push gcr.io/GCP_PROJECT_ID/myDocFile:v1**<br>
To view the container image - **Navigation menu > Container Registry**<br>

##### Create a container cluster<br>
Kubernetes Engine cluster consists of a Kubernetes master API server hosted by Google and a set of worker nodes. The worker nodes are Compute Engine virtual machines.<br>
Two ways to create Kubernetes Engine cluster (2 n1-standard-1 nodes):<br>
1. Command Line- **gcloud container clusters create myDocFile \<br>
                --num-nodes 2 \<br>
                --machine-type n1-standard-1 \<br>
                --zone us-central1-a**<br>
2. GUI - Navigation menu -> Kubernetes Engine -> Kubernetes clusters -> Create cluster<br>
Once created, cluster can be viewed by going to Navigation menu > Kubernetes Engine

##### Create a Kubernetes pod
A Kubernetes pod is a group of containers tied together for administration and networking purposes. It can contain single or multiple containers.
Command to create pod - **kubectl run myDocFile -image=gcr.io/GCP_PROJECT_ID/myDocFile:v1 --port=8080**
Command to view deployment - **kubectl get deployments**
Command to view dockers created by the deployment above - **kubectl get pods**
Allow external traffic to access docker image by exposing the deployment - **kubectl expose deployment myDocFile --type="LoadBalancer"**
Find the External IP of exposed deployment - **kubectl get services**
Execute or reach docker service - http://<EXTERNAL_IP>:8080


##### Scale up Kubernetes services
Command - **kubectl scale deployment myDocFile --replicas=4** - declare # of instances that should be running at all time (here 4)
Command to get description of updated deployment - **kubectl get deployment**
Command to list all pods : **kubectl get pods**

### How to Roll out an upgrade to Kubernetes service:
1. Suppose there is some change in the file "myfile.js"
2. After the changes are made, update the docker image and push the docker image again as version 2
**docker build -t gcr.io/GCP_PROJECT_ID/myDocFile:v2 .
gcloud docker -- push gcr.io/GCP_PROJECT_ID/myDocFile:v2**
3. Edit the deployment file using command **kubectl edit deployment myDocFile** and change the image from gcr.io/GCP_PROJECT_ID/myDocFile:v1 to gcr.io/GCP_PROJECT_ID/myDocFile:v2


