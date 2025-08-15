# -ddtimer-apm-lab
Hands-on lab for instrumenting Datadog Agent and Datadog APM in a Flask application (ddtimer)
# Create the main README
cat > README.md << 'EOF'
# Datadog APM Lab: Flask Application Monitoring

Learn hands-on Datadog APM instrumentation by adding monitoring to a real Flask application through progressive exercises.

## 🎯 Lab Objectives

By the end of this lab, you will know how to:
- Deploy a Datadog Agent container
- Configure APM environment variables
- Instrument a Flask application with ddtrace
- Verify traces are flowing to Datadog

## 📋 Prerequisites

### Required
- **Docker Desktop** installed and running
- **Datadog account** ([free 14-day trial](https://www.datadoghq.com/free-datadog-trial/))
- **Basic Docker knowledge** (docker compose commands)

### Helpful
- Python/Flask familiarity (not required for lab completion)

## 🚀 Quick Start

1. **Clone this repository**
   ```bash
   git clone https://github.com/lancel00zz/ddtimer-apm-lab.git
   cd ddtimer-apm-lab
   ```

2. **Set up your Datadog API key**
   ```bash
   cp env.example .env
   # Edit .env and add your DD_API_KEY
   ```

3. **Start Step 0 - Clean Environment**
   ```bash
   docker compose -f docker-compose.apm-lab-step0.yml up -d
   open http://localhost:5049
   ```

4. **Verify the application works** (no monitoring yet)

## 📚 Lab Steps

| Step | Description | Environment | What You'll Learn |
|------|-------------|-------------|-------------------|
| **[Step 0](lab-instructions/step0-environment-setup.md)** | Clean Flask app | No monitoring | Baseline application |
| **[Step 1](lab-instructions/step1-add-datadog-agent.md)** | Add Datadog Agent | Infrastructure monitoring | Agent deployment |
| **[Step 2](lab-instructions/step2-instrument-apm.md)** | Instrument APM | Full APM traces | Application instrumentation |

## 🏗️ Application Overview

**ddtimer** is a facilitator timer application with:
- ⏱️ Countdown timer functionality
- 🔴🟢 Team progress tracking with animated dots
- 📱 QR code check-in system
- 🗄️ PostgreSQL database integration
- 🎨 Dynamic configuration system

Perfect for learning APM because it has:
- **Web requests** (Flask routes)
- **Database queries** (PostgreSQL)
- **Background processes** (timer intervals)
- **Real user interactions** (QR scans)

## 🆘 Troubleshooting

### Common Issues
- **Port conflicts**: Make sure ports 5049 and 5435 are available
- **Docker issues**: Restart Docker Desktop if containers won't start
- **API key**: Verify your DD_API_KEY is correct in .env file

### Getting Help
- Check the [troubleshooting guide](lab-instructions/troubleshooting.md)
- View container logs: `docker compose logs <service-name>`
- Start fresh: `docker compose down && docker compose up -d`

## 📖 Additional Resources

- [Datadog APM Documentation](https://docs.datadoghq.com/tracing/)
- [Python Tracer Documentation](https://ddtrace.readthedocs.io/)
- [Flask Integration Guide](https://docs.datadoghq.com/tracing/trace_collection/dd_libraries/python/#flask)

## 🎓 Lab Environment

- **Application**: http://localhost:5049
- **Database**: PostgreSQL on port 5435
- **Images**: Pre-built and hosted on Docker Hub
- **No build required**: Everything downloads automatically

---

**Ready to start?** → [Begin with Step 0](lab-instructions/step0-environment-setup.md)

---

*Made with 💜 for hands-on learning*
EOF
