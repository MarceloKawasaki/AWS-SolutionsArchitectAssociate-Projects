# Sysprep and AMI Creation

## Prerequisites

Requirements:

- Instance running
- Accessible through SSM

---

# Windows Server 2019 and Later

Download EC2Launch V2:

```text
https://s3.amazonaws.com/amazon-ec2launch-v2/windows/amd64/latest/AmazonEC2Launch.msi
```

Install and validate:

```powershell
ec2launch
```

Execute Sysprep:

```powershell
ec2launch sysprep -s
```

Expected behavior:

- Sysprep runs
- Instance shuts down automatically

---

# Create AMI

Navigate:

```text
EC2 → Actions → Image and Templates → Create Image
```

Validate:

```text
Delete On Termination = Enabled
```

for all EBS volumes.

---

# Create Launch Template Using AMI

Validate:

- AMI
- Instance type
- Security Groups
- Storage
- Tags

Recommended role:

```text
AmazonSSMManagedInstanceCore
```

---

# Active Directory Integration

After deployment:

- Join Active Directory
- Register in credential vault
- Validate network access
- Validate RDP access
