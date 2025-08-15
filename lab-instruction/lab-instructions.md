# Create step 0 instructions
cat > lab-instructions/step0-environment-setup.md << 'EOF'
# Step 0: Environment Setup

Set up a clean Flask application environment without any monitoring.

## 🎯 Objectives
- Deploy a working Flask application
- Understand the baseline (no monitoring)
- Verify application functionality

## 🚀 Instructions

### 1. Start the Clean Environment
```bash
# Make sure you're in the lab directory
cd ddtimer-apm-lab

# Start step 0 containers
docker compose -f docker-compose.apm-lab-step0.yml up -d

# Check containers are running
docker compose -f docker-compose.apm-lab-step0.yml ps
```

### 2. Access the Application
Open your browser to: **http://localhost:5049**

### 3. Test Application Features
- ⏱️ **Timer**: Set a timer (e.g., 2 minutes) and start it
- 🔴 **Red dots**: Set some red teams (e.g., 3 teams)
- 📱 **QR code**: Click the QR code to open the check-in page
- ✅ **Check-in**: Use the QR popup to simulate a team finishing

### 4. Observe Current State
- ❌ **No monitoring**: Application works but sends no data to Datadog
- ❌ **No traces**: No performance insights available
- ❌ **No metrics**: No application-level monitoring

## ✅ Success Criteria

- [ ] Application loads at http://localhost:5049
- [ ] Timer functionality works
- [ ] QR code generates and opens popup
- [ ] Red dots can be created and animated
- [ ] No Datadog traces (this is expected!)

## 🔍 What's Running?

```bash
# View running containers
docker ps

# Should see:
# apm-lab-step0-ddtimer-1  (Flask app on port 5049)
# apm-lab-step0-db-1       (PostgreSQL on port 5435)
```

## 🧹 Clean Up (Optional)

```bash
# Stop step 0 environment
docker compose -f docker-compose.apm-lab-step0.yml down

# Remove volumes (optional - resets database)
docker compose -f docker-compose.apm-lab-step0.yml down -v
```

---

**Next:** [Step 1 - Add Datadog Agent →](step1-add-datadog-agent.md)
EOF
