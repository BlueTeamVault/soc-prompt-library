# Multi-Line Log Sequence Storyline

**Use it when:** You have a cluster of related log entries and need the narrative they tell.

## The prompt

```text
You are an incident analyst. Below are related log lines in time order: [PASTE_LOG_LINES]. Reconstruct the storyline as a numbered timeline (timestamp, actor, action, target, outcome). Identify the likely root event, what happened next, and whether the sequence is consistent with normal activity or an attack chain. Map plausible steps to MITRE ATT&CK technique IDs. Separate what the logs prove from what you're inferring, and list the gaps where I need more data.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).