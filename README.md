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
# 🐳 docker-dev-wordpress: WordPress + MariaDB (Docker) — Local Development Setup
This repository provides a **lightweight, Docker-based WordPress environment** using:

- `wordpress:php8.2-apache` *(or `php8.2-fpm-alpine` + Nginx if you prefer)*
- `mariadb:10.6`
- Docker Compose

> ⚠️ **This setup is for development purposes only. It is not intended for production use.**

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/ptylr/docker-dev-wordpress.git
cd docker-dev-wordpress
```

### 2. Create `.env` File

Create a `.env` file based on the provided template. It defines database credentials and WordPress environment variables.

```env
# .env

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

### 3. Start the Containers

```bash
docker-compose up -d
```

### 4. Access WordPress

Open your browser and go to:

```
http://localhost:8080
```

Follow the WordPress installer to complete setup.

---

## 🛠️ Included Services

| Service     | Image                        | Port(s)     | Purpose              |
|-------------|------------------------------|-------------|----------------------|
| WordPress   | `wordpress:php8.2-apache`    | `8080:80`   | WordPress app server |
| MariaDB     | `mariadb:10.6`               | Internal    | MySQL-compatible DB  |

---

## 🧹 Cleanup

To stop and remove containers, networks, and volumes:

```bash
docker-compose down -v
```

---

## ⚠️ Disclaimer

This setup is **not hardened** and **not secure**. It is designed for **local development only**.  
Do **not** use this configuration in production environments.

---

##  Legal Notices
This is an example solution subject to the [MIT license](./LICENSE).

## Disclaimer
This document is provided for information purposes only. Paul Taylor may change the contents hereof without notice. This document is not warranted to be error-free, nor subject to any other warranties or conditions, whether expressed orally or implied in law, including implied warranties and conditions of merchantability or fitness for a particular purpose. Paul Taylor specifically disclaims any liability with respect to this document and no contractual obligations are formed either directly or indirectly by this document. The technologies, functionality, services, and processes described herein are subject to change without notice.
