# DevOps Assignment: Nginx Reverse Proxy with Microservices

This project demonstrates a containerized microservice architecture using **Docker Compose**, featuring:
- A reverse proxy using **Nginx**
- Two backend services (Service 1 in Go, Service 2 in Python-Flask)
- Healthchecks and clear structured logging

---

## Project Structure

```
.
├── docker-compose.yml
├── nginx/
│   ├── nginx.conf
│   └── Dockerfile
├── service_1/           # Go service
│   ├── app.go
│   ├── Dockerfile
│   └── ... 
├── service_2/           # Python Flask service
│   ├── app.py
│   ├── Dockerfile
│   └── ...
```

---

## ⚙️ Services Overview

### Service 1 – Go

- Simple Go-based service that returns a message.
- **Endpoints:**
  - `GET /ping`: Health check
  - `GET /hello`: Returns greeting from service 1

---

### Service 2 – Python + Flask

- Python Flask API with structured logging.
- **Endpoints:**
  - `GET /ping`: Health check
  - `GET /hello`: Returns greeting from service 2
- Uses Python `logging` module for clarity.

---

## Nginx Reverse Proxy

Nginx listens on port **8080** and routes traffic to the appropriate service:

| URL                                | Proxied To                 |
|-----------------------------------|----------------------------|
| `http://localhost:8080/service1/` | `http://service_1:8001/`   |
| `http://localhost:8080/service2/` | `http://service_2:8002/`   |

---

## How to Run

Make sure you have Docker and Docker Compose installed.

```bash
git clone https://github.com/yourusername/devops-nginx-proxy.git
cd devops-nginx-proxy
docker compose up --build
```

Then visit in your browser or test via curl:

- `http://localhost:8080/service1/hello`
- `http://localhost:8080/service2/hello`

---

## Healthchecks

Both services are monitored with Docker Compose healthchecks:

- Service 1: `http://localhost:8001/health`
- Service 2: `http://localhost:8002/health`

---

## Logging

Flask logs are now structured using Python’s `logging` module:

```bash
2025-06-28 10:45:13 [INFO] Incoming GET request to /ping
2025-06-28 10:45:13 [INFO] Health check ping received
```

This improves **debuggability** and meets bonus point criteria.

---

## Bonus Improvements Implemented

✅ **Logging Clarity**  
✅ **Modular Docker Setup**  
✅ **Healthcheck Integration**  

---

## 📌 Author

**Snehil Singh**  
DevOps Enthusiast | Intern Applicant at DPDzero
