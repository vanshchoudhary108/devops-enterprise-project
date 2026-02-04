# Automated DevOps Infrastructure Project

This project demonstrates an end-to-end DevOps automation workflow using
Git, Jenkins, Docker, Ansible, Terraform, and Nagios.

---

## Tools & Technologies
- Git & GitHub
- Jenkins
- Docker
- Ansible
- Terraform
- Nagios
- Linux (Ubuntu / WSL)

---

## Nagios Monitoring (Docker)

Nagios is deployed inside a Docker container to monitor system and service health.

### Monitored Services
- HTTP Service
- Disk Usage
- Swap Usage
- Load Average

### Features
- Service health monitoring
- HTTP warning & critical state handling
- Docker-based Nagios deployment

### Access Nagios UI
http://localhost:8095

### Run Nagios Container
```bash
docker run -d --name nagios -p 8095:80 nagios/nagios

