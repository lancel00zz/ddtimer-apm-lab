
### Repository

```bash
https://github.com/lancel00zz/ddtimer-apm-lab
```

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


### Install Docker Desktop

```bash
brew install --cask docker
```


### Install Baseline Scenario (2 containers: ddtimer and db)

```bash
docker compose -f docker-compose.apm-lab-0-baseline.yml up -d
```

Run ddtimer app from your browser: 
```bash
http://localhost:5049
```



### Install Infra Scenario (3 containers: ddtimer, db and datadog-agent)

create the .env file
```bash
cp env.example .env
```
```bash
nano .env
```

install docker-compose step 1
```bash
docker compose -f docker-compose.apm-lab-1-infra.yml up -d
```


### Install APM Scenario (3 containers with APM instrumented)

```bash
docker compose -f docker-compose.apm-lab-2-apm.yml up -d
```


### Install APM-fixed Scenario (3 containers with APM bug fixed)

```bash
docker compose -f docker-compose.apm-lab-3-apm-fixed.yml up -d
```
