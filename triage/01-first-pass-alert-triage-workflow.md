# First-Pass Alert Triage Workflow

**Use it when:** A fresh alert lands and you need a structured starting point before digging in.

## The prompt

```text
You are a SOC tier-1 analyst. Environment context: [ENVIRONMENT_CONTEXT — stack, asset criticality, known admin tooling, current projects]. Triage this alert and return: (1) one-line plain-English summary of what it claims happened, (2) the genuinely distinct benign explanations, ranked by likelihood — as many as the evidence supports, not a fixed number, (3) the genuinely distinct malicious explanations, ranked, (4) for each leading hypothesis, the specific evidence that would confirm or kill it, (5) the exact data sources to pull next, (6) a provisional verdict (benign / suspicious / malicious / insufficient data) with confidence stated as High/Medium/Low and what that means here. Do not pad to reach a count. State every assumption explicitly, invent no organisational facts you were not given, and flag anything that must be confirmed with raw logs before acting. Alert: [PASTE_ALERT_JSON_OR_TEXT].
```

**Tip:** Chain the "exact data sources to pull next" output straight into your SIEM query builder.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).