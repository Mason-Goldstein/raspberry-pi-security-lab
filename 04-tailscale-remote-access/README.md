# Tailscale Remote Access for Raspberry Pi

## Overview

In this project, I configured Tailscale so I could securely access my Raspberry Pi 5 remotely. The goal was to connect to my Pi from outside my home network without exposing SSH directly to the public internet.

Tailscale creates a private network between trusted devices. This lets me SSH into my Raspberry Pi using a private Tailscale IP address instead of opening SSH to the whole internet.

## Skills Practiced

- Secure remote access
- SSH administration
- VPN basics
- Private networking
- Linux command line
- Device management
- Network security basics

## Tools Used

- Raspberry Pi 5
- Ubuntu Server LTS
- Tailscale
- SSH
- UFW

## Steps

### 1. Installed Tailscale

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

This command installs Tailscale on the Raspberry Pi.

### 2. Started Tailscale

```bash
sudo tailscale up
```

This starts Tailscale and connects the Raspberry Pi to my private Tailscale network.

### 3. Checked the Tailscale IP address

```bash
tailscale ip -4
```

This shows the private Tailscale IPv4 address assigned to the Raspberry Pi.

### 4. Checked Tailscale connection status

```bash
tailscale status
```

This shows the devices connected to the private Tailscale network.

### 5. Connected to the Raspberry Pi over Tailscale

```bash
ssh username@tailscale-ip-address -p 2222
```

This connects to the Raspberry Pi through the private Tailscale network using my custom SSH port.

In my real setup, I replaced `username` and `tailscale-ip-address` with my own information. I did not include that private information in this repository.

## Example Final Configuration

```text
Remote access method: Tailscale
SSH port: 2222
Public SSH exposure: Not required
Connection type: Private Tailscale network
Firewall: UFW enabled
```

## What I Learned

This project helped me understand how private networking can make remote access safer. Instead of opening SSH directly to the public internet, I can use Tailscale to connect only from trusted devices.

I also learned that remote access should be convenient but still secure. Tailscale makes it easier to reach my Raspberry Pi while reducing exposure to random internet scanning and brute-force attempts.

## Why This Matters for Cybersecurity

Remote access is common in IT and cybersecurity. Administrators often need to manage servers, workstations, or lab machines from another location. However, exposing remote access services directly to the internet can create security risks.

This project helped me practice a safer remote access design: use a private network, limit access to trusted devices, keep SSH protected, and avoid unnecessary public exposure.

## Security Notes

- This project was completed on my own Raspberry Pi in my personal home lab.
- No Tailscale authentication keys, usernames, passwords, private keys, or real IP addresses are included.
- SSH access was only configured for my own device.
- This lab was done for learning and defensive security practice.
