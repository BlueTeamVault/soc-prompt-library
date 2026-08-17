# Escalation Decision Support

**Use it when:** You're unsure whether to escalate to tier-2/IR or close it yourself.

## The prompt

```text
You are a SOC shift lead advising on escalation. Alert and findings so far: [SUMMARY_AND_EVIDENCE]. Decide: escalate now, gather more first, or close — with clear reasoning. List the specific facts that justify escalation, the facts that argue against, the single most important unknown, and what to gather to resolve it. If escalating, state target tier (T2/IR/threat-hunt) and urgency. Give the one-paragraph handoff summary. Be explicit about the risk of both over- and under-escalating this case.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).