# Installation

## Using Docker

```bash
docker pull tchevalleraud/nginx-traffic-manager:latest

docker run -d \
  --name nginx-traffic-manager \
  -p 81:81 \
  -p 80:80 \
  -p 443:443 \
  tchevalleraud/nginx-traffic-manager:latest
```

## Using Docker Compose

```yaml
version: "3.8"

services:
  nginx-traffic-manager:
    image: tchevalleraud/nginx-traffic-manager:latest
    ports:
      - "81:81"
      - "80:80"
      - "443:443"
    volumes:
      - ntm-data:/var/lib/postgresql/data
      - ntm-certs:/etc/nginx/certs
    restart: unless-stopped

volumes:
  ntm-data:
  ntm-certs:
```

## First Login

Open your browser and navigate to `http://localhost:81`.

Default credentials:

- **Username:** `admin`
- **Password:** `admin`

!!! warning
    You will be prompted to change the default password on first login.
