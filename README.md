# MUST READ: UPS Monitoring System Extension

## Overview
This repository extends the MET-DPG Monitoring system by integrating UPS monitoring functionality. The setup uses Network UPS Tools (NUT), Prometheus, and Grafana to track the performance and health of Uninterruptible Power Supplies (UPS) in real-time. This document provides essential details to get started, understand the repository structure, and set up UPS monitoring correctly.

---

## Key Features
- **Real-Time Monitoring**: Tracks UPS metrics such as battery charge, input/output voltage, and load.
- **Alerts**: Configurable alerts for critical events (e.g., low battery, voltage anomalies).
- **Grafana Dashboards**: Prebuilt dashboards for visualizing UPS performance.
- **Scalable Design**: Easy to integrate into the existing monitoring stack.

---

## Repository Structure

### Root Files:
- **`README.md`**: General documentation for the repository.
- **`docker-compose.yml`**: Docker Compose configuration for the monitoring system.
- **`.env`**: Environment file for sensitive configuration variables.

### Directories:
1. **`nut/`**: NUT configuration files.
   - `ups.conf`: Defines connected UPS devices.
   - `upsd.users`: Sets up user credentials for NUT.
   - `upsd.conf`: Configures the NUT daemon.
   - `upsmon.conf`: Configures the monitoring daemon.

2. **`prometheus/`**: Prometheus configurations.
   - `prometheus.yml`: Scrape configuration, including UPS metrics.
   - `web_targets.yml.example`: Example for monitoring web services.
   - `server_targets.yml.example`: Example for monitoring servers.
   - `alert_rules.yml.example`: Example alert rules for UPS metrics.

3. **`grafana/`**: Grafana dashboards.
   - `UPS_Monitoring_Dashboard.json`: Preconfigured Grafana dashboard for UPS monitoring.

4. **`data/`**: Stores persistent data (e.g., metrics and Grafana configurations).
   - `.gitkeep`: Placeholder for the directory.

---

## How to Set Up

### 1. Install Dependencies
- Install Docker and Docker Compose.
- Install Network UPS Tools (NUT).

### 2. Clone the Repository
```bash
git clone git@github.com:metdpg/monitoring.git
cd monitoring
```

### 3. Configure the System
1. **NUT Configuration**:
   - Edit `nut/ups.conf` to define connected UPS devices.
   - Edit `nut/upsd.users` to set up user credentials.

2. **Prometheus Configuration**:
   - Add NUT Exporter settings to `prometheus/prometheus.yml`.
   - Add UPS alert rules to `prometheus/alert_rules.yml`.

3. **Grafana Dashboard**:
   - Import `grafana/UPS_Monitoring_Dashboard.json` into Grafana.

### 4. Start the System
- Default Setup:
  ```bash
  docker-compose up -d
  ```
- With Alerts:
  ```bash
  docker-compose --profile alertmanager up -d
  ```

---

## Maintenance

### Check System Status
- **Verify containers are running**:
  ```bash
  docker-compose ls
  ```
- **Check logs**:
  ```bash
  docker-compose logs
  ```

### Clean Up Disk Space
- Prune unused Docker images:
  ```bash
  docker image prune
  ```

### Update the System
- Pull the latest updates and restart the system:
  ```bash
  docker-compose stop
  docker-compose pull
  docker-compose up -d
  ```

---

## Important Notes
1. **Data Retention**:
   - Metrics data is retained for 90 days. Ensure adequate disk space is allocated for `/var/lib/docker`.
2. **Custom Dashboards**:
   - Changes to the default dashboard (`Status of Servers and Services`) may be overwritten during updates. Create new dashboards for custom visualizations.
3. **Security**:
   - Update `grafana/env.config` to set a strong admin password.

---

## Troubleshooting

### NUT Service Issues
- Ensure the NUT service is running by checking the logs:
  ```bash
  docker-compose logs nut_exporter
  ```

### Prometheus Configuration Errors
- Validate `prometheus.yml` syntax:
  ```bash
  promtool check config prometheus/prometheus.yml
  ```

### Alert Testing
- Simulate a UPS event and check for alerts firing in Prometheus:
  - Prometheus Alerts: http://localhost:9090/alerts
  - Grafana Alerts: http://localhost:3000

---

## Acknowledgments
This extension uses:
- **Network UPS Tools (NUT)** for UPS monitoring.
- **Prometheus** for metrics scraping and alerting.
- **Grafana** for dashboards and visualization.

---

For further details or issues, contact the repository maintainers.
