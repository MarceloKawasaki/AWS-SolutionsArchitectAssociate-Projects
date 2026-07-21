# Replication Instance

## Create a DMS Replication Instance

Navigate:

```text
AWS DMS
 └── Provisioned Instances
      └── Create Replication Instance
```

---

# Instance Configuration

## Name

Provide a meaningful name.

Example:

```text
dms-prod-replication
```

---

## Instance Class

Choose according to:

- Database size
- CDC volume
- Migration duration requirements

Larger instances improve migration throughput.

---

## Engine Version

Use the latest supported version.

---

## High Availability

For testing:

```text
Single-AZ
```

For production:

```text
Multi-AZ
```

(Optional according to business requirements)

---

## Storage

Allocate sufficient storage.

Consider:

- Cached transactions
- LOB processing
- CDC workload
