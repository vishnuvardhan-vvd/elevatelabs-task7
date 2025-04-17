# Netdata System Monitoring with Docker

This project sets up **Netdata**, a powerful, lightweight, real-time monitoring tool, using **Docker**. It helps visualize your system's performance metrics such as CPU, memory, disk usage, and running containers.

# Objectives

- Install Netdata via Docker
- Access the monitoring dashboard
- View system metrics (CPU, Memory, Disk, Network, etc.)
- Understand lightweight monitoring for servers or apps

---

# Prerequisites

- Docker installed and running on your machine  
  (Check by running `docker --version` in your terminal)

---

# Installation & Usage

# 1. Pull and Run Netdata Container

Run this command in your terminal or PowerShell (one single line):

code:
docker run -d --name=netdata -p 19999:19999 --cap-add SYS_PTRACE --security-opt apparmor=unconfined -v netdataconfig:/etc/netdata -v netdatalib:/var/lib/netdata -v netdatacache:/var/cache/netdata -v /etc/passwd:/host/etc/passwd:ro -v /etc/group:/host/etc/group:ro -v /proc:/host/proc:ro -v /sys:/host/sys:ro -v /etc/os-release:/host/etc/os-release:ro netdata/netdata


> **Tip:** If this is too complex, you can run a simpler version:
> bash
> docker run -d --name=netdata -p 19999:19999 netdata/netdata



# 2. Access the Dashboard

Open your browser and go to:


http://localhost:19999


- If prompted to sign in, click **"Continue without signing in"** or try going directly to:
  
  http://localhost:19999/#menu_system
  

# 3. Features to Explore

- **CPU, Memory, Disk, Network** usage
- Docker container metrics (if running any)
- Real-time chart panels
- Alerts and system health checks
- Logs (inside container: `/var/log/netdata`)


# Screenshot

> Include a screenshot of your dashboard here after setup  
> (e.g., showing system metrics like CPU and Memory)


# Troubleshooting

- Make sure Docker is running.
- If port 19999 is in use, change it in the `-p` flag (e.g., `-p 20000:19999`)
- If the dashboard doesn't load, try restarting the container:
  code:
  docker restart netdata
  
# Cleanup

To stop and remove the Netdata container:

code:
docker stop netdata
docker rm netdata
