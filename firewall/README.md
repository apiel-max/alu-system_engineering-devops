# Firewall Project

## Description
This project configures UFW (Uncomplicated Firewall) on web-01 to block all
incoming traffic by default, while explicitly allowing only the ports needed
for the server to function: SSH, HTTP, and HTTPS.

## Task 0: Block all incoming traffic but...
File: `0-block_all_incoming_traffic_but`

Configures ufw on web-01 so that:
- All incoming traffic is denied by default
- Port 22 (SSH) remains open
- Port 80 (HTTP) remains open
- Port 443 (HTTPS) remains open

### Important safety note
Port 22 (SSH) must always be explicitly allowed *before* enabling ufw or
setting the default policy to deny incoming traffic. Enabling the firewall
before allowing SSH would immediately block the active SSH session and
permanently lock out remote access to the server, with no way to recover it.

### Commands used
```bash
sudo apt update
sudo apt install -y ufw

sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

sudo ufw default deny incoming
sudo ufw enable
```

### Verification
```bash
sudo ufw status
```
Output confirms ufw is active with only ports 22, 80, and 443 allowed, all
other incoming traffic denied.

## Author
Alier Akuang Alier Piel — Software Engineering student, African Leadership
University (ALU)
