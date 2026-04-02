# n8n Workflow Development Practices

**Authoritative sources:** Synta best practices (synta-mcp:get_best_practices), Ryan Hildebrandt methodology, Vasuman/Varick agent principles.

## Before Building

1. **Search templates first.** `search_templates` → `get_template` for at least 2 results → study proven patterns before writing a single node.
2. **Read ALL relevant best practices.** Call `get_best_practices` for every technique the workflow touches (scheduling, data_persistence, notification, triage, etc.).
3. **Validate manually.** `curl` the API. Confirm the response shape. Verify field names against actual data. Then build.
4. **Document the design.** Write RUNBOOK.md with architecture, credentials, failure modes BEFORE building.

## While Building

5. **Build incrementally.** One node → test → next node → test. Never deploy a multi-node workflow blind.
6. **Use Synta MCP or n8n REST API.** Never build workflows through browser JavaScript injection. It causes field name mismatches, missing credentials, and untestable changes.
7. **Use native n8n nodes.** Prefer built-in nodes over HTTP Request hacks. Check if a native node exists before building a raw API call.
8. **Validate schema before expressions.** Check Airtable field names, Graph API response shapes, and node parameter paths against actual data before writing any expressions.
9. **Set credentials explicitly.** After adding any node, verify credentials are linked. New nodes don't inherit credentials from existing ones.

## Production Hardening (from day one, not retrofitted)

10. **Dedup:** Use unique identifiers (Graph Message ID, etc.) with search-before-create or upsert operations. Never rely on read status as a dedup mechanism.
11. **Error handling:** Every external service call needs error output routing. Use Log Error Decision for audit trail.
12. **Alerting:** When errors occur, notify humans (email, Slack). Don't just log to a table nobody monitors.
13. **State tracking:** Use n8n Data Tables to store last poll timestamp, processing state. Don't use time-window hacks.
14. **Audit trail:** Never delete records from decision/interaction/audit tables. Mark bad data with notes.

## Known Antipatterns

- `isRead eq false` for shared mailboxes — any Outlook client auto-marks emails as read before n8n polls. Use `receivedDateTime ge {timestamp}` with dedup.
- Hardcoded credentials in HTTP Request nodes — use n8n credential system or External Secrets.
- Building through browser Chrome automation — fragile, untestable, causes field name bugs.
- Deploying to localhost n8n on a Mac — use cloud instance (cafatech.app.n8n.cloud) for 24/7 uptime.

## Workflow Lifecycle

1. Design → search templates + best practices
2. Build → incremental, validated at each step
3. Test → manual execution with known test data
4. Document → RUNBOOK.md committed to GitHub
5. Publish → with version name and change description
6. Monitor → check Executions tab and Agent Decisions table
7. Iterate → validate each change, re-publish
