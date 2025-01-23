# METDPG-UPS-MONITORING
Description for UPS Monitoring in the Repository
Project Title:
UPS Monitoring System Extension for MET-DPG Monitoring

Overview:
This project extends the existing MET-DPG Monitoring system by integrating UPS (Uninterruptible Power Supply) monitoring. The UPS monitoring setup leverages Network UPS Tools (NUT), Prometheus, and Grafana to provide real-time tracking of UPS performance, ensuring enhanced visibility of backup power systems in critical environments.

Features:
Real-Time Monitoring:
Tracks UPS metrics such as battery charge, input/output voltage, load, and runtime.
Customizable Alerts:
Alerts for critical events like low battery, input voltage loss, or system overload.
Grafana Dashboards:
Visual representation of UPS status and performance metrics.
Scalable Integration:
Easily integrates with existing monitoring setups.
Purpose:
To ensure power reliability by monitoring UPS devices and alerting users of any anomalies that may affect system availability.

What to Include in the Repository
1. Updated Repository Structure:
Include the following directories/files:

nut/: Contains NUT configuration files.
ups.conf: Configuration for connected UPS devices.
upsd.users: Authentication for NUT monitoring users.
docker-compose.yml: Updated to include the NUT Exporter service.
prometheus/:
prometheus.yml: Updated to include the NUT Exporter scrape job.
alert_rules.yml: New alert rules for UPS monitoring.
grafana/:
Preconfigured JSON files for Grafana dashboards (e.g., UPS_Monitoring_Dashboard.json).
README.md: Updated documentation for setup and usage.
2. README Documentation:
Include detailed setup instructions. Example structure:

Title:
UPS Monitoring System Extension for MET-DPG Monitoring

Sections:
Overview
Brief explanation of the UPS monitoring system and its purpose.

System Requirements

NUT
Docker & Docker Compose
Prometheus
Grafana
Setup Instructions

Install Dependencies:
NUT installation and configuration.
Docker and Git setup.
Clone the Repository:
bash
Copy
Edit
git clone git@github.com:metdpg/monitoring.git
cd monitoring
Add UPS Monitoring:
Configure UPS details in nut/ups.conf.
Add the NUT Exporter service in docker-compose.yml.
Prometheus Configuration:
Add NUT Exporter scrape job to prometheus/prometheus.yml.
Grafana Integration:
Import UPS Monitoring Dashboard.
Configure Alerts:
Define UPS-related alerts in prometheus/alert_rules.yml.
Usage

Commands to start, stop, and restart the system:
bash
Copy
Edit
docker compose up -d
docker compose stop
docker compose restart
Accessing dashboards in Grafana.
Testing alerts with a simulated UPS event.
Troubleshooting

Common issues and their resolutions (e.g., NUT service not starting, exporter not reachable).
Maintenance

Instructions for disk space management, log monitoring, and Docker image updates.
Acknowledgments

Mention of tools like NUT, Prometheus, Grafana, and contributors.
3. Example Files:
prometheus.yml.example: Include a configured example with NUT Exporter settings.
alert_rules.yml.example: Predefined UPS alert rules.
UPS_Monitoring_Dashboard.json: Exported Grafana dashboard for easy import.
Additional Notes:
Ensure all new configurations (e.g., UPS-specific settings) are optional and do not disrupt the existing monitoring system.
Test all configurations before pushing changes to the repository.
Document any changes made to the existing files in a changelog or commit history.
Overview: This project extends the existing MET-DPG Monitoring system by integrating UPS (Uninterruptible Power Supply) monitoring. The UPS monitoring setup leverages Network UPS Tools (NUT), Prometheus, and Grafana to provide real-time tracking of UPS performance, ensuring enhanced visibility of backup power systems in critical environments.
