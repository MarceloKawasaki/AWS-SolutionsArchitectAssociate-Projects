# Prerequisites

## Overview

Before starting an AWS DMS migration, validate all source database and AWS environment requirements.

---

# Create DMS User

A dedicated DMS account with administrative privileges is required.

## SQL Server

Open SQL Server Management Studio (SSMS):

```text
Security
 └── Logins
      └── New Login
```

Configure:

- SQL Server Authentication
- Strong password
- Disable password policy if required

Grant:

```text
Server Roles
 └── sysadmin
```

---

# Enable CDC

Enable Change Data Capture on the source database.

```sql
EXEC sys.sp_cdc_enable_db
```

Confirm CDC is active before creating replication tasks.

---

# Analyze Database Sizes

Execute the following query to identify table sizes.

```sql
SELECT
    t.name AS TableName,
    SUM(p.rows) AS RowCounts,
    (SUM(a.total_pages) * 8) / 1024.0 AS TotalSpaceMB,
    (SUM(a.used_pages) * 8) / 1024.0 AS UsedSpaceMB,
    (SUM(a.data_pages) * 8) / 1024.0 AS DataSpaceMB
FROM sys.tables t
INNER JOIN sys.indexes i
    ON t.object_id = i.object_id
INNER JOIN sys.partitions p
    ON i.object_id = p.object_id
    AND i.index_id = p.index_id
INNER JOIN sys.allocation_units a
    ON p.partition_id = a.container_id
WHERE i.object_id > 255
AND i.index_id IN (0,1)
GROUP BY t.name
ORDER BY TotalSpaceMB ASC;
```

The query provides:

- Table name
- Row count
- Used space
- Data size
- Total size

---

# AWS Requirements

Prepare:

- VPC
- Private Subnets
- Security Groups
- IAM Permissions
- DMS Replication Instance
