# Lab Commands Reference

Copy and paste these commands in order during the lab:

## Install Docker Desktop
```bash
# if not installed on you computer
https://docs.docker.com/desktop/setup/install/mac-install/
```

## Clone the lab repository
```bash
# create a directory for the lab files
# select it with Terminal and run the line to clone the repo:
git clone git@github.com:lance100zz/ddtimer-apm-lab.git
```

## Install ddtimer
```bash
# this is "customer-like" application with no Datadog instrumentation whatsoever at this point
# when you will run the command it will create an docker environment on your computer
docker compose -f docker-compose.apm-lab-step0.yml up -d

# Open the "customer-like" ddtimer app from your browser: 
http://localhost:5049
```

## Add Datadog Agent as a side car (through Terminal)
```bash
# Get the command line from your account in Datagog UI:
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
# Create an environment template for you API key (not hard-coded in Docker-Compose)
# and edit it with your real API key (copy-paste)
cp .env.example .env

# Stop all ddtimer running containers by cliking "🗑️" on Docker Desktop, 
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


