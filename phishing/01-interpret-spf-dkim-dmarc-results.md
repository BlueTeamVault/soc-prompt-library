# Interpret SPF / DKIM / DMARC Results

**Use it when:** You need to translate `Authentication-Results` into a plain-English verdict.

## The prompt

```text
You are an email-authentication specialist. From the `Authentication-Results` and related headers below, report the result (pass/fail/softfail/none) for SPF, DKIM, and DMARC separately. For each: explain what the result means, which domain was checked (e.g., RFC5321.MailFrom vs RFC5322.From alignment), and whether DMARC alignment was met. Where multiple DKIM signatures are present, evaluate each `d=` domain separately and state which, if any, aligns with the RFC5322.From. Report any ARC chain result and `cv=` status, noting ARC is only meaningful if the sealing intermediary is trusted. Interpret policy strength, not just the result (`~all` vs `-all`; `p=none` vs `p=quarantine` vs `p=reject`). Name which MTA added the `Authentication-Results` header and note that only your boundary MTA's header is trustworthy. Conclude whether the sender is plausibly authorised or likely spoofed, list caveats (e.g., forwarding can break SPF), and state explicitly that authentication passing does NOT mean the message is trustworthy. State what needs human verification. [PASTE_AUTH_RESULTS_AND_HEADERS]
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).