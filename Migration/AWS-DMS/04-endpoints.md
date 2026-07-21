# Source and Target Endpoints

## Create Source Endpoint

Navigate:

```text
DMS → Endpoints
```

Select:

```text
Create Endpoint
```

---

# Source Endpoint

Example:

```text
Endpoint Type: Source
Engine: SQL Server
Server Name: Source SQL Server
Port: 1433
User: dms_user
Database: ApplicationDB
```

---

# Target Endpoint

Example:

```text
Endpoint Type: Target
Engine: SQL Server
Server Name: Target SQL Server
Port: 1433
User: dms_user
Database: ApplicationDB
```

---

# Test Connectivity

Navigate:

```text
Endpoint
 └── Connections
      └── Test Connection
```

Expected result:

```text
Successful
```

Validate both:

- Source Endpoint
- Target Endpoint

before creating tasks.
