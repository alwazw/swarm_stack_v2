⚡ Manus Swarm 90 - Integrated Enterprise & Homelab Stack

A comprehensive, production-ready Docker Swarm stack focused on a secure, integrated, and modular infrastructure for both enterprise testing and advanced homelab environments.

🚀 Quick Start & Principles

Core Principles of the Integrated Ecosystem

Ingress: Traefik acts as the single entry point for all web services, automatically managing load balancing and SSL certificates (Let's Encrypt).

Authentication: Authelia (preferred) or Authentik provides a central Single Sign-On (SSO) layer for all services via Traefik middleware.

Data Segregation: Databases (Postgres, MariaDB, MSSQL) and Caching (Redis) run on a dedicated internal network, isolated from web traffic.

Configuration Management: Variables are strictly separated:

.env: Project settings (Domain, TZ, Ports, Paths).

SECRETS.txt: High-entropy passwords (used to populate the sensitive variables in the .env file). For production Swarm deployments, these should be converted to true Docker Secrets.

Prerequisites

Linux Host (Ubuntu 20.04+ or Debian 11+)

16GB+ RAM (32GB+ recommended for full stack deployment)

Docker and Docker Compose (or Docker Engine for Swarm)

Installation

Clone & Configure:

git clone [https://github.com/alwazw/manus_swarm_90.git](https://github.com/alwazw/manus_swarm_90.git)
cd manus_swarm_90/configs/production
# Copy and edit the configuration files
cp .env.example .env
cp SECRETS.txt.example SECRETS.txt


Crucially, populate the secrets in your new SECRETS.txt and copy those values to the corresponding fields in your .env file.

Deploy the Stack (Docker Swarm):

# Ensure Docker Swarm is initialized (if not already)
docker swarm init
# Deploy the stack using the configured files
docker stack deploy -c docker-compose.yml --with-registry-auth manus-swarm


📊 What's Included (Refined Core)

Category

Service

Description

Integration Point

🏗️ Core & Auth

Traefik

Reverse Proxy, SSL Termination (Let's Encrypt)

Ingress



Authelia

Centralized Two-Factor Authentication & SSO Gateway

Traefik Middleware



PostgreSQL

Primary Relational Database

Internal Database Network



Redis

High-Performance Caching and Session Storage

Internal Database Network

🗄️ Databases

MariaDB

MySQL-compatible Database Server

Internal Database Network



MSSQL

Microsoft SQL Server (Enterprise Testing)

Internal Database Network

🛠️ DB Management

pgAdmin

Web interface for PostgreSQL

Connects to postgres service



phpMyAdmin

Web interface for MariaDB/MySQL

Connects to mariadb service



Adminer

Single interface for multiple DB types (optional failover)

Connects to all DBs

📈 Monitoring/SIEM

Prometheus

Time-series metrics collection

Scrapes Exporters/cAdvisor



Grafana

Visualization and Dashboarding

Connects to Prometheus/Loki



Loki/Promtail

Log Aggregation and Shipping

Captures logs from all services



Wazuh

Security Information and Event Management (SIEM)

Deep Host & Endpoint Security

⚙️ Management

Portainer

Web-based Docker Container Management

Docker Socket Access (Restricted)



NetBox

IP Address Management (IPAM) & DCIM

Connects to postgres service

🏢 Business Apps

Inventree

Open-source Inventory Management System

Connects to postgres service



Dolibarr

ERP and CRM system

Connects to mariadb service

🔗 Automation

n8n

Workflow Automation and Integration Platform

Connects to postgres service

🌐 Networking

AdGuard Home

Network-wide DNS Ad and Tracker Blocking

Uses Host Network/Ports



WireGuard

High-speed VPN Server

Dedicated VPN Network



Guacamole

Remote Desktop Gateway (VNC/RDP/SSH)

Connects to mariadb service

🔧 Configuration

All sensitive variables in the included docker-compose.yml are pulled directly from your local .env file.

Volumes and Storage Organization

The project assumes a standardized local storage layout:

Volume Name

Usage

Description

postgres_data

/var/lib/postgresql/data

Persistent data for all PostgreSQL services.

mariadb_data

/var/lib/mysql

Persistent data for all MariaDB/MySQL services.

app_configs

/opt/config/...

Configuration files for non-database services (Grafana, Traefik, etc.).

user_data

/data/files/...

Large file storage for Nextcloud, Syncthing, Media.

This centralized approach makes backup and recovery significantly easier.
