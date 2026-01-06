# linux-networking-labs
This project documents the deployment and administration of a Linux-based multi-user Evennia MUD server. The goal was to gain hands-on experience with Linux system administration, networking, and basic security controls.
## Architecture

[Internet]
    |
[Router / NAT]
    |  (Port Forwarding)
[Firewall (iptables/firewalld)]
    |
[Debian Linux Server]
    |-- Evennia (Python venv)
    |-- Telnet Service
    |-- Web Client
