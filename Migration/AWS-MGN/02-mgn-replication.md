# AWS MGN Replication

## Prerequisites

Before starting:

- Align with application owners
- Validate available bandwidth
- Verify firewall rules

---

# Security Group Configuration

## Inbound

| Protocol | Port |
|----------|------|
| TCP | 1500 |

## Outbound

| Protocol | Port |
|-----------|------|
| HTTPS | 443 |
| DNS UDP | 53 |

---

# Firewall Configuration

Allow:

```text
TCP 443
TCP 1500
```

---

# IAM User

Required policy:

```text
AWSApplicationMigrationAgentInstallationPolicy
```

Generate:

- Access Key
- Secret Access Key

Store securely.

---

# Configure Replication Template

Navigate:

```text
MGN → Settings → Replication Template
```

Recommended settings:

- Private subnet
- Custom Security Group
- Standardized tags

Example:

```text
Name
environment
capacity
startup
shutdown
```

---

# Add Source Server

Navigate:

```text
MGN → Source Servers → Add Server
```

Steps:

1. Choose OS
2. Select disks
3. Enter AWS credentials
4. Download installer
5. Copy installation command

Example:

```powershell
.\AwsReplicationWindowsInstaller.exe `
--region us-east-1 `
--aws-access-key-id <key> `
--aws-secret-access-key <secret> `
--no-prompt
```

---

# Replication Settings

Enable:

```text
Use IPv4 address for replication = Yes
```

---

# Install Agent

Run installer as Administrator.

Expected status:

```text
Replicating
```

---

# Post Launch Actions

Enable:

```text
Install AWS Systems Manager Agent
```

---

# Remove Agent

Disconnect source server:

```text
MGN → Source Servers → Disconnect From AWS
```

Run:

```cmd
install_agent_windows.exe --remove
```

Reboot:

```cmd
shutdown -r -t 00
```
