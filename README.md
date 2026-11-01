## 👋 Welcome to kimai 🚀

Web-based time-tracking application

## 📋 Description

Kimai is a web-based time-tracking application aimed at small and medium teams
and freelancers. It records timesheets against projects, activities and
customers, and stores its data in MariaDB.

## 🚀 Services

- **app**: kimai/kimai2:latest

### Infrastructure Components

- **db**: MariaDB database

## 📦 Installation

### Option 1: Quick Install

```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/kimai/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone

```bash
git clone "https://github.com/composemgr/kimai" ~/.local/srv/docker/kimai
cd ~/.local/srv/docker/kimai
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr

```bash
composemgr install kimai
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
APP_ADMIN_USER=admin
APP_ADMIN_PASS=replace-with-a-random-password
DB_USER_NAME=kimai
DB_USER_PASS=replace-with-a-random-password
DB_CREATE_DATABASE_NAME=kimai
EMAIL_SERVER_HOST=172.17.0.1
EMAIL_SERVER_PORT=587
EMAIL_SERVER_MAIL_FROM=no-reply@example.com
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64224` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

The proxy variants publish no host ports. The app is reachable only through the
proxy network, and the MariaDB service stays internal to the project network in
every variant.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64224

## 📂 Volumes

- `./volumes/data/kimai` - Application data storage
- `./volumes/config/kimai` - Local configuration overrides
- `./volumes/db/mariadb/kimai` - MariaDB database data

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

`TRUSTED_HOSTS` is set from `BASE_HOST_NAME`, so set that variable to the public
hostname before starting the stack or Kimai will reject proxied requests.

## 🔍 Logging

```shell
docker compose --env-file .env logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
