# SSH Hardening on Raspberry Pi

## Overview

In this project, I hardened SSH access on my Raspberry Pi 5 running Ubuntu Server LTS. The goal was to make remote access more secure by changing default SSH settings and limiting how the Pi can be accessed.

SSH stands for Secure Shell. It allows me to remotely connect to my Raspberry Pi from another computer and manage it through the command line.

## Skills Practiced

- SSH configuration
- Linux command line
- Secure remote access
- Editing configuration files
- Restarting system services
- Basic Linux hardening

## Tools Used

- Raspberry Pi 5
- Ubuntu Server LTS
- OpenSSH
- Nano text editor
- UFW

## Steps

### 1. Opened the SSH configuration file

```bash
sudo nano /etc/ssh/sshd_config
```

This file controls the main SSH settings for the Raspberry Pi.

### 2. Changed the default SSH port

```text
Port 2222
```

I changed SSH from the default port `22` to a custom port, `2222`.

This does not make the system fully secure by itself, but it can reduce random automated login attempts that commonly target the default SSH port.

### 3. Allowed the custom SSH port through the firewall

```bash
sudo ufw allow 2222/tcp
```

This makes sure the firewall allows SSH traffic on the new custom port.

### 4. Restarted the SSH service

```bash
sudo systemctl restart ssh
```

Restarting SSH applies the configuration changes.

### 5. Checked the SSH service status

```bash
sudo systemctl status ssh
```

This confirms that SSH is running correctly after the configuration change.

### 6. Connected using the custom SSH port

```bash
ssh username@pi-ip-address -p 2222
```

This command connects to the Raspberry Pi using the custom SSH port.

In my real setup, I replaced `username` and `pi-ip-address` with my own information. I did not include that private information in this repository.

## Optional Key-Based Authentication

A stronger SSH setup uses SSH keys instead of only passwords. SSH keys are more secure because they are much harder to brute force than normal passwords.

A common command to create an SSH key is:

```bash
ssh-keygen
```

After creating a key, the public key can be copied to the Raspberry Pi. The private key should stay protected on my own computer and should never be uploaded to GitHub.

## Example Final Configuration

```text
SSH port: 2222
Firewall: allows 2222/tcp
Remote access: SSH
Private keys/passwords: not uploaded
```

## What I Learned

This project helped me understand how SSH is used for remote administration and why default settings should be reviewed. I learned how to edit SSH configuration files, restart services, check service status, and make sure firewall rules match SSH settings.

I also learned that changing the SSH port is not a complete security solution by itself. It should be combined with other protections like strong passwords, SSH keys, firewall rules, and Fail2Ban.

## Why This Matters for Cybersecurity

SSH is commonly used by system administrators to manage Linux servers. Because of this, it is also commonly targeted by attackers and bots.

Hardening SSH is an important basic security skill. This project helped me practice reducing risk while still keeping remote access available for legitimate use.

## Security Notes

- This project was completed on my own Raspberry Pi in my personal home lab.
- No passwords, private keys, usernames, or real IP addresses are included.
- SSH access was only configured for my own device.
- This lab was done for learning and defensive security practice.
