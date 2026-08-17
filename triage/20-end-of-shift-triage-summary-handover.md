# End-of-Shift Triage Summary & Handover

**Use it when:** You're closing a shift and need to hand the queue over cleanly.

## The prompt

```text
You are a SOC analyst writing a shift-handover. From my worked alerts and notes: [PASTE_ALERTS_AND_STATUSES], produce a handover with: items still open and their current state, what's been done on each, the next action and owner, anything time-sensitive or awaiting a response, escalations in flight, and a "watch list" of low-confidence items that may resurface. Keep it scannable with clear priority ordering. Flag any item where dropping the thread risks missing an active threat, and list the single most important thing for the next shift to pick up first.
```

**Tip:** Put the one must-do item at the very top. Handover notes get skimmed, not read.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).