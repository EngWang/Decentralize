# OpenWhisk Infrastructure Scripts

## Overview
This repository contains scripts for deploying and managing an Apache OpenWhisk cluster.

## Prerequisites
- Docker
- Docker Compose

## Quick Start

### Method 1: Using individual scripts
```bash
# Make scripts executable
chmod +x *.sh

# Deploy cluster
./deploy-openwhisk.sh

# Check status
./health-check.sh

# Monitor resources
./monitor-resources.sh
