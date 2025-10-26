🌐 Cloudflare Tunnel Configuration

This document outlines the current configuration for secure external access using the Cloudflare Tunnel service, provided by the ephemeral cloudflared_temp_delete container.

🔗 Tunnel Details

Setting

Value

Tunnel ID

f0b0cf34-7d17-4a00-b465-08d2c0571f4f

Cloudflared Version

$2025.7.0$

Protocol

QUIC

Metrics Server Port

$20241$

Connection Status

Active ($4$ connections to Cloudflare edge)

Locations

yyz03, yyz04, yyz06 (Toronto region)

⚙️ Configured Ingress Rules

The tunnel uses the following ingress rules to map public hostnames to internal service addresses, providing a secure bridge without direct port exposure.

Hostname

Destination (Internal)

Notes

nextcloud.visionvation.com

https://10.10.10.131:8443

HTTP/2, no TLS verify

grafana.visionvation.com

http://10.10.10.131:3000

Redirecting to a specific Grafana instance.

plex.visionvation.com

http://plex:32400

Direct service name resolution.

ssh.visionvation.com

ssh://10.10.10.132:22

Secure Shell access to the host.

laravel.visionvation.com

http://10.10.10.10:80

External/Legacy Service Mapping.

laravel-ssh.visionvation.com

ssh://10.10.10.10:22

External/Legacy Service Mapping.

neko.visionvation.com

http://10.10.10.10:8080

External/Legacy Service Mapping.

Default

http_status:404

Catch-all rule for undefined routes.

🔒 Security Features

Encrypted Tunnels: All traffic is secured via Cloudflare's network.

No Direct Port Exposure: Services are accessible only through the tunnel; no host ports are opened to the public internet.

ICMP Proxy: IPv4 ($172.24.0.2$) and IPv6 ($::1$) support is configured.
