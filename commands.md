
### Repository

https://github.com/lancel00zz/ddtimer-apm-lab

### Clone the repo

```bash
mkdir ~/Desktop/repo
```
```bash
cd ~/Desktop/repo
```
```bash
git clone git@github.com:lancel00zz/ddtimer-apm-lab.git
```


### Install Colima

```bash
brew install colima
colima --version
```

### Final Colima Checks and Start

```bash
docker --version
if not installed:
brew install docker
```

```bash
docker compose  version
if not installed:
brew install docker-compose
```

```bash
colima start
```


### Starting APM-lab-0-Baseline

```bash
cd ~/Desktop/repo/ddtimer-apm-lab
docker compose -f docker-compose.apm-lab-0-baseline.yml up -d
docker ps
```

Run ddtimer app from your browser: 
```bash
http://localhost:5049
```

Start and Stop the docker containers:
```bash
docker compose -f docker-compose.apm-lab-0-baseline.yml stop
docker compose -f docker-compose.apm-lab-0-baseline.yml start
```


### Starting APM-lab-1-Infra

create the Shell Environment Varible
```bash
export DD_API_KEY=your_api_key_here
echo $DD_API_KEY
```

Starting apm-lab-1-infra
```bash
docker compose -f docker-compose.apm-lab-0-baseline.yml down
docker compose -f docker-compose.apm-lab-1-infra.yml up -d
docker ps
```

Displaying injected API key inside the Datadog Agent Container
```bash
docker exec -it apm-lab-1-infra-datadog-agent-1 /bin/bash
printenv | grep DD
```


### Starting APM-lab-2-apm

```bash
docker compose -f docker-compose.apm-lab-1-infra.yml down
docker compose -f docker-compose.apm-lab-2-apm.yml up -d
docker ps
```


### Starting APM-lab-3-apm-fixed

```bash
docker compose -f docker-compose.apm-lab-2-apm.yml down
docker compose -f docker-compose.apm-lab-3-apm-fixed.yml up -d
docker ps
```
