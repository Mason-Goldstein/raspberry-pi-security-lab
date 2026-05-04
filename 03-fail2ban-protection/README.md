# Fail2Ban SSH Protection on Raspberry Pi

## Overview

In this project, I configured Fail2Ban on my Raspberry Pi 5 running Ubuntu Server LTS. The goal was to protect SSH from repeated failed login attempts by monitoring authentication logs and temporarily banning suspicious IP addresses.

Fail2Ban is a security tool that watches log files for suspicious activity. When it sees too many failed login attempts, it can automatically block that source using firewall rules.

## Skills Practiced

- Linux command line
- Log monitoring
- SSH security
- Brute-force protection
- Linux service management
- Defensive cybersecurity basics

## Tools Used

- Raspberry Pi 5
- Ubuntu Server LTS
- Fail2Ban
- SSH
- UFW

## Steps

### 1. Updated the system

```bash
sudo apt update
```

This makes sure the package list is up to date before installing new software.

### 2. Installed Fail2Ban

```bash
sudo apt install fail2ban
```

This installs Fail2Ban on the Raspberry Pi.

### 3. Checked the Fail2Ban service

```bash
sudo systemctl status fail2ban
```

This confirms whether Fail2Ban is installed and running.

### 4. Created or edited the local jail configuration

```bash
sudo nano /etc/fail2ban/jail.local
```

The `jail.local` file is used for custom Fail2Ban settings. It is better to use this file instead of editing the default configuration directly.

### 5. Added an SSH jail configuration

```ini
[sshd]
enabled = true
port = 2222
filter = sshd
logpath = /var/log/auth.log
maxretry = 5
bantime = 10m
findtime = 10m
```

This tells Fail2Ban to watch SSH login attempts on my custom SSH port.

### 6. Restarted Fail2Ban

```bash
sudo systemctl restart fail2ban
```

Restarting the service applies the new configuration.

### 7. Checked Fail2Ban status

```bash
sudo fail2ban-client status
```

This shows the active Fail2Ban jails.

### 8. Checked the SSH jail

```bash
sudo fail2ban-client status sshd
```

This shows information about the SSH jail, including any banned IP addresses.

## Example Final Configuration

```text
Service protected: SSH
SSH port: 2222
Max retries: 5
Find time: 10 minutes
Ban time: 10 minutes
Log file monitored: /var/log/auth.log
```

## What I Learned

This project showed me how a defensive security tool can automatically respond to suspicious activity. I learned that Fail2Ban does not prevent every attack, but it helps reduce repeated brute-force login attempts by blocking sources that fail too many times.

I also learned how authentication logs are important for security monitoring. Logs can show failed login attempts, successful logins, and other activity that helps system administrators understand what is happening on a machine.

## Why This Matters for Cybersecurity

Brute-force login attempts are common against internet-facing systems. Even though my Raspberry Pi is only a home lab device, the same security idea applies to real servers and networks.

Fail2Ban helped me practice an important defensive concept: detecting suspicious behavior and responding automatically. This connects to real cybersecurity work such as monitoring logs, identifying threats, and reducing risk.

## Security Notes

- This project was completed on my own Raspberry Pi in my personal home lab.
- No passwords, private keys, usernames, or real IP addresses are included.
- Any testing was done only on my own device.
- This lab was done for learning and defensive security practice.
