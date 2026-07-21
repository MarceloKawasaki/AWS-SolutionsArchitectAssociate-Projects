# Server Preparation

## Overview

Preparing the source server is critical to ensure a successful migration using AWS MGN.

---

# Create a Migration Administrator

## Windows

Create a local migration account:

```powershell
net user awsmig <password> /add /expires:never
net localgroup administrators awsmig /add
```

Optional password reset:

```powershell
$newpassword = ConvertTo-SecureString -AsPlainText "<new-password>" -Force
Set-LocalUser -Name "local_admin" -Password $newpassword
```

## Linux

```bash
sudo useradd awsmig
sudo passwd awsmig
sudo usermod -aG wheel awsmig
```

---

# Install Operating System Updates

Recommended before migration:

- Install all updates
- Reboot the server
- Confirm application functionality

Restart command:

```cmd
shutdown -r -t 00
```

Monitor:

```cmd
ping -t <server-ip>
```

---

# Configure Proxy (If Required)

PowerShell:

```powershell
$env:HTTP_PROXY="http://proxy.company.local:8080"
$env:HTTPS_PROXY="http://proxy.company.local:8080"
```

Also validate:

- Internet Options
- LAN Settings
- Proxy Server
- Bypass Local Addresses

Verify internet access before installing the MGN agent.

---

# Validate System Health

## System File Checker

```cmd
sfc /scannow
```

## DISM

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

## Check Disk

```cmd
chkdsk C: /f /r
```

---

# Benefits

- Improved migration reliability
- Reduced launch failures
- Better driver compatibility
- Faster troubleshooting
