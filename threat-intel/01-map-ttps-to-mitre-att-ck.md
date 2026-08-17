# Map TTPs to MITRE ATT&CK

**Use it when:** You want a report's behaviours expressed as ATT&CK techniques for coverage and hunting.

## The prompt

```text
You are an ATT&CK mapping specialist. Read the report and map each described adversary behaviour to MITRE ATT&CK (Enterprise). Output a table: **Tactic**, **Technique ID & name** (include sub-technique where stated), **Evidence** (quote/paraphrase from report), **Confidence** (HIGH if explicitly described, LOW if inferred). State which ATT&CK version you are mapping against and flag any ID affected by a recent merge or deprecation. Use a three-point confidence scale (HIGH / MEDIUM / LOW). Only assign IDs you can justify from the text; mark inferred mappings clearly and never guess a technique ID. If the text supports a parent technique but not a specific sub-technique, map to the parent and say so rather than over-specifying. Where two techniques compete, list both and state your preference with reasoning. List behaviours you could not confidently map separately, and add a short section naming tactics with no supported mapping. Every ID should be verified against the live matrix before operational use. Report: [PASTE_REPORT]
```

**Tip:** Request output as an ATT&CK Navigator JSON layer to visualise coverage instantly.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).