# IP Address Enrichment Summary

**Use it when:** An alert references an external IP and you need fast context without ten browser tabs.

## The prompt

```text
You are a threat-intel analyst. For the IP [IP_ADDRESS], produce a structured enrichment brief: likely ASN/owner and hosting type (residential / cloud / VPS / Tor / CDN), typical legitimate uses of that hosting, what would make traffic to it suspicious in my environment, and the specific reputation checks I should run (with what a "bad" result looks like). Do not invent reputation scores or geolocation you cannot derive — clearly separate inference from verified fact and list what I must confirm in a TI source.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).