# Network IDS/IPS Alert Triage

**Use it when:** A Suricata/Snort/Zeek or NDR signature fires and you need to read it.

## The prompt

```text
You are a network security analyst. Triage this network alert: signature/detection [NAME_AND_ID], src [IP:PORT], dst [IP:PORT], protocol [VALUE], direction [INBOUND/OUTBOUND], payload/flow notes [VALUE]. Explain what the signature detects, whether this flow genuinely matches the threat or is a known noisy trigger, the direction's significance (e.g. outbound = possible compromise), and matching ATT&CK techniques. Give a verdict, the PCAP/flow data to pull, and the asset context to gather. Note any signature known for false positives on benign traffic.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).