# Nginx Traffic Manager

An open-source alternative to F5 BIG-IP, built on Nginx and delivered as a single Docker image. Manage load balancing, traffic routing, SSL certificates, and health monitoring through a modern web UI.

## Features

### Core
- **Virtual Servers** - Create and manage Nginx server blocks with a visual interface
- **Pools & Members** - Backend server management with health status tracking
- **Load Balancing** - Multiple algorithms: round-robin, least connections, IP hash, weighted
- **Health Monitors** - Automated HTTP/TCP/ICMP health checks with configurable thresholds
- **SSL/TLS Management** - Certificate management with Let's Encrypt integration and SSL offloading

### Advanced
- **Traffic Policies** - Conditional routing, URL rewrites, header manipulation, and redirects
- **Rate Limiting** - Request throttling and basic WAF capabilities
- **Session Persistence** - Cookie-based and source IP persistence
- **Monitoring & Analytics** - Real-time dashboard with traffic metrics, logs, and alerts
- **Authentication & RBAC** - Role-based access control for the management interface

### Planned
- **High Availability** - Multi-container failover and clustering
- **API Gateway** - API-specific traffic management features
- **Advanced WAF** - Extended web application firewall rules

## Tech Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| Reverse Proxy | Nginx | Core traffic management engine |
| Backend API | Go | System operations, config management, REST API |
| Frontend | Next.js + Tailwind CSS + shadcn/ui | Management web interface |
| Database | PostgreSQL | Configuration persistence, logs, metrics |
| Container | Docker (multi-stage build) | Single-image deployment |

## Quick Start

### Using Docker

```bash
docker pull tchevalleraud/nginx-traffic-manager:latest

docker run -d \
  --name nginx-traffic-manager \
  -p 81:81 \
  -p 80:80 \
  -p 443:443 \
  tchevalleraud/nginx-traffic-manager:latest
```

### Using Docker Compose

```yaml
version: "3.8"

services:
  nginx-traffic-manager:
    image: tchevalleraud/nginx-traffic-manager:latest
    ports:
      - "81:81"    # Management UI
      - "80:80"    # HTTP traffic
      - "443:443"  # HTTPS traffic
    volumes:
      - ntm-data:/var/lib/postgresql/data
      - ntm-certs:/etc/nginx/certs
    restart: unless-stopped

volumes:
  ntm-data:
  ntm-certs:
```

### Access the Management UI

Open your browser and navigate to `http://localhost:81`. Default credentials:

- **Username:** `admin`
- **Password:** `admin`

> You will be prompted to change the default password on first login.

## Network Interfaces

The container supports multiple network interfaces to isolate management traffic from application traffic. Network interfaces can be added and mapped directly from the web UI — no need to modify your Docker Compose file.

Simply attach additional Docker networks to the container, then assign their roles (Management, Traffic IN, Traffic OUT) through the management interface.

## Project Structure

```
/
├── frontend/          # Next.js application
├── backend/           # Go application
├── docker/            # Docker configuration files
├── nginx/             # Default Nginx configs & templates
├── docs/              # Documentation (EN + FR)
├── .github/           # GitHub Actions workflows
├── tests/             # E2E tests
├── Dockerfile
└── docker-compose.yml
```

## Development

### Prerequisites

- Docker & Docker Compose
- Go 1.22+
- Node.js 20+
- PostgreSQL 16+ (for local development)

### Local Setup

```bash
git clone https://github.com/tchevalleraud/nginx-traffic-manager.git
cd nginx-traffic-manager
docker compose up -d
```

## Documentation

Full documentation is available at [tchevalleraud.github.io/nginx-traffic-manager](https://tchevalleraud.github.io/nginx-traffic-manager/), in both English and French.

## Contributing

Contributions are welcome! Please read the contributing guidelines before submitting a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
