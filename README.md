# ddTimer APM Lab

This hands-on lab teaches Datadog Application Performance Monitoring (APM) fundamentals using a sample Flask timer application. You'll progress through 4 steps: baseline setup, adding the Datadog Agent, enabling APM instrumentation, and analyzing performance bottlenecks.

The lab demonstrates distributed tracing, flame graphs, span analysis, and real-world performance optimization. Students will learn how to instrument applications, configure the Datadog Agent as a sidecar container, and use APM data to identify and fix application issues. Perfect for Technical Solutions engineers getting hands-on experience with Datadog's observability platform.

## Quick Start

1. **Prerequisites**: Docker Desktop installed
2. **Setup**: `cp .env.example .env` and add your Datadog API key
3. **Follow along**: Use `commands.md` for copy/paste terminal commands
4. **Access app**: http://localhost:5049 once containers are running

## Lab Steps
- **Step 0**: Baseline Flask + PostgreSQL application
- **Step 1**: Add Datadog Agent sidecar container  
- **Step 2**: Enable APM tracing with ddtrace instrumentation
- **Step 3**: Analyze and fix performance bottlenecks

See `commands.md` for all terminal commands in chronological order.
