# Migration Tasks

## Create Task

Navigate:

```text
DMS
 └── Database Migration Tasks
      └── Create Task
```

---

# Basic Configuration

## Task Name

Example:

```text
production-sql-migration
```

---

## Source Endpoint

Select previously created Source Endpoint.

---

## Target Endpoint

Select previously created Target Endpoint.

---

## Migration Type

Recommended:

```text
Migrate Existing Data and Replicate Ongoing Changes
```

This performs:

- Full Load
- Continuous CDC Replication

---

# Task Settings

## Target Table Preparation

Recommended:

```text
Drop Tables On Target
```

---

## Stop Task After Full Load

```text
Do Not Stop
```

---

## LOB Settings

Mode:

```text
Full LOB Mode
```

LOB Chunk:

```text
64 KB
```

Maximum Inline LOB:

```text
0
```

---

## Validation

Recommended:

```text
Disabled
```

for large migrations.

---

# Start Task

Start migration and monitor:

```text
Full Load Progress
CDC Latency
Task Status
```
