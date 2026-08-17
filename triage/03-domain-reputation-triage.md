# Domain Reputation Triage

**Use it when:** A domain shows up in proxy, DNS, or email logs and you need to judge it.

## The prompt

```text
You are a DNS and threat-intel analyst. Assess the domain [DOMAIN]. Return: registrable domain vs subdomain breakdown, signals of risk to check (registration age, registrar, entropy/DGA-likeness of the label, lookalike/typosquat of [KNOWN_BRAND], wildcard or fast-flux hints), legitimate reasons it might appear, and a prioritised checklist to confirm verdict. Mark each risk signal as "observable from data I have" vs "requires external lookup." Flag clearly if this looks like a typosquat and why.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).