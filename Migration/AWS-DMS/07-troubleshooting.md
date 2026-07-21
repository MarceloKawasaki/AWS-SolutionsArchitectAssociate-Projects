# Troubleshooting

# Endpoint Connectivity Failure

Symptoms:

```text
Test Connection Failed
```

Check:

- Security Groups
- Routing
- Firewalls
- DNS Resolution

Validate connectivity between:

```text
DMS Instance
      ↓
Source Database

DMS Instance
      ↓
Target Database
```

---

# CDC Not Starting

Check:

```sql
EXEC sys.sp_cdc_help_change_data_capture
```

Confirm CDC is enabled.

If disabled:

```sql
EXEC sys.sp_cdc_enable_db
```

---

# Task Full Load Slow

Possible causes:

- Small replication instance
- Large LOB objects
- Network latency
- Insufficient source database resources

Actions:

- Upgrade replication instance class
- Verify CPU utilization
- Verify storage throughput

---

# High CPU on Target Database

Common causes:

- Large batch transactions
- Missing indexes
- CDC catch-up activity

Recommendations:

- Monitor database performance metrics
- Review execution plans
- Reduce migration parallelism if needed

---

# Task Stuck in Starting State

Review:

```text
CloudWatch Logs
```

Common causes:

- Endpoint authentication failure
- Insufficient permissions
- Network connectivity issues

---

# SQL Server Always On Issues

Verify:

- Listener configuration
- Port accessibility
- CDC enabled database
- DMS user sysadmin privileges

Ensure DMS connects through the SQL Server Always On Listener whenever possible.

---

# Best Practices

✅ Use dedicated DMS credentials.

✅ Always enable CDC before starting migration.

✅ Run Premigration Assessments.

✅ Deploy replication instances in private subnets.

✅ Prefer Security Group references over IP ranges.

✅ Enable CloudWatch logging.

✅ Use Full Load + CDC whenever possible.

✅ Monitor CDC latency throughout migration.

✅ Perform reconciliation before cutover.

✅ Keep rollback procedures documented.
