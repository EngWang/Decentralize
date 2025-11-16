
# 🚀 OpenWhisk Infrastructure Deployment

Complete infrastructure setup for Apache OpenWhisk including CouchDB and Nginx gateway.

## 📋 PREREQUISITES

- **Docker** (version 20.10+)
- **Docker Compose** (version 2.0+)
- **curl** (for health checks)

### Verify Installation
```bash
docker --version
docker-compose --version
curl --version
```

## 🚀 QUICK DEPLOYMENT

### Method 1: Using Deployment Script (Recommended)
```bash
# Make scripts executable
chmod +x *.sh

# Deploy full infrastructure
./deploy-openwhisk.sh

# Verify deployment
./health-check.sh
```

### Method 2: Using Docker Compose
```bash
# Deploy with Docker Compose
docker-compose up -d

# Check status
docker-compose ps
```

## 📊 DEPLOYED SERVICES

| Service | Port | Purpose | Access URL |
|---------|------|---------|------------|
| CouchDB | 5984 | Database | http://localhost:5984/_utils |
| Nginx | 8080 | API Gateway | http://localhost:8080 |

**Credentials:** admin/password

## 🛠️ MANAGEMENT SCRIPTS

| Script | Purpose | Command |
|--------|---------|---------|
| `deploy-openwhisk.sh` | Full deployment | `./deploy-openwhisk.sh` |
| `start-cluster.sh` | Start services | `./start-cluster.sh` |
| `stop-cluster.sh` | Stop services | `./stop-cluster.sh` |
| `health-check.sh` | Health verification | `./health-check.sh` |
| `monitor-resources.sh` | System monitoring | `./monitor-resources.sh` |
| `logs-couchdb.sh` | CouchDB logs | `./logs-couchdb.sh` |
| `logs-nginx.sh` | Nginx logs | `./logs-nginx.sh` |
| `cleanup.sh` | Remove everything | `./cleanup.sh` |

## 🔧 DETAILED USAGE GUIDE

### 1. Initial Setup
```bash
# Create directory and copy all scripts
mkdir openwhisk-infra
cd openwhisk-infra

# Make scripts executable
chmod +x *.sh
```

### 2. Deployment
```bash
# Deploy infrastructure
./deploy-openwhisk.sh

# Wait for completion (takes 30-60 seconds)
# Check status
./health-check.sh
```

### 3. Verification
```bash
# Check all services are healthy
./health-check.sh

# Monitor system resources
./monitor-resources.sh

# Test CouchDB connection
curl http://localhost:5984/

# Test Nginx
curl http://localhost:8080/health
```

### 4. Daily Operations
```bash
# Stop services (preserves data)
./stop-cluster.sh

# Start services
./start-cluster.sh

# View real-time logs
./logs-couchdb.sh
./logs-nginx.sh
```

## 🎯 ACCESS POINTS

- **CouchDB Fauxton UI**: http://localhost:5984/_utils
- **Nginx Gateway**: http://localhost:8080
- **CouchDB Admin**: http://localhost:5986/_utils

## 🔍 TROUBLESHOOTING

### Port Conflicts
```bash
# Check what's using ports
sudo netstat -tulpn | grep :5984
sudo netstat -tulpn | grep :8080
```

### CouchDB Not Starting
```bash
# Check logs
docker logs couchdb

# Wait longer (CouchDB takes 30+ seconds to initialize)
sleep 40 && ./health-check.sh
```

### Permission Issues
```bash
# Fix script permissions
chmod +x *.sh

# Run with sudo if needed
sudo ./deploy-openwhisk.sh
```

## 🧹 MAINTENANCE

### Regular Checks
```bash
# Daily health check
./health-check.sh

# Resource monitoring
./monitor-resources.sh
```

### Complete Reset
```bash
# Remove everything (including data)
./cleanup.sh

# Redeploy fresh
./deploy-openwhisk.sh
```

## 📝 SCRIPT DETAILS

### deploy-openwhisk.sh
- Creates Docker network
- Deploys CouchDB with persistence
- Deploys Nginx as API gateway
- Initializes CouchDB databases
- Waits for services to be ready

### health-check.sh
- Checks container status
- Verifies HTTP endpoints
- Reports service health
- Shows port availability

### monitor-resources.sh
- Displays CPU/RAM/Disk usage
- Shows Docker container status
- Provides log previews
- Checks network connectivity

## ⚠️ IMPORTANT NOTES

1. **First deployment takes 30-60 seconds** for CouchDB initialization
2. **Data persistence** is enabled for CouchDB
3. **Port 8080** is used for Nginx to avoid conflicts
4. **Cleanup script removes all data** - use with caution
5. **Credentials** are set to admin/password - change for production

## 🆘 SUPPORT

### Quick Diagnostics
```bash
# Full system check
./health-check.sh && ./monitor-resources.sh

# Log investigation
./logs-couchdb.sh
```

### Common Issues
- **Port 5984 busy**: Stop other CouchDB instances
- **Port 8080 busy**: Change port in docker-compose.yml
- **CouchDB slow**: Wait 30+ seconds for initialization
- **Permission denied**: Run with `chmod +x *.sh`

## 📞 NEXT STEPS

After successful infrastructure deployment:
1. Build OpenWhisk components from source
2. Configure OpenWhisk to use this CouchDB instance
3. Deploy OpenWhisk Controller and Invokers
4. Set up Nginx reverse proxy for OpenWhisk API

