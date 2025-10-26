🚀 Docker Swarm Infrastructure Health Summary

📋 System and Deployment Metrics

This summary reflects the state of the Docker Swarm stack running on the docker-prod-2 (10.10.10.132) host as of July 29, 2025.

Metric

Value

Status

Total Containers

48+ running services

Healthy

Total Planned Services

61

$79\%$ Success Rate

System Load

$1.76 - 2.54$

Variable (High for low core count)

Memory Usage

$14\% - 28\%$

Nominal

Disk Usage

$49.6\%$ of $97.87\text{GB}$

Moderate

Active Networks

14

Segmented Architecture

Persistent Volumes

74+

Robust

✅ Service Inventory Snapshot (Completed Categories)

The following 8 service categories are $100\%$ operational, accounting for the majority of the deployed containers.

Category

Service Count

Key Services

Notable Detail

🗄️ Database

6/6

PostgreSQL, MariaDB, Redis, pgAdmin

Primary and Caching databases fully deployed.

🎬 Media

6/6

Jellyfin, Plex, Radarr, Sonarr, qBittorrent

Complete media management and streaming suite.

📈 Monitoring

9/9

Grafana, Prometheus, Uptime Kuma, cAdvisor

Full stack for metrics collection and visualization.

📊 Dashboards

5/5

Heimdall, Homarr, Homepage, Organizr

Warning: Excessive redundancy detected in this category.

🔒 Security

2/2

Vaultwarden, Wazuh Platform

Security monitoring and password management are active.

☁️ Nextcloud

1/1

Nextcloud

Self-hosted cloud storage operational.

📢 Alerts

5/5

NTFY, AlertManager

Push notification and Prometheus alert routing.

🔧 Automation

2/2

n8n, Home Assistant

Workflow and smart home automation hubs active.

🟡 Partially Deployed Categories (Focus Areas)

These categories are under development and represent the lowest current completion rates, offering the greatest potential for future enhancement.

Category

Status

Complete $\%$

Key Active Service

Planned Services

Logging

1/10 deployed

$10\%$

Dozzle

Elasticsearch, Kibana, Loki, Promtail (ELK/Loki Stack)

Backup

1/5 deployed

$20\%$

Kopia

Duplicati, rclone, Resilio Sync

Networking

4/7 deployed

$57\%$

AdGuard Home, Gotify

LibreSpeed, Webhook Relay
