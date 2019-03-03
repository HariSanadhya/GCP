# GCP

Link to GCP compute engine documentation - https://cloud.google.com/compute/docs/
Link to **gcloud command line tool** overview - https://cloud.google.com/sdk/gcloud/
Link to **How to guide** - https://cloud.google.com/compute/docs/how-to 


**Google Cloud Shell** is a virtual machine that is loaded with development tools. It provides command-line access to your GCP resources.

**gcloud** is the command-line tool for Google Cloud Platform. It comes pre-installed on Cloud Shell and supports tab-completion.

Command to list the active account name - **gcloud auth list**
Command to list project ID - **gcloud config list project**

To create VM instances, 2 ways:-
1. Using GUI - Navigation menu > Compute Engine > VM Instances
2. Using shell command - gcloud compute instances create INSTANCE_NAME --zone XXXXXX

set the default region and zones that gcloud uses:
**gcloud config set compute/zone XXXXX**
**gcloud config set compute/region XXXXX**

SSH can be done by using GUI or shell command - **gcloud compute ssh INSTANCE_NAME --zone XXXXX**

Install nginx web server: (Can be installed from GCP marketplace as well)
1. **sudo su -**
2. apt-get update
3. apt_get install nginx

Check if nginx is running- **ps auwx | grep nginx**

To view the nginx web page - 
1. Go to the Cloud Console and click the External IP link of the virtual machine instance. 
2. Copy the External IP and http it. **http://EXTERNAL_IP/** 

gcloud help
1. gcloud -h
2. gcloud config --help
3. gcloud help config

Command to  view the list of configuration in GCP environment
1. gcloud config list
2. gcloud config list --all

Command to Manage cloud storage data - **gsutil**
create new storage bucket: **gsutil mb gs://BUCKET_NAME**
Move file to bucket: **gsutil cp test.dat gs://BUCKET_NAME**

**GCP Marketplace** - way to quickly launch common software packages and stacks on Google Compute Engine. It supports many common web frameworks, databases, CMSs, and CRMs. Its one of the fastest ways to get up and running on the GCP.

Persistent disks are durable network storage devices that GCP instances can access like physical disks in a desktop or a server. The data on each persistent disk is distributed across several physical disks. Compute Engine manages the physical disks and the data distribution to ensure redundancy and optimize performance for you. Standard persistent disks are backed by standard hard disk drives (HDD). SSD persistent disks are backed by solid-state drives (SSD)
**Standard persistent disks are efficient and economical for handling sequential read/write operations, but are not optimized to handle high rates of random input/output operations per second (IOPS). If high rates of random IOPS is required, use SSD persistent disks. SSD persistent disks are designed for single-digit millisecond latencies. Observed latency is application-specific.**

