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

## Key Configuration Areas
- Linux user and permission management
- Python virtual environments
- SSH key-based authentication
- Firewall rules using iptables/firewalld
- LAN and WAN port forwarding
- Service monitoring and log analysis

## Security Considerations
- Disabled password-based SSH authentication
- Restricted administrative access by IP
- Allowed only required ports through firewall
- Monitored logs using journalctl

## Troubleshooting Highlights
- Diagnosed wireless firmware issues on Debian systems
- Used dmesg and journalctl to identify driver loading errors
- Verified network connectivity and port accessibility across devices

## Lessons Learned
- Importance of firewall rule order
- How NAT affects service exposure
- Value of methodical troubleshooting and documentation

- 
## 📡 Networking Issues

<details>
<summary>WAN Connectivity Issues – Clients Could Not Connect</summary>

**Diagnosis:**
- Verified router port forwarding and NAT configuration
- Checked firewall rules on the Linux server
- Tested port accessibility from external devices using `nc` and `telnet`

**Solution:**
- Corrected router port forwarding for required service ports (Telnet, HTTP/HTTPS)
- Configured firewall to allow only required incoming ports
- Ensured Evennia server was listening on the correct network interfaces

</details>

<details>
<summary>NetworkManager Password Prompt Loop</summary>

**Diagnosis:**
- Repeated password prompts observed using `nmcli` logs
- Checked `wpa_supplicant` configuration
- Verified interface state with `ip a`

**Solution:**
- Ensured correct WiFi credentials and security settings
- Restarted NetworkManager service
- Brought interface up manually when needed

</details>

<details>
<summary>Wireless Driver / Firmware Issues</summary>

**Diagnosis:**
- Network interface showed `state DOWN` / `DORMANT`
- `dmesg` reported missing Broadcom firmware
- Required `.fw` files missing in `/lib/firmware`

**Solution:**
- Extracted Broadcom firmware using `b43-fwcutter`
- Copied files to `/lib/firmware/b43`
- Restarted network service and verified interface came online

  

