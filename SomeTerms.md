**Stackdriver** Monitoring provides visibility into the performance, uptime, and overall health of cloud-powered applications. Stackdriver collects metrics, events, and metadata from Google Cloud Platform, Amazon Web Services, hosted uptime probes, application instrumentation, and a variety of common application components including Cassandra, Nginx, Apache Web Server, Elasticsearch, and many others. Stackdriver ingests that data and generates insights via dashboards, charts, and alerts. Stackdriver alerting helps you collaborate by integrating with Slack, PagerDuty, HipChat, Campfire, and more.
Accessed by clicking on **Navigation menu > Monitoring**

Flask is a framework for creating lightweight web applications with Python. 

Commands to initialize local variables:<br>
**export PROJECT_ID=$(gcloud info --format='value(config.project)')<br>
export BUCKET=${PROJECT_ID}-ml<br>
MYSQLIP=$(gcloud sql instances describe DB_NAME --format="value(ipAddresses.ipAddress)")**  # Command to get IP address of Cloud SQL instance<br> 

