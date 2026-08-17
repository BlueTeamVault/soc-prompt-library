# Detect LSASS credential access (T1003.001)

**Use it when:** You want to detect credential dumping attempts against LSASS memory.

## The prompt

```text
You are an EDR detection engineer. Write detection logic in [QUERY_LANGUAGE] for LSASS memory access (ATT&CK T1003.001). Base it on handle/access events to `lsass.exe` (e.g., Sysmon Event ID 10, or EDR equivalents) with suspicious access rights from any **non-allowlisted** process — do NOT scope to "non-SYSTEM" processes, since credential dumping is typically performed by a SYSTEM-integrity process after escalation. Use **bitmask** logic against the granted access rights, not equality matching on literal values, and include the fork-and-dump path (PROCESS_CREATE_PROCESS, 0x0080) alongside the common read/query combinations. Output: (1) the detection, (2) required fields (`SourceImage`, `GrantedAccess`, `TargetImage`, `CallTrace`), (3) the telemetry prerequisite — confirm Sysmon/EDR is configured to emit ProcessAccess events for lsass, or the rule silently returns nothing forever, (4) assumptions, (5) false positives (AV, EDR, legitimate security and backup tooling) and an allowlist strategy keyed on signer and path. Note known evasions (handle duplication, direct syscalls, fork-and-dump) and their detection limits, including where `CallTrace` is the only partial answer.
```

**Tip:** Ask it to include the common known-good `SourceImage` allowlist (AV/EDR agents) as a starter lookup.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).