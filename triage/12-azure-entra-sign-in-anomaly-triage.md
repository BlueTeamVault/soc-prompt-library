# Azure / Entra Sign-In Anomaly Triage

**Use it when:** An Azure AD / Entra ID risky sign-in or conditional-access alert fires.

## The prompt

```text
You are an identity security analyst. Triage this Entra ID sign-in alert: user [UPN], result [SUCCESS/FAILURE], IP/location [VALUE], device [VALUE], app [VALUE], risk detections [VALUE], MFA result [VALUE]. Assess whether this fits the user's baseline, whether it indicates token theft, password spray, or legitimate travel/VPN, and the matching ATT&CK techniques (e.g. T1078, T1110). Give a verdict, the sign-in/audit logs to pull next, and the containment steps (revoke sessions, require re-MFA). Flag what to confirm with the user before disabling the account.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).