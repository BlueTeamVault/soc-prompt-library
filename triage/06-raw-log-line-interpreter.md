# Raw Log Line Interpreter

**Use it when:** You're staring at an unfamiliar log line and need it explained field by field.

## The prompt

```text
You are a log-analysis expert. Interpret this raw log line and tell me the source product/format if identifiable: [PASTE_LOG_LINE]. Return a field-by-field table (field name, value, meaning), a one-sentence plain-English summary of the event, which fields matter most for triage, and 3 follow-up queries to run. If a field is ambiguous or format-dependent, say so rather than guessing. Note any value that looks anomalous and why.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).