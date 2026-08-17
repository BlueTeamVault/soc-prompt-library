## Before you run any prompt — the version block

Models drift, vendors rename things, frameworks change. Paste this block **once** at the top of your session, then run any prompt from the pack. Nothing else you do will stop a model inventing an event ID, a table name or an ATT&CK mapping as reliably.

```
VERSION AND VALIDATION REQUIREMENTS

Reference date: [YYYY-MM-DD]
Target product / platform and version: [VALUE]
Target query surface or execution environment: [VALUE]
Available telemetry, tables and representative sample events: [VALUE]
Framework / specification versions where known: [ATT&CK / Sigma / NIST CSF / vendor]

Use the evidence I supply and current authoritative documentation.
Do NOT invent event IDs, field names, table names, APIs, ATT&CK mappings,
GUIDs, or product capabilities. If you cannot determine something
deterministically, say so plainly rather than filling the gap.
Mark anything requiring documentation or environment verification.
Produce a draft for validation — never an assumed production-ready artefact.
```

Two habits that go with it:

- **Treat executable output as a draft.** A query, a rule, a regex, a GUID: none of it counts until you have run it against real data and confirmed the fields exist in your environment.
- **Watch for fluent certainty.** When a prompt asks for something the model cannot derive (decoding a multi-layer payload, an ASN it was never given, a record count you didn't supply), the right answer is "I cannot determine this." Push back if you get anything else.
