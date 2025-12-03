# APM Lab Commands Reference

## Repository

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

### Install Step 0 (2 containers: ddtimer and db)
```bash
cd ~/Desktop/repo/ddtimer-apm-lab
```
```bash
docker compose -f docker-compose.apm-lab-step0.yml up -d
```

Run ddtimer app from your browser: 
```bash
http://localhost:5049
```

### Install Step 1 (3 containers: ddtimer, db and datadog-agent)
create the .env file
```bash
cp env.example .env
```
```bash
nano .env
```
install docker-compose step 1
```bash
docker compose -f docker-compose.apm-lab-step1.yml up -d
```

### Install Step 2 (3 containers with APM instrumented)
```bash
docker compose -f docker-compose.apm-lab-step1.yml down
```
```bash
docker compose -f docker-compose.apm-lab-step2.yml up -d
```

### Install Step 3 (3 containers with bug fixed)
```bash
docker compose -f docker-compose.apm-lab-step2.yml down
```
```bash
docker compose -f docker-compose.apm-lab-step3.yml up -d
```


