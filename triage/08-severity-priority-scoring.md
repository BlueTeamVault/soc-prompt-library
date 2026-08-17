# Severity & Priority Scoring

**Use it when:** You must assign or sanity-check a severity rating before queue ordering.

## The prompt

```text
You are a SOC triage lead. Score this alert for severity and priority. Inputs — alert: [ALERT_SUMMARY]; affected asset: [ASSET_ROLE_AND_CRITICALITY]; data sensitivity: [DATA]; exposure: [INTERNET_FACING_YES/NO]; exploitability/confidence: [NOTES]. Return: severity (1–5) and priority (P1–P4) with one-line justification each, the single biggest factor driving the score, what would raise or lower it by one level, and a recommended SLA. State assumptions and flag any input that materially changes the score if wrong.
```

**Tip:** Standardise the asset-criticality wording across the team so scores stay comparable.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).