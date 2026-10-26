# Local C2 Redirector Lab (Tier 2 Red Team Infrastructure)

## 📌 Executive Summary
In real-world Red Team engagements, exposing a C2 Teamserver directly to the internet is a critical OPSEC failure. This repository documents the architecture and implementation of a cost-effective, locally hosted **C2 Redirector** using VirtualBox, Ubuntu Server, and NGINX. 

This lab demonstrates how to segregate the **Management Plane** (Operator to Teamserver) from the **Payload Plane** (Implant to Redirector), preventing the exposure of the Teamserver's true IP address.

## 🏗️ Network Architecture
- **Parrot OS (Host):** The Operator's workstation running the Sliver Client.
- **Ubuntu Minimal Server (VM):** The C2 infrastructure. Configured with two network interfaces:
  - `Adapter 1 (Host-Only):` Used strictly for management traffic.
  - `Adapter 2 (Bridged):` Used for payload traffic.
- **Windows 10 (VM):** The simulated Victim.

## ⚙️ Redirector Configuration (NGINX)
The NGINX redirector sits on the Bridged adapter and proxies traffic to the Sliver Teamserver listening on localhost. 

*(Configuration files will be added in the `configs/` directory).*

## 🛡️ Defensive Mitigations (Blue Team)
- **Network Security:** Implement egress filtering to block unauthorized outbound HTTP/S traffic.
- **Proxy Logs:** Monitor for sequential requests lacking standard browser headers or TLS fingerprints (JA3/JA3S).

---
*Authored by Bytz (SpyderBytz). For educational and professional portfolio use only.*
