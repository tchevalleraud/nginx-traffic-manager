# Nginx Traffic Manager

An open-source alternative to F5 BIG-IP, built on Nginx and delivered as a single Docker image.

Manage load balancing, traffic routing, SSL certificates, and health monitoring through a modern web UI.

## Key Features

- **Virtual Servers** - Create and manage Nginx server blocks with a visual interface
- **Pools & Members** - Backend server management with health status tracking
- **Load Balancing** - Multiple algorithms: round-robin, least connections, IP hash, weighted
- **Health Monitors** - Automated HTTP/TCP/ICMP health checks with configurable thresholds
- **SSL/TLS Management** - Certificate management with Let's Encrypt integration
- **Network Interfaces** - Multi-interface support configurable from the web UI
- **Monitoring & Analytics** - Real-time dashboard with traffic metrics and logs

## Quick Start

```bash
docker run -d \
  --name nginx-traffic-manager \
  -p 81:81 \
  -p 80:80 \
  -p 443:443 \
  tchevalleraud/nginx-traffic-manager:latest
```

Then open [http://localhost:81](http://localhost:81) to access the management UI.
