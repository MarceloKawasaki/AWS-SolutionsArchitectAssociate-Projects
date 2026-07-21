# AWS DMS Migration Runbook

This repository contains operational procedures and best practices for migrating databases using AWS Database Migration Service (DMS).

The guide focuses primarily on Microsoft SQL Server migrations, including SQL Server Always On environments.

## Documentation

### Migration Flow

1. docs/01-prerequisites.md
2. docs/02-replication-instance.md
3. docs/03-networking-and-security.md
4. docs/04-endpoints.md
5. docs/05-tasks.md
6. docs/06-premigration-assessment.md
7. docs/07-troubleshooting.md

## Architecture Overview

```text
Source Database
       |
       |
       v
AWS DMS Replication Instance
       |
       |
       v
Target Database
       |
       |
CDC Replication
```

## Scope

This runbook covers:

- SQL Server migrations
- SQL Server Always On
- Change Data Capture (CDC)
- AWS DMS Replication Instances
- Source and Target Endpoints
- Migration Tasks
- Pre-Migration Assessments
- Troubleshooting

---

Version: 1.0
