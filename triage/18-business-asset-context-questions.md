# Business & Asset Context Questions

**Use it when:** An alert's severity depends on context only the business or asset owner has.

## The prompt

```text
You are a SOC analyst gathering context to finalise triage. For this alert: [ALERT_SUMMARY] on asset [ASSET]/user [USER], generate the precise questions I should ask to resolve severity — covering asset criticality and data classification, whether the activity was authorised/expected, change-window or maintenance overlap, account ownership and role, and any known projects (pen-test, migration, new software) that could explain it. Group questions by who to ask (asset owner, IT, user, management). Flag which answers would most change the verdict.
```

**Tip:** A scheduled pen-test or migration explains a surprising share of "scary" alerts. Always ask.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).