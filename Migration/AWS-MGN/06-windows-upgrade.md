# Windows In-Place Upgrade

## Overview

This procedure covers Windows Server upgrades after migration to AWS.

---

# Prerequisites

Before upgrading:

- Create an AMI backup
- Update AWS drivers
- Update EC2Launch
- Update EC2Config

---

# Update AWS Drivers

## PV Driver

Download latest AWS PV driver.

---

## ENA Driver

Install latest Elastic Network Adapter driver.

Expected behavior:

- Temporary connectivity loss
- Reboot may be required

---

## NVMe Driver

Install latest NVMe driver.

Execute:

```powershell
start rundll32.exe sppnp.dll,Sysprep_Generalize_Pnp -wait
```

---

# Update EC2Launch

Verify version:

```powershell
& "C:\Program Files\Amazon\EC2Launch\EC2Launch.exe" version
```

Update if needed.

---

# Upgrade Windows

Mount installation media.

Execute:

```cmd
setup.exe /auto upgrade /dynamicupdate disable
```

Select:

```text
Desktop Experience
```

Complete installation.

---

# Post Upgrade

Validate:

- RDP
- SSM
- Applications
- Services
- Drivers
