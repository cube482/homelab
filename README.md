# homelab

A fully containerized homelab running on a single Debian server, publicly accessible via a custom domain. All services are orchestrated with Docker Compose and managed through Dockge.

## Hardware

- **CPU:** AMD Ryzen 5700G
- **OS:** Debian Linux
- **Network:** UniFi — 19 VLANs across 3 sites

## Services

| Service | Description |
|---|---|
| [Caddy](https://caddyserver.com) | Reverse proxy with automatic HTTPS via Cloudflare DNS |
| [Nextcloud](https://nextcloud.com) | Self-hosted file storage |
| [Vaultwarden](https://github.com/dani-garcia/vaultwarden) | Self-hosted Bitwarden-compatible password manager |
| [Frigate](https://frigate.video) | NVR with object detection for 7 IP cameras across 3 sites |
| [Pi-hole](https://pi-hole.net) | Network-wide DNS ad blocking |
| [Uptime Kuma](https://github.com/louislam/uptime-kuma) | Service uptime monitoring with Discord alerts |
| [Grafana](https://grafana.com) | Server and container metrics dashboard |
| [Prometheus](https://prometheus.io) | Metrics collection |
| [cAdvisor](https://github.com/google/cadvisor) | Docker container resource usage |
| [Homepage](https://gethomepage.dev) | Self-hosted dashboard |
| [Dockge](https://github.com/louislam/dockge) | Docker Compose stack manager |

## Network

- **Sites:** Home, Speedalice Nails, The Jangwon
- **VLANs:** 19 total across all sites
  - Secure devices, infrastructure, IoT, VPN clients, POS, surveillance, guest WiFi, staff WiFi, VoIP
- **Remote access:** WireGuard, Unifi site-to-site VPN
- **DNS:** Cloudflare with Pi-hole for local ad blocking
- **Security:** PCI-DSS informed segmentation for POS systems

## Cameras

7 IP cameras across 3 sites feeding into Frigate for NVR and object detection:
- **Speedalice Nails:** parking lot, front section, middle section, pedicure section
- **The Jangwon:** front, back, rear

## Structure

```
homelab/
├── caddy/          # Reverse proxy config and Caddyfile
├── nextcloud/      # File storage stack
├── vaultwarden/    # Password manager stack
├── frigate/        # NVR stack and camera config
├── pihole/         # DNS stack
├── uptime/         # Uptime Kuma stack
├── monitoring/     # Grafana + Prometheus + cAdvisor stack
├── homepage/       # Dashboard config
└── dockge/         # Stack manager
```

## Secrets

All sensitive values are stored in `.env` files and are not committed to this repository. See each service directory for a corresponding `.env.example`.
