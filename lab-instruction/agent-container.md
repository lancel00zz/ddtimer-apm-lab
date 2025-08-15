  datadog-agent:
    image: gcr.io/datadoghq/agent:7.67.0
    platform: linux/amd64
    environment:
      - DD_API_KEY=${DD_API_KEY}
      - DD_SITE=datadoghq.com
      - DD_APM_ENABLED=true
      - DD_LOGS_ENABLED=true
      - DD_LOGS_CONFIG_CONTAINER_COLLECT_ALL=true
      - DD_PROCESS_AGENT_ENABLED=true
      - DD_CONTAINER_EXCLUDE=name:datadog-agent
      - DD_HOSTNAME=ddtimer-agent-apm-lab
      - DD_ENV=apm-lab
      - DD_SERVICE=ddtimer
      - DD_VERSION=apm-lab-step1
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - /proc/:/host/proc/:ro
      - /sys/fs/cgroup/:/host/sys/fs/cgroup:ro
      - /var/lib/docker/containers:/var/lib/docker/containers:ro
    restart: unless-stopped
    networks:
      - ddtimer-network
