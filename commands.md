# Lab Commands Reference

Copy and paste these commands in order during the lab:

## Prerequisites
```bash
# Verify Docker is running
docker --version
```

## Step 0: Baseline Application
```bash
# Clone the lab repository
git clone git@github.com:lance100zz/ddtimer-apm-lab.git
cd ddtimer-apm-lab

# Start baseline environment
docker compose -f docker-compose.apm-lab-step0.yml up -d

# Verify containers are running
docker ps

# Open app in browser: http://localhost:5049
```

## Step 1: Add Datadog Agent
```bash
# Copy environment template
cp .env.example .env
# Edit .env file with your DD_API_KEY

# Stop previous environment
docker compose -f docker-compose.apm-lab-step0.yml down

# Start with Datadog Agent
docker compose -f docker-compose.apm-lab-step1.yml up -d

# Verify all containers
docker ps
```

## Step 2: Enable APM
```bash
# Stop step 1
docker compose -f docker-compose.apm-lab-step1.yml down

# Start APM-instrumented version
docker compose -f docker-compose.apm-lab-step2.yml up -d
```

## Step 3: Performance Optimization
```bash
# Stop step 2
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
```

This gives you:
- **Flat structure** - no confusing subdirectories
- **Single commands file** - chronological copy/paste ready
- **Essential files only** - exactly what you specified
- **Clear progression** - step0 → step1 → step2 → step3

Perfect for students who want to focus on learning APM rather than navigating complex folder structures.
