# Launch Test Instances

## Prerequisites

Requirements:

- Replication completed
- Ready for Testing status
- SSM available

---

# Configure Launch Settings

Navigate:

```text
Launch Settings → General Launch Settings
```

Set:

```text
Instance Type Right Sizing = Disabled
```

---

# Modify Launch Template

## Instance Type

Choose the appropriate EC2 size.

---

## Networking

Select:

- Private subnet
- Existing Security Group

---

## Storage

Validate:

- Size
- IOPS
- Throughput
- Delete on termination = Yes

---

## Tags

Apply tags to:

```text
Instances
Volumes
```

---

## Metadata Service

Enable:

```text
IMDSv2 Only
```

---

# Launch Instance

Navigate:

```text
Test and Cutover → Launch Test Instances
```

Monitor Job ID until completion.

---

# Validate

Confirm:

- OS booted successfully
- Network connectivity
- Application functionality
- SSM connectivity
