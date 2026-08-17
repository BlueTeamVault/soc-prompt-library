# Ready-to-Paste Case Note

**Use it when:** You've finished triage and need a clean, defensible ticket note.

## The prompt

```text
You are a SOC analyst documenting a case. From these findings: [PASTE_FINDINGS], write a structured case note with: Summary (2 sentences), Affected entities (host/user/IP), Timeline (UTC), Observations (bullet facts), Assessment (verdict + confidence + reasoning), MITRE ATT&CK techniques, Actions taken, Recommendation/Next steps. Use neutral, factual language suitable for audit and possible legal review. Clearly separate confirmed facts from analyst inference, and mark any item still pending verification. Keep it copy-paste ready for our ticketing system.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).