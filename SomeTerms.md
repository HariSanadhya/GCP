**Stackdriver** Monitoring provides visibility into the performance, uptime, and overall health of cloud-powered applications. Stackdriver collects metrics, events, and metadata from Google Cloud Platform, Amazon Web Services, hosted uptime probes, application instrumentation, and a variety of common application components including Cassandra, Nginx, Apache Web Server, Elasticsearch, and many others. Stackdriver ingests that data and generates insights via dashboards, charts, and alerts. Stackdriver alerting helps you collaborate by integrating with Slack, PagerDuty, HipChat, Campfire, and more.
Accessed by clicking on **Navigation menu > Monitoring**

Flask is a framework for creating lightweight web applications with Python. 

Commands to initialize local variables:<br>
**export PROJECT_ID=$(gcloud info --format='value(config.project)')<br>
export BUCKET=${PROJECT_ID}-ml<br>
MYSQLIP=$(gcloud sql instances describe DB_NAME --format="value(ipAddresses.ipAddress)")**  # Command to get IP address of Cloud SQL instance<br> 

------------------------------------------------------

**Data Studio** is a free, modern business intelligence product that lets user create dynamic, visually compelling reports and dashboards. With Data Studio, one can:

    Easily connect to a variety of data sources.
    Visualize your data through attractive, dynamic, and interactive reports and dashboards.
    Share and collaborate with others, just as you can in Google Drive.
Data Studio automatically saves every change that the user makes, so there's no need to click Save when editing a report.<br>
Link - https://datastudio.google.com/

-----------------------------------------

**Google Genomics** helps the life science community organize the world’s genomic information and make it accessible and useful. Google Genomics is an API that is part of Google Cloud Platform. Through this and other add-ons, user can apply the same technologies that power Google Search and Maps to securely store, process, explore, and share large, complex datasets.

Link to BAM, BAI, SAM and SAI file explanation : http://software.broadinstitute.org/software/igv/bam

Command to generate BAI file from BAM file:  in the command, ${BAM} is environment variable containing location where BAM file is present and ${BAI} is environment variable containing location where BAI file should be created.
**gcloud alpha genomics pipelines run \
    --regions us-east1 \
    --command-line 'samtools index ${BAM} ${BAI}' \
    --docker-image "gcr.io/genomics-tools/samtools" \
    --inputs BAM=${BAM} \
    --outputs BAI=${BAI}**

--------------------------------------------------------

**Python virtual environment** is a directory tree containing its own Python distribution. <br>
install it by command **sudo pip install --upgrade virtualenv**<br>
create python2.7 virtual env **virtualenv -p python2.7 env**<br>
Link - https://virtualenv.pypa.io/en/stable/<br>

------------------------------------------

**Cloud Datalab**
An easy to use interactive tool for data exploration, analysis, visualization and machine learning 
1. Powerful Data Exploration : Cloud Datalab is a powerful interactive tool created to explore, analyze, transform and visualize data and build machine learning models on Google Cloud Platform. It runs on Google Compute Engine and connects to multiple cloud services easily so you can focus on your data science tasks.
2. Integrated & Open Source: Cloud Datalab is built on Jupyter (formerly IPython), which boasts a thriving ecosystem of modules and a robust knowledge base. Cloud Datalab enables analysis of your data on Google BigQuery, Cloud Machine Learning Engine, Google Compute Engine, and Google Cloud Storage using Python, SQL, and JavaScript (for BigQuery user-defined functions).
3. Scalable : Whether you're analyzing megabytes or terabytes, Cloud Datalab has you covered. Query terabytes of data in BigQuery, run local analysis on sampled data and run training jobs on terabytes of data in Cloud Machine Learning Engine seamlessly.
4. Data Management & Visualization : Use Cloud Datalab to gain insight from your data. Interactively explore, transform, analyze, and visualize your data using BigQuery, Cloud Storage and Python.
5. Machine Learning with Lifecycle Support : Go from data to deployed machine-learning (ML) models ready for prediction. Explore data, build, evaluate and optimize Machine Learning models using TensorFlow or Cloud Machine Learning Engine.

Link for Datalab installation instructions and other information - https://cloud.google.com/datalab/docs/quickstart

-----------------------------------
Google BigQuery is a RESTful web service that enables interactive analysis of massively large datasets working in conjunction with Google Storage.

**export PROJECT_ID=$(gcloud info --format='value(config.project)')**<br> #Env variable setup
**export BUCKET=$PROJECT_ID-ml**<br> # Env variable setup
**Using the GUI or gcloud shell, create the bucket with name as the value of BUCKET environment variable** 
**bq mk --external_table_definition=./tzcorr.json@CSV=gs://$BUCKET/flights/tzcorr/all_flights-00001-of-00025 flights.fedtzcorr**<br> #Loads a CSV file from google cloud storage to BigQuery table. The table schema here is present in a json file.

-------------------------------

