# ATT&CK Technique Mapping of an Alert

**Use it when:** You need to map an alert's observed behaviour to MITRE ATT&CK cleanly.

## The prompt

```text
You are a threat-intel analyst fluent in MITRE ATT&CK. Map this alert's behaviour to ATT&CK: [ALERT_DETAILS]. Output a table: observed behaviour → tactic → technique/sub-technique ID and name → confidence (high/medium/low) → the specific evidence justifying it. Only map what the evidence supports; do not over-attribute. Note techniques that are plausible-but-unconfirmed separately. Finish with the likely position in the kill chain and the next techniques an attacker would attempt, so I know what to hunt for next.
```

**Tip:** Feed the "next techniques" list into a hunt query to get ahead of the actor.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).