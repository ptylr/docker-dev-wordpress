```
        __          .__
_______/  |_ ___.__.|  |_______
\____ \   __<   |  ||  |\_  __ \
|  |_> >  |  \___  ||  |_|  | \/
|   __/|__|  / ____||____/__|
|__|         \/

https://ptylr.com
https://www.linkedin.com/in/ptylr/
```
# 🐳 WordPress + MariaDB + ngrok (Docker) — Local Development Setup

This repository provides a **Docker-based WordPress development environment** with:

- `wordpress:php8.2-apache` (WordPress with Apache)
- `mariadb:10.6` (MariaDB database)
- `ngrok` (for public tunneling)

> ⚠️ **This is for development purposes only. Do NOT use this setup in production.**

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/ptylr/docker-dev-wordpress.git
cd docker-dev-wordpress
```

### 2. Create `.env`

Create a `.env` file with these values:

```env
# WordPress DB settings
WORDPRESS_DB_HOST=db:3306
WORDPRESS_DB_NAME=wordpress
WORDPRESS_DB_USER=wordpress
WORDPRESS_DB_PASSWORD=wordpress

# MariaDB settings
MYSQL_DATABASE=wordpress
MYSQL_USER=wordpress
MYSQL_PASSWORD=wordpress
MYSQL_ROOT_PASSWORD=rootpass
```

---

## 🌐 Public Tunneling with ngrok
This setup includes an `ngrok` container to expose your local WordPress site to the internet via secure tunnels.

### 3. Configure ngrok
1. Copy the example config:
```bash
cp ngrok.yml.example ngrok.yml
```

2. Edit `ngrok.yml` to include your **authtoken** from [https://dashboard.ngrok.com](https://dashboard.ngrok.com):
```yaml
authtoken: YOUR_NGROK_AUTH_TOKEN
tunnels:
  wordpress:
    proto: http
    addr: wordpress-app:80
```

> You can rename the tunnel or expose other ports if needed.

---

### 4. Start the Environment
```bash
docker-compose up -d --build
```

---

### 5. Access WordPress

- Local: [http://https://your-subdomain.ngrok-free.app](http://https://your-subdomain.ngrok-free.app)
- Public (ngrok): After `docker-compose` starts, look in the logs:

```bash
docker logs -f wordpress-ngrok
```

You'll see a forwarding URL like:

```
Forwarding http://your-subdomain.ngrok-free.app -> http://wordpress-app:80
```

Visit that URL from anywhere.

---

## 🧹 Cleanup

```bash
docker-compose down -v
```

---

## 📂 Docker Services Overview

| Service     | Description                        | Port        |
|-------------|------------------------------------|-------------|
| `wordpress` | WordPress running on Apache        | `80:80`     |
| `db`        | MariaDB database                   | Internal    |
| `ngrok`     | Secure tunnel to WordPress         | auto        |

---

##  Legal Notices
This is an example solution subject to the [MIT license](./LICENSE).

## Disclaimer

This setup is **not hardened** and **not secure**. It is designed for **local development only**.  
Do **not** use this configuration in production environments.

This document is provided for information purposes only. Paul Taylor may change the contents hereof without notice. This document is not warranted to be error-free, nor subject to any other warranties or conditions, whether expressed orally or implied in law, including implied warranties and conditions of merchantability or fitness for a particular purpose. Paul Taylor specifically disclaims any liability with respect to this document and no contractual obligations are formed either directly or indirectly by this document. The technologies, functionality, services, and processes described herein are subject to change without notice.
