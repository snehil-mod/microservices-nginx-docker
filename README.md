# DevOps Assignment: Nginx Reverse Proxy + Docker Compose

## Setup Instructions

1. Clone the repository and navigate to the project root.
2. Build and start all services with:
   ```
   docker-compose up --build
   ```
3. Access services via:
   - http://localhost:8080/service1
   - http://localhost:8080/service2

## Routing
- Nginx reverse proxy routes:
  - `/service1` → Go backend (service_1)
  - `/service2` → Python backend (service_2)
- All services are accessible via a single port (8080).

## Health Checks
- Both services have health checks configured in `docker-compose.yml`.

## Logging
- Nginx logs all incoming requests with timestamp and path.

## Bonus
- Health checks for both services.
- Modular Docker setup.


http://localhost:8080/service1/ping
http://localhost:8080/service1/hello
http://localhost:8080/service2/ping
http://localhost:8080/service2/hello