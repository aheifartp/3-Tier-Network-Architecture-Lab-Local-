# 🔒 Nginx Reverse Proxy + HTTPS (Self-Signed SSL)

## Overview
Menambahkan Nginx sebagai reverse proxy di depan Apache, dengan HTTPS menggunakan self-signed SSL certificate.

## Topology
Client PC → Nginx (:443 HTTPS) → Apache (:8080) → PHP/WordPress

## Tech Stack
- Nginx 1.28
- OpenSSL (Self-Signed Certificate)
- Apache2 (dipindah ke port 8080)

## Key Configurations
1. **Apache dipindah ke port 8080** - edit `/etc/apache2/ports.conf` dan virtualhost
2. **Self-signed SSL certificate** - generate dengan openssl, validity 365 hari
3. **Nginx reverse proxy** - listen 80 & 443, forward ke localhost:8080
4. **HTTP → HTTPS redirect** - return 301

## How to Run
```bash
sudo systemctl start nginx
sudo systemctl start apache2
```

## Troubleshooting
- Jika port 80 conflict: pastikan Apache sudah pindah ke 8080
- Jika SSL error: cek path certificate di nginx config
