# APM Lab Commands Reference

## Clone the lab repository
```bash
# visit the repo:
https://github.com/lancel00zz/ddtimer-apm-lab

# clone the repo
mkdir ~/Desktop/repo
cd ~/Desktop/repo
git clone git@github.com:lancel00zz/ddtimer-apm-lab.git
```

## Install Docker Desktop
```bash
brew install --cask docker
```

## Install Step 0
```bash
cd ~/Desktop/repo/ddtimer-apm-lab
docker compose -f docker-compose.apm-lab-step0.yml up -d

# Open ddtimer app from your browser: 
http://localhost:5049
```

## Install Step 1
```bash
# create the .env file
cp .env.example .env
nano .env

# install step 1 environment
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


