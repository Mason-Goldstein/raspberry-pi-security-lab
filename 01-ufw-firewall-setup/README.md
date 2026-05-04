# UFW Firewall Setup on Raspberry Pi

## Overview

In this project, I configured UFW on my Raspberry Pi 5 running Ubuntu Server LTS. The goal was to secure the Pi by blocking unnecessary incoming traffic and only allowing approved services.

UFW stands for Uncomplicated Firewall. It is a beginner-friendly way to manage firewall rules on Linux systems.

## Skills Practiced

- Linux command line
- Firewall configuration
- SSH access control
- Basic network security
- System hardening
- Checking service and firewall status

## Tools Used

- Raspberry Pi 5
- Ubuntu Server LTS
- UFW
- SSH

## Steps

### 1. Checked UFW status

```bash
sudo ufw status
```

This command checks whether UFW is active and shows the current firewall rules.

### 2. Set default incoming traffic to deny

```bash
sudo ufw default deny incoming
```

This blocks incoming connections unless I specifically allow them.

### 3. Set default outgoing traffic to allow

```bash
sudo ufw default allow outgoing
```

This allows the Raspberry Pi to make normal outbound connections, such as updates or internet requests.

### 4. Allowed SSH on my custom SSH port

```bash
sudo ufw allow 2222/tcp
```

I allowed SSH on port `2222` because my Raspberry Pi uses a custom SSH port instead of the default port `22`.

### 5. Enabled UFW

```bash
sudo ufw enable
```

This turns on the firewall using the rules I configured.

### 6. Checked final firewall status

```bash
sudo ufw status verbose
```

This shows the active firewall rules and confirms that UFW is running.

## Example Final Configuration

The final setup allows SSH on my custom port and denies other unnecessary incoming traffic.

```text
Default: deny incoming
Default: allow outgoing
Allowed: 2222/tcp
```

## What I Learned

This project taught me how a host-based firewall can reduce the attack surface of a Linux system. By denying unnecessary incoming traffic, the Raspberry Pi is less exposed to unwanted connections.

I also learned why it is important to allow SSH before enabling the firewall. If SSH is not allowed first, I could accidentally lock myself out of the Pi when connecting remotely.

## Why This Matters for Cybersecurity

Firewalls are one of the basic layers of defense in cybersecurity. Even on a small home lab device like a Raspberry Pi, firewall rules help control what services are reachable over the network.

This project helped me practice the same basic security idea used in real IT and cybersecurity environments: only allow what is needed and block everything else by default.

## Security Notes

- This project was completed on my own Raspberry Pi in my personal home lab.
- No passwords, private keys, or real public IP addresses are included.
- SSH access was only configured for my own device.
- This lab was done for learning and defensive security practice.
