# VS Code: Code Server vs Apple Container - Setup Guide

## Quick Comparison

| Feature | Code Server | Apple Container |
|---------|-------------|-----------------|
| **What it is** | VS Code in browser ([vscode.dev](http://vscode.dev)) | Apple's new container framework for macOS (like Docker) [1] |
| **Platform** | Any device via browser | macOS only [1] |
| **Host** | Remote Linux server / MacBook | Local macOS container [2] |
| **VS Code Extension** | None (browser-based) | Dev Containers [3][2] |
| **Best For** | iPad/mobile coding, remote dev | Local macOS dev with containers |

***

## Option 1: Code Server (VS Code in Browser)

### Setup on MacBook (for iPad access)

```markdown
# 1. Install code-server via Homebrew
brew install code-server

# 2. Run code-server (manual mode)
brew services run code-server -v

# 3. Or register as auto-start service
brew services start code-server -v

# 4. Find password
cat ~/.config/code-server/config.yaml

# 5. Access locally
# http://127.0.0.1:8080
``` 

### Setup on Remote Linux Server

```markdown
# Install VS Code Server
wget -O- https://aka.ms/install-vscode-server/setup.sh | sh

# Start server
code-server

# Authenticate via GitHub tunnel
# Follow device code at: https://github.com/login/device
# Get generated vscode.dev URL
``` 

### Access from Any Device

```markdown
# From iPad/Blink Shell:
code https://your-vscode-dev-url.vscode.dev

# Or open browser directly
# https://your-device-name.vscode.dev
```

**Pros**: Works on any device, GitHub remote tunnels, no subscription[4][5]
**Cons**: Requires server setup, needs network access[4]

***

## Option 2: Apple Container (macOS Native)

Apple Container is a **new container framework** (similar to Docker) for macOS.

### Setup in VS Code

```markdown
# 1. Install Apple Container CLI
# (from GitHub: github.com/apple/container)

# 2. Create container
container run --rm -v ~/Developer:/workspace --user node node:24 sleep infinity

# 3. Enable experimental setting in VS Code
# cmd + shift + p → Settings → Enable:
# "devContainers.experimental苹果ContainerSupport": true

# 4. Attach to running container
# cmd + shift + p → "Dev Containers: Attach to Running Apple Container..."
# Select your container (e.g., swift-dev-ntp)
``` 

### VS Code Dev Container Setup

```json
// .devcontainer.json
{
  "name": "Node.js Dev Container",
  "image": "node:24",
  "workspaceFolder": "/workspace",
  "mounts": [
    "source=${localEnv:HOME}/Developer,target=/workspace,type=bind"
  ]
}
```

```markdown
# 1. Create dev container
container run -d --name node-dev node:24

# 2. Attach in VS Code
# cmd + shift + p → Dev Containers: Attach to Running Apple Container
``` 

**Pros**: Native macOS, no Docker Desktop, fast local dev[1][3]
**Cons**: macOS only, experimental support, port forwarding issues[3]

***

## Option 3: Docker + Code Server (Combined)

Run Code Server **inside** a Docker/Apple Container:

```markdown
# Docker + Code Server
docker run -d \
  -p 8080:8080 \
  -v ~/project:/home/coder/project \
  -e PASSWORD=yourpassword \
  coder/code-server:latest

# Access: http://localhost:8080
``` 

***

## Recommendation

| Your Goal | Best Option |
|-----------|-------------|
| **Code on iPad/mobile** | Code Server (Option 1) [4] |
| **Local macOS dev** | Apple Container (Option 2) [3][2] |
| **Remote Linux server** | Code Server on Linux (Option 1) [5] |
| **Both mobile + containers** | Docker + Code Server (Option 3) [6] |

### For Blink Shell + iPad:

```markdown
# Use Code Server (browser-based VS Code)
brew install code-server
brew services start code-server

# From iPad/Blink:
code https://localhost:8080
# Or: Open browser → https://127.0.0.1:8080
``` 

**Code Server** is the right choice if you want to use VS Code from **Blink Shell or iPad**. Apple Container is for **local macOS container development** with VS Code Desktop.

Sources
[1] Apple Container 0.9.0 https://news.ycombinator.com/item?id=46938181
[2] VSCode dev container settings #912 https://github.com/apple/container/discussions/912
[3] Support for the Containerization Framework on macOS https://github.com/microsoft/vscode-remote-release/issues/11012
[4] Setting up your MacBook to run VSCode anywhere using ... https://medium.com/@gdimitro/setting-up-your-macbook-to-run-vscode-anywhere-using-code-server-b7ee5e32b3a4
[5] The Visual Studio Code Server https://code.visualstudio.com/blogs/2022/07/07/vscode-server
[6] My coding environment in docker with Codeserver https://www.reddit.com/r/docker/comments/smm4xg/my_coding_environment_in_docker_with_codeserver_a/
[7] Remote Docker Visual Studio Code - No running containers https://stackoverflow.com/questions/61557492/remote-docker-visual-studio-code-no-running-containers-mac-os
[8] Is there an open source alternative to use vscode remote ... https://www.reddit.com/r/docker/comments/rct2ve/is_there_an_open_source_alternative_to_use_vscode/
[9] VS Code Remote Containers https://docs.rancherdesktop.io/how-to-guides/vs-code-remote-containers
[10] coder/code-server: VS Code in the browser https://github.com/coder/code-server
