# Nagios Monitoring Project (Docker)

## Tools Used
- Nagios Core
- Docker
- Linux (Ubuntu / WSL)
- Git & GitHub

## Project Description
This project demonstrates monitoring of system services using Nagios
running inside a Docker container.

## Monitored Services
- HTTP Service
- Disk Usage
- Swap Usage
- Load Average

## Features
- Service health monitoring
- HTTP warning & critical state handling
- Docker-based Nagios deployment

## How to Run
```bash
docker run -d --name nagios -p 8095:80 nagios/nagios

