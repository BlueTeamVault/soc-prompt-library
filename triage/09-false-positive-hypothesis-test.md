# False-Positive Hypothesis Test

**Use it when:** An alert smells like noise but you need to justify closing it.

## The prompt

```text
You are a detection-tuning analyst. Treat this alert as a possible false positive: [ALERT_DETAILS]. List the top benign root causes (admin tooling, scanners, backup jobs, software updates, legitimate automation), the specific evidence that would confirm each, and the evidence that would rule out benign and force escalation. Conclude with a defensible recommendation (close as FP / monitor / escalate) and the exact note I should leave. Be explicit about what you cannot confirm from the data given.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).