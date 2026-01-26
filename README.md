## 👋 Welcome to kimai 🚀

Web-based time-tracking application

## 📋 Description

Web-based time-tracking application

## 🚀 Services

- **kimai**: kimai/kimai2:latest

### Infrastructure Components

- **kimai-db**: Mariadb database


## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/kimai/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/kimai" ~/.local/srv/docker/kimai
cd ~/.local/srv/docker/kimai
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install kimai
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:8075

## 📂 Volumes

- `./rootfs/data/kimai` - Data storage
- `./rootfs/config/kimai` - Data storage
- `./rootfs/data/db/mariadb/kimai` - Data storage

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose logs -f kimai
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
