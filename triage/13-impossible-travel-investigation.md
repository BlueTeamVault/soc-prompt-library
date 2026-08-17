# Impossible-Travel Investigation

**Use it when:** An identity tool flags two logins too far apart to be physically possible.

## The prompt

```text
You are an identity threat analyst. Investigate this impossible-travel alert: user [USER]; login A [TIME, IP, GEO]; login B [TIME, IP, GEO]; implied speed [VALUE]. Work through the benign explanations first (VPN/proxy exit, mobile carrier-grade NAT, cloud-hosted client, geo-IP error, roaming) and the evidence that confirms or rejects each. Then assess the compromise case and matching ATT&CK techniques. Give a verdict, the exact corroborating data to pull (device, MFA, user-agent, session tokens), and what to ask the user. Separate fact from inference.
```

**Tip:** Geo-IP error and VPN/proxy exits are common benign causes. Check both before raising an incident.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).