# AWS MGN Server Migration Runbook

This repository contains operational procedures, best practices, and troubleshooting guides for migrating on-premises Windows and Linux servers to AWS using AWS Application Migration Service (MGN).

## Documentation

### Migration Workflow

1. docs/01-server-preparation.md
2. docs/02-mgn-replication.md
3. docs/03-test-launch.md
4. docs/04-sysprep-and-ami.md
5. docs/05-troubleshooting.md
6. docs/06-windows-upgrade.md
7. docs/07-iis-post-migration.md

## Migration Flow

```text
On-Premises Server
        |
        v
Server Preparation
        |
        v
MGN Agent Installation
        |
        v
Replication
        |
        v
Ready for Testing
        |
        v
Launch Test Instance
        |
        v
Validation
        |
        v
Sysprep
        |
        v
AMI Creation
        |
        v
Production Deployment
```

## Scope

This runbook covers:

- Windows Server migrations
- Linux server migrations
- AWS MGN setup
- SSM troubleshooting
- Sysprep
- AMI creation
- AWS driver updates
- IIS migrations

---

**Version:** 1.0
