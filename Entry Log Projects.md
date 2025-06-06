# Home-Projects
a log of all the home projects that I have done

ogs/2025-05-10-proxmox-install.md

# [2025-05-10] Proxmox Installation & Setup

**Location**: Home Server Closet  
**Main Task**: Installed Proxmox VE 8.4 on Samsung 970 EVO 500GB SSD

---

## What I Did

- Flashed Proxmox VE to USB using Balena Etcher
- Disabled RAID mode in BIOS
- Set static IP: `192.168.1.208`
- Installed Proxmox with hostname: `pve.myfiosgateway.com`
- Moved system into closet with switch + router for full control

---

## Next Up

- Set up Home Assistant VM
- Restore Home Assistant backup
- Start Plex + Docker container layout

---
Home Assistant VM Setup
Created a new Ubuntu Server virtual machine on Proxmox dedicated to Home Assistant

Assigned static IP and allocated appropriate CPU/RAM resources

Installed Home Assistant via Docker inside the VM

Successfully restored a previous Home Assistant backup to retain all automations and integrations

Verified access to the Home Assistant web UI from the local network

## 🛠️ Building My Self-Hosted Dashboard (Ubuntu Server Log – May 11, 2025)

Yesterday was a huge step forward in building out my self-hosted infrastructure on my Ubuntu-based Proxmox VM. I spent the entire day setting up my dashboard stack and making it look and feel like my own personal control center. Here's what went down:

---

### ✅ Installed Flame Dashboard via Docker

I deployed [Flame](https://github.com/pawelmalak/flame) as my central home server dashboard. It's lightweight, fast, and Dockerized, so I was able to run it with a simple command:

```bash
sudo docker run -d \
  --name flame \
  --restart unless-stopped \
  -p 5005:5005 \
  -v flame-data:/app/data \
  -e PASSWORD=my_password \
  pawelmalak/flame
```

> 🔐 Secured the dashboard with a custom password, accessible on my local network at `http://192.168.1.211:5005`.

---

### 🧠 Customized the Dashboard (CSS/Visuals)

Once Flame was up and running, I dove into the CSS editor and added:

* 🟥 Neon red hover glow effects on app cards
* 💥 Bounce-on-hover animation
* 🌟 Glowing, animated title bar for a cyber/retro feel

> It honestly turned the stock interface into something way more fun and uniquely mine.

---

### 🧩 Integrated Core Applications

I added quick-access tiles for:

* 🔧 **Proxmox** – to manage my virtual machines
* 📉 **Glances (Web View)** – for live resource monitoring
* 🏠 **Home Assistant** – to eventually tie in smart home automations

---

### 🌤️ Added Weather & Uptime (No API Required)

To keep things simple and free:

* 🌦️ I used `https://wttr.in` for weather info, no API key required
* ⏱️ I exposed VM uptime via a bash script and `python3 -m http.server`

---

### 🧪 Troubleshooting & Lessons

* Learned how to correctly expose and access Docker containers
* Had to manually kill some broken containers (`docker rm -f`)
* Tried adding a custom banner image from Imgur/Flickr/DeviantArt, but all failed to render in Flame — fell back to color themes for now

---

### 🧭 Next Up:

* Add monitoring for disk space and network stats
* Set up authentication for remote access
* Start adding media tools (e.g. Plex, Overseerr, Sonarr)

---

---

Everything's hosted on my Ubuntu VM under Proxmox, and it's finally starting to feel like a real server stack. Flame has been a dope frontend for all my services — still early, but this setup's evolving fast.

---
