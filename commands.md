**to convert .md to .docx, run "pandoc <path/to/.md> -o <path/to/.docx>"**

The following instructions are designed **specifically for the APM Lab**, which covers installing **Docker Desktop** and running the **Datadog Agent as a sidecar**.  
 
This document **complements the “APM Lab” presentation slides** and has not been designed to be used as a stand-alone guide.  

It is intended as a facilitator to support participants through the installation and configuration phases of the lab.

Copy and paste these commands to follow along through the lab:

# Lab Commands Reference

## Install Docker Desktop
```bash
# if not installed locally, browse to the address below to select the appropriate version
# of Docker-Desktop to install
https://docs.docker.com/desktop/setup/install/mac-install/
```

## Clone the lab repository
```bash
# ⚠️ Create a local folder for the lab files ⚠️
# ⚠️ In Terminal, cd into this folder -  all following commands must be run here ⚠️

# cloning the repo:
git clone git@github.com:lancel00zz/ddtimer-apm-lab.git
```

## Install ddtimer
```bash
# this is "customer-like" application with no Datadog instrumentation whatsoever at this point
docker compose -f docker-compose.apm-lab-step0.yml up -d

# Open ddtimer app from your browser: 
http://localhost:5049
```

## Add Datadog Agent as a side car (through Terminal)
```bash
# Get the command line from your account in Datadog UI:
# Integrations -> Fleet Automation -> Install Agents -> Docker
# Make sure to toggle "Log Management" to ON
# In the UI, select your real API Key with the blue "Select API Key" button, 
# or paste it directly in the command below BEFORE TO RUN IT!

docker run -d --name dd-agent \
-e DD_API_KEY=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX \
-e DD_SITE="datadoghq.com" \
-e DD_DOGSTATSD_NON_LOCAL_TRAFFIC=true \
-e DD_LOGS_ENABLED=true \
-e DD_LOGS_CONFIG_CONTAINER_COLLECT_ALL=true \
-e DD_CONTAINER_EXCLUDE_LOGS="name:dd-agent" \
-v /opt/datadog-agent/run:/opt/datadog-agent/run:rw \
-v /var/run/docker.sock:/var/run/docker.sock:ro \
-v /proc/:/host/proc/:ro \
-v /sys/fs/cgroup/:/host/sys/fs/cgroup:ro \
-v /var/lib/docker/containers:/var/lib/docker/containers:ro \
gcr.io/datadoghq/agent:7
```

## Add Datadog Agent as a side car (through Docker-Compose)
```bash
# Create an environment file to store your API key (not hard-coded in Docker-Compose)
# and edit it with your real API key (copy-paste)
cp .env.example .env

# Stop all ddtimer running containers by clicking "🗑️" on Docker Desktop UI, 
# or from the terminal by running each line below in sequence:
docker stop dd-agent
docker rm dd-agent
docker compose -f docker-compose.apm-lab-step0.yml down

# Start the new environment with the Agent configuration from Docker-Compose
docker compose -f docker-compose.apm-lab-step1.yml up -d
```


## Enable APM 
```bash
# Prior to run the APM-instrumented environment, you need to shut down the running one:
docker compose -f docker-compose.apm-lab-step1.yml down

# Start APM-instrumented version
docker compose -f docker-compose.apm-lab-step2.yml up -d
```

## Use APM to fix app issue
```bash
# Shut down running containers:
docker compose -f docker-compose.apm-lab-step2.yml down

# Start optimized version
docker compose -f docker-compose.apm-lab-step3.yml up -d
```

## Cleanup
```bash
# Stop all containers
docker compose -f docker-compose.apm-lab-step3.yml down

# Remove volumes
docker compose -f docker-compose.apm-lab-step3.yml down -v

# Clean up system
docker system prune -f
```


