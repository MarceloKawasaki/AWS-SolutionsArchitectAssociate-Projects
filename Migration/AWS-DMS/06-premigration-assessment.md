# Pre-Migration Assessment

## Overview

AWS DMS provides migration assessments to identify possible migration blockers before data movement begins.

---

# Create Assessment

Open the migration task.

Navigate:

```text
Task
 └── Premigration Assessments
      └── Create Assessment
```

---

# Assessment Configuration

## Name

Provide an assessment name.

Example:

```text
sqlserver-precheck
```

---

## Report Storage

Select an S3 bucket.

The reports will be stored automatically.

---

## IAM Role

AWS can automatically create the required role.

---

## Assessment Selection

Recommended:

```text
Select All
```

This performs a complete analysis of:

- Database compatibility
- Schema compatibility
- Migration readiness
- Object conversion requirements
- CDC requirements

---

# Review Results

Inspect all generated reports before starting production migration.

Important findings include:

- Unsupported objects
- Feature incompatibilities
- Performance recommendations
- Migration blockers
