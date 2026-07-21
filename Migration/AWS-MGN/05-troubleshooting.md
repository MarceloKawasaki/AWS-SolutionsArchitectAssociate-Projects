# Troubleshooting Guide

# SSM Connectivity Issues

## Review Logs

Location:

```text
C:\ProgramData\Amazon\SSM\Logs
```

---

## Verify Proxy

Check:

```cmd
netsh winhttp show proxy
```

Bypass EC2 metadata:

```cmd
netsh winhttp set proxy proxy-server="proxy.company.local:8080" bypass-list="169.254.169.254"
```

Restart SSM Agent afterward.

---

# Create Emergency User

Use EC2 User Data:

```xml
<powershell>
net user awsmig <password> /add
net localgroup administrators awsmig /add
</powershell>
<persist>true</persist>
```

---

# Sysprep Errors

View logs:

```text
%WINDIR%\System32\Sysprep\Panther\setupact.log
```

Common package issue:

```powershell
Get-AppxPackage -AllUsers *MicrosoftEdge*
```

Remove:

```powershell
Remove-AppxPackage -Package <package-name> -AllUsers
```

---

# Linux Installation Errors

Error:

```text
Kernel headers are missing
```

Resolution:

```bash
yum groupinstall "Development Tools"

yum install gcc --nogpgcheck

yum install kernel-devel-$(uname -r)
```

---

# Replication Server Not Starting

Review CloudTrail:

```text
Event Name = RunInstances
```

Common causes:

- Invalid tags
- Missing permissions
- Security group issues

Verify all tags are correctly formatted and follow organizational standards.
``
