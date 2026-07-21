# Networking and Security

## Create Subnet Group

Navigate:

```text
DMS → Subnet Groups
```

Create:

```text
Create Subnet Group
```

Configure:

- Name
- Description
- VPC
- Private Subnets

---

# Replication Instance Placement

Always deploy replication instances in private subnets.

Benefits:

- Increased security
- Reduced exposure
- Internal AWS traffic

---

# Availability Zone

Recommended:

Use the same AZ as the target database whenever possible to reduce latency.

---

# Security Groups

## Database Security Group

Allow inbound access from the DMS Replication Instance.

Examples:

### SQL Server

```text
TCP 1433
```

### PostgreSQL

```text
TCP 5432
```

### MySQL

```text
TCP 3306
```

---

# Replication Instance Security Group

Allow outbound connectivity to:

- Source Database
- Target Database

Use Security Group references whenever possible.

Avoid:

```text
0.0.0.0/0
```

unless absolutely necessary.
