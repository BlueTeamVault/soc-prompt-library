# Incident Timeline From Raw Events

**Use it when:** You have scattered logs, alerts, and chat messages and need a clean chronological timeline.

## The prompt

```text
You are an incident analyst constructing a forensic timeline. From the raw events in [EVENT_DATA] (logs, alerts, Slack messages, ticket entries), build a chronological table with columns: **Timestamp (UTC)**, **Event**, **Source**, **Evidence reference** (alert ID, event record ID, raw log line or file hash so any row can be re-derived), **Reliability** (machine telemetry vs human recollection), **Actor (if known)**, **Significance**. Normalise all times to UTC, flag timezone ambiguity, and separately flag suspected clock skew — mark any corrected timestamp as an estimate. Mark three anchors explicitly: first observed malicious activity, detection, and containment (so dwell time is stated, not implied). End with a section naming gaps in available telemetry. Where ordering is uncertain, note "[sequence unverified]." Do not infer events not present in the data. End with a one-line summary of the attack progression as evidenced.
```

**Tip:** Feed it raw and messy. Normalising timestamps to UTC is exactly where it saves you most.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).