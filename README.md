# Docker - Sons of the Forest Dedicated Server with RedLoader

Docker image for Sons of the Forest dedicated server with pre-installed RedLoader.

## Quick Start

```yaml
# docker-compose.yml
version: '3.9'
services:
  sons-of-the-forest-dedicated-server-redloader:
    container_name: sons-of-the-forest-dedicated-server-redloader
    image: dontworryimmafine/sons-of-the-forest-dedicated-server-redloader:latest
    restart: always
    environment:
      PUID: 1000
      PGID: 1000
      ALWAYS_UPDATE_ON_START: true
      SKIP_NETWORK_ACCESSIBILITY_TEST: true
      FILTER_SHADER_AND_MESH_AND_WINE_DEBUG: true
      ENABLE_REDLOADER: true
      REDLOADER_VERSION: 0.7.3 # Latest stable version for linux
    ports:
      - "0.0.0.0:8766:8766/udp"
      - "0.0.0.0:27016:27016/udp"
      - "0.0.0.0:9700:9700/udp"
    volumes:
      - ./game:/sonsoftheforest
    # GPU devices - Uncomment for NAS systems with Intel integrated graphics (QNAP, Synology, etc.)
    # Check if devices exist: ls /dev/dri/
    # devices:
    #   - /dev/dri/renderD128:/dev/dri/renderD128
    #   - /dev/dri/card0:/dev/dri/card0
```

### Environment Variables
ALWAYS_UPDATE_ON_START - automatic server updates on startup  (default: true)

SKIP_NETWORK_ACCESSIBILITY_TEST - skip network accessibility test  (default: true)

FILTER_SHADER_AND_MESH_AND_WINE_DEBUG - filter shader warnings from logs (default: true)

ENABLE_REDLOADER - determine if the RedLoader should be installed or not (default: true)

REDLOADER_VERSION - RedLoader version. (default: 0.7.3)

## Features
Automatic RedLoader installation

Auto-update support via ALWAYS_UPDATE_ON_START

Optimized logs with shader warning filtering

Based on the original jammsen repository

##  Links
[Original Repository](https://github.com/jammsen/docker-sons-of-the-forest-dedicated-server)

[RedLoader](https://github.com/ToniMacaroni/RedLoader)
