# Two-Tier Flask Application (Flask + MySQL)

## Overview

This repository demonstrates a **production-style DevOps deployment** of a **two-tier web application** using **Flask** and **MySQL**, containerized with **Docker**, orchestrated using **Docker Compose**, and deployed to **AWS EC2** via a **GitHub Actions CI/CD pipeline**.

> The focus of this project is **infrastructure, automation, and reliability**, not application complexity.

---

## What the Application Does

* Users access the app via the EC2 public IP
* Users submit messages through a simple UI
* Messages are stored in a MySQL database
* Stored messages persist and are displayed on page reload

This demonstrates **stateful persistence with a stateless application layer**.

---

## Architecture

```
Browser
  ↓
EC2 (Port 80)
  ↓
Flask Container
  ↓
MySQL Container
```

Containers communicate over a **custom Docker network** using service discovery.

---

## CI/CD Pipeline Purpose

The GitHub Actions pipeline automates deployment on every push to the `main` branch.

**Pipeline responsibilities:**

* Checkout source code
* Run on a self-hosted EC2 runner
* Build and deploy containers with Docker Compose
* Inject secrets securely at runtime
* Restart services and verify health

This ensures **consistent, repeatable, and automated deployments**.

---

## DevOps Best Practices Used

* Dockerized application and database
* Multi-container orchestration with Docker Compose
* Environment-based configuration (12-factor principles)
* Secrets management via GitHub Actions
* Health checks and dependency handling
* Persistent storage using Docker volumes
* Clear separation of application and data tiers

---

## How to Run Locally

```bash
git clone https://github.com/r94l/aws-devops-docker-compose
cd aws-devops-docker-compose
docker compose up -d
```

Access the app:

```
http://localhost:80
```

---

✔ Project completed
✔ CI/CD functional
