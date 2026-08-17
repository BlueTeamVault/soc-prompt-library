# C2 Beaconing Analysis

**Use it when:** A host shows repetitive outbound connections that may be command-and-control.

## The prompt

```text
You are a C2-detection analyst. Analyse possible beaconing from host [HOST] to [DEST]. Data: connection timestamps/intervals [PASTE], bytes per connection [VALUE], destination [IP/DOMAIN], user-agent/JA3 if known [VALUE]. Assess regularity (interval, jitter), data-volume symmetry, and destination reputation to judge whether this is C2 (T1071) vs benign polling (telemetry, updates, monitoring, sync). Give a beaconing-likelihood verdict with reasoning, the destinations to enrich, and the host-side checks. List the benign apps that mimic this pattern, and flag what needs PCAP confirmation.
```

**Tip:** Low jitter plus a long-lived, low-reputation destination is the strongest single tell. But confirm against software-update traffic.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).