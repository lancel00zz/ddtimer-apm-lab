# APM Lab Commands Reference

## Clone the lab repository
Location of the repo:
```bash
https://github.com/lancel00zz/ddtimer-apm-lab
```

# clone the repo
```bash
mkdir ~/Desktop/repo
```
```bash
cd ~/Desktop/repo
```
```bash
git clone git@github.com:lancel00zz/ddtimer-apm-lab.git
```

## Install Docker Desktop
```bash
brew install --cask docker
```

## Install Step 0
```bash
cd ~/Desktop/repo/ddtimer-apm-lab
```
```bash
docker compose -f docker-compose.apm-lab-step0.yml up -d
```

# Open ddtimer app from your browser: 
```bash
http://localhost:5049
```

## Install Step 1
# create the .env file
```bash
cp env.example .env
```
```bash
nano .env
```

# install step 1 environment
```bash
docker compose -f docker-compose.apm-lab-step1.yml up -d
```

## Install Step 2 
```bash
docker compose -f docker-compose.apm-lab-step1.yml down
docker compose -f docker-compose.apm-lab-step2.yml up -d
```

## Install Step 3
```bash
docker compose -f docker-compose.apm-lab-step2.yml down
docker compose -f docker-compose.apm-lab-step3.yml up -d
```


